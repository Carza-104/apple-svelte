<script>
	export let inputGroup = 'tab-bar-button';
	export let state = 'default';
	/* export let state = "selected"; */
	export let symbol = 'star';
	export let label = 'Tab';

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

<label {style}>
	{#if state === 'selected'}
		<input
			bind:this={inputElement}
			checked
			class="hidden-input"
			{id}
			name={inputGroup}
			on:click={handlePress}
			type="radio"
		/>
	{:else}
		<input
			bind:this={inputElement}
			class="hidden-input"
			{id}
			name={inputGroup}
			on:click={handlePress}
			type="radio"
		/>
	{/if}
	<p class="symbol">{symbol}</p>
	<p class="label">{label}</p>
</label>

<style>
	label {
		align-items: center;
		display: flex;
		flex-direction: column;
		gap: 7px;
		width: 48px;
	}

	input:checked ~ p {
		color: var(--colors-accent);
	}

	.symbol {
		color: #999;
		font-size: calc(18px * var(--medium-symbol-font-size-multiplier));
		font-weight: calc(510 / var(--medium-symbol-font-size-multiplier));
	}

	.label {
		color: #999;
		font-size: 10px;
		font-weight: 510;
	}

	input:active ~ p {
		opacity: var(--symbol-press-opacity) !important;
	}

	input:active ~ .symbol {
		background: unset !important;
		outline: unset !important;
	}

	input:focus ~ .symbol {
		background: var(--colors-accent-2);
		border-radius: 5px;
		outline: 4px solid var(--colors-accent-2);
	}

	input:hover {
		opacity: var(--hover-opacity);
	}
</style>
