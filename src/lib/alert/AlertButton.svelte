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
		<button bind:this={inputElement} class="body" on:click={handlePress}>{label}</button>
	{:else}
		<button bind:this={inputElement} class="body-emphasized" on:click={handlePress}>{label}</button>
	{/if}
</label>

<style>
	label {
		align-items: center;
		border-top: 0.33px solid var(--separators-non-opaque);
		display: flex;
		height: 44px;
		justify-content: center;
	}

	button {
		color: var(--colors-accent);
	}

	label:active,
	label:focus {
		background: linear-gradient(var(--press-overlay) 0%, var(--press-overlay)),
			var(--materials-regular);
		opacity: unset !important;
	}

	button:hover {
		opacity: var(--hover-opacity);
	}
</style>
