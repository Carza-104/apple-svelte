<script>
	export let showPlatter = false;

	export let id = undefined;
	export let style = undefined;

	let backdropFilterStyle = 'unset';
	let backgroundStyle = 'unset';

	if (showPlatter) {
		backdropFilterStyle = '20px';
		backgroundStyle = 'var(--materials-ultrathin)';
	}
</script>

<div class="page-control" {id} {style}>
	<div
		class="platter"
		style="backdrop-filter: {backdropFilterStyle}; background: {backgroundStyle}; -webkit-backdrop-filter {backdropFilterStyle}"
	>
		<slot />
	</div>
</div>

<style>
	.page-control {
		align-items: center;
		display: flex;
		height: 44px;
		justify-content: center;
	}

	.platter {
		align-items: center;
		border-radius: 12px;
		display: flex;
		gap: 8px;
		justify-content: center;
		padding: 8px 12px;
		width: min-content;
	}
</style>
