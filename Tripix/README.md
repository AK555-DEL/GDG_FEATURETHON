# Tripix

**Upstream:** [github.com/MiladJoodi/Tripix](https://github.com/MiladJoodi/Tripix)

## About the project

Tripix is a sample travel search and booking app for bus, train, and air trips. It uses local demo data and does not purchase real tickets.

This guide is for teams assigned to this project; see the [central event README](../README.md) for the event format and presentation details.

## Prerequisites

- **Git:** [install Git](https://git-scm.com/install/).
- **Node.js:** [install Node.js 24 LTS](https://nodejs.org/en/download). Next.js 16 requires Node.js `>=20.9.0`; npm is included with Node.js.
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
git clone https://github.com/MiladJoodi/Tripix.git
cd Tripix
```

## Install dependencies

Run from the project root, where `package-lock.json` is located:

```powershell
npm.cmd ci
```

## Environment configuration

No database, API credentials, or environment variables are required. Search and booking data are sample data stored in the browser.

## Run the application

```powershell
npm.cmd run dev
```

## Open the application

Visit [http://localhost:3000](http://localhost:3000). If Next.js reports another port, use that URL.

## Where to add features

- `src/app/` — routes and pages.
- `src/features/` — search and booking flows.
- `src/components/` — shared interface.
- `src/data/` — sample travel data.

## Troubleshooting

- **Node version error:** use Node.js 24 LTS or another version meeting Next.js 16's `>=20.9.0` requirement.
- **Port 3000 is busy:** use the alternate URL printed by Next.js.
- **Lint:** the upstream `lint` script invokes `next lint`, which is unsupported by Next.js 16. Do not run it during the event.
- **Lockfile metadata:** `package-lock.json` names the project `bilit`, while `package.json` names it `tripix`. Current `npm ci` is **NOT TESTED**; if it reports an out-of-sync lockfile, ask an organizer rather than regenerating the lockfile.
- **Build:** `npm.cmd run build` is available. It succeeded in a previous clean-clone audit; the current upstream snapshot is **NOT TESTED** in this documentation audit.
- **Current install and browser launch:** **NOT TESTED** in this documentation audit.

## Final demonstration checklist

- What problem did we identify?
- Why does it matter to users?
- What feature did we propose?
- What did we implement?
- Can we demonstrate it working?
- How is the improved application better than the original?

Present a meaningful implementation or working prototype, not only an idea. A production-ready feature is not required.
