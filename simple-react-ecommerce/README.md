# Simple React Ecommerce

Simple React Ecommerce is a React and TypeScript storefront demo. It provides product browsing and categories, search, product details, cart and wishlist behavior, and sample account pages.

**Upstream repository:** [alim1496/simple-react-ecommerce](https://github.com/alim1496/simple-react-ecommerce)

For event details, see the [central README](../README.md).

## Prerequisites

- [Git](https://git-scm.com/install/)
- [Node.js](https://nodejs.org/en/download) 24 LTS is recommended. The upstream Vite 5.0.8 dependency supports Node.js `^18.0.0` or `>=20.0.0`.
- npm, included with Node.js.
- Internet access for product data from [DummyJSON](https://dummyjson.com/)
- A modern browser such as [Google Chrome](https://www.google.com/chrome/); [Visual Studio Code](https://code.visualstudio.com/download) is optional.

## Verify the tools

In PowerShell:

```powershell
git --version
node --version
npm.cmd --version
```

On macOS or Linux, run `npm --version` instead of `npm.cmd --version`.

## Clone the project

In PowerShell:

```powershell
git clone https://github.com/alim1496/simple-react-ecommerce.git
cd simple-react-ecommerce
```

## Install dependencies

The repository contains an npm lockfile (`package-lock.json`, lockfile version 3). Run the clean, lockfile-based install from the project directory:

```powershell
npm.cmd ci
```

On macOS or Linux, use `npm ci`.

## Environment configuration

No environment variables or API keys are required for the basic application. Product data is fetched from DummyJSON and requires internet access.

## Start the development server

```powershell
npm.cmd run dev
```

Open [http://localhost:5173](http://localhost:5173), or use the URL printed by Vite if 5173 is already in use.

On macOS or Linux, use `npm run dev`.

## Where to implement features

- `src/pages/` — page-level views and routes.
- `src/components/` — reusable storefront, cart, navigation, and product UI.
- `src/redux/` — application state management.
- `src/hooks/` — reusable React logic.
- `src/models/` — product and application data types.
- `src/api.ts` — DummyJSON API requests.
- `src/App.tsx` — application routes and top-level composition.

Before changing code, explore the existing cart, wishlist, category, product detail, and account flows. Useful areas to improve include filtering and sorting, empty states, loading errors, saved preferences, checkout feedback, accessibility, responsive layout, and cart or wishlist usability.

## Troubleshooting

- **Node.js version error:** use Node.js 24 LTS or another version that satisfies Vite's supported range.
- **Products do not load:** check internet access and whether DummyJSON is reachable.
- **Port 5173 is busy:** open the alternate URL printed by Vite.
- **Install stalls or fails:** do not replace the lockfile or switch package managers. Ask an organizer for help. A successful clean install was not performed in this documentation audit.
- **Code or dependency changes need validation:** run `npm.cmd run build` on Windows or `npm run build` on macOS/Linux. This script exists in the upstream `package.json`.

## Final demonstration checklist

- What problem did you identify, and why does it matter to users?
- What improvement did you propose?
- What did you implement?
- Can you demonstrate the feature on the running application?
- How is the improved user experience better than the original?

Present a meaningful implementation or working prototype, not only an idea. A production-ready feature is not required.
