<script>
	export let type = 'symbol';
	/* export let type = "label"; */
	export let symbol = 'select';
	export let label = 'Action';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;
</script>

<button {id} on:click={onPress} {style}>
	{#if type === 'symbol'}
		<p class="symbol">{symbol}</p>
	{:else}
		<p class="label">{label}</p>
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
		font-size: 17px;
		font-weight: 400;
		line-height: 22px;
	}

	button:active p {
		opacity: var(--symbol-press-opacity);
	}

	button:focus p {
		opacity: var(--symbol-press-opacity);
	}
</style>
