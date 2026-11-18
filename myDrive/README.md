# myDrive

**Upstream:** [github.com/subnub/myDrive](https://github.com/subnub/myDrive)

> **NOT READY for the event:** the previous clean-install audit's backend TypeScript build failed at `backend/db/mongoDB/fileDB.ts:360` (`new` is not accepted in the options passed to `File.updateMany`). The frontend build succeeded, but the backend failure prevents a verified full app startup. Use another project unless organizers confirm an upstream fix.

## About the project

myDrive is a self-hosted file-storage app with a React frontend and Node.js/Express backend. MongoDB stores file metadata; files can use local disk storage.

## Prerequisites

- **Git**: install the [Windows version](https://git-scm.com/install/) with the default options.
- **Node.js 20.14+** and npm: install the Windows LTS `.msi` from [nodejs.org](https://nodejs.org/en/download).
- **MongoDB service** (required for the backend; the project does not pin a server version): install the current stable [MongoDB Community Server](https://www.mongodb.com/docs/manual/installation/) as a Windows service, or use [MongoDB Atlas](https://www.mongodb.com/products/platform/atlas-database). For Atlas, create a database user, allow your IP, and copy its connection URI.
- A modern browser. [VS Code](https://code.visualstudio.com/download) and [Chrome](https://www.google.com/chrome/) are optional. Docker and WSL are not required.

## Verify installation

In PowerShell:

```powershell
git --version
node -v
npm.cmd -v
Get-Service MongoDB
Test-NetConnection 127.0.0.1 -Port 27017
```

Use Node 20.14+. For local MongoDB, `Get-Service` should show `Running` and the last command should report `TcpTestSucceeded : True`. Skip both MongoDB commands if using Atlas.

## Clone the project

```powershell
git clone https://github.com/subnub/myDrive.git
cd myDrive
```

For push access, fork the upstream repository first and clone your fork instead.

## Install dependencies

There is no root lockfile. From the project root:

```powershell
npm.cmd install
```

This resolves unpinned versions and may create a `package-lock.json`; do not commit a generated lockfile without maintainer approval.

## Configure MongoDB and environment

Create the backend environment file:

```powershell
Copy-Item backend\config\.env.development.example backend\config\.env.development
```

Set these required values in `backend\config\.env.development`:

```dotenv
MONGODB_URL=mongodb://127.0.0.1:27017/mydrive
DB_TYPE=fs
FS_DIRECTORY=C:/Users/YOUR-USERNAME/mydrive-data/
KEY=REPLACE_WITH_PRIVATE_RANDOM_VALUE
PASSWORD_ACCESS=REPLACE_WITH_DISTINCT_PRIVATE_VALUE
PASSWORD_REFRESH=REPLACE_WITH_DISTINCT_PRIVATE_VALUE
PASSWORD_COOKIE=REPLACE_WITH_DISTINCT_PRIVATE_VALUE
```

Replace `YOUR-USERNAME`; create the storage folder with:

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\mydrive-data"
```

`FS_DIRECTORY` must be absolute and end in `/`. Generate each secret separately with `node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"`; never share or commit them. For Atlas, put its URI in `MONGODB_URL`. The frontend `.env.development` is unnecessary for the default `localhost:3000` proxy.

## Run the application

**Blocked until the upstream backend build error is fixed.** After that fix, run these from the project root in separate PowerShell terminals:

1. Build the backend: `npm.cmd run build:backend`.
2. Start the backend:

   ```powershell
   $env:NODE_ENV = "development"
   npx.cmd nodemon --quiet .\dist-backend\server\server-start.js
   ```

3. Watch backend changes: `npx.cmd tsc --watch -p .\backend\tsconfig.json`.
4. Start Vite: `npx.cmd vite`, then open [http://localhost:5173](http://localhost:5173).

The backend uses port 3000. Keep all terminals open; stop each with **Ctrl+C**.

## Where to add features

- `src/` — React frontend.
- `backend/` — Express API, MongoDB, and storage.

## Troubleshooting

- **Backend build reports TS2353 for `new`:** this is the known upstream failure above, not a local configuration error.
- **MongoDB connection error:** start the local MongoDB service or correct `MONGODB_URL`.
- **Missing key/secrets:** fill all four secret variables in the backend environment file.
- **PowerShell rejects `npm run dev`:** the upstream script uses POSIX environment syntax; use the documented manual terminals after the build is fixed.
- **Windows lint reports no files matching the quoted `src/**/*` pattern:** the upstream lint script is incompatible with the current Windows shell.

The previous audit's tests passed (179 tests) with test-only secrets configured. A complete local app run was **NOT TESTED** because MongoDB and a working backend build were unavailable.

## Submission

Fork, branch, commit, and push to your fork. Follow [the central event instructions](../README.md); submit a pull request only if the maintainers permit it.
