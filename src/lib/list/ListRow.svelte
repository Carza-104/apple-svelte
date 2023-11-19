<script>
	export let height = 'regular';
	/* export let height = "tall"; */
	export let showEditButton = false;
	export let editButtonType = 'checkmark';
	/* export let editButtonType = "plus" */
	/* export let editButtonType = "minus" */
	export let checkmarkEditButtonState = 'default';
	/* export let checkmarkEditButtonState = "selected"; */
	export let checkmarkSymbol = 'done';
	export let plusSymbol = 'add';
	export let minusSymbol = 'remove';
	export let title = 'Title';
	export let showSubtitle = false;
	export let subtitle = 'Subtitle';

	export let id = undefined;
	export let checkmarkEditButtonId = undefined;
	export let onPlusPress = undefined;
	export let onMinusPress = undefined;
	export let style = undefined;

	let heightStyle = 'unset';
	if (height === 'regular') {
		heightStyle = '44px';
	} else {
		heightStyle = '60px';
	}

	let inputElement = undefined;

	function handleCheckmarkPress() {
		if (checkmarkEditButtonState === 'default') {
			checkmarkEditButtonState = 'selected';
		} else {
			checkmarkEditButtonState = 'default';
		}
		inputElement.blur();
	}

	function handlePlusPress() {
		if (onPlusPress) {
			onPlusPress();
		}
		inputElement.blur();
	}

	function handleMinusPress() {
		if (onMinusPress) {
			onMinusPress();
		}
		inputElement.blur();
	}
</script>

<label class="row" {id} style="{style}; height: {heightStyle}">
	{#if showEditButton}
		{#if editButtonType === 'checkmark'}
			{#if checkmarkEditButtonState === 'default'}
				<label class="default-edit-button">
					<input
						bind:this={inputElement}
						class="hidden-input"
						id={checkmarkEditButtonId}
						name="list-row"
						on:click={handleCheckmarkPress}
						type="checkbox"
					/>
				</label>
			{:else}
				<label class="symbol primary">
					{checkmarkSymbol}
					<input
						bind:this={inputElement}
						checked
						class="hidden-input"
						id={checkmarkEditButtonId}
						name="list-row"
						on:click={handleCheckmarkPress}
						type="checkbox"
					/>
				</label>
			{/if}
		{:else if editButtonType === 'plus'}
			<button bind:this={inputElement} class="symbol secondary" on:click={handlePlusPress}
				>{plusSymbol}</button
			>
		{:else}
			<button bind:this={inputElement} class="symbol tertiary" on:click={handleMinusPress}
				>{minusSymbol}</button
			>
		{/if}
	{/if}
	<slot name="image" />
	<div class="title-and-trailing-accessories">
		<div class="title-and-subtitle">
			<p class="body">{title}</p>
			{#if showSubtitle}
				{#if height === 'regular'}
					<p class="footnote">{subtitle}</p>
				{:else}
					<p class="subheadline">{subtitle}</p>
				{/if}
			{/if}
		</div>
		<slot name="trailing" />
	</div>
</label>

<style>
	.row {
		align-items: center;
		background: var(--bg-grouped-secondary);
		display: flex;
		gap: 12px;
		padding-left: 16px;
	}

	.default-edit-button {
		border: 1.5px solid var(--grays-gray-3);
		border-radius: 50%;
		height: 19px;
		margin: 1px 5px 1px 1px;
		width: 19px;
	}

	.primary {
		align-items: center;
		background: var(--colors-accent);
		border-radius: 50%;
		color: var(--grays-white);
		display: flex;
		flex-shrink: 0;
		font-feature-settings: 'ss15' on;
		font-size: calc(14.5px * var(--small-symbol-font-size-multiplier));
		font-weight: calc(590 / var(--small-symbol-font-size-multiplier));
		height: 22px;
		justify-content: center;
		line-height: 22px;
		margin: 1px 5px 1px 1px;
		width: 22px;
	}

	.secondary {
		align-items: center;
		background: var(--colors-green);
		border-radius: 50%;
		color: var(--grays-white);
		display: flex;
		flex-shrink: 0;
		font-feature-settings: 'ss15' on;
		font-size: calc(14.5px * var(--small-symbol-font-size-multiplier));
		font-weight: calc(590 / var(--small-symbol-font-size-multiplier));
		height: 22px;
		justify-content: center;
		line-height: 22px;
		margin: 1px 5px 1px 1px;
		width: 22px;
	}

	.tertiary {
		align-items: center;
		background: var(--colors-red);
		border-radius: 50%;
		color: var(--grays-white);
		display: flex;
		flex-shrink: 0;
		font-feature-settings: 'ss15' on;
		font-size: calc(14.5 * var(--small-symbol-font-size-multiplier));
		font-weight: calc(590 / var(--small-symbol-font-size-multiplier));
		height: 22px;
		justify-content: center;
		line-height: 22px;
		margin: 1px 5px 1px 1px;
		width: 22px;
	}

	.title-and-trailing-accessories {
		align-items: center;
		border-bottom: 0.5px solid var(--separators-non-opaque);
		display: flex;
		flex: 1;
		height: 100%;
		justify-content: space-between;
		padding-right: 16px;
	}

	.footnote {
		margin-top: -4px;
	}

	.subheadline {
		color: var(--labels-secondary);
	}

	.row:last-child > .title-and-trailing-accessories {
		border-bottom: unset;
	}

	.row:active {
		background: linear-gradient(var(--press-overlay) 0%, var(--press-overlay)),
			var(--bg-grouped-secondary) !important;
	}

	.row:focus {
		background: var(--colors-accent-2);
	}
</style>
