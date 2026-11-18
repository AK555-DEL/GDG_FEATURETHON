# PancakeMaker

**Upstream:** [github.com/momentmaker/pancakemaker](https://github.com/momentmaker/pancakemaker)

## About the project

PancakeMaker is an offline-first expense tracker. Its monorepo contains the web app, shared TypeScript package, and optional cloud-sync API.

This guide is for teams assigned to this project; see the [central event README](../README.md) for the event format and presentation details.

## Prerequisites

- **Git:** [install Git](https://git-scm.com/install/).
- **Node.js:** [install Node.js 24 LTS](https://nodejs.org/en/download). The project requires Node.js `>=20` and npm `10.9.0`.
- [VS Code](https://code.visualstudio.com/download) and [Google Chrome](https://www.google.com/chrome/) are optional; any modern browser can be used.
- Cloudflare and Resend are needed only for optional cloud sync.

## Verify software installation

In PowerShell:

```powershell
git --version
node -v
npm.cmd -v
```

Confirm npm prints `10.9.0`. If needed, install that version with `npm.cmd install --global npm@10.9.0`. On macOS or Linux, use `npm` instead of `npm.cmd`.

## Clone the project

```powershell
git clone https://github.com/momentmaker/pancakemaker.git
cd pancakemaker
```

## Install dependencies

Install from the monorepo root:

```powershell
npm.cmd install
```

## Environment configuration

No configuration is needed for offline local expense tracking. Cloud sync is optional and requires Cloudflare Workers/D1 and Resend configuration.

## Run the application

Build shared packages from the monorepo root first:

```powershell
npm.cmd run build
```

Run the frontend (works offline):

```powershell
npm.cmd run dev --workspace=@pancakemaker/web
```

For the optional API, run this in another terminal:

```powershell
npm.cmd run dev --workspace=@pancakemaker/api
```

The root `npm.cmd run dev` starts both development servers.

## Open the application

The web app is at [http://localhost:5173](http://localhost:5173). The optional API runs at [http://localhost:8787](http://localhost:8787).

## Where to add features

- `apps/web/src/` — frontend, including views, components, and local database code.
- `packages/shared/` — shared types and schemas.
- `workers/api/src/` — optional cloud-sync API.

## Troubleshooting

- **Shared package cannot be resolved:** run `npm.cmd run build` from the monorepo root before starting a workspace.
- **Cloud sync is unavailable:** expected when using the offline frontend without the optional API and cloud configuration.
- **Lockfile issue:** if installation reports a version mismatch, ask an organizer rather than regenerating the lockfile.

## Final demonstration checklist

- What problem did we identify?
- Why does it matter to users?
- What feature did we propose?
- What did we implement?
- Can we demonstrate it working?
- How is the improved application better than the original?

Present a meaningful implementation or working prototype, not only an idea. A production-ready feature is not required.
