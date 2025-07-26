<script>
	export let value = undefined;
	export let min = '0';
	export let max = '100';
	export let showSymbols = false;
	export let minSymbol = 'wb_sunny';
	export let maxSymbol = 'sunny';

	export let id = undefined;
	export let style = undefined;

	let inputElement = undefined;

	function handlePress() {
		inputElement.blur();
	}
</script>

<label {style}>
	<div>
		{#if showSymbols}
			<p class="symbol">{minSymbol}</p>
		{/if}
		<input
			bind:this={inputElement}
			bind:value
			class="body"
			{id}
			{max}
			{min}
			on:click={handlePress}
			type="range"
		/>
		{#if showSymbols}
			<p class="symbol">{maxSymbol}</p>
		{/if}
	</div>
</label>

<style>
	label {
		align-items: center;
		background: var(--bg-grouped-secondary);
		display: flex;
		height: 52px;
		padding-left: 16px;
	}

	div {
		align-items: center;
		box-shadow: 0px 0.5px var(--separators-non-opaque);
		display: flex;
		flex: 1;
		flex-direction: row;
		gap: 12px;
		height: 100%;
		padding-right: 16px;
	}

	.symbol {
		align-items: center;
		color: var(--labels-secondary);
		display: flex;
		font-size: calc(17px * var(--medium-symbol-font-size-multiplier));
		font-weight: calc(590 / var(--medium-symbol-font-size-multiplier));
		height: 22px;
		justify-content: center;
		line-height: 22px;
		width: 22px;
	}

	input[type='range'] {
		appearance: none;
		align-items: center;
		border-radius: 6px;
		background: var(--fills-secondary);
		cursor: pointer;
		display: flex;
		height: 6px;
		width: 100%;
	}

	input[type='range']::-moz-range-thumb {
		appearance: none;
		background: var(--grays-white);
		border: none;
		border-radius: 24px;
		box-shadow: 0px 6px 13px rgb(0, 0, 0, 0.12), 0px 0.5px 4px rgb(0, 0, 0, 0.12);
		height: 24px;
		width: 38px;
	}

	input[type='range']::-webkit-slider-thumb {
		appearance: none;
		background: var(--grays-white);
		border-radius: 24px;
		box-shadow: 0px 6px 13px rgb(0, 0, 0, 0.12), 0px 0.5px 4px rgb(0, 0, 0, 0.12);
		height: 24px;
		width: 38px;
	}

	input[type='range']::-moz-range-progress {
		appearance: none;
		border-radius: 6px;
		background: var(--colors-accent);
		cursor: pointer;
		height: 6px;
		width: 100%;
	}

	label:last-child > div {
		border-bottom: unset;
	}

	input[type='range']:active::-moz-range-thumb,
	input[type='range']:active::-webkit-slider-thumb {
		background: var(--grays-white) !important;
		outline: unset !important;
	}

	input[type='range']:focus::-moz-range-thumb,
	input[type='range']:focus::-webkit-slider-thumb {
		background: linear-gradient(var(--colors-accent-2) 0%, var(--colors-accent-2)),
			var(--grays-white);
		outline: 2px solid var(--colors-accent);
		outline-offset: -2px;
	}
</style>
