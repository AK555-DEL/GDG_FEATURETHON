# PancakeMaker

**Original repository:** [https://github.com/momentmaker/pancakemaker.git](https://github.com/momentmaker/pancakemaker.git)

## 1. Overview

PancakeMaker is an offline-first personal and business expense tracker. It stores data in the browser and does not require an account or backend for local expense tracking. Cloud sync is optional.

The project is a monorepo using React, TypeScript, Vite, Turborepo, npm workspaces, and Vitest.

## 2. Prerequisites

Required:

- Git.
- Node.js 20 or newer.
- npm 10.9.0, as specified by the root `package.json`.
- A modern browser.

Cloudflare Workers/D1 and a Resend account are only needed if you choose to configure and deploy cloud sync. Docker is not required for local development. A GitHub account is needed only if you want to fork and push your work.

## 3. Verify prerequisites

In PowerShell:

```powershell
node -v
npm -v
git --version
```

Confirm Node reports version 20 or newer and npm reports version 10.9.0.
If npm is a different version, install the version pinned by the project and verify it again:

```powershell
npm install --global npm@10.9.0
npm -v
```

## 4. Fork and clone

For work you plan to push, open the [original repository](https://github.com/momentmaker/pancakemaker.git) on GitHub and select **Fork**. Then clone your fork, replacing `YOUR-USERNAME` with your GitHub username:

```powershell
git clone https://github.com/YOUR-USERNAME/pancakemaker.git
cd pancakemaker
```

To explore without pushing changes, clone the original URL instead.

## 5. Install dependencies

Install the root npm workspaces using the committed `package-lock.json`:

```powershell
npm ci
```

Use the root `package.json`; do not run a separate install in a subfolder.

## 6. Environment configuration

No environment file, account, or backend is required for local expense tracking. The frontend works without cloud sync. Currency conversion rates may require internet access.

The frontend's `VITE_API_URL` defaults to `http://localhost:8787` for the local API. Cloud sync requires a configured backend; its Cloudflare and Resend setup is optional and is not needed to try the local app.

## 7. Build and run locally

Build the shared packages and workspace apps first:

```powershell
npm run build
```

Then start the development servers:

```powershell
npm run dev
```

The frontend is normally available at [http://localhost:5173](http://localhost:5173); the optional local API runs at [http://localhost:8787](http://localhost:8787). Keep the terminal open while using the app. Press **Ctrl+C** to stop the development processes.

## 8. Verify the app

- Open the Vite URL and confirm the dashboard loads.
- Add or edit a sample expense and confirm it remains available after refreshing the page.
- Local expense tracking should work without signing in or configuring the API.
- If Vite reports a different port, use the URL it prints.
- Sync features require the optional backend and are not part of the frontend-only check.

## 9. Project structure

| Path | Purpose |
| --- | --- |
| `apps/web/` | React PWA frontend, browser database, views, and sync client. |
| `workers/api/` | Optional Cloudflare Worker API for authentication and sync. |
| `packages/shared/` | Shared types, schemas, and constants. |
| `turbo.json` | Turborepo task configuration. |

## 10. Start developing a feature

For frontend work, look in `apps/web/src/` and follow the existing component, hook, database, and view patterns. For shared types and schemas, use `packages/shared/`. Backend sync work belongs in `workers/api/` and needs the optional cloud setup.

After making changes, rerun the build and tests from the repository root.

## 11. Test, build, and deploy

Run the workspace test suite:

```powershell
npm run test
```

You can run one workspace's tests, if needed:

```powershell
npm run test -w @pancakemaker/web
npm run test -w @pancakemaker/api
npm run test -w @pancakemaker/shared
```

The root `npm run lint` currently fails in the web workspace because its script calls `eslint`, which is not declared or installed by the checked-in workspace dependencies. Treat lint as unavailable unless that upstream dependency issue is fixed.

For a frontend-only production build, run `npm run build`. The static frontend output is `apps/web/dist/`; deploy that directory to a static hosting provider. Without a configured API, local browser-based expense tracking still works, but cloud sync is unavailable.

Full-stack sync deployment requires Cloudflare D1 migrations, Worker configuration/secrets, and Resend email credentials. **NOT TESTED:** cloud sync deployment requires those external accounts and secrets. Follow the upstream self-hosting guide if you intend to deploy sync. Never commit or share secret values.

On the Windows clean-clone check with Node.js 24.22.3 and npm 10.9.0, `npm ci`, `npm run build`, and `npm run test` succeeded (412 tests passed). `npm run lint` failed for the missing ESLint dependency noted above.

## 12. Troubleshooting and submission

- **Unsupported Node or npm:** Check `node -v` and `npm -v`; use Node 20+ and npm 10.9.0.
- **Workspace build fails:** Run `npm ci` from the repository root, then `npm run build` before starting development servers.
- **Sync is unavailable:** This is expected without the optional API and its Cloudflare/Resend configuration. Local tracking does not require sync.
- **Port 5173 or 8787 is occupied:** Stop the other process and restart, or use the alternate URL printed by the dev server.
- **Saved data is not shared across browsers:** Local data is stored in the browser; it is not synchronized unless the optional sync service is configured.

For event work, fork the original project, create a feature branch, commit and push to your fork, then follow the organizers' announced submission process. Open an upstream pull request only if the maintainers accept contributions. Do not push directly to the original repository.
