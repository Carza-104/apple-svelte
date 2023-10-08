<script>
	export let inputGroup = 'segmented-control-button';
	export let state = 'default';
	/* export let state = "selected"; */
	export let label = 'Label';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;
</script>

<div class="button">
	<label {style}>
		{#if state === 'default'}
			<input class="hidden-input" {id} name={inputGroup} on:click={onPress} type="radio" />
		{:else}
			<input checked class="hidden-input" {id} name={inputGroup} on:click={onPress} type="radio" />
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
		border-radius: 7px;
		display: flex;
		flex: 1;
		height: 100%;
		justify-content: center;
	}

	label:has(> input:checked) {
		background: var(--grays-white);
		border: 0.5px solid rgb(0, 0, 0, 0.04);
		box-shadow: 0px 3px 1px rgb(0, 0, 0, 0.04), 0px 3px 8px rgb(0, 0, 0, 0.12);
	}

	input:checked + p {
		font-size: 13px;
		font-weight: 590;
		line-height: 18px;
	}

	p {
		font-size: 13px;
		font-weight: 400;
		line-height: 18px;
		transition: all 0.25s;
	}

	.separator {
		background: rgb(142, 142, 147, 0.3);
		border-radius: 0.5px;
		height: 12px;
		width: 1px;
	}

	.button:last-child > .separator {
		display: none;
	}

	/* label:has(> input:checked) + .separator {
        display: none;
    } */

	label:active,
	label:focus {
		background: linear-gradient(var(--press-overlay) 0%, var(--press-overlay)),
			var(--fills-tertiary);
	}

	@media (prefers-color-scheme: dark) {
		label:has(> input:checked) {
			background: #636366;
			border: unset;
			box-shadow: unset;
		}
	}
</style>
