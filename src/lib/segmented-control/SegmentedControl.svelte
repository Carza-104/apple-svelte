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
		border-radius: 9px;
		display: flex;
		height: 24px;
		overflow: hidden;
		padding: 2px;
	}
</style>
