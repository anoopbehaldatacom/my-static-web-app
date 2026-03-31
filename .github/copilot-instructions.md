# AI Coding Instructions for my-static-web-app

## Architecture Overview
This repository contains four isomorphic frontend applications (Angular, React, Svelte, Vue) each implementing a shopping-themed app with products listing and management. Each app is self-contained with similar structure: `src/components/` for UI, `src/products/` for domain logic, `src/store/` for state management. Data flows from mock APIs through stores to components. No shared code between frameworks.

## Key Patterns
- **State Management**: React uses Redux + Sagas (see `react-app/src/store/`), Vue uses Vuex modules (see `vue-app/src/store/`), Svelte uses custom writable stores (see `svelte-app/src/store/`), Angular uses services with in-memory web API (see `angular-app/src/app/in-memory-data.service.ts`).
- **Component Organization**: React/Svelte export components via `src/components/index.js` for clean imports. Use PascalCase naming (e.g., `ProductList`).
- **Mock Data**: All apps use hardcoded product data; no real APIs. Products include id, name, description, quantity.
- **Routing**: Each app has /products and /about routes, with SPA fallback in `staticwebapp.config.json`.

## Workflows
- **Running Apps**: `cd {framework}-app && npm install && npm start` (e.g., `cd react-app && npm start`).
- **No Global Scripts**: Each app has independent `package.json`; no monorepo tooling.
- **Testing**: Use framework-specific test runners (e.g., `npm test` in React app).
- **Deployment**: Configured for Azure Static Web Apps via `staticwebapp.config.json` in each app folder.

## Conventions
- **File Naming**: kebab-case for files (e.g., `product-list.js`), PascalCase for components/classes.
- **Imports**: Prefer relative imports; export components from index.js where present.
- **Error Handling**: Minimal; focus on user-friendly messages in components.
- **Styling**: Each app uses SCSS; global styles in `src/styles.scss`.

## Examples
- Adding a product: Update mock data in store/API files, dispatch actions in components.
- New component: Create in `src/components/`, export from index.js (React/Svelte), import in pages.

Reference: `react-app/src/store/product.saga.js` for async patterns, `angular-app/src/app/router.ts` for routing.