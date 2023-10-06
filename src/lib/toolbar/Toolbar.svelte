<script>
	export let id = undefined;
	export let style = undefined;
</script>

<div {id} {style}>
	<slot />
</div>

<style>
	div {
		backdrop-filter: blur(10px);
		background: var(--materials-chrome);
		background-blend-mode: var(--materials-chrome-background-blend-mode);
		bottom: 0px;
		box-shadow: 0px -0.33px rgb(0, 0, 0, 0.3);
		display: flex;
		justify-content: space-between;
		padding: 13px 16px 42px;
		position: fixed;
		-webkit-backdrop-filter: blur(10px);
	}

	@media (prefers-color-scheme: dark) {
		div {
			box-shadow: 0px -0.33px rgb(255, 255, 255, 0.15);
		}
	}
</style>
