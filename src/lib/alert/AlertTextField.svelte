<script>
	export let value = undefined;
	export let placeholder = 'Placeholder';

	export let id = undefined;
	export let onPress = undefined;
	export let style = undefined;
</script>

<input bind:value class="body" {id} on:click={onPress} {placeholder} {style} type="text" />

<style>
	:root {
		color-scheme: light dark;
		--alert-text-field-background: var(--grays-white);
		--alert-text-field-border: rgb(60, 60, 67, 0.29);
	}

	@media (prefers-color-scheme: dark) {
		:root {
			--alert-text-field-background: var(--bg-grouped-secondary);
			--alert-text-field-border: rgb(84, 84, 88, 0.65);
		}
	}

	input {
		background: var(--alert-text-field-background);
		border: 0.5px solid var(--alert-text-field-border);
		border-radius: 5px;
		margin-top: 14px;
		padding: 2px 6px;
		width: calc(100% - 12px);
	}

	input::placeholder {
		color: var(--labels-tertiary);
	}

	input:focus {
		background: var(--alert-text-field-background);
	}
</style>
