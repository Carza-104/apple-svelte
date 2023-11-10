<script>
	import NavigationBar from '$lib/navigation-bar/NavigationBar.svelte';
	import NavigationBarLeading from '$lib/navigation-bar/NavigationBarLeading.svelte';
	import NavigationBarTrailing from '$lib/navigation-bar/NavigationBarTrailing.svelte';
	import '../lib/styles.css';
</script>

<main>
	<NavigationBar>
		<NavigationBarLeading slot="leading" />
		<NavigationBarTrailing slot="trailing-1" />
	</NavigationBar>
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
