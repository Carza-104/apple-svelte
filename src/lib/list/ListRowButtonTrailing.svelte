<script>
	export let label = 'Button';

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

<button bind:this={inputElement} class="body" {id} on:click={handlePress} {style}>{label}</button>

<style>
	button {
		color: var(--colors-accent);
	}

	button:active {
		background: unset !important;
		opacity: unset !important;
		outline: unset !important;
	}

	button:focus {
		background: var(--colors-accent-2);
		border-radius: 5px;
		outline: 4px solid var(--colors-accent-2);
	}

	button:hover {
		opacity: var(--hover-opacity);
	}
</style>
