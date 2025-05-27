## Project Structure

The project is structured as follows:

```
src
├── app.css
├── App.svelte (routes)
├── main.tsx
├── vite-env.d.ts
├── assets
│   ├── css
│   │   ├── fonts.css
│   │   ├── index.css
│   │   └── ...files.css (map, slider, etc.)
│   ├── images
│   │   ├── common
│   │   ├── pages
│   │   └── ...directories (dots, blobs, etc.)
│   └── svgs
│       ├── icons
│       │   ├── Close.tsx
│       │   ├── LoadingSpinner.tsx
│       │   └── ...icons (trash, check, etc.)
│       └── ...directories or files.tsx
├── components
│   ├── common
│   │   └── ...directories or files.tsx (socials, cards, etc.)
│   ├── inputs
│   │   ├── Checkbox.tsx
│   │   ├── Input.tsx
│   │   ├── Radio.tsx
│   │   └── Select.tsx
│   ├── interactive
│   │   └── Button.tsx
│   ├── sections
│   │   └── directories or files.tsx (contact, faq, etc.)
│   ├── template
│   │   ├── Footer.tsx
│   │   ├── Header.tsx
│   │   ├── Main.tsx
│   │   └── Modal.tsx
│   └── utils
│       └── RequiresAuthentication.tsx
├── constants
│   └── ...constants.ts (const SCREAMING_SNAKE_CASE)
├── pages
│   ├── NotFound.tsx
│   ├── home
│   │   ├── _hooks.tsx
│   │   ├── _index.tsx
│   │   └── ...OtherComponents.tsx
│   └── ...directories or files.tsx (about, pricing, etc.)
├── types
│   ├── ...files.ts
│   └── utils
│       ├── components.tsx
│       └── laravel.ts
└── utils
    ├── functions.ts
    └── middleware.ts
```

## Project dependencies

The project is using the following dependencies:
svelte
typescript
axios
svelte-routing
tailwindcss
clsx
tailwind-merge
svelte-sonner
prettier - prettier-plugin-tailwindcss\

"svelte": "^5.20.2" -D
Svelte is the library used to create the user interface.

"typescript": "~5.7.2" -D
Typescript is used for making the project type safe.

"svelte-routing": "^2.13.0" -D
Svelte-routing is used to handle the routing of the application.

"axios": "^1.7.9" -D
Axios is used to make http requests.

"zod": "^3.24.2" -D
Zod is a typescript library for data validation.

"tailwindcss": "^4.0.6" -D
Tailwindcss v4 is used to style the project. No tailwind.config.js file is provided, as it is not necessary. All the configuration is done in the App.css file.

"clsx": "^2.1.1" -D
Clsx is used to display conditional classes.

"tailwind-merge": "^3.0.1" -D
Tailwind-merge is used to merge the tailwind classes.

"svelte-sonner": "^0.3.28" -D
Sonner is used to create the toast notifications.

"prettier": "^3.5.0" -D
Prettier is used to format the code.

"prettier-plugin-tailwindcss": "^0.6.11" -D
Prettier-plugin-tailwindcss is used to format the tailwind classes.

## Technical considerations

**Why `global.d.ts` instead of `compilerOptions.types` inside `jsconfig.json` or `tsconfig.json`?**

Setting `compilerOptions.types` shuts out all other types not explicitly listed in the configuration. Using triple-slash references keeps the default TypeScript setting of accepting type information from the entire workspace, while also adding `svelte` and `vite/client` type information.

**Why include `.vscode/extensions.json`?**

Other templates indirectly recommend extensions via the README, but this file allows VS Code to prompt the user to install the recommended extension upon opening the project.

**Why enable `allowJs` in the TS template?**

While `allowJs: false` would indeed prevent the use of `.js` files in the project, it does not prevent the use of JavaScript syntax in `.svelte` files. In addition, it would force `checkJs: false`, bringing the worst of both worlds: not being able to guarantee the entire codebase is TypeScript, and also having worse typechecking for the existing JavaScript. In addition, there are valid use cases in which a mixed codebase may be relevant.

**Why is HMR not preserving my local component state?**

HMR state preservation comes with a number of gotchas! It has been disabled by default in both `svelte-hmr` and `@sveltejs/vite-plugin-svelte` due to its often surprising behavior. You can read the details [here](https://github.com/rixo/svelte-hmr#svelte-hmr).

If you have state that's important to retain within a component, consider creating an external store which would not be replaced by HMR.

```ts
// store.ts
// An extremely simple external store
import { writable } from "svelte/store";
export default writable(0);
```
