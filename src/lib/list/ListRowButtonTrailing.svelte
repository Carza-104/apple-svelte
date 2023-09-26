<script>
	export let label = 'Button';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;
</script>

<button class="body" {id} on:click={onPress} {style}>{label}</button>

<style>
	button {
		color: var(--colors-accent);
	}
</style>
