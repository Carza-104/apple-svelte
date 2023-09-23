<!-- @format -->
<script>
    export let id = undefined;
    export let style = undefined;
</script>

<aside {id} {style}>
    <slot />
</aside>

<style>
    aside {
        background-color: var(--bg-grouped-primary);
        box-shadow: 0.5px 0px rgb(60, 60, 67, 0.36);
        float: left;
        height: 100vh;
        max-width: 320px;
        overflow: scroll;
        position: sticky;
        top: 0px;
        width: 100%;
        z-index: 1;
    }

    @media (max-width: 809px) {
        aside {
            backdrop-filter: blur(50px);
            background: var(--materials-regular);
            background-blend-mode: var(--materials-background-blend-mode);
            float: unset;
            position: fixed;
            -webkit-backdrop-filter: blur(50px);
        }
    }

    @media (prefers-color-scheme: dark) {
        aside {
            box-shadow: 0.5px 0px rgb(84, 84, 88, 0.65);
        }
    }
</style>
