<script>
	export let onMaterial = false;
	export let size = 'small';
	/* export let size = "medium"; */
	/* export let size = "large"; */
	export let state = 'enabled';
	/* export let state = "disabled"; */
	export let type = 'borderless';
	/* export let type = "bezeled-gray"; */
	/* export let type = "bezeled"; */
	/* export let type = "filled"; */
	export let labelType = 'symbol-and-text';
	/* export let labelType = "symbol"; */
	/* export let labelType = "text"; */
	export let symbol = 'play_arrow';
	export let label = 'Play';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;

	let borderRadiusStyle = 'unset';
	let gapStyle = 'unset';
	let paddingStyle = 'unset';
	if (size === 'small') {
		borderRadiusStyle = '40px';
		gapStyle = '3px';
		paddingStyle = '4px 10px';
	} else if (size === 'medium') {
		borderRadiusStyle = '40px';
		gapStyle = '4px';
		paddingStyle = '7px 14px';
	} else {
		borderRadiusStyle = '12px';
		gapStyle = '4px';
		paddingStyle = '14px 20px';
	}

	let backgroundStyle = 'unset';
	let colorStyle = 'unset';
	if (state === 'enabled') {
		if (type === 'borderless') {
			colorStyle = 'var(--colors-accent)';
		} else if (type === 'bezeled-gray') {
			backgroundStyle = 'var(--fills-tertiary)';
			colorStyle = 'var(--colors-accent)';
		} else if (type === 'bezeled') {
			backgroundStyle = 'var(--colors-accent-2)';
			colorStyle = 'var(--colors-accent)';
		} else {
			backgroundStyle = 'var(--colors-accent)';
			colorStyle = 'var(--grays-white)';
		}
	} else {
		/* For some reason, this section doesn't work. */
		if (type === 'borderless') {
			colorStyle = 'var(--labels-tertiary)';
		} else {
			if (onMaterial) {
				backgroundStyle = 'var(--background)';
				colorStyle = 'var(--labels-tertiary)';
			} else {
				backgroundStyle = 'var(--fills-tertiary)';
				colorStyle = 'var(--labels-tertiary)';
			}
		}
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

	if (state === 'disabled') {
		onPress = undefined;
	}
</script>

{#if labelType === 'symbol'}
	<button
		class="symbol-button"
		{id}
		on:click={onPress}
		style="{style}; background: {backgroundStyle}; color: {colorStyle}; height: {heightStyle}; width: {widthStyle}"
	>
		{#if size === 'large'}
			<p class="symbol primary">{symbol}</p>
		{:else}
			<p class="symbol secondary">{symbol}</p>
		{/if}
	</button>
{:else if labelType === 'text'}
	<button
		class="text-button"
		{id}
		on:click={onPress}
		style="{style}; background: {backgroundStyle}; border-radius: {borderRadiusStyle}; color: {colorStyle}; gap: {gapStyle}; padding: {paddingStyle}"
	>
		{#if size === 'large'}
			<p class="body">{label}</p>
		{:else}
			<p class="subheadline">{label}</p>
		{/if}
	</button>
{:else}
	<button
		class="text-button"
		{id}
		on:click={onPress}
		style="{style}; background: {backgroundStyle}; border-radius: {borderRadiusStyle}; color: {colorStyle}; gap: {gapStyle}; padding: {paddingStyle}"
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

<style>
	:root {
		color-scheme: light dark;
		--background: rgb(255, 255, 255, 0.12);
	}

	@media (prefers-color-scheme: dark) {
		:root {
			--background: rgb(118, 118, 128, 0.24);
		}
	}

	.symbol-button {
		align-items: center;
		border-radius: 50%;
		display: flex;
		justify-content: center;
	}

	.primary {
		font-size: calc(17px * var(--medium-symbol-font-size-multiplier));
		font-weight: calc(400 / var(--medium-symbol-font-size-multiplier));
		line-height: 22px;
	}

	.text-button {
		align-items: center;
		display: flex;
		width: min-content;
	}

	.secondary {
		font-size: calc(15px * var(--medium-symbol-font-size-multiplier));
		font-weight: calc(400 / var(--medium-symbol-font-size-multiplier));
		line-height: 20px;
	}
</style>
