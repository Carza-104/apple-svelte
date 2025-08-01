<script>
	export let id = undefined;
	export let style = undefined;
</script>

<div class="liquid-glass liquid-glass-medium" {id} {style}>
	<slot />
</div>

<style>
	div {
		border-radius: 66px;
		bottom: 0px;
		box-shadow: 0px -0.33px rgb(0, 0, 0, 0.3);
		display: flex;
		justify-content: space-between;
		margin: 16px 28px 32px;
		padding: 4px;
		position: fixed;
	}

	div::before {
		border-radius: 66px;
	}

	div::after {
		border-radius: 66px;
	}

	@media (prefers-color-scheme: dark) {
		div {
			box-shadow: 0px -0.33px rgb(255, 255, 255, 0.15);
		}
	}
</style>
