<!-- @format -->
<script>
    export let state = "default";
    /* export let state = "selected"; */
    export let symbol = "star";
    export let label = "Tab";

    export let id = undefined;
    export let onPress = undefined;
    export let style = undefined;
</script>

<label {style}>
    {#if state === "selected"}
        <input
            checked
            class="hidden-input"
            {id}
            name="tab-bar-button"
            on:click={onPress}
            type="radio"
        />
    {:else}
        <input
            class="hidden-input"
            {id}
            name="tab-bar-button"
            on:click={onPress}
            type="radio"
        />
    {/if}
    <p class="symbol">{symbol}</p>
    <p class="label">{label}</p>
</label>

<style>
    label {
        align-items: center;
        display: flex;
        flex-direction: column;
        gap: 7px;
        width: 48px;
    }

    input:checked ~ p {
        color: var(--colors-accent);
    }

    .symbol {
        color: #999;
        font-size: calc(18px * var(--medium-symbol-font-size-multiplier));
        font-weight: calc(510 / var(--medium-symbol-font-size-multiplier));
    }

    .label {
        color: #999;
        font-size: 10px;
        font-weight: 510;
    }
</style>
