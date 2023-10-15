<script>
	import { onMount } from 'svelte';

	export let state = 'default';
	/* export let state = "hidden"; */
	export let id = undefined;
	export let style = undefined;

	let windowHeight = undefined;
	let windowWidth = undefined;

	let heightStyle = '100vh';
	let maxWidthStyle = '320px';

	let backgroundHeightStyle = undefined;
	let backgroundWidthStyle = undefined;
	let backgroundDisplayStyle = undefined;

	$: {
		backgroundHeightStyle = `${windowHeight}px`;
		backgroundWidthStyle = `${windowHeight}px`;
		heightStyle = `${windowHeight}px`;

		if (windowWidth > 809) {
			backgroundDisplayStyle = 'none';
			if (state === 'default') {
				maxWidthStyle = '320px';
			} else {
				maxWidthStyle = '0px';
			}
		} else {
			if (state === 'default') {
				backgroundDisplayStyle = 'unset';
				maxWidthStyle = '320px';
			} else {
				backgroundDisplayStyle = 'none';
				maxWidthStyle = '0px';
			}
		}
	}

	$: {
		if (windowWidth <= 809) {
			state = 'hidden';
		} else {
			state = 'default';
		}
	}

	let usesWebKit = false;
	let elementClass = 'default';

	onMount(() => {
		if (navigator.userAgent.includes('WebKit')) {
			usesWebKit = true;
		}
		if (navigator.userAgent.includes('Windows')) {
			elementClass = 'windows';
		}
	});

	let backdropFilter = 'blur(50px)';

	/* Fix a WebKit issue that causes the backdrop filter to disappear. */
	$: {
		if (usesWebKit && state === 'default' && windowWidth <= 809) {
			setInterval(() => {
				backdropFilter = 'unset';
				setTimeout(() => {
					backdropFilter = 'blur(50px)';
				}, 1);
			}, 1);
		}
	}

	let inputElement = undefined;

	export function handlePress() {
		if (state === 'default') {
			state = 'hidden';
		} else {
			state = 'default';
		}
		inputElement.blur();
	}
</script>

<svelte:window
	bind:innerHeight={windowHeight}
	bind:innerWidth={windowWidth}
	on:keydown={(e) => {
		if (e.key === 'Escape' && windowWidth <= 809) state = 'hidden';
	}}
/>

<aside
	class={elementClass}
	{id}
	style="{style}; height: {heightStyle}; max-width: {maxWidthStyle}; transition: max-width 0.25s; -webkit-backdrop-filter: {backdropFilter}"
>
	<slot />
</aside>
<label
	style="display: {backgroundDisplayStyle}; height: {backgroundHeightStyle}; width: {backgroundWidthStyle}"
>
	<button bind:this={inputElement} class="hidden-input" on:click={handlePress} />
</label>

<style>
	label {
		cursor: unset;
		height: 100vh;
		left: 0px;
		position: fixed;
		top: 0px;
		width: 100vw;
		z-index: 1;
	}

	aside {
		background-color: var(--bg-grouped-primary);
		box-shadow: 0.5px 0px rgb(60, 60, 67, 0.36);
		float: left;
		height: 100vh;
		overflow-y: auto;
		position: sticky;
		top: 0px;
		width: 100%;
		z-index: 2;
	}

	#windows::-webkit-scrollbar {
		display: none;
	}

	@media (max-width: 809px) {
		aside {
			backdrop-filter: blur(50px);
			background: var(--materials-regular);
			background-blend-mode: var(--materials-background-blend-mode);
			float: unset;
			position: fixed;
			-webkit-backdrop-filter: blur(50px);
		}
	}

	@media (prefers-color-scheme: dark) {
		aside {
			box-shadow: 0.5px 0px rgb(84, 84, 88, 0.65);
		}
	}
</style>
