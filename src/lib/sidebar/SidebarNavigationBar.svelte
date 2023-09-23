<!-- @format -->
<script>
    export let scrollPosition = "top";
    /* export let scrollPosition = "lower"; */
    export let title = "Title";

    export let id = undefined;
    export let style = undefined;

    let backdropFilterStyle = "unset";
    let backgroundStyle = "unset";
    let backgroundBlendModeStyle = "unset";
    let boxShadowStyle = "unset";
    let marginBottomStyle = "unset";
    if (scrollPosition === "lower") {
        backdropFilterStyle = "var(--materials-backdrop-filter)";
        backgroundStyle = "var(--materials-chrome)";
        backgroundBlendModeStyle =
            "var(--materials-chrome-background-blend-mode)";
        boxShadowStyle = "0px 0.33px var(--box-shadow)";
        marginBottomStyle = "4px";
    }
</script>

<section
    {id}
    style="{style}; backdrop-filter: {backdropFilterStyle}; background: {backgroundStyle}; background-blend-mode: {backgroundBlendModeStyle}; box-shadow: {boxShadowStyle}; margin-bottom: {marginBottomStyle}; -webkit-backdrop-filter: {backdropFilterStyle}"
>
    <div>
        <slot name="leading" />
        {#if scrollPosition === "lower"}
            <p>{title}</p>
        {/if}
        <slot name="trailing" />
    </div>
    {#if scrollPosition === "top"}
        <h1>{title}</h1>
    {/if}
</section>

<style>
    :root {
        color-scheme: light dark;
        --box-shadow: rgb(0, 0, 0, 0.3);
    }

    @media (prefers-color-scheme: dark) {
        :root {
            --box-shadow: rgb(255, 255, 255, 0.15);
        }
    }

    section {
        display: flex;
        flex-direction: column;
        gap: 2px;
        padding: 27px 16px 0px;
    }

    div {
        display: flex;
        justify-content: space-between;
        padding: 11px 8px;
    }

    p {
        font-size: 17px;
        font-weight: 590;
        line-height: 22px;
    }

    h1 {
        font-size: 34px;
        font-weight: 700;
        line-height: 41px;
        margin: 4px 8px;
    }
</style>
