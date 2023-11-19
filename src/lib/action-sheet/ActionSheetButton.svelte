<script>
	export let state = 'default';
	/* export let state = 'destructive'; */
	/* export let state = 'disabled'; */
	export let label = 'Action';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;

	let colorStyle = 'unset';
	if (state === 'default') {
		colorStyle = 'var(--colors-accent)';
	} else if (state === 'destructive') {
		colorStyle = 'var(--colors-red)';
	} else {
		colorStyle = 'var(--grays-gray-2)';
	}

	if (state === 'disabled') {
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

<button bind:this={inputElement} {id} {style} on:click={handlePress}>
	<p class="body" style="color: {colorStyle}">{label}</p>
</button>

<style>
	button {
		align-items: center;
		backdrop-filter: blur(40px);
		background: var(--materials-regular);
		border-top: 0.33px solid var(--separators-non-opaque);
		display: flex;
		height: 56px;
		justify-content: center;
		-webkit-backdrop-filter: blur(40px);
		width: 100%;
	}

	button:last-child {
		border-bottom: 14px;
	}

	button:active {
		background: linear-gradient(var(--press-overlay) 0%, var(--press-overlay)),
			var(--materials-regular);
		border: unset !important;
		opacity: unset !important;
	}

	button:focus {
		border: 4px solid var(--colors-accent-2);
	}

	button:hover {
		opacity: var(--hover-opacity);
	}
</style>
