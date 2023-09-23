<!-- @format -->
<script>
    export let showHeader = false;
    export let headerType = "default";
    /* export let headerType = "plain"; */
    /* export let headerType = "prominent"; */
    export let header = "Header text";
    export let disclosure = "arrow_forward_ios";
    export let showFooter = false;
    export let footer = "Footer text";

    export let id = undefined;
    export let onPress = undefined;
    export let style = undefined;

    let marginTop = "unset";
    if (showHeader) {
        marginTop = "18px";
    } else {
        marginTop = "24px";
    }

    let marginBottom = "unset";
    if (showFooter) {
        marginBottom = "18px";
    } else {
        marginBottom = "24px";
    }
</script>

<div
    class="collection"
    {id}
    style="{style}; margin: {marginTop} 0px {marginBottom}"
>
    {#if showHeader}
        {#if headerType === "default"}
            <p class="header">{header}</p>
        {:else if headerType === "plain"}
            <p class="subheadline-emphasized">{header}</p>
        {:else}
            <label class="title3-emphasized">
                {header}
                <button class="symbol" on:click={onPress}>{disclosure}</button>
            </label>
        {/if}
    {/if}
    <div class="list">
        <slot />
    </div>
    {#if showFooter}
        <p class="footer">{footer}</p>
    {/if}
</div>

<style>
    .header {
        color: var(--labels-secondary);
        font-size: 13px;
        font-weight: 400;
        line-height: 16px;
        margin: 0px 16px 7px;
        text-transform: uppercase;
    }

    .subheadline-emphasized {
        color: var(--labels-secondary);
        margin: 0px 16px 7px;
    }

    .title3-emphasized {
        display: flex;
        justify-content: space-between;
        margin: 0px 19px 5px;
    }

    .symbol {
        color: var(--colors-accent);
        font-feature-settings: "ss15" on;
        font-size: calc(17px * var(--small-symbol-font-size-multiplier));
        font-weight: 590;
        line-height: 25px;
    }

    .list {
        border-radius: 10px;
        overflow: hidden;
    }

    .footer {
        color: var(--labels-secondary);
        font-size: 13px;
        font-weight: 400;
        line-height: 16px;
        margin: 5px 16px 0px;
    }
</style>
