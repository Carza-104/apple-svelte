<!-- @format -->
<script>
    export let id = undefined;
    export let style = undefined;
</script>

<div {id} {style}>
    <slot />
</div>

<style>
    div {
        align-items: start;
        column-gap: 16px;
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(361px, 1fr));
    }

    @media (max-width: 548px) {
        div {
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
        }
    }
</style>
