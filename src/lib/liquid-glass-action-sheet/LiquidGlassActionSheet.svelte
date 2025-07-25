<script>
	export let state = 'default';
	/* export let state = 'hidden'; */
	export let headerTitle = 'Header Title';
	export let showDescription = false;
	export let headerDescription = 'A message should be a short, complete sentence.';

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
	<div class="action-sheet liquid-glass liquid-glass-medium" {id} {style}>
		<div class="header">
			<p class="headline">{headerTitle}</p>
			{#if showDescription}
				<p class="body">{headerDescription}</p>
			{/if}
		</div>
		<slot />
	</div>
</label>

<style>
	label {
		align-items: end;
		cursor: unset;
		display: flex;
		height: 100vh;
		justify-content: center;
		left: 0px;
		position: fixed;
		top: 0px;
		width: 100vw;
		z-index: 3;
	}

	.action-sheet {
		border-radius: 34px;
		box-shadow: 0px 0px 20px rgb(0, 0, 0, 0.08);
		display: flex;
		flex: 1;
		flex-direction: column;
		gap: 10px;
		margin: 14px;
		padding: 14px;
		width: 300px;
	}

	.action-sheet::before {
		border-radius: 34px;
	}

	.action-sheet::after {
		border-radius: 34px;
	}

	.header {
		display: flex;
		flex-direction: column;
		gap: 10px;
		padding: 8px 8px 24px;
	}
</style>
