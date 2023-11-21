<script>
	export let state = 'enabled';
	/* export let state = "disabled"; */
	export let type = 'symbol';
	/* export let type = "label"; */
	/* export let type = "label-emphasized"; */
	export let symbol = 'select';
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

{#if type === 'symbol'}
	<button
		bind:this={inputElement}
		class="symbol"
		{id}
		on:click={handlePress}
		style="{style}; color: {colorStyle}">{symbol}</button
	>
{:else if type === 'label'}
	<button
		bind:this={inputElement}
		class="label"
		{id}
		on:click={handlePress}
		style="{style}; color: {colorStyle}">{label}</button
	>
{:else}
	<button
		bind:this={inputElement}
		class="label-emphasized"
		{id}
		on:click={handlePress}
		style="{style}; color: {colorStyle}">{label}</button
	>
{/if}

<style>
	.symbol {
		font-feature-settings: 'ss16' on;
		font-size: calc(17px * var(--large-symbol-font-size-multiplier));
		font-weight: calc(400 / var(--large-symbol-font-size-multiplier));
		line-height: 22px;
	}

	.label {
		font-size: 17px;
		font-weight: 400;
		line-height: 22px;
	}

	.label-emphasized {
		font-size: 17px;
		font-weight: 590;
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
