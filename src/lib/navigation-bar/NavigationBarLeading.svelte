<script>
	export let state = 'enabled';
	/* export let state = "disabled"; */
	export let symbol = 'arrow_back_ios_new';
	export let label = 'Label';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;

	export let colorStyle = 'unset';
	if (state === 'enabled') {
		colorStyle = 'var(--colors-accent)';
	} else {
		colorStyle = 'var(--labels-quaternary)';
	}

	if (state === 'disabled') {
		onPress = undefined;
	}

	let inputElement = undefined;

	function handlePress() {
		if (onPress) {
			onPress();
		}
		inputElement.blur();
	}
</script>

<button bind:this={inputElement} {id} on:click={handlePress} style="{style}; color: {colorStyle}">
	<p class="symbol">{symbol}</p>
	<p class="body">{label}</p>
</button>

<style>
	button {
		align-items: center;
		display: flex;
		gap: 3px;
	}

	.symbol {
		font-feature-settings: 'ss16' on;
		font-size: calc(17px * var(--large-symbol-font-size-multiplier));
		font-weight: calc(590 / var(--large-symbol-font-size-multiplier));
		line-height: 22px;
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

	button:hover {
		opacity: var(--hover-opacity);
	}
</style>
