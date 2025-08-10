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
			marginStyle = '0px 2px 0px calc(100% - 41px)';
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

<svg style="display: none" xmlns="http://www.w3.org/2000/svg">
	<filter height="100%" id="displacementDistortionFilter" width="100%" x="0px" y="0px">
		<!-- <feImage href="%sveltekit.assets%/filter.svg" result="colorMap" /> -->
		<feDisplacementMap
			in="SourceGraphic"
			in2="colorMap"
			scale="50"
			xChannelSelector="R"
			yChannelSelector="G"
		/>
	</filter>
</svg>
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
	<div style="margin: {marginStyle}"></div>
</label>

<style>
	label {
		align-items: center;
		background: var(--colors-green);
		border-radius: 28px;
		display: flex;
		height: 28px;
		overflow: hidden;
		transition: background 0.25s;
		width: 64px;
	}

	div {
		background: var(--grays-white);
		border-radius: 24px;
		box-shadow:
			0px 3px 1px rgb(0, 0, 0, 0.06),
			0px 3px 8px rgb(0, 0, 0, 0.15),
			0px 0px 0px 1px rgb(0, 0, 0, 0.04);
		height: 24px;
		margin: 0px 2px;
		transition: margin 0.25s;
		width: 39px;
	}

	label:has(input:active) {
		overflow: unset;
	}

	input:active + div {
		-webkit-backdrop-filter: blur(calc(5px + var(--liquid-glass-small-background-blur-addend) / 2));
		backdrop-filter: blur(calc(5px + var(--liquid-glass-small-background-blur-addend) / 2));
		background: var(--liquid-glass-small-bg);
		outline: unset !important;
		transform: scale(1.5);
		transition: transform 0.25s ease;
	}

	@supports (-webkit-app-region: inherit) {
		input:active + div {
			backdrop-filter: blur(calc(var(--liquid-glass-small-background-blur-addend) / 2))
				url(#displacementDistortionFilter);
		}
	}

	input:focus + div {
		background:
			linear-gradient(var(--colors-accent-2) 0%, var(--colors-accent-2)), var(--grays-white);
		outline: 2px solid var(--colors-accent);
		outline-offset: -2px;
	}
</style>
