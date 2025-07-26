<script>
	export let showHeader = false;
	export let headerType = 'default';
	/* export let headerType = "plain"; */
	/* export let headerType = "prominent"; */
	export let header = 'Header text';
	export let detail = 'Detail';
	export let disclosure = 'arrow_forward_ios';
	export let showFooter = false;
	export let footer = 'Footer text';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;

	let marginTop = 'unset';
	if (showHeader) {
		marginTop = '18px';
	} else {
		marginTop = '24px';
	}

	let marginBottom = 'unset';
	if (showFooter) {
		marginBottom = '18px';
	} else {
		marginBottom = '24px';
	}
</script>

<div class="collection" {id} style="{style}; margin: {marginTop} 0px {marginBottom}">
	{#if showHeader}
		{#if headerType === 'default'}
			<p class="headline">{header}</p>
		{:else if headerType === 'plain'}
			<p class="title3-emphasized">{header}</p>
		{:else}
			<label class="header">
				{header}
				<div class="detail">
					<p class="body">{detail}</p>
					<button class="symbol" on:click={onPress}>{disclosure}</button>
				</div>
			</label>
		{/if}
	{/if}
	<div class="list">
		<slot />
	</div>
	{#if showFooter}
		<p class="footnote">{footer}</p>
	{/if}
</div>

<style>
	.headline {
		color: var(--labels-secondary);
		margin: 0px 16px 10px;
	}

	.title3-emphasized {
		margin: 0px 16px 5px;
	}

	.header {
		display: flex;
		font-size: 20px;
		font-weight: 590;
		justify-content: space-between;
		line-height: 25px;
		margin: 0px 16px 8px;
		text-size-adjust: none;
	}

	.detail {
		display: flex;
		gap: 4px;
	}

	.body {
		color: var(--labels-secondary);
	}

	.symbol {
		color: var(--colors-accent);
		font-feature-settings: 'ss15' on;
		font-size: calc(19px * var(--small-symbol-font-size-multiplier));
		font-weight: 590;
		line-height: 22px;
	}

	.list {
		border-radius: 10px;
		overflow: hidden;
	}

	.footnote {
		color: var(--labels-secondary);
		margin: 8px 16px 6px;
	}
</style>
