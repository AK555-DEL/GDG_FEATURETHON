# PancakeMaker

PancakeMaker is an offline-first expense tracker in a monorepo. Existing features include adding, editing, filtering, and reviewing expenses; category views; quick entry; charts and summaries; local database storage; keyboard help; PWA support; and an optional cloud-sync API.

**Upstream repository:** [momentmaker/pancakemaker](https://github.com/momentmaker/pancakemaker)

For event details, see the [central README](../README.md).

## Prerequisites

- [Git](https://git-scm.com/install/)
- [Node.js](https://nodejs.org/en/download) `>=20`; Node.js 24 LTS is recommended.
- npm `10.9.0`, as declared by `packageManager` in the upstream root `package.json`.
- Cloudflare Workers/D1 and Resend are required only if you configure optional cloud sync.
- [Visual Studio Code](https://code.visualstudio.com/download) and [Google Chrome](https://www.google.com/chrome/) are optional.

## Verify the tools

In PowerShell:

```powershell
git --version
node --version
npm.cmd --version
```

Confirm npm prints `10.9.0`. If needed:

```powershell
npm.cmd install --global npm@10.9.0
```

On macOS or Linux, run `npm --version` and use `npm` instead of `npm.cmd`.

## Clone the project

In PowerShell:

```powershell
git clone https://github.com/momentmaker/pancakemaker.git
cd pancakemaker
```

## Install dependencies

The repository contains an npm lockfile. Run the install from the monorepo root:

```powershell
npm.cmd install
```

On macOS or Linux, use `npm install`.

This project has a known upstream version mismatch: root `package.json` is `1.8.1`, while the lockfile root is `1.8.0`. This is why `npm install` is shown rather than a clean `npm ci`; do not regenerate or replace the lockfile. Ask an organizer if installation fails.

## Environment configuration

No environment variables are required for basic offline expense tracking. The checked-in worker has local Wrangler configuration, including a D1 binding.

Cloud synchronization is optional. Full cloud sync requires Cloudflare Workers/D1 configuration and Resend where email-related sync features are configured. Do not commit Cloudflare credentials, account secrets, Resend keys, `.env` files, or passwords.

## Build shared packages

Before starting the workspaces if dependencies cannot be resolved, run:

```powershell
npm.cmd run build
```

On macOS or Linux, use `npm run build`.

## Start the development servers

The root script starts both the web app and API:

```powershell
npm.cmd run dev
```

On macOS or Linux, use `npm run dev`.

To start only one workspace:

```powershell
npm.cmd run dev --workspace=@pancakemaker/web
npm.cmd run dev --workspace=@pancakemaker/api
```

The web app is at [http://localhost:5173](http://localhost:5173). The optional API uses [http://localhost:8787](http://localhost:8787) unless Wrangler prints another URL.

## Where to implement features

- `apps/web/src/App.tsx` — application routes and top-level composition.
- `apps/web/src/components/` — reusable interface components.
- `apps/web/src/db/` — local database integration.
- `apps/web/src/hooks/` — reusable frontend logic.
- `apps/web/src/lib/` and `apps/web/src/sync/` — shared frontend utilities and synchronization.
- `packages/shared/` — shared types and schemas.
- `workers/api/src/` — optional cloud-sync API.
- `workers/api/migrations/` — D1 database migrations.

Before changing code, test expense entry, editing, categories, filtering, summaries, charts, PWA behavior, and offline operation. Useful improvements include faster entry, category insights, budget feedback, accessibility, responsive charts, duplicate detection, CSV or export usability, and clearer sync status.

## Troubleshooting

- **Shared package cannot be resolved:** run `npm.cmd run build` or `npm run build` from the monorepo root before starting the development servers.
- **Cloud sync is unavailable:** this is expected when using only the offline frontend or without optional Cloudflare/D1 setup.
- **Lockfile mismatch:** the root package and lockfile versions differ. Ask an organizer rather than regenerating the lockfile.
- **Lint script:** the web workspace references ESLint; the current workspace dependencies did not verify that the required package is available. Do not assume lint is configured until dependencies and scripts are verified.
- **API port:** use the URL printed by Wrangler if it differs from 8787.
- **Clean install, build, and browser launch:** not fully verified in this documentation audit.

## Final demonstration checklist

- What problem did you identify, and why does it matter to users?
- What improvement did you propose?
- What did you implement?
- Can you demonstrate the feature with the app running locally?
- How is the improved experience better than the original?

Present a meaningful implementation or working prototype, not only an idea. A production-ready feature is not required.
