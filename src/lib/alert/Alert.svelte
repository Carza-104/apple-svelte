<script>
	export let state = 'default';
	/* export let state = 'hidden'; */
	export let title = 'Title';
	export let showDescription = false;
	export let description = 'A message should be a short, complete sentence.';

	export let id = undefined;
	export let style = undefined;

	let windowHeight = undefined;
	let windowWidth = undefined;
	let heightStyle = '100vh';
	let widthStyle = '100vh';

	$: {
		heightStyle = `${windowHeight}px`;
		widthStyle = `${windowWidth}px`;
	}

	let displayStyle = 'flex';

	$: {
		if (state === 'default') {
			displayStyle = 'flex';
		} else {
			displayStyle = 'none';
		}
	}

	let inputElement = undefined;

	function handlePress() {
		state = 'hidden';
		inputElement.blur();
	}
</script>

<svelte:window
	bind:innerHeight={windowHeight}
	bind:innerWidth={windowWidth}
	on:keydown={(e) => {
		if (e.key === 'Escape') state = 'hidden';
	}}
/>

<label style="display: {displayStyle}; height: {heightStyle}; width: {widthStyle}">
	<button bind:this={inputElement} class="hidden-input" on:click={handlePress} />
	<div class="alert" {id} {style}>
		<div class="title-and-description">
			<p class="headline">{title}</p>
			{#if showDescription}
				<p class="footnote">{description}</p>
			{/if}
			<slot name="text-field" />
		</div>
		<div class="buttons">
			<slot name="button-1" />
			<slot name="button-2" />
			<slot name="button-3" />
		</div>
	</div>
</label>

<style>
	:root {
		color-scheme: light dark;
		--background: rgb(0, 0, 0, 0.4);
	}

	@media (prefers-color-scheme: dark) {
		:root {
			--background: rgb(0, 0, 0, 0.6);
		}
	}

	label {
		align-items: center;
		background: var(--background);
		cursor: unset;
		display: flex;
		height: 100vh;
		justify-content: center;
		left: 0px;
		padding: 34px 8px;
		position: fixed;
		top: 0px;
		width: 100vw;
		z-index: 3;
	}

	.alert {
		backdrop-filter: blur(40px);
		background: var(--materials-regular);
		border-radius: 14px;
		display: flex;
		flex: 1;
		flex-direction: column;
		gap: 2px;
		justify-content: center;
		max-width: 270px;
		overflow: hidden;
		-webkit-backdrop-filter: blur(40px);
	}

	.title-and-description {
		display: flex;
		flex: 1;
		flex-direction: column;
		gap: 2px;
		padding: 19px 16px 15px;
	}

	p {
		text-align: center;
	}
</style>
