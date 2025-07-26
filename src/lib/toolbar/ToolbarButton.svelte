<script>
	export let type = 'symbol';
	/* export let type = "label"; */
	export let symbol = 'select';
	export let label = 'Action';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;

	let inputElement = undefined;

	function handlePress() {
		if (onPress) {
			onPress();
		}
		inputElement.blur();
	}
</script>

<button bind:this={inputElement} {id} on:click={handlePress} {style}>
	{#if type === 'symbol'}
		<p class="symbol">{symbol}</p>
	{:else}
		<p class="label body">{label}</p>
	{/if}
</button>

<style>
	.symbol {
		align-items: center;
		color: var(--colors-accent);
		display: flex;
		font-feature-settings: 'ss16' on;
		font-size: calc(17px * var(--large-symbol-font-size-multiplier));
		font-weight: calc(400 / var(--large-symbol-font-size-multiplier));
		height: 28px;
		justify-content: center;
		width: 28px;
	}

	.label {
		color: var(--colors-accent);
	}

	button:active p {
		opacity: var(--symbol-press-opacity) !important;
		outline: unset !important;
	}

	button:focus p {
		border-radius: 5px;
		outline: 2px solid var(--colors-accent);
		outline-offset: 4px;
	}

	button:hover {
		opacity: var(--hover-opacity);
	}
</style>
