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
		display: flex;
		justify-content: space-between;
		margin: 16px 28px 32px;
		padding: 4px;
		position: fixed;
		width: calc(100vw - 96px);
	}

	div::before {
		border-radius: 66px;
	}

	div::after {
		border-radius: 66px;
	}
</style>
