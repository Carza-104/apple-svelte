<script>
	export let symbol = 'select';

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

<button
	bind:this={inputElement}
	class="liquid-glass liquid-glass-small"
	{id}
	on:click={handlePress}
	{style}
>
	<p class="symbol">{symbol}</p>
</button>

<style>
	button {
		align-items: center;
		border-radius: 50%;
		display: flex;
		height: 48px;
		justify-content: center;
		width: 48px;
	}

	button::before {
		border-radius: 50%;
	}

	button::after {
		border-radius: 50%;
	}

	.symbol {
		align-items: center;
		color: var(--colors-accent);
		display: flex;
		font-feature-settings: 'ss16' on;
		font-size: calc(17px * var(--large-symbol-font-size-multiplier));
		font-weight: calc(400 / var(--large-symbol-font-size-multiplier));
		justify-content: center;
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
