<script>
	export let state = 'primary';
	/* export let state = 'secondary'; */
	/* export let state = 'destructive'; */
	export let label = 'Action';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;

	let backgroundStyle = 'unset';
	let colorStyle = 'unset';
	let mixBlendMode = 'unset';
	if (state === 'primary') {
		backgroundStyle = 'var(--colors-accent)';
		colorStyle = '#fff';
		mixBlendMode = 'unset';
	} else if (state === 'secondary') {
		backgroundStyle = 'var(--fills-secondary)';
		colorStyle = 'var(--labels-primary)';
		mixBlendMode = 'var(--liquid-glass-tertiary-blend-mode)';
	} else {
		backgroundStyle = 'var(--fills-secondary)';
		colorStyle = 'var(--colors-red)';
		mixBlendMode = 'var(--liquid-glass-tertiary-blend-mode)';
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

<button
	bind:this={inputElement}
	{id}
	style="{style}; background: {backgroundStyle}; color: {colorStyle}; mix-blend-mode: {mixBlendMode}"
	on:click={handlePress}
>
	<p class="body">{label}</p>
</button>

<style>
	button {
		align-items: center;
		border-radius: 54px;
		display: flex;
		justify-content: center;
		padding: 16px 13px;
		/* width: 100%; */
	}

	button:active {
		background: linear-gradient(var(--press-overlay) 0%, var(--press-overlay)),
			var(--fills-secondary) !important;
		border: unset !important;
		opacity: unset !important;
	}

	button:focus {
		border: 2px solid var(--colors-accent);
	}

	button:hover {
		opacity: var(--hover-opacity);
	}
</style>
