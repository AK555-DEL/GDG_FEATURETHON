# Simple React Ecommerce

**Original repository:** [https://github.com/alim1496/simple-react-ecommerce.git](https://github.com/alim1496/simple-react-ecommerce.git)

## 1. Overview

This is a React e-commerce demo with product browsing, cart, wishlist, and sample account flows. It uses React, TypeScript, Vite, Tailwind CSS, Redux Toolkit, and Cypress. Product data is requested from DummyJSON, so an internet connection is needed for product loading.

## 2. Prerequisites

Required:

- Git.
- Node.js 18 or newer, excluding Node 19 as required by Vite 5; use a current Node.js LTS release. The repository does not pin an exact Node version.
- npm, included with Node.js.
- A modern browser.
- Internet access for the DummyJSON product API.

Docker is optional; the repository's Dockerfile currently refers to a `yarn.lock` file, but the project provides `package-lock.json`. **NOT TESTED:** Docker is not a verified setup path unless that mismatch is resolved. A GitHub account is needed only if you want to fork and push your work.

## 3. Verify prerequisites

In PowerShell:

```powershell
node -v
npm -v
git --version
```

Confirm Node is version 18 or newer and is not version 19.

## 4. Fork and clone

For work you plan to push, open the [original repository](https://github.com/alim1496/simple-react-ecommerce.git) on GitHub and select **Fork**. Then clone your fork, replacing `YOUR-USERNAME` with your GitHub username:

```powershell
git clone https://github.com/YOUR-USERNAME/simple-react-ecommerce.git
cd simple-react-ecommerce
```

To explore without pushing changes, clone the original URL instead.

## 5. Install dependencies

Use the committed `package-lock.json` with `npm ci`:

```powershell
npm ci
```

This installs the locked dependencies. If installation fails, check that you are in the folder containing `package.json` and `package-lock.json`.

## 6. Environment configuration

No local environment file or database is required for the basic frontend. The app uses the external DummyJSON product API; an internet connection is required to load remote products.

## 7. Run locally

From the project folder:

```powershell
npm run dev
```

Keep the terminal open and use the local URL printed by Vite (normally [http://localhost:5173](http://localhost:5173)). Press **Ctrl+C** to stop the server.

## 8. Verify the app

- Open the Vite URL and confirm the store page appears.
- Confirm product cards load when internet access is available.
- Try adding an item to the cart and wishlist.
- Check the terminal and browser console for errors.
- If Vite reports a different port, use the URL it prints.

## 9. Project structure

| Path | Purpose |
| --- | --- |
| `src/` | Application source code. |
| `src/components/` | Reusable interface components. |
| `src/pages/` | Page-level views and routes. |
| `src/redux/` | Redux Toolkit state management. |
| `cypress/` | Cypress end-to-end tests. |
| `package.json` | Scripts and dependency manifest. |

Use the actual folder names in your checkout as the source of truth if the project structure changes.

## 10. Start developing a feature

Start with a small feature, such as a product card improvement, a cart interaction, or a usability fix. Search for the existing component or page that owns the behavior, follow nearby styling and state-management patterns, and keep `npm run dev` running to check changes in the browser.

## 11. Test, build, and deploy

Run the available checks:

```powershell
npm run lint
npm run build
```

In the audit, lint and build succeeded in the temporary clone, but the clean `npm ci` attempt did not finish after about 29 minutes, so a fresh install was not verified. Cypress tests were not run.

The repository includes Cypress end-to-end tests. Start the Vite server in one PowerShell terminal:

```powershell
npm run dev
```

In a second terminal, from the project folder, run:

```powershell
npx cypress run
```

Keep the dev server running while Cypress tests run. To open Cypress interactively, use:

```powershell
npx cypress open
```

The production build is written to `dist/`. Preview it locally with:

```powershell
npm run preview
```

Use the preview URL Vite prints (normally [http://localhost:4173](http://localhost:4173)).

**Docker:** The checked-in Dockerfile copies `yarn.lock`, while this repository has an npm lockfile. Docker has not been verified as a working participant setup path; prefer the npm workflow above.

## 12. Troubleshooting and submission

- **Product data is missing:** Confirm internet access and that the browser can reach DummyJSON. This frontend depends on a third-party API.
- **`npm ci` fails:** Confirm Node is version 18 or newer, that you are in the project root, and that `package-lock.json` is present. Avoid replacing `npm ci` with a different package manager unless the project changes its lockfile.
- **The dev server does not open:** Leave the terminal running and use the exact URL Vite prints. If port 5173 is occupied, Vite may select another port.
- **Cypress fails to start:** Confirm dependencies were installed and allow Cypress to complete its first-run setup.
- **Docker build fails:** The current Dockerfile expects `yarn.lock`, which is not present in the repository; use the documented npm workflow instead.

For event work, fork the original project, create a feature branch, commit and push to your fork, then follow the organizers' announced submission process. Open an upstream pull request only if the maintainers accept contributions. Do not push directly to the original repository.
