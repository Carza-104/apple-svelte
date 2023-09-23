<!-- @format -->
<script>
    export let state = "enabled";
    /* export let state = "disabled"; */
    export let type = "symbol";
    /* export let type = "text"; */
    /* export let type = "text-emphasized"; */
    export let symbol = "select";
    export let label = "Label";

    export let id = undefined;
    export let onPress = undefined;
    export let style = undefined;

    export let colorStyle = "unset";
    if (state === "enabled") {
        colorStyle = "var(--colors-accent)";
    } else {
        colorStyle = "var(--labels-quaternary)";
    }

    if (state === "disabled") {
        onPress = undefined;
    }
</script>

<button {id} on:click={onPress} style="{style}; color: {colorStyle}">
    {#if type === "symbol"}
        <p class="symbol">{symbol}</p>
    {:else if type === "text"}
        <p class="text">{label}</p>
    {:else}
        <p class="text-emphasized">{label}</p>
    {/if}
</button>

<style>
    .symbol {
        font-feature-settings: "ss16" on;
        font-size: calc(17px * var(--large-symbol-font-size-multiplier));
        font-weight: calc(400 / var(--large-symbol-font-size-multiplier));
        line-height: 22px;
    }

    .text {
        font-size: 17px;
        font-weight: 400;
        line-height: 22px;
    }

    .text-emphasized {
        font-size: 17px;
        font-weight: 590;
        line-height: 22px;
    }
</style>
