# IT Tools

A collection of handy online tools for developers and people working in IT.

**Original repository:** [https://github.com/CorentinTh/it-tools.git](https://github.com/CorentinTh/it-tools.git)

## Prerequisites

- Git
- Node.js 18.18.2 (the version in the repository's `.nvmrc`)
- pnpm 9.11.0 (the version declared in `package.json`)
- A modern web browser

## Clone the project

In PowerShell:

```powershell
git clone https://github.com/CorentinTh/it-tools.git
cd it-tools
```

## Install dependencies

Install the project's pnpm version and dependencies:

```powershell
npm install --global pnpm@9.11.0
pnpm install
```

## Run locally

```powershell
pnpm dev
```

Open the local address printed in the terminal (Vite normally uses `http://localhost:5173`).

## Test

Run the unit tests:

```powershell
pnpm test
```

## Build and deployment

For production deployment, the repository includes a Dockerfile that builds the app and serves it with Nginx. Docker is optional:

```powershell
docker build -t it-tools .
docker run --rm -p 8080:80 it-tools
```

Then open [http://localhost:8080](http://localhost:8080). The upstream README also lists other self-hosting options.

The upstream `pnpm build` script sets `NODE_OPTIONS` using POSIX shell syntax. If that command fails in PowerShell, use:

```powershell
$env:NODE_OPTIONS = "--max_old_space_size=4096"
pnpm exec vue-tsc --noEmit
if ($LASTEXITCODE -eq 0) { pnpm exec vite build }
```

## Common issues

- **`pnpm` is not recognized:** Install pnpm 9.11.0 with the command above, then open a new terminal.
- **Wrong Node.js version:** Install Node.js 18.18.2 as listed in `.nvmrc`, then check with `node --version`.
- **Port is already in use:** Stop the other process using the Vite port or use the local URL printed by Vite.
- **Build reports a `NODE_OPTIONS` error in PowerShell:** Use the PowerShell build commands above, or run the upstream build command in Git Bash.
