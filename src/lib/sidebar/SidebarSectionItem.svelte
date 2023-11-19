<script>
	export let inputGroup = 'sidebar-section-item';
	export let state = 'default';
	/* export let state = "selected"; */
	/* export let state = "selected-secondary"; */
	export let indentLevel = '0';
	/* export let indentLevel = "1"; */
	/* export let indentLevel = "2"; */
	/* export let indentLevel = "3"; */
	/* export let indentLevel = "4"; */
	export let showImage = false;
	export let imageType = 'symbol';
	/* export let imageType = "bitmap"; */
	/* export let imageType = "collection"; */
	export let symbol = 'star';
	export let image = undefined;
	export let imageAlt = '';
	export let title = 'Title';
	export let showSubtitle = false;
	export let subtitle = 'Subtitle';
	export let showDetail = false;
	export let detail = 'Detail';
	export let showTrailingSymbol = false;
	export let trailingSymbol = 'select';
	export let showDisclosure = false;
	export let disclosureState = 'open';
	/* export let disclosureState = "closed"; */
	export let disclosure = 'arrow_forward_ios';

	export let id = undefined;
	export let onPress = undefined;
	export let onTrailingSymbolPress = undefined;
	export let style = undefined;

	let paddingStyle = 'unset';
	if (indentLevel === '0') {
		paddingStyle = '0px 8px';
	} else if (indentLevel === '1') {
		paddingStyle = '0px 8px 0px 20px';
	} else if (indentLevel === '2') {
		paddingStyle = '0px 8px 0px 32px';
	} else if (indentLevel === '3') {
		paddingStyle = '0px 8px 0px 44px';
	} else if (indentLevel === '4') {
		paddingStyle = '0px 8px 0px 56px';
	}

	/* Instead of using conditional rendering with {#if} conditions, set the slot's display property to none to retain the state of variables like disclosureState. */
	let displayStyle = 'unset';
	let rotateStyle = '0.5turn';
	$: {
		if (showDisclosure) {
			if (disclosureState === 'open') {
				displayStyle = 'unset';
				rotateStyle = '0.25turn';
			} else {
				displayStyle = 'none';
				rotateStyle = 'unset';
			}
		}
	}

	let inputElement = undefined;

	function handlePress() {
		if (onPress) {
			onPress();
		}
		inputElement.blur();
	}

	function handleTrailingSymbolPress() {
		if (onTrailingSymbolPress) {
			onTrailingSymbolPress();
		}
		inputElement.blur();
	}

	function handleDisclosurePress() {
		if (disclosureState === 'open') {
			disclosureState = 'closed';
		} else {
			disclosureState = 'open';
		}
		inputElement.blur();
	}
</script>

<label class="item" style="{style}; padding: {paddingStyle}">
	{#if !showDisclosure}
		{#if state === 'default'}
			<input
				bind:this={inputElement}
				class="hidden-input"
				{id}
				name={inputGroup}
				on:click={handlePress}
				type="radio"
			/>
		{:else}
			<input
				bind:this={inputElement}
				checked
				class="hidden-input"
				{id}
				name={inputGroup}
				on:click={handlePress}
				type="radio"
			/>
		{/if}
	{/if}
	<div class="leading">
		{#if showImage}
			{#if imageType === 'symbol'}
				<p class="symbol primary">{symbol}</p>
			{:else if imageType === 'bitmap'}
				<img alt={imageAlt} src={image} />
			{:else}
				<div class="collection">
					<div class="rect" />
					<div class="rect" />
					<div class="rect" />
					<div class="rect" />
				</div>
			{/if}
		{/if}
		<div class="title-and-subtitle">
			<p class="title">{title}</p>
			{#if showSubtitle}
				<p class="subtitle">{subtitle}</p>
			{/if}
		</div>
	</div>
	<div class="trailing">
		{#if showDetail}
			<p class="detail">{detail}</p>
		{/if}
		{#if showTrailingSymbol}
			<button bind:this={inputElement} class="symbol secondary" on:click={handleTrailingSymbolPress}
				>{trailingSymbol}</button
			>
		{:else if showDisclosure}
			<button
				bind:this={inputElement}
				class="symbol tertiary"
				on:click={handleDisclosurePress}
				style="rotate: {rotateStyle}"
			>
				{disclosure}
			</button>
		{/if}
	</div>
</label>
<div class="slot" style="display: {displayStyle}">
	<slot />
</div>

<style>
	label {
		align-items: center;
		border-radius: 11px;
		display: flex;
		height: 44px;
		justify-content: space-between;
		margin: 0px 16px;
		white-space: nowrap;
	}

	label:has(> input:checked) {
		background: var(--fills-secondary);
	}

	.leading {
		align-items: center;
		display: flex;
		gap: 10px;
	}

	.primary {
		align-items: center;
		color: var(--colors-accent);
		display: flex;
		font-feature-settings: 'ss16' on;
		font-size: calc(17px * var(--large-symbol-font-size-multiplier));
		font-weight: calc(400 / var(--large-symbol-font-size-multiplier));
		line-height: 22px;
		height: 28px;
		justify-content: center;
		width: 28px;
	}

	img {
		border: 0.5px solid rgb(0, 0, 0, 0.06);
		border-radius: 6px;
		height: 28px;
		object-fit: cover;
		width: 28px;
	}

	.collection {
		border-radius: 3px;
		display: flex;
		flex-wrap: wrap;
		gap: 2px;
		height: 28px;
		overflow: hidden;
		width: 28px;
	}

	.rect {
		background: var(--fills-tertiary);
		height: 13px;
		width: 13px;
	}

	.title {
		font-size: 17px;
		font-weight: 400;
		line-height: 19px;
	}

	.subtitle {
		color: var(--labels-secondary);
		font-size: 13px;
		font-weight: 400;
		line-height: 17px;
	}

	.trailing {
		align-items: center;
		display: flex;
		gap: 8px;
	}

	.detail {
		color: var(--labels-secondary);
		font-size: 17px;
		font-weight: 400;
		line-height: 19px;
	}

	.secondary {
		color: var(--colors-accent);
		align-items: center;
		display: flex;
		font-feature-settings: 'ss16' on;
		font-size: calc(17px * var(--large-symbol-font-size-multiplier));
		font-weight: calc(400 / var(--large-symbol-font-size-multiplier));
		height: 22px;
		justify-content: center;
		line-height: 22px;
		width: 24px;
	}

	.tertiary {
		color: var(--colors-accent);
		font-feature-settings: 'ss15' on;
		font-size: calc(17px * var(--small-symbol-font-size-multiplier));
		font-weight: calc(590 / var(--small-symbol-font-size-multiplier));
		line-height: 22px;
		transition: rotate 0.25s;
	}

	label:active:has(input) {
		background: var(--press-overlay) !important;
		opacity: unset !important;
	}

	label:active {
		opacity: var(--symbol-press-opacity) !important;
	}

	label:focus {
		background: var(--colors-accent-2);
	}

	label:hover {
		opacity: var(--hover-opacity);
	}
</style>
