# Simple React Ecommerce

**Upstream:** [github.com/alim1496/simple-react-ecommerce](https://github.com/alim1496/simple-react-ecommerce)

## About the project

A React storefront demo with product browsing, cart, wishlist, and sample account pages.

This guide is for teams assigned to this project; see the [central event README](../README.md) for the event format and presentation details.

## Prerequisites

- **Git:** [install Git](https://git-scm.com/install/).
- **Node.js:** [install Node.js 24 LTS](https://nodejs.org/en/download). The project does not declare a root Node engine; its Vite 5.0.8 dependency supports Node `^18.0.0` or `>=20.0.0`. npm is included with Node.js.
- **Internet:** required for product data from [DummyJSON](https://dummyjson.com/).
- [VS Code](https://code.visualstudio.com/download) and [Google Chrome](https://www.google.com/chrome/) are optional; any modern browser can be used.

## Verify software installation

In PowerShell:

```powershell
git --version
node -v
npm.cmd -v
```

On macOS or Linux, use `npm` instead of `npm.cmd`.

## Clone the project

```powershell
git clone https://github.com/alim1496/simple-react-ecommerce.git
cd simple-react-ecommerce
```

## Install dependencies

The repository includes an npm lockfile (lockfile version 3). From the project root:

```powershell
npm.cmd ci
```

## Environment configuration

No environment variables are required. Product data requires internet access to DummyJSON.

## Run the application

```powershell
npm.cmd run dev
```

## Open the application

Open [http://localhost:5173](http://localhost:5173), or use the URL Vite prints.

## Where to add features

- `src/pages/` — page-level views.
- `src/components/` — reusable UI.
- `src/redux/` — application state.

## Troubleshooting

- **Products do not load:** check internet access to DummyJSON.

## Final demonstration checklist

- What problem did we identify?
- Why does it matter to users?
- What feature did we propose?
- What did we implement?
- Can we demonstrate it working?
- How is the improved application better than the original?

Present a meaningful implementation or working prototype, not only an idea. A production-ready feature is not required.
