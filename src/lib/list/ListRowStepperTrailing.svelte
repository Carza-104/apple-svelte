<script>
	export let decrement = 'remove';
	export let increment = 'add';

	export let id = undefined;
	export let onDecrementPress = undefined;
	export let onIncrementPress = undefined;
	export let style = undefined;

	let inputElement = undefined;

	function handleDecrementPress() {
		if (onDecrementPress) {
			onDecrementPress();
		}
		inputElement.blur();
	}

	function handleIncrementPress() {
		if (onIncrementPress) {
			onIncrementPress();
		}
		inputElement.blur();
	}
</script>

<div {id} class="stepper" {style}>
	<button bind:this={inputElement} class="symbol" on:click={handleDecrementPress}
		>{decrement}</button
	>
	<div class="separator" />
	<button bind:this={inputElement} class="symbol" on:click={handleIncrementPress}
		>{increment}</button
	>
</div>

<style>
	.stepper {
		align-items: center;
		background: var(--fills-tertiary);
		border-radius: 8px;
		display: flex;
		height: 32px;
		justify-content: space-evenly;
		width: 94px;
	}

	.symbol {
		color: var(--labels-primary);
		font-size: calc(17px * var(--medium-symbol-font-size-multiplier));
		font-weight: calc(400 / var(--medium-symbol-font-size-multiplier));
		line-height: 22px;
	}

	.symbol:active,
	.symbol:focus {
		opacity: var(--symbol-press-opacity);
	}

	.symbol:hover {
		opacity: var(--hover-opacity);
	}

	.separator {
		background: var(--labels-tertiary);
		border-radius: 0.5px;
		height: 18px;
		width: 1px;
	}
</style>
