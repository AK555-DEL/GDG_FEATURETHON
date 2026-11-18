# Tripix

**Upstream:** [github.com/MiladJoodi/Tripix](https://github.com/MiladJoodi/Tripix)

## About the project

Tripix is a travel-search and sample booking frontend for bus, train, and flight trips. Search and booking data are demo data stored in the browser; it does not purchase real tickets.

## Prerequisites

- **Git** (clone the project): install the [Windows version](https://git-scm.com/install/) with the default options.
- **Node.js 20.9+** (required by Next.js 16; includes npm): install the Windows LTS `.msi` from [nodejs.org](https://nodejs.org/en/download) and reopen PowerShell.
- A modern browser. [VS Code](https://code.visualstudio.com/download) and [Chrome](https://www.google.com/chrome/) are optional.

No database, API credentials, Docker, or WSL are needed for the local demo.

## Verify installation

In PowerShell:

```powershell
git --version
node -v
npm.cmd -v
```

Use Node 20.9 or newer; npm should print a version number.

## Clone the project

```powershell
git clone https://github.com/MiladJoodi/Tripix.git
cd Tripix
```

For push access, fork the upstream repository first and clone your fork instead.

## Install dependencies

Run from the folder containing `package.json` and `package-lock.json`:

```powershell
npm.cmd ci
```

## Run the application

```powershell
npm.cmd run dev
```

Keep the terminal open and visit [http://localhost:3000](http://localhost:3000). If Next.js reports another port, use that URL. Stop the server with **Ctrl+C**.

## Where to add features

- `src/app/` — pages and routes.
- `src/features/` — search and booking flows.
- `src/components/` — shared interface components.
- `src/data/` — sample travel data.

## Troubleshooting

- **Node version error:** install Node 20.9+ and reopen PowerShell.
- **`npm ci` fails:** confirm you are in the project root and `package-lock.json` is present; do not switch package managers.
- **Port 3000 is busy:** use the alternate URL printed by Next.js.
- **`npm run lint` fails:** the upstream script runs `next lint`, which is unsupported by the project's Next.js 16. The previous clean-clone audit's `npm run build` succeeded; manual browser flows were not tested.

## Submission

Fork, branch, commit, and push to your fork. Follow [the central event instructions](../README.md); submit a pull request only if the maintainers permit it.
