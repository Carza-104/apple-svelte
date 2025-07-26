<script>
	export let type = 'fill';
	/* export let type = "circular"; */
	/* export let type = "rounded"; */
	/* export let type = "symbol"; */
	export let image = undefined;
	export let imageAlt = '';
	export let symbol = 'star';

	export let id = undefined;
	export let style = undefined;

	let borderRadiusStyle = 'unset';
	let heightStyle = 'unset';
	let widthStyle = 'unset';
	if (type === 'fill') {
		heightStyle = '52px';
		widthStyle = '52px';
	} else if (type === 'circular') {
		borderRadiusStyle = '50%';
		heightStyle = '42px';
		widthStyle = '42px';
	} else if (type === 'rounded') {
		borderRadiusStyle = '7px';
		heightStyle = '30px';
		widthStyle = '30px';
	}
</script>

{#if type === 'symbol'}
	<p class="symbol">{symbol}</p>
{:else}
	<img
		alt={imageAlt}
		{id}
		src={image}
		style="{style}; border-radius: {borderRadiusStyle}; height: {heightStyle}; width: {widthStyle}"
	/>
{/if}

<style>
	.symbol {
		color: var(--colors-accent);
		font-feature-settings: 'ss16' on;
		font-size: calc(17px * var(--large-symbol-font-size-multiplier));
		font-weight: calc(400 / var(--large-symbol-font-size-multiplier));
		line-height: 22px;
	}

	img {
		object-fit: cover;
	}
</style>
