<script>
	export let inputGroup = 'page-control-button';
	export let state = 'default';
	/* export let state = 'selected'; */

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
			tabindex="0"
			type="radio"
		/>
	{:else}
		<input
			bind:this={inputElement}
			class="hidden-input"
			{id}
			name={inputGroup}
			on:click={handlePress}
			tabindex="0"
			type="radio"
		/>
	{/if}
</label>

<style>
	label {
		background: var(--labels-primary);
		border-radius: 50%;
		height: 8px;
		opacity: 30%;
		width: 8px;
	}

	label:has(> input:checked) {
		opacity: unset;
	}

	label:has(> input:focus) {
		outline: 4px solid var(--colors-accent-2);
	}
</style>
