<script>
	export let showAccentColor = false;
	export let state = 'on';
	/* export let state = "off"; */

	export let id = undefined;
	export let style = undefined;

	let backgroundStyle = 'unset';
	let marginStyle = 'unset';
	$: {
		if (state === 'on') {
			if (showAccentColor) {
				backgroundStyle = 'var(--colors-accent)';
			} else {
				backgroundStyle = 'var(--colors-green)';
			}
			marginStyle = '0px 2px 0px calc(100% - 29px)';
		} else {
			backgroundStyle = 'var(--fills-secondary)';
			marginStyle = '0px 2px';
		}
	}

	function onTogglePress() {
		if (state === 'on') {
			state = 'off';
		} else {
			state = 'on';
		}
	}
</script>

<label style="{style}; background: {backgroundStyle}">
	{#if state === 'on'}
		<input
			checked
			class="hidden-input"
			{id}
			name="list-row-toggle-trailing"
			on:click={onTogglePress}
			type="checkbox"
		/>
	{:else}
		<input
			class="hidden-input"
			{id}
			name="list-row-toggle-trailing"
			on:click={onTogglePress}
			type="checkbox"
		/>
	{/if}
	<div style="margin: {marginStyle}" />
</label>

<style>
	label {
		align-items: center;
		background: var(--colors-green);
		border-radius: 15.5px;
		display: flex;
		height: 31px;
		overflow: hidden;
		transition: background 0.25s;
		width: 51px;
	}

	div {
		background: var(--grays-white);
		border-radius: 50%;
		box-shadow: 0px 3px 1px rgb(0, 0, 0, 0.06), 0px 3px 8px rgb(0, 0, 0, 0.15),
			0px 0px 0px 1px rgb(0, 0, 0, 0.04);
		height: 27px;
		margin: 0px 2px;
		transition: margin 0.25s;
		width: 27px;
	}

	input:active + div {
		background: var(--grays-white) !important;
		outline: unset !important;
	}

	input:focus + div {
		background: linear-gradient(var(--colors-accent-2) 0%, var(--colors-accent-2)),
			var(--grays-white);
		outline: 2px solid var(--colors-accent);
		outline-offset: -2px;
	}
</style>
