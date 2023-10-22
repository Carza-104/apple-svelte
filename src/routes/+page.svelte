<script>
	import '../lib/styles.css';
	import ActionSheet from "$lib/action-sheet/ActionSheet.svelte";
</script>

<main>
	<ActionSheet showCancelButton showDescription showHeader />
	<h1>apple-svelte</h1>
	<p>UI component library for Svelte based on Apple's Human Interface design language.</p>
</main>

<style>
	* {
		margin-block-end: 0px;
		margin-inline-end: 0px;
		margin-block-start: 0px;
		margin-inline-start: 0px;
	}

	main {
		display: flex;
		flex-direction: column;
		font-family: ui-sans-serif, 'SF Pro', Roboto, 'Fira Sans', Oxygen, Ubuntu, 'Segoe UI',
			'Helvetica Neue', 'Noto Sans', Arial, sans-serif;
		gap: 24px;
		padding: 16px;
	}
</style>
