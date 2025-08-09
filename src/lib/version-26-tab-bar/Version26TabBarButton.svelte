<script>
	export let behavior = 'default';
	/* export let behavior = 'hyperlink'; */
	export let href = '/';
	export let inputGroup = 'tab-bar-button';
	export let state = 'default';
	/* export let state = "selected"; */
	export let symbol = 'star';
	export let label = 'Tab';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;

	let inputElement = undefined;

	function handlePress() {
		if (onPress) {
			onPress();
		}
		if (behavior === 'hyperlink') {
			let anchor = document.createElement('a');
			anchor.href = href;
			anchor.classList.add('hidden-input');
			document.body.appendChild(anchor);
			anchor.click();
		}
		inputElement.blur();
	}
</script>

<label {style}>
	{#if state === 'selected'}
		<input
			bind:this={inputElement}
			checked
			class="hidden-input"
			{id}
			name={inputGroup}
			on:click={handlePress}
			type="radio"
		/>
	{:else}
		<input
			bind:this={inputElement}
			class="hidden-input"
			{id}
			name={inputGroup}
			on:click={handlePress}
			type="radio"
		/>
	{/if}
	<div>
		<p class="symbol">{symbol}</p>
		<p class="label">{label}</p>
	</div>
</label>

<style>
	label {
		align-items: center;
		border-radius: 58px;
		display: flex;
		flex-direction: column;
		/* min-width: 102px; */
		padding: 6px 8px 7px;
		width: 100%;
	}

	label:has(input:checked) {
		background: var(--fills-tertiary);
	}

	/* label:first-child {
		align-items: start;
		width: calc(24px + 50%);
	}

	label:last-child {
		align-items: end;
		width: calc(24px + 50%);
	} */

	div {
		align-items: center;
		display: flex;
		flex-direction: column;
		gap: 1px;
		width: 48px;
	}

	input:checked ~ div > p {
		color: var(--colors-accent);
	}

	.symbol {
		color: var(--labels-primary);
		font-size: calc(18px * var(--medium-symbol-font-size-multiplier));
		font-weight: calc(510 / var(--medium-symbol-font-size-multiplier));
	}

	.label {
		color: var(--labels-primary);
		font-size: 10px;
		font-weight: 510;
	}

	input:active ~ div > p {
		opacity: var(--symbol-press-opacity) !important;
	}

	input:active ~ div > .symbol {
		outline: unset !important;
	}

	input:focus ~ div > .symbol {
		border-radius: 5px;
		outline: 2px solid var(--colors-accent);
		outline-offset: 2px;
	}

	label:hover {
		opacity: var(--hover-opacity);
	}
</style>
