# myDrive

**Original repository:** [https://github.com/subnub/myDrive.git](https://github.com/subnub/myDrive.git)

## 1. Overview

myDrive is a self-hosted file storage app with a React/TypeScript browser interface and a Node.js/Express backend. MongoDB stores file and folder metadata; uploaded file contents can be stored on the local filesystem or in Amazon S3.

## 2. Prerequisites

Required:

- Git.
- Node.js 20.14.0 or newer.
- npm, included with Node.js.
- A MongoDB service that the backend can reach ([local MongoDB Community Server](https://www.mongodb.com/try/download/community) or [MongoDB Atlas](https://www.mongodb.com/products/platform/atlas-database)).
- A modern browser.

Docker Desktop is optional. FFmpeg is optional and is only needed for video thumbnail generation. S3, email verification, and HTTPS are optional; the local setup below uses filesystem storage and does not require email.

A GitHub account is needed only if you want to fork and push your work.

## 3. Verify prerequisites

In PowerShell:

```powershell
node -v
npm -v
git --version
```

Confirm Node reports version 20.14.0 or newer. This repository does not include a root `package-lock.json`; use `npm install`, not `npm ci`.

## 4. Fork and clone

For work you plan to push, open the [original repository](https://github.com/subnub/myDrive.git) on GitHub and select **Fork**. Then clone your fork, replacing `YOUR-USERNAME` with your GitHub username:

```powershell
git clone https://github.com/YOUR-USERNAME/myDrive.git
cd myDrive
```

To explore without pushing changes, clone the original URL instead.

## 5. Install dependencies

From the project root:

```powershell
npm install
```

There is no root lockfile, so npm resolves dependency versions during installation.
`npm install` may create a local `package-lock.json`; check `git status` before committing and do not include a new lockfile unless the upstream maintainers want that change.

**Clean-install audit note:** With Node.js 24.22.3 and npm 11.19.1, the frontend build passed, but the backend build failed with a TypeScript error at `backend/db/mongoDB/fileDB.ts:360` (`new` is not accepted in the options passed to `File.updateMany`). The resolved dependency versions are not locked, so other installs may resolve differently. The backend startup steps below could not be verified against this install.

## 6. Configure MongoDB and environment

Create local development environment files from the checked-in examples:

```powershell
Copy-Item backend\config\.env.development.example backend\config\.env.development
Copy-Item src\config\.env.development.example src\config\.env.development
```

Edit `backend\config\.env.development` for local filesystem storage:

```dotenv
MONGODB_URL=mongodb://127.0.0.1:27017/mydrive
DB_TYPE=fs
FS_DIRECTORY=C:/Users/YOUR-USERNAME/mydrive-data/
KEY=REPLACE_WITH_A_PRIVATE_RANDOM_KEY
PASSWORD_ACCESS=REPLACE_WITH_A_PRIVATE_RANDOM_SECRET
PASSWORD_REFRESH=REPLACE_WITH_A_DIFFERENT_PRIVATE_RANDOM_SECRET
PASSWORD_COOKIE=REPLACE_WITH_ANOTHER_PRIVATE_RANDOM_SECRET
```

Replace `YOUR-USERNAME` with your Windows account folder. The `FS_DIRECTORY` path must be absolute and end in `/`; Node accepts this slash-separated path format on Windows. Create the storage directory before starting the app.

For example, create the matching storage folder with:

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\mydrive-data"
```

Use your MongoDB connection string if it differs from the local example. `KEY` is important for development and must be kept safe; losing it can make stored files unrecoverable. Generate a private value with `node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"` and use a separate generated value for each of the three password variables. Do not copy the sample placeholders into a shared deployment or commit your `.env.development` file.

The frontend file can keep the example's default proxy, which points local API requests at `http://localhost:3000`. If you change the backend port, set `VITE_PROXY_URL` in `src\config\.env.development` to the backend origin.

`S3_ID`, `S3_KEY`, and `S3_BUCKET` are only needed if `DB_TYPE=s3`. Email, HTTPS, and video-thumbnail settings are optional.

## 7. Run locally in PowerShell

The repository's `npm run dev` script and some other scripts set `NODE_ENV` using POSIX shell syntax. Do not rely on that script in Windows PowerShell. Use separate PowerShell terminals:

**Terminal 1 - build the backend once:**

```powershell
npm run build:backend
```

**Terminal 2 - start the backend:**

```powershell
$env:NODE_ENV = "development"
npx nodemon --quiet .\dist-backend\server\server-start.js
```

**Terminal 3 - watch and compile backend changes:**

```powershell
npx tsc --watch -p .\backend\tsconfig.json
```

**Terminal 4 - run the Vite frontend:**

```powershell
npx vite
```

Keep the backend, TypeScript watcher, and Vite terminals running and open [http://localhost:5173](http://localhost:5173). The backend listens on port 3000 by default; the Vite proxy forwards API requests there. Stop each process with **Ctrl+C** in its terminal.

## 8. Verify the app

- Confirm MongoDB is running and the backend terminal has started without a connection error.
- Open the Vite URL and confirm the myDrive interface loads.
- Try the account flow and a small file upload.
- Confirm uploaded files are stored under the configured `FS_DIRECTORY`.
- Check the browser console and all server terminals for errors.

**NOT TESTED:** a full local app run requires a configured MongoDB service and environment secrets; those were not configured in this documentation audit.

## 9. Project structure

| Path | Purpose |
| --- | --- |
| `src/` | React frontend, Vite configuration, and frontend environment example. |
| `backend/` | Express backend, TypeScript configuration, and backend environment example. |
| `serverUtils/` | Server-side utility scripts. |
| `dist-backend/` | Generated backend output; recreated by the build. |
| `docker-compose.yml` | Optional Compose setup using the project's published app image. |

## 10. Start developing a feature

Frontend changes belong in `src/`; backend changes belong in `backend/`. Keep the TypeScript watcher and Vite process running while developing. Backend changes are recompiled into `dist-backend/`, where nodemon restarts the server.

For file-storage changes, test with a small file and keep the configured encryption key safe. Do not add credentials or personal files to commits.

## 11. Test, build, and deploy

Build both the frontend and backend:

```powershell
npm run build
```

In the clean-install audit above, the frontend portion completed but the backend portion failed with the noted TypeScript error. This is an upstream code/dependency issue, not a missing local setup step.

Create the test environment file:

```powershell
Copy-Item backend\config\.env.test.example backend\config\.env.test
```

Edit `backend\config\.env.test` and set `KEY`, `PASSWORD_ACCESS`, `PASSWORD_REFRESH`, and `PASSWORD_COOKIE` to distinct test-only random values. Do not reuse production secrets or commit this local file. Then invoke Jest with the installed `cross-env` package in PowerShell, since the npm test script uses a POSIX-style environment assignment:

```powershell
npx cross-env NODE_ENV=test jest --runInBand
```

The tests may require downloading a MongoDB Memory Server binary on first run. With the four test-only secrets configured, all 179 tests passed in the clean-install audit. In that same audit, `npm run lint` failed on Windows because ESLint treated the quoted glob as a literal path; this is an upstream script issue.

For a production build, first create the environment files from the production examples:

```powershell
Copy-Item backend\config\.env.production.example backend\config\.env.production
Copy-Item src\config\.env.production.example src\config\.env.production
```

Configure them for your deployment, then run `npm run build`. The upstream production start script also uses POSIX syntax; in PowerShell, start the backend with:

```powershell
$env:NODE_ENV = "production"
node .\dist-backend\server\server-start.js
```

The repository's Docker Compose file is optional and uses the published app image rather than building the participant's current source. Follow the upstream deployment guide for a real self-hosted deployment and its required secrets; do not treat the sample Compose file as a local source-development workflow.

## 12. Troubleshooting and submission

- **MongoDB connection error:** Confirm the database service is running and `MONGODB_URL` is correct in `backend\config\.env.development`.
- **Missing environment values:** Confirm both development files were copied from their `.example` files and the required backend values were filled in.
- **PowerShell rejects `npm run dev`:** Use the four-terminal PowerShell workflow above; the upstream script uses POSIX environment syntax.
- **The frontend cannot reach the backend:** Confirm the backend is listening on port 3000 and `VITE_PROXY_URL` points to that origin.
- **Storage path error:** Confirm `FS_DIRECTORY` is an absolute path, ends in `/`, and the directory exists.
- **Backend build reports that `new` is not allowed in update options:** This was observed at `backend/db/mongoDB/fileDB.ts:360` in the clean-install audit. Check for an upstream fix before trying the backend workflow; the project does not pin dependencies with a root lockfile.
- **`npm run lint` reports no files matching the quoted `src/**/*` pattern:** This Windows script issue was observed in the clean-install audit; it is not caused by missing app configuration.
- **Tests report missing key or JWT secrets:** Create `backend\config\.env.test` from its example and set distinct test-only values for `KEY`, `PASSWORD_ACCESS`, `PASSWORD_REFRESH`, and `PASSWORD_COOKIE`.
- **Video thumbnails are unavailable:** FFmpeg is optional; install and configure it only if you need that feature.
- **Build runs out of memory:** In PowerShell, set `$env:NODE_OPTIONS = "--max-old-space-size=4096"` before running `npm run build`.

For event work, fork the original project, create a feature branch, commit and push to your fork, then follow the organizers' announced submission process. Open an upstream pull request only if the maintainers accept contributions. Do not push directly to the original repository.
