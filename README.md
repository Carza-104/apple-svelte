# apple-svelte

apple-svelte is a component library for Svelte based on Apple's Human Interface design language.
To get started with apple-svelte, check out [the docs](https://apple-svelte.vercel.app).

## Installation

Open a [Svelte project](https://kit.svelte.dev/docs/creating-a-project) and enter the following command into your terminal:

```
npm i apple-svelte
```

Include [Material Symbols](https://fonts.google.com/icons?icon.style=Rounded) or whatever symbol library you're using into your HTML head and import apple-svelte's stylesheet, as well as the components you need.

```
<script>
    import { Button } from 'apple-svelte';
</script>

<svelte:head>
    <link rel="stylesheet" href="node_modules/apple-svelte/dist/styles.css" />
    <link
        rel="stylesheet"
        href="https://fonts.googleapis.com/css2?family=Material+Symbols+Rounded:opsz,wght,FILL,GRAD@20..48,100..700,0..1,-50..200"
    />
</svelte:head>
```

If the above syntax doesn't work, you can copy the stylesheet and paste it into your project.

To learn how to customize apple-svelte, check out [the docs](https://apple-svelte.vercel.app).
