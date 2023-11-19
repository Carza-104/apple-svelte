<script>
	export let symbol = 'add';
	export let title = 'Add Item';

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

<label {id} {style}>
	<button aria-label="Add item" bind:this={inputElement} class="symbol" on:click={handlePress}
		>{symbol}</button
	>
	<p>{title}</p>
</label>

<style>
	label {
		align-items: center;
		border-radius: 11px;
		display: flex;
		gap: 8px;
		height: 44px;
		margin: 0px 16px;
		padding: 0px 8px;
		white-space: nowrap;
	}

	.symbol {
		align-items: center;
		background: var(--fills-tertiary);
		border-radius: 3px;
		color: var(--colors-accent);
		display: flex;
		flex-shrink: 0;
		font-size: calc(17px * var(--medium-symbol-font-size-multiplier));
		font-weight: calc(590 / var(--medium-symbol-font-size-multiplier));
		line-height: 22px;
		height: 28px;
		justify-content: center;
		width: 28px;
	}

	p {
		font-size: 17px;
		font-weight: 400;
		line-height: 19px;
	}

	label:active {
		background: unset !important;
		opacity: var(--symbol-press-opacity) !important;
	}

	label:focus {
		background: var(--colors-accent-2);
	}

	label:hover {
		opacity: var(--hover-opacity);
	}
</style>
