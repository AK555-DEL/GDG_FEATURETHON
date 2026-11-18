# Simple React Ecommerce

A demo e-commerce application built with React, TypeScript, Vite, Tailwind CSS, and Redux Toolkit. It includes product listings, a cart, user-authenticated pages, and a wishlist.

**Original repository:** [https://github.com/alim1496/simple-react-ecommerce.git](https://github.com/alim1496/simple-react-ecommerce.git)

## Prerequisites

- Git
- Node.js and npm. The repository does not declare a specific Node.js version.
- A modern web browser

## Clone the project

In PowerShell:

```powershell
git clone https://github.com/alim1496/simple-react-ecommerce.git
cd simple-react-ecommerce
```

## Install dependencies

The repository includes `package-lock.json`; use npm:

```powershell
npm install
```

## Run locally

```powershell
npm run dev
```

Open [http://localhost:5173](http://localhost:5173).

## Test

The project has Cypress end-to-end specs under `cypress/e2e`. Start the app in one terminal:

```powershell
npm run dev
```

In a second terminal in the project folder, run the tests:

```powershell
npx cypress run
```

To open the Cypress test runner instead:

```powershell
npx cypress open
```

The repository does not define an `npm test` script. To check a production build, run:

```powershell
npm run build
```

## Deployment

The upstream README does not specify a deployment provider. `npm run build` creates the Vite production output in `dist`. Publish that folder with a static host configured to serve the app's client-side routes; follow the chosen host's instructions.

## Common issues

- **`npm` is not recognized:** Install Node.js, which includes npm, and reopen PowerShell.
- **Cypress cannot reach the app:** Keep `npm run dev` running in the first terminal and confirm the app is available at port 5173.
- **Port 5173 is occupied:** Stop the other development server, then restart this app and use the URL Vite prints.
- **Install or build fails:** Run `node --version` and `npm --version`, then retry `npm install` from the project folder.
