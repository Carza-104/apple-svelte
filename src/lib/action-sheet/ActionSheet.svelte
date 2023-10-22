<script>
	export let state = 'default';
	/* export let state = 'hidden'; */
	export let showHeader = false;
	export let headerTitle = 'Header Title';
	export let showDescription = false;
	export let headerDescription = 'A message should be a short, complete sentence.';
	export let showCancelButton = false;
	export let cancelButtonLabel = 'Cancel';

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
	<div class="action-sheet" {id} {style}>
		<div class="buttons">
			{#if showHeader}
				<div class="header">
					<p class="footnote-emphasized">{headerTitle}</p>
					{#if showDescription}
						<p class="footnote">{headerDescription}</p>
					{/if}
				</div>
			{/if}
			<slot />
		</div>
		{#if showCancelButton}
			<button class="cancel" on:click={handlePress}>
				<p class="body-emphasized">{cancelButtonLabel}</p>
			</button>
		{/if}
	</div>
</label>

<style>
	:root {
		color-scheme: light dark;
		--action-sheet-background: rgb(0, 0, 0, 0.4);
	}

	@media (prefers-color-scheme: dark) {
		:root {
			--action-sheet-background: rgb(0, 0, 0, 0.6);
		}
	}

	label {
		align-items: center;
		background: var(--action-sheet-background);
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

	.action-sheet {
		display: flex;
		flex: 1;
		flex-direction: column;
		gap: 8px;
		max-width: 377px;
	}

	.buttons {
		border-radius: 14px;
		overflow: hidden;
	}

	.buttons :first-child {
		border-top: unset;
	}

	.header {
		align-items: center;
		backdrop-filter: blur(40px);
		background: var(--materials-regular);
		display: flex;
		flex-direction: column;
		gap: 4px;
		padding: 12px 16px 12.5px;
		-webkit-backdrop-filter: blur(40px);
	}

	.footnote-emphasized {
		color: var(--labels-secondary);
	}

	.footnote {
		color: var(--labels-secondary);
	}

	.cancel {
		align-items: center;
		border-radius: 14px;
		backdrop-filter: blur(40px);
		background: var(--materials-regular);
		display: flex;
		height: 56px;
		justify-content: center;
		-webkit-backdrop-filter: blur(40px);
	}

	.body-emphasized {
		color: var(--colors-accent);
		width: 56px;
	}

	button:active,
	button:focus {
		background: linear-gradient(var(--press-overlay) 0%, var(--press-overlay)),
			var(--materials-regular);
	}
</style>
