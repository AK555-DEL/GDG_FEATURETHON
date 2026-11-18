# PancakeMaker

An offline-first personal and business expense tracker with optional cloud sync. The local frontend works without an account or backend.

**Original repository:** [https://github.com/momentmaker/pancakemaker.git](https://github.com/momentmaker/pancakemaker.git)

## Prerequisites

- Git
- Node.js 20 or newer
- npm 10 or newer
- A modern web browser

Cloud sync and backend self-hosting are optional. They require a Cloudflare account (Workers and D1) and a Resend account for magic-link email.

## Clone the project

In PowerShell:

```powershell
git clone https://github.com/momentmaker/pancakemaker.git
cd pancakemaker
```

## Install dependencies

```powershell
npm install
```

## Build and run locally

Build the shared packages first, then start the development servers:

```powershell
npm run build
npm run dev
```

The frontend is normally available at [http://localhost:5173](http://localhost:5173); the local API runs at [http://localhost:8787](http://localhost:8787). The frontend works offline without the API; sync features need backend configuration.

## Test

Run the workspace test suite:

```powershell
npm run test
```

## Deployment

For a frontend-only deployment, build the app:

```powershell
npm run build
```

The project README identifies `apps/web/dist` as the static frontend output. Deploy that folder to a static host such as Cloudflare Pages, Netlify, or Vercel. Without the API, local expense tracking still works; cloud sync will not.

For full-stack cloud sync, follow the upstream README's self-hosting instructions. That setup includes a Cloudflare D1 database, migrations, Worker secrets, and a Resend API key. Do not commit or share those secret values.

## Common issues

- **`npm run dev` starts before shared types are built:** Run `npm run build` once before starting the development servers.
- **Sync features are unavailable:** The frontend works offline by design. Configure the optional API and its environment variables to use cloud sync.
- **Unsupported Node.js or npm version:** Check `node --version` and `npm --version`; the root `package.json` requires Node.js 20+ and specifies npm 10.9.0.
- **Port 5173 or 8787 is occupied:** Stop the process using the port, then restart the development servers.
