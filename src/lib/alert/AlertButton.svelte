<script>
	export let state = 'default';
	/* export let state = "preferred"; */
	export let label = 'Action';

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

<label {id} {style}>
	{#if state === 'default'}
		<button bind:this={inputElement} class="body" on:click={handlePress} tabindex="0"
			>{label}</button
		>
	{:else}
		<button bind:this={inputElement} class="body-emphasized" on:click={handlePress} tabindex="0"
			>{label}</button
		>
	{/if}
</label>

<style>
	label {
		align-items: center;
		background: var(--materials-regular);
		border-top: 0.33px solid var(--separators-non-opaque);
		display: flex;
		height: 44px;
		justify-content: center;
	}

	label:last-child {
		border-radius: 0px 0px 14px 14px;
	}

	button {
		color: var(--colors-accent);
	}

	label:active {
		background: linear-gradient(var(--press-overlay) 0%, var(--press-overlay)),
			var(--materials-regular);
		opacity: unset !important;
		outline: unset !important;
	}

	label:focus {
		outline: 4px solid var(--colors-accent-2);
		outline-offset: -4px;
	}

	label:hover {
		opacity: var(--hover-opacity);
	}
</style>
