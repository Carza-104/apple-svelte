<script>
	export let showDetail = false;
	export let detail = 'Detail';
	export let showSymbol = false;
	export let symbol = 'star';
	export let showInfo = false;
	export let info = 'info';
	export let showCheckmark = false;
	export let checkmark = 'done';
	export let showDisclosure = false;
	export let disclosure = 'arrow_forward_ios';

	export let id = undefined;
	export let onDetailPress = undefined;
	export let onSymbolPress = undefined;
	export let onInfoPress = undefined;
	export let onCheckmarkPress = undefined;
	export let onDisclosurePress = undefined;
	export let style = undefined;

	let detailInputElement = undefined;

	function handleDetailPress() {
		if (onDetailPress) {
			onDetailPress();
		}
		detailInputElement.blur();
	}

	let symbolInputElement = undefined;

	function handleSymbolPress() {
		if (onSymbolPress) {
			onSymbolPress();
		}
		symbolInputElement.blur();
	}

	let infoInputElement = undefined;

	function handleInfoPress() {
		if (onInfoPress) {
			onInfoPress();
		}
		infoInputElement.blur();
	}

	let checkmarkInputElement = undefined;

	function handleCheckmarkPress() {
		if (onCheckmarkPress) {
			onCheckmarkPress();
		}
		checkmarkInputElement.blur();
	}

	let disclosureInputElement = undefined;

	function handleDisclosurePress() {
		if (onDisclosurePress) {
			onDisclosurePress();
		}
		disclosureInputElement.blur();
	}
</script>

<div {id} {style}>
	{#if showDetail}
		<button bind:this={detailInputElement} class="body" {id} on:click={handleDetailPress}
			>{detail}</button
		>
	{/if}
	{#if showSymbol}
		<button bind:this={symbolInputElement} class="symbol primary" {id} on:click={handleSymbolPress}
			>{symbol}</button
		>
	{/if}
	{#if showInfo}
		<button bind:this={infoInputElement} class="symbol primary" {id} on:click={handleInfoPress}
			>{info}</button
		>
	{/if}
	{#if showCheckmark}
		<button
			bind:this={checkmarkInputElement}
			class="symbol secondary"
			{id}
			on:click={handleCheckmarkPress}>{checkmark}</button
		>
	{/if}
	{#if showDisclosure}
		<button
			bind:this={disclosureInputElement}
			class="symbol tertiary"
			{id}
			on:click={handleDisclosurePress}>{disclosure}</button
		>
	{/if}
</div>

<style>
	div {
		align-items: center;
		display: flex;
		gap: 16px;
	}

	button:active {
		opacity: unset !important;
		outline: unset !important;
	}

	button:focus {
		border-radius: 5px;
		outline: 2px solid var(--colors-accent);
		outline-offset: 4px;
	}

	button:hover {
		opacity: var(--hover-opacity);
	}

	.body {
		color: var(--labels-secondary);
	}

	.primary {
		align-items: center;
		color: var(--colors-accent);
		display: flex;
		font-feature-settings: 'ss16' on;
		font-size: calc(17px * var(--large-symbol-font-size-multiplier));
		font-weight: calc(400 / var(--large-symbol-font-size-multiplier));
		height: 22px;
		justify-content: center;
		line-height: 22px;
		width: 18px;
	}

	.secondary {
		align-items: center;
		color: var(--colors-accent);
		display: flex;
		font-size: calc(17px * var(--medium-symbol-font-size-multiplier));
		font-weight: calc(590 / var(--medium-symbol-font-size-multiplier));
		height: 22px;
		justify-content: center;
		line-height: 22px;
		width: 18px;
	}

	.tertiary {
		color: var(--labels-tertiary);
		font-feature-settings: 'ss15' on;
		font-size: calc(17px * var(--small-symbol-font-size-multiplier));
		font-weight: calc(590 / var(--small-symbol-font-size-multiplier));
		line-height: 22px;
	}
</style>
