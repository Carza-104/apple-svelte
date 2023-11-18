<script>
	export let id = undefined;
	export let style = undefined;

	let amountOfButtons = undefined;
	let paddingStyle = 'unset';
	if ($$slots['button-5']) {
		amountOfButtons = 5;
		paddingStyle = '7px 15px 36px';
	} else if ($$slots['button-4']) {
		amountOfButtons = 4;
		paddingStyle = '7px 24px 36px';
	} else {
		if ($$slots['button-3']) {
			amountOfButtons = 3;
		} else if ($$slots['button-2']) {
			amountOfButtons = 2;
		} else {
			amountOfButtons = 1;
		}
		paddingStyle = '7px 42px 36px';
	}

	let amountOfPadding = undefined;
	if (amountOfButtons === 5) {
		amountOfPadding = '15px';
	} else if (amountOfButtons === 4) {
		amountOfPadding = '24px';
	} else {
		amountOfPadding = '42px';
	}

	let primaryInputElement = undefined;
	let secondaryInputElement = undefined;
	let tertiaryInputElement = undefined;
	let quaternaryInputElement = undefined;
	let quinaryInputElement = undefined;

	function handlePrimaryPress() {
		primaryInputElement.click();
	}

	function handleSecondaryPress() {
		secondaryInputElement.click();
	}

	function handleTertiaryPress() {
		tertiaryInputElement.click();
	}

	function handleQuaternaryPress() {
		quaternaryInputElement.click();
	}

	function handleQuinaryPress() {
		quinaryInputElement.click();
	}
</script>

<div {id} style="{style}; padding: {paddingStyle}">
	<label bind:this={primaryInputElement} id="primary">
		<slot name="button-1" />
	</label>
	<button
		on:click={handlePrimaryPress}
		style="transform: translateX(-{amountOfPadding}); width: calc(100% / {amountOfButtons})"
	/>
	{#if $$slots['button-2']}
		<label bind:this={secondaryInputElement} id="secondary">
			<slot name="button-2" />
		</label>
		<button
			on:click={handleSecondaryPress}
			style="transform: translateX(calc(100% - {amountOfPadding})); width: calc(100% / {amountOfButtons})"
		/>
	{/if}
	{#if $$slots['button-3']}
		<label bind:this={tertiaryInputElement} id="tertiary">
			<slot name="button-3" />
		</label>
		<button
			on:click={handleTertiaryPress}
			style="transform: translateX(calc(200% - {amountOfPadding})); width: calc(100% / {amountOfButtons})"
		/>
	{/if}
	{#if $$slots['button-4']}
		<label bind:this={quaternaryInputElement} id="quaternary">
			<slot name="button-4" />
		</label>
		<button
			on:click={handleQuaternaryPress}
			style="transform: translateX(calc(300% - {amountOfPadding})); width: calc(100% / {amountOfButtons})"
		/>
	{/if}
	{#if $$slots['button-5']}
		<label bind:this={quinaryInputElement} id="quinary">
			<slot name="button-5" />
		</label>
		<button
			on:click={handleQuinaryPress}
			style="transform: translateX(calc(400% - {amountOfPadding})); width: calc(100% / {amountOfButtons})"
		/>
	{/if}
</div>

<style>
	div {
		backdrop-filter: blur(25px);
		background: var(--materials-chrome);
		background-blend-mode: var(--materials-chrome-background-blend-mode);
		bottom: 0px;
		box-shadow: 0px -0.33px rgb(0, 0, 0, 0.3);
		display: flex;
		justify-content: space-between;
		position: fixed;
		-webkit-backdrop-filter: blur(25px);
	}

	@media (prefers-color-scheme: dark) {
		div {
			box-shadow: 0px -0.33px rgb(255, 255, 255, 0.15);
		}
	}

	button {
		height: 94px;
		position: absolute;
		margin-top: -7px;
		width: 48px;
		z-index: -1;
	}
</style>
