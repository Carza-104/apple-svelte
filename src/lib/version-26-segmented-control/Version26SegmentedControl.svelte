<script>
	export let id = undefined;
	export let style = undefined;
</script>

<div {id} {style}>
	<slot />
</div>

<style>
	div {
		align-items: center;
		background: var(--fills-tertiary);
		border-radius: 36px;
		display: flex;
		height: 36px;
		overflow: hidden;
		padding: 4px;
	}
</style>
