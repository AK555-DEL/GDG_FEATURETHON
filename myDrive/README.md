# myDrive

An open-source, self-hosted cloud file storage server with a browser-based interface. It uses MongoDB for file and folder metadata and supports local filesystem or Amazon S3 storage for file chunks.

**Original repository:** [https://github.com/subnub/myDrive.git](https://github.com/subnub/myDrive.git)

## Prerequisites

- Git
- Node.js 20.14.0 or newer
- npm
- MongoDB, either installed locally or provided by a MongoDB service
- A modern web browser

Docker Desktop is optional. FFmpeg is also optional and is only needed for video thumbnail generation.

## Clone the project

In PowerShell:

```powershell
git clone https://github.com/subnub/myDrive.git
cd myDrive
```

## Install dependencies and configure

```powershell
npm install
Copy-Item backend\config\.env.development.example backend\config\.env.development
Copy-Item src\config\.env.development.example src\config\.env.development
```

Edit the two new environment files using the upstream README and examples. Configure a reachable MongoDB connection. Keep passwords and other secrets private, and do not commit local `.env` files.

## Run locally

The upstream development scripts use POSIX-style `NODE_ENV=...` assignments. On Windows, run them unchanged from WSL with Node.js and npm installed inside WSL. Git Bash alone may not change the shell npm uses to run package scripts.

Alternatively, build and run the app locally from PowerShell in production mode. Create production environment files from the provided examples:

```powershell
Copy-Item backend\config\.env.production.example backend\config\.env.production
Copy-Item src\config\.env.production.example src\config\.env.production
npm run build
$env:NODE_ENV = "production"
node .\dist-backend\server\server-start.js
```

Open [http://localhost:3000](http://localhost:3000), unless your configuration specifies a different port.

## Test

Create the test environment file, then run Jest with a Windows-compatible environment-variable command:

```powershell
Copy-Item backend\config\.env.test.example backend\config\.env.test
npx cross-env NODE_ENV=test jest
```

The repository also defines `npm test`; in Windows PowerShell, the command above avoids the POSIX environment assignment in that script.

## Deployment

The upstream repository provides an optional Docker Compose setup. From PowerShell:

```powershell
Copy-Item .env.example .env
```

Edit `.env` with the values required by the upstream README, then start the app and MongoDB:

```powershell
docker compose up -d
```

Open [http://localhost:3000](http://localhost:3000). Docker is not required for local development if you configure MongoDB separately.

## Common issues

- **MongoDB connection errors:** Check that MongoDB is running and that the connection string in the backend environment file is correct.
- **`npm run dev` fails in PowerShell:** Use Git Bash or WSL as noted above; the upstream script uses POSIX-style environment assignments.
- **Missing environment configuration:** Confirm that each example file was copied without the `.example` suffix and that required values were filled in.
- **Video thumbnails are unavailable:** FFmpeg is optional; install it only if you need video thumbnail generation.
- **Build runs out of memory:** In PowerShell, set the Node.js memory option before building: `$env:NODE_OPTIONS = "--max-old-space-size=4096"` and then run `npm run build`.
