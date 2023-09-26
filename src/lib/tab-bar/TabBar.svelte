<script>
	export let id = undefined;
	export let style = undefined;

	let paddingStyle = 'unset';
	if ($$slots['button-5']) {
		paddingStyle = '7px 15px 36px';
	} else if ($$slots['button-4']) {
		paddingStyle = '7px 24px 36px';
	} else {
		paddingStyle = '7px 42px 36px';
	}
</script>

<div {id} style="{style}; padding: {paddingStyle}">
	<slot name="button-1" />
	<slot name="button-2" />
	<slot name="button-3" />
	<slot name="button-4" />
	<slot name="button-5" state="selected" />
</div>

<style>
	div {
		backdrop-filter: blur(25px);
		background: var(--materials-chrome);
		background-blend-mode: var(--materials-chrome-background-blend-mode);
		bottom: 0px;
		box-shadow: 0px -0.33px rgb(0, 0, 0, 0.3);
		display: flex;
		justify-content: space-between;
		position: sticky;
		-webkit-backdrop-filter: blur(25px);
	}

	@media (prefers-color-scheme: dark) {
		div {
			box-shadow: 0px -0.33px rgb(255, 255, 255, 0.15);
		}
	}
</style>
