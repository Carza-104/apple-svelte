<script>
	export let value = undefined;
	export let searchSymbol = 'search';
	export let showPlaceholder = false;
	export let placeholder = 'Search';
	export let dictationSymbol = 'mic';
	export let cancelSymbol = 'cancel';
	export let cancelLabel = 'Cancel';

	export let id = undefined;
	export let style = undefined;

	let inputElement = undefined;

	function handleCancelPress() {
		value = undefined;
		inputElement.blur();
	}
</script>

<div class="search-field" {style}>
	<label>
		<p class="symbol primary">{searchSymbol}</p>
		{#if showPlaceholder}
			<input bind:value {id} type="text" />
		{:else}
			<input bind:value {id} {placeholder} type="text" />
		{/if}
		<p class="symbol secondary">{dictationSymbol}</p>
		<button class="symbol secondary" on:click={handleCancelPress}>{cancelSymbol}</button>
	</label>
	<button bind:this={inputElement} class="label" on:click={handleCancelPress}>{cancelLabel}</button>
</div>

<style>
	.search-field {
		align-items: center;
		display: flex;
		gap: 16px;
		margin: 1px 16px 15px;
	}

	label {
		align-items: center;
		background: var(--fills-tertiary);
		border-radius: 10px;
		display: flex;
		flex: 1;
		padding: 7px 8px;
	}

	.primary {
		color: var(--labels-secondary);
		font-size: calc(17px * var(--medium-symbol-font-size-multiplier));
		font-weight: calc(400 / var(--medium-symbol-font-size-multiplier));
		line-height: 22px;
		width: 25px;
	}

	input {
		display: flex;
		font-size: 17px;
		font-weight: 400;
		line-height: 22px;
		width: 100%;
	}

	input::placeholder {
		color: var(--labels-secondary);
	}

	.secondary {
		color: var(--labels-secondary);
		font-size: 17px;
		font-weight: 400;
		line-height: 22px;
	}

	.label {
		color: var(--colors-accent);
		font-size: 17px;
		font-weight: 400;
		line-height: 22px;
		transition: width 0.1s;
	}

	input:focus + .secondary {
		display: none;
	}

	input:not(:focus) + .secondary + .secondary {
		display: none;
	}

	label:has(input:not(:focus)) + .label {
		display: none;
	}

	button:active {
		opacity: var(--symbol-press-opacity) !important;
		outline: unset !important;
	}

	button:focus {
		border-radius: 5px;
		outline: 2px solid var(--colors-accent);
		outline-offset: 4px;
	}

	.symbol:hover {
		opacity: var(--hover-opacity);
	}
</style>
