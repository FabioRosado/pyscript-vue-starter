# Pyscript-vue-starter

This is a starter template for [Pyscript](https://pyscript.net) using [Vue 3](https://v3.vuejs.org/), [Vite](https://vitejs.dev/), [TypeScript](https://www.typescriptlang.org/), [Tailwind CSS](https://tailwindcss.com/), [Jest](https://jestjs.io/) and [Playwright](https://playwright.dev/).

Using this template, you can quickly get started with Pyscript and Vue 3. Pyscript gives you the ability to write Python code in your Vue components, and it also provides a way to use Python libraries in your Vue components. 

We are adding and loading Pyscript in the header of the `index.html` file. This will allow Pyscript to be available in your Vue components and pages.


## Features

In this template, we have included different features and examples to help you get started with Pyscript and Vue 3.

- [x] Import python files and use them in your Vue components with the `<py-script src="path/to/file.py" />` tag.
- [x] Use Python libraries in your Vue components by writing your Python code in the `<py-script>` tag.
- [ ] Save state in your Vue components using the `useStore` hook and read it in python code.
- [ ] Save data in local and session storage using the `useStorage` hook and read it in python code.
- [ ] Install python dependencies and reuse them in your Vue components.
- [ ] Dynamically install python dependencies and reuse them in your Vue components.


## Key changes for Pyscript to work with Vue 3


### Changes to the configuration

We have changed the vite configuration to enable you to write Python code inside the `<py-script>` tag. These changes are:

```ts
export default defineConfig({
  plugins: [
    vue({
      template: {
        compilerOptions: {
          isCustomElement: (tag) => tag.includes("-"),
          whitespace: "preserve",
        },
      },
    }),
    vueJsx(),
  ],
  resolve: {
    alias: {
      "@": fileURLToPath(new URL("./src", import.meta.url)),
    },
  },
});
```

These two `compilerOptions` are important for Pyscript to work with Vue. 

- The `isCustomElement` allow us to use the Pyscript custom elements such as `<py-config>`, `<py-script>`, etc.
- The `whitespace` option is set to `preserve` to allow us to write Python code inside the `<py-script>` tag and preserve the indentation. Otherwise, the Python code would be placed in a single line, and it would not work.

### Changes to the CSS 

Since we are using Tailwind CSS, we didn't import Pyscript's CSS file. So, we have to add the following CSS to our `index.css` file to hide any of the Pyscript custom elements until Pyscript finishes loading.

```css
/* py-config - not a component */
py-config {
  display: none
}

/* py-{el} - components not defined */
py-script:not(:defined) {
  display: none
}

py-repl:not(:defined) {
  display: none
}
```

We have also hidden the splashscreen of Pyscript so that it doesn't seem like the page is taking a while to load. 

```css
.py-overlay, .py-pop-up, .label {
  display: none;
}
```

**Note:** You can remove these CSS rules if you want to see the splashscreen of Pyscript. Also, as of the writing of this README, I have a PR open to allow users to disable the splashscreen.



## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```

### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
npm run test:unit
```

### Run End-to-End Tests with [Playwright](https://playwright.dev)

```sh
# Install browsers for the first run
npx playwright install

# When testing on CI, must build the project first
npm run build

# Runs the end-to-end tests
npm run test:e2e
# Runs the tests only on Chromium
npm run test:e2e -- --project=chromium
# Runs the tests of a specific file
npm run test:e2e -- tests/example.spec.ts
# Runs the tests in debug mode
npm run test:e2e -- --debug
```

