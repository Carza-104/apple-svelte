<script>
	export let showDetail = false;
	export let detail = 'Detail';
	export let disclosure = 'arrow_forward_ios';

	export let id = undefined;
	export let onDetailPress = undefined;
	export let onDisclosurePress = undefined;
	export let style = undefined;

	let detailInputElement = undefined;

	function handleDetailPress() {
		if (onDetailPress) {
			onDetailPress();
		}
		detailInputElement.blur();
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
		<button bind:this={detailInputElement} class="body" on:click={onDetailPress}>{detail}</button>
	{/if}
	<button bind:this={disclosureInputElement} class="symbol" on:click={onDisclosurePress}
		>{disclosure}</button
	>
</div>

<style>
	div {
		align-items: center;
		display: flex;
		gap: 16px;
	}

	button:active,
	button:focus {
		opacity: unset !important;
	}

	button:hover {
		opacity: var(--hover-opacity);
	}

	.body {
		color: var(--labels-secondary);
	}

	.symbol {
		align-items: center;
		color: var(--colors-accent);
		display: flex;
		font-feature-settings: 'ss15' on;
		font-size: calc(17px * var(--small-symbol-font-size-multiplier));
		font-weight: calc(590 / var(--small-symbol-font-size-multiplier));
		height: 18.18px;
		justify-content: center;
		line-height: 25px;
		width: 11px;
	}
</style>
