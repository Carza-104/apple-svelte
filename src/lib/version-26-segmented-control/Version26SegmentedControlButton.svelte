<script>
	export let inputGroup = 'segmented-control-button';
	export let state = 'default';
	/* export let state = "selected"; */
	export let label = 'Label';

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

<div class="button">
	<label {style}>
		{#if state === 'default'}
			<input
				bind:this={inputElement}
				class="hidden-input"
				{id}
				name={inputGroup}
				on:click={handlePress}
				type="radio"
			/>
		{:else}
			<input
				bind:this={inputElement}
				checked
				class="hidden-input"
				{id}
				name={inputGroup}
				on:click={handlePress}
				type="radio"
			/>
		{/if}
		<p>{label}</p>
	</label>
	<div class="separator" />
</div>

<style>
	.button {
		align-items: center;
		display: flex;
		flex: 1;
		height: 100%;
		justify-content: center;
	}

	label {
		align-items: center;
		border-radius: 28px;
		display: flex;
		flex: 1;
		height: 100%;
		justify-content: center;
		transition: transform 0.25s;
	}

	label:has(> input:checked) {
		background: var(--grays-white);
		border: 0.5px solid rgb(0, 0, 0, 0.04);
		box-shadow:
			0px 3px 1px rgb(0, 0, 0, 0.04),
			0px 3px 8px rgb(0, 0, 0, 0.12);
	}

	input:checked + p {
		font-size: 14px;
		font-weight: 590;
		line-height: 18px;
	}

	p {
		font-size: 14px;
		font-weight: 400;
		line-height: 18px;
		transition: all 0.25s;
	}

	.separator {
		background: rgb(142, 142, 147, 0.3);
		border-radius: 0.5px;
		height: 100%;
		width: 1px;
	}

	.button:last-child > .separator {
		display: none;
	}

	/* label:has(> input:checked) + .separator {
        display: none;
    } */

	input:not(:checked):hover + p {
		opacity: var(--hover-opacity);
	}

	label:active > p {
		opacity: var(--symbol-press-opacity);
	}

	label:active:has(input:checked) {
		background: var(--grays-white) !important;
	}

	label:active {
		background: unset !important;
		outline: unset !important;
	}

	label:has(input:active) {
		background: var(--grays-white) !important;
		outline: unset !important;
	}

	label:has(input:focus) {
		outline: 1.5px solid var(--colors-accent);
	}

	label:has(input:active) {
		background: unset !important;
	}

	label:has(input:checked:active) {
		background: var(--grays-white) !important;
	}

	.button:first-child > label {
		transform-origin: left;
	}

	.button:first-child:active > label {
		transform: scale(0.9581298332) translateX(0.5024420016px);
	}

	.button:active > label {
		transform: scale(0.9581298332);
	}

	.button:last-child > label {
		transform-origin: right;
	}

	.button:last-child:active > label {
		transform: scale(0.9581298332) translateX(-0.5024420016px);
	}

	@media (prefers-color-scheme: dark) {
		label:has(> input:checked) {
			background: #636366;
			border: unset;
			box-shadow: unset;
		}

		label:active:has(input:checked) {
			background: #636366 !important;
		}

		label:has(input:active) {
			background: #636366 !important;
			outline: unset !important;
		}

		label:has(input:checked:active) {
			background: #636366 !important;
		}
	}
</style>
