# PancakeMaker

**Upstream:** [github.com/momentmaker/pancakemaker](https://github.com/momentmaker/pancakemaker)

## About the project

PancakeMaker is an offline-first expense tracker. Data stays in the browser; account-based cloud sync is optional.

## Prerequisites

- **Git**: install the [Windows version](https://git-scm.com/install/) with the default options.
- **Node.js 20+** and **npm 10.9.0** (declared by the project): install the Windows LTS `.msi` from [nodejs.org](https://nodejs.org/en/download). If needed, set npm to the declared version with `npm.cmd install --global npm@10.9.0`.
- A modern browser. [VS Code](https://code.visualstudio.com/download) and [Chrome](https://www.google.com/chrome/) are optional.

Cloudflare and Resend are needed only to configure or deploy cloud sync. No database, Docker, or WSL is required for local expense tracking.

## Verify installation

In PowerShell:

```powershell
git --version
node -v
npm.cmd -v
```

Use Node 20+ and confirm npm prints `10.9.0`.

## Clone the project

```powershell
git clone https://github.com/momentmaker/pancakemaker.git
cd pancakemaker
```

For push access, fork the upstream repository first and clone your fork instead.

## Install dependencies

The monorepo uses npm workspaces. The upstream quick-start specifies:

```powershell
npm.cmd install
```

The repository has a `package-lock.json`, but its root version is `1.8.0` while `package.json` says `1.8.1`. **NOT TESTED:** a clean install from the current upstream snapshot. If npm changes the lockfile, do not commit that change without organizer/maintainer approval.

## Run the application

Build the shared workspace packages and apps from the repository root:

```powershell
npm.cmd run build
```

For the frontend-only workflow (supported by the web workspace), run:

```powershell
npm.cmd run dev --workspace=@pancakemaker/web
```

Open [http://localhost:5173](http://localhost:5173), or use the URL Vite prints. The root `npm.cmd run dev` starts both Vite and the Wrangler API; the API is unnecessary for offline expense tracking and sync needs Cloudflare/Resend configuration.

## Where to add features

- `apps/web/src/` — frontend, including `views/`, `components/`, and `db/`.
- `packages/shared/` — shared types and schemas.
- `workers/api/` — optional cloud-sync API.

## Troubleshooting

- **Shared package cannot be resolved:** run `npm.cmd run build` from the monorepo root before starting the web workspace.
- **Sync is unavailable:** expected in frontend-only mode; local expenses remain in the browser.
- **Lint fails:** the web workspace calls `eslint`, which is not declared in the current workspace dependencies.
- **Lockfile/install warning:** the current package and lock versions differ as noted above; do not delete the lockfile or run a separate install in a workspace.

The previous clean-clone audit on an earlier snapshot passed the build and 412 tests; current upstream lockfile consistency has not been verified.

## Submission

Fork, branch, commit, and push to your fork. Follow [the central event instructions](../README.md); submit a pull request only if the maintainers permit it.
