<script>
	export let size = 'small';
	/* export let size = "medium"; */
	/* export let size = "large"; */
	export let labelType = 'symbol-and-text';
	/* export let labelType = "symbol"; */
	/* export let labelType = "text"; */
	export let symbol = 'play_arrow';
	export let label = 'Play';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;

	let gapStyle = 'unset';
	let paddingStyle = 'unset';
	if (size === 'small') {
		gapStyle = '3px';
		paddingStyle = '4px 10px';
	} else if (size === 'medium') {
		gapStyle = '4px';
		paddingStyle = '7px 14px';
	} else {
		gapStyle = '4px';
		paddingStyle = '14px 20px';
	}

	let heightStyle = 'unset';
	let widthStyle = 'unset';
	if (labelType === 'symbol') {
		if (size === 'small') {
			heightStyle = '28px';
			widthStyle = '28px';
		} else if (size === 'medium') {
			heightStyle = '34px';
			widthStyle = '34px';
		} else {
			heightStyle = '50px';
			widthStyle = '50px';
		}
	}

	let inputElement = undefined;

	function handlePress() {
		if (onPress) {
			onPress();
		}
		inputElement.blur();
	}
</script>

<label>
	{#if labelType === 'symbol'}
		<button
			bind:this={inputElement}
			class="symbol-button liquid-glass liquid-glass-small"
			{id}
			on:click={handlePress}
			style="{style}; height: {heightStyle}; width: {widthStyle}"
		>
			{#if size === 'large'}
				<p class="symbol primary">{symbol}</p>
			{:else}
				<p class="symbol secondary">{symbol}</p>
			{/if}
		</button>
	{:else if labelType === 'text'}
		<button
			bind:this={inputElement}
			class="text-button liquid-glass liquid-glass-small"
			{id}
			on:click={handlePress}
			style="{style}; gap: {gapStyle}; padding: {paddingStyle}"
		>
			{#if size === 'large'}
				<p class="body">{label}</p>
			{:else}
				<p class="subheadline">{label}</p>
			{/if}
		</button>
	{:else}
		<button
			bind:this={inputElement}
			class="text-button liquid-glass liquid-glass-small"
			{id}
			on:click={handlePress}
			style="{style}; gap: {gapStyle}; padding: {paddingStyle}"
		>
			{#if size === 'large'}
				<p class="symbol primary">{symbol}</p>
				<p class="body">{label}</p>
			{:else}
				<p class="symbol secondary">{symbol}</p>
				<p class="subheadline">{label}</p>
			{/if}
		</button>
	{/if}
</label>

<style>
	.symbol-button {
		align-items: center;
		display: flex;
		justify-content: center;
		white-space: pre;
	}

	.primary {
		font-size: calc(17px * var(--medium-symbol-font-size-multiplier));
		font-weight: calc(400 / var(--medium-symbol-font-size-multiplier));
		line-height: 22px;
	}

	.text-button {
		align-items: center;
		display: flex;
		white-space: pre;
		width: min-content;
	}

	.secondary {
		font-size: calc(15px * var(--medium-symbol-font-size-multiplier));
		font-weight: calc(400 / var(--medium-symbol-font-size-multiplier));
		line-height: 20px;
	}

	button {
		border-radius: 50px;
	}

	button::before {
		border-radius: 50px;
	}

	button::after {
		border-radius: 50px;
	}

	button:active {
		background: linear-gradient(var(--press-overlay) 0%, var(--press-overlay)),
			var(--liquid-glass-small-bg) !important;
		opacity: unset !important;
		outline: unset !important;
	}

	button:focus {
		outline: 2px solid var(--colors-accent);
	}

	button:hover {
		opacity: var(--hover-opacity);
	}
</style>
