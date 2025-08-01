<script>
	export let id = undefined;
	export let style = undefined;
</script>

<div {id} {style}>
	<slot />
</div>

<style>
	div {
		bottom: 0px;
		display: flex;
		justify-content: space-between;
		padding: 4px 16px 36px;
		position: fixed;
	}
</style>
