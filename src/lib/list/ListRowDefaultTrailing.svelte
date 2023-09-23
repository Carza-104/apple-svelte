<!-- @format -->
<script>
    export let showDetail = false;
    export let detail = "Detail";
    export let showSymbol = false;
    export let symbol = "star";
    export let showInfo = false;
    export let info = "info";
    export let showCheckmark = false;
    export let checkmark = "done";
    export let showDisclosure = false;
    export let disclosure = "arrow_forward_ios";

    export let id = undefined;
    export let onDetailPress = undefined;
    export let onSymbolPress = undefined;
    export let onInfoPress = undefined;
    export let onCheckmarkPress = undefined;
    export let onDisclosurePress = undefined;
    export let style = undefined;
</script>

<div {id} {style}>
    {#if showDetail}
        <button class="body" {id} on:click={onDetailPress}>{detail}</button>
    {/if}
    {#if showSymbol}
        <button class="symbol primary" {id} on:click={onSymbolPress}
            >{symbol}</button
        >
    {/if}
    {#if showInfo}
        <button class="symbol primary" {id} on:click={onInfoPress}
            >{info}</button
        >
    {/if}
    {#if showCheckmark}
        <button class="symbol secondary" {id} on:click={onCheckmarkPress}
            >{checkmark}</button
        >
    {/if}
    {#if showDisclosure}
        <button class="symbol tertiary" {id} on:click={onDisclosurePress}
            >{disclosure}</button
        >
    {/if}
</div>

<style>
    div {
        align-items: center;
        display: flex;
        gap: 16px;
    }

    .body {
        color: var(--labels-secondary);
    }

    .primary {
        align-items: center;
        color: var(--colors-accent);
        display: flex;
        font-feature-settings: "ss16" on;
        font-size: calc(17px * var(--large-symbol-font-size-multiplier));
        font-weight: calc(400 / var(--large-symbol-font-size-multiplier));
        height: 22px;
        justify-content: center;
        line-height: 22px;
        width: 18px;
    }

    .secondary {
        align-items: center;
        color: var(--colors-accent);
        display: flex;
        font-size: calc(17px * var(--medium-symbol-font-size-multiplier));
        font-weight: calc(590 / var(--medium-symbol-font-size-multiplier));
        height: 22px;
        justify-content: center;
        line-height: 22px;
        width: 18px;
    }

    .tertiary {
        color: var(--labels-tertiary);
        font-feature-settings: "ss15" on;
        font-size: calc(17px * var(--small-symbol-font-size-multiplier));
        font-weight: calc(590 / var(--small-symbol-font-size-multiplier));
        line-height: 22px;
    }
</style>
