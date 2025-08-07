<script>
	export let showBackground = false;
	export let size = 'default';
	/* export let size = "large"; */
	/* export let showPrompt = false;
    export let prompt = "This is a prompt message."; */
	export let title = 'Title';

	export let id = undefined;
	export let style = undefined;

	let backdropFilterStyle = 'unset';
	let backgroundBlendModeStyle = 'unset';
	let backgroundStyle = 'unset';
	let borderBottomStyle = 'unset';
	if (showBackground) {
		backdropFilterStyle = 'blur(25px)';
		backgroundBlendModeStyle = 'var(--materials-chrome-background-blend-mode)';
		backgroundStyle = 'var(--materials-chrome)';
		borderBottomStyle = '0.33px solid var(--navigation-bar-border-bottom)';
	}
</script>

<div
	class="navigation-bar"
	{id}
	style="{style}; backdrop-filter: {backdropFilterStyle}; background-blend-mode: {backgroundBlendModeStyle}; background: {backgroundStyle}; border-bottom: {borderBottomStyle}; -webkit-backdrop-filter: {backdropFilterStyle}"
>
	<!-- {#if showPrompt}
        <p class="prompt">{prompt}</p>
    {/if} -->
	<div class="title-and-controls">
		<slot name="leading" />
		{#if size === 'default'}
			<p class="body-emphasized">{title}</p>
		{/if}
		<div class="trailing">
			<slot name="trailing-1" />
			<slot name="trailing-2" />
			<slot name="trailing-3" />
		</div>
	</div>
	{#if size === 'large'}
		<h1 class="large-title-emphasized">{title}</h1>
	{/if}
	<slot name="search-field" />
</div>

<style>
	:root {
		color-scheme: light dark;
		--navigation-bar-border-bottom: rgb(0, 0, 0, 0.3);
	}

	@media (prefers-color-scheme: dark) {
		:root {
			--navigation-bar-border-bottom: rgb(255, 255, 255, 0.15);
		}
	}

	.navigation-bar {
		display: flex;
		flex-direction: column;
	}

	.title-and-controls {
		align-items: center;
		display: flex;
		justify-content: space-between;
		padding: 11px 16px 11px 8px;
	}

	h1 {
		padding-left: 16px;
	}

	.trailing {
		display: flex;
		gap: 16px;
	}
</style>
