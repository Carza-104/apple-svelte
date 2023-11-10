<script>
	export let showHeading = false;
	export let heading = 'Section 1';
	export let state = 'open';
	/* export let state = "closed"; */
	export let openSymbol = 'keyboard_arrow_down';
	export let closedSymbol = 'arrow_forward_ios';

	export let id = undefined;
	export let style = undefined;

	let borderBottomStyle = 'unset';
	$: {
		if (state === 'open') {
			borderBottomStyle = 'unset';
		} else {
			borderBottomStyle = '0.33px solid var(--sidebar-section-border-bottom)';
		}
	}

	/* Instead of using conditional rendering with {#if} conditions, set the slot's display property to none to retain the state of variables like state. */
	let displayStyle = 'unset';
	$: {
		if (state === 'open') {
			displayStyle = 'unset';
		} else {
			displayStyle = 'none';
		}
	}

	let inputElement = undefined;

	function handlePress() {
		if (state === 'open') {
			state = 'closed';
		} else {
			state = 'open';
		}
		inputElement.blur();
	}
</script>

<section>
	{#if showHeading}
		<label {id} style="{style}; border-bottom: {borderBottomStyle}">
			<p>{heading}</p>
			<button bind:this={inputElement} class="symbol" on:click={handlePress}>
				{#if state === 'open'}
					{openSymbol}
				{:else}
					{closedSymbol}
				{/if}
			</button>
		</label>
	{/if}
	<div style="display: {displayStyle}">
		<slot />
	</div>
</section>

<style>
	:root {
		color-scheme: light dark;
		--sidebar-section-border-bottom: rgb(60, 60, 67, 0.29);
	}

	@media (prefers-color-scheme: dark) {
		:root {
			--sidebar-section-border-bottom: rgb(84, 84, 88, 0.65);
		}
	}

	section {
		padding-bottom: 12px;
	}

	label {
		align-items: center;
		display: flex;
		gap: 6px;
		height: 44px;
		justify-content: space-between;
		margin: 0px 16px;
		padding: 0px 8px;
	}

	p {
		font-size: 20px;
		font-weight: 590;
		line-height: 25px;
	}

	.symbol {
		color: var(--colors-accent);
		font-feature-settings: 'ss15' on;
		font-size: calc(17px * var(--small-symbol-font-size-multiplier));
		font-weight: calc(590 / var(--small-symbol-font-size-multiplier));
		line-height: 22px;
	}

	button:active,
	button:focus {
		opacity: var(--symbol-press-opacity) !important;
	}

	button:hover {
		opacity: var(--hover-opacity);
	}
</style>
