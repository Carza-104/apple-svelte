<script>
	export let id = undefined;
	export let style = undefined;
</script>

<div {id} {style}>
	<slot />
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
		padding: 7px 15px 36px;
		position: fixed;
		-webkit-backdrop-filter: blur(25px);
	}

	@media (prefers-color-scheme: dark) {
		div {
			box-shadow: 0px -0.33px rgb(255, 255, 255, 0.15);
		}
	}
</style>
