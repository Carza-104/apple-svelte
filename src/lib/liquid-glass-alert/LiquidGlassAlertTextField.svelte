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
		background: var(--fills-secondary);
		border-radius: 26px;
		margin-bottom: 19px;
		padding: 16px;
		width: calc(100% - 28px);
	}

	input::placeholder {
		color: var(--labels-tertiary);
	}

	input:focus {
		background: linear-gradient(var(--press-overlay) 0%, var(--press-overlay)),
			var(--fills-secondary) !important;
	}
</style>
