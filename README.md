# SvelteKit + TailwindCSS starter template

This repo is a working skeleton project that integrates Tailwind's JIT mode with SvelteKit.

## Steps

1. Set up the project structure, and rename Tailwind and PostCSS config files to `.cjs` format:

```bash
npm init svelte@next my-app
cd my-app
npm install
npm install --save-dev autoprefixer@latest postcss@latest tailwindcss@latest
npx tailwindcss init -p
mv tailwind.config.js tailwind.config.cjs
mv postcss.config.js postcss.config.cjs
mkdir src/styles
touch src/styles/styles.css
touch src/routes/__layout.svelte
```

1. Edit the Tailwind config to use JIT mode and purge appropriate files:

```js
// tailwind.config.cjs

module.exports = {
    mode: 'jit',
    purge: [
        './src/**/*.{html,js,jsx,svelte,ts,tsx}'
    ],
    //...
}
```

1. Set the `TAILWIND_MODE` environment variable to `watch` inside the `dev` script:

```js
// package.json

//...
"scripts": {
    "dev": "TAILWIND_MODE=watch svelte-kit dev",
    //...
},
//...
```

1. Add base Tailwind styles:

```css
/* styles/styles.css */

@tailwind base;
@tailwind components;
@tailwind utilities;
```

1. Import Tailwind styles to `__layout.svelte`:

```html
<!-- src/routes/__layout.svelte -->

<script>
    import '../styles/styles.css';
</script>

<div id="test-div" class="bg-blue-500">Edit the classes on this div in <code>__layout.svelte</code> to test HMR</div>
```

1. Start the dev server and visit http://localhost:3000/:

```bash
npm run dev
```
