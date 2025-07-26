<script>
	export let decrement = 'remove';
	export let increment = 'add';

	export let id = undefined;
	export let onDecrementPress = undefined;
	export let onIncrementPress = undefined;
	export let style = undefined;

	let decrementInputElement = undefined;

	function handleDecrementPress() {
		if (onDecrementPress) {
			onDecrementPress();
		}
		decrementInputElement.blur();
	}

	let incrementInputElement = undefined;

	function handleIncrementPress() {
		if (onIncrementPress) {
			onIncrementPress();
		}
		incrementInputElement.blur();
	}
</script>

<div {id} class="stepper" {style}>
	<button bind:this={decrementInputElement} class="symbol" on:click={handleDecrementPress}
		>{decrement}</button
	>
	<div class="separator" />
	<button bind:this={incrementInputElement} class="symbol" on:click={handleIncrementPress}
		>{increment}</button
	>
</div>

<style>
	.stepper {
		align-items: center;
		background: var(--fills-tertiary);
		border-radius: 32px;
		display: flex;
		height: 32px;
		justify-content: space-evenly;
		overflow: hidden;
		width: 92px;
	}

	.symbol {
		align-items: center;
		color: var(--labels-primary);
		display: flex;
		font-size: calc(17px * var(--medium-symbol-font-size-multiplier));
		font-weight: calc(400 / var(--medium-symbol-font-size-multiplier));
		height: 100%;
		justify-content: center;
		line-height: 22px;
		width: 100%;
	}

	.symbol:active {
		opacity: var(--symbol-press-opacity) !important;
		outline: unset !important;
	}

	.symbol:focus {
		border-radius: 8px;
		outline: 2px solid var(--colors-accent);
		outline-offset: -2px;
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
