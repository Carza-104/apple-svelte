<script>
	export let type = 'enabled';
	/* export let type = "destructive"; */
	/* export let type = "disabled"; */
	export let label = 'Title';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;

	export let colorStyle = 'unset';
	if (type === 'enabled') {
		colorStyle = 'var(--colors-accent)';
	} else if (type === 'destructive') {
		colorStyle = 'var(--colors-red)';
	} else {
		colorStyle = 'var(--grays-gray-2)';
	}

	if (type === 'disabled') {
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

<label {id} {style}>
	<button bind:this={inputElement} class="body" on:click={handlePress} style="color: {colorStyle}"
		>{label}</button
	>
</label>

<style>
	label {
		align-items: center;
		background: var(--bg-grouped-secondary);
		display: flex;
		height: 52px;
		padding-left: 16px;
	}

	button {
		align-items: center;
		box-shadow: 0px 0.5px var(--separators-non-opaque);
		display: flex;
		flex: 1;
		height: 100%;
	}

	label:last-child > button {
		border-bottom: unset;
	}

	label:active {
		background: linear-gradient(var(--press-overlay) 0%, var(--press-overlay)),
			var(--bg-grouped-secondary) !important;
		opacity: unset !important;
	}

	button:active {
		opacity: unset;
		outline: unset !important;
	}

	button:focus {
		border-radius: 10px;
		outline: 2px solid var(--colors-accent);
		outline-offset: -2px;
	}

	button:hover {
		opacity: var(--hover-opacity);
	}
</style>
