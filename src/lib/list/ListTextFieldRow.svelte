<script>
	export let value = undefined;
	export let title = 'Title';
	export let placeholder = 'Value';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;
</script>

<label {style}>
	<div>
		<p class="body">{title}</p>
		<input bind:value class="body" {id} on:click={onPress} {placeholder} type="text" />
	</div>
</label>

<style>
	label {
		align-items: center;
		background: var(--bg-grouped-secondary);
		display: flex;
		height: 44px;
		padding-left: 16px;
	}

	div {
		align-items: center;
		border-bottom: 0.33px solid var(--separators-non-opaque);
		display: flex;
		flex: 1;
		height: 100%;
		padding-right: 16px;
	}

	p {
		width: 100px;
	}

	input {
		width: 100%;
	}

	input::placeholder {
		color: var(--labels-secondary);
	}

	label:last-child > div {
		border-bottom: unset;
	}
</style>
