# Simple React Ecommerce

**Upstream:** [github.com/alim1496/simple-react-ecommerce](https://github.com/alim1496/simple-react-ecommerce)

## About the project

A React storefront demo with product browsing, cart, wishlist, and sample account pages. Product information comes from DummyJSON, so product loading needs internet access.

## Prerequisites

- **Git** (clone the project): install the [Windows version](https://git-scm.com/install/) with the default options.
- **Node.js 18+** (Vite 5 supports Node 18 or 20+, not Node 19; use a supported 20+ LTS release; npm is included): install the Windows `.msi` from [nodejs.org](https://nodejs.org/en/download) and reopen PowerShell.
- Internet access for the product API.
- A modern browser. [VS Code](https://code.visualstudio.com/download) and [Chrome](https://www.google.com/chrome/) are optional.

## Verify installation

In PowerShell:

```powershell
git --version
node -v
npm.cmd -v
```

Use Node 20+ LTS; npm should print a version number.

## Clone the project

```powershell
git clone https://github.com/alim1496/simple-react-ecommerce.git
cd simple-react-ecommerce
```

For push access, fork the upstream repository first and clone your fork instead.

## Install dependencies

The project has a compatible npm `package-lock.json`. From the project root:

```powershell
npm.cmd ci
```

**NOT TESTED:** a clean `npm ci` did not finish during the previous Windows audit (stopped after about 29 minutes). Do not replace the lockfile or change package managers; ask organizers before spending event time on a stalled install.

## Run the application

```powershell
npm.cmd run dev
```

Keep the terminal open and visit [http://localhost:5173](http://localhost:5173), or use the URL Vite prints. Product data requires internet access.

## Where to add features

- `src/components/` — reusable UI.
- `src/pages/` — page-level views.
- `src/redux/` — application state.
- `cypress/` — end-to-end tests.

## Troubleshooting

- **Products do not load:** check internet access to DummyJSON.
- **Node/npm error:** use Node 20+ LTS, reopen PowerShell, then check `node -v` and `npm.cmd -v`.
- **Port 5173 is busy:** use Vite's alternate URL.
- **Docker build fails:** the Dockerfile expects `yarn.lock`, but the repository uses npm. Docker is not needed for this event.
- **Install status:** the previous audit's build and lint succeeded only after dependencies were partly installed; Cypress was not tested. A full clean install and start remain unverified.

## Submission

Fork, branch, commit, and push to your fork. Follow [the central event instructions](../README.md); submit a pull request only if the maintainers permit it.
