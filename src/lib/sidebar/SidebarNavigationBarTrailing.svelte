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
</script>

{#if type === 'symbol'}
	<button class="symbol" {id} on:click={onPress} style="{style}; color: {colorStyle}"
		>{symbol}</button
	>
{:else if type === 'label'}
	<button class="label" {id} on:click={onPress} style="{style}; color: {colorStyle}">{label}</button
	>
{:else}
	<button class="label-emphasized" {id} on:click={onPress} style="{style}; color: {colorStyle}"
		>{label}</button
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
</style>
