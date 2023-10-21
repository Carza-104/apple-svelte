<script>
	export let value = undefined;
	export let placeholder = 'Placeholder';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;
</script>

<input bind:value class="body" {id} on:click={onPress} {placeholder} {style} type="text" />

<style>
	input {
		background: var(--grays-white);
		border: 0.5px solid rgb(60, 60, 67, 0.29);
		border-radius: 5px;
		margin-top: 14px;
		padding: 2px 6px;
		width: calc(100% - 12px);
	}

	input::placeholder {
		color: var(--labels-tertiary);
	}
</style>
