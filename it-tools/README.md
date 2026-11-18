# IT Tools

**Original repository:** [https://github.com/CorentinTh/it-tools.git](https://github.com/CorentinTh/it-tools.git)

## 1. Overview

IT Tools is a browser-based collection of utilities for developers and IT professionals. It is built with Vue, TypeScript, and Vite. Participants can improve an existing tool or add a new one; the project includes a generator for tool scaffolding.

## 2. Prerequisites

Required:

- Git.
- Node.js 18.18.2, as specified in the repository's `.nvmrc`.
- pnpm 9.11.0, as specified by `packageManager` in `package.json`.
- A modern browser.

Node.js 18 is end-of-life. This project pins 18.18.2; use a version manager to isolate it and do not use it for unrelated projects. Docker is optional for container deployment. A GitHub account is needed only if you want to fork and push your work.

The clean-clone checks in this audit used Node.js 24.22.3 because Node.js 18.18.2 was not available. **NOT TESTED:** setup and build with the repository's pinned Node.js 18.18.2.

With Node.js 24.22.3 and pnpm 9.11.0, the audit's install, typecheck, and build succeeded; all 138 unit tests passed. Lint completed with three ordering warnings and no errors.

## 3. Verify prerequisites

In PowerShell:

```powershell
node -v
npm -v
git --version
```

Confirm Node reports `v18.18.2`. Install pnpm in Step 5, then confirm `pnpm.cmd --version` reports `9.11.0`. If PowerShell says scripts are disabled, use the `.cmd` shim shown above and use `pnpm.cmd` in the commands below.

## 4. Fork and clone

For work you plan to push, open the [original repository](https://github.com/CorentinTh/it-tools.git) on GitHub and select **Fork**. Then clone your fork, replacing `YOUR-USERNAME` with your GitHub username:

```powershell
git clone https://github.com/YOUR-USERNAME/it-tools.git
cd it-tools
```

To explore without pushing changes, clone the original URL instead.

## 5. Install dependencies

The project uses `pnpm-lock.yaml`; use the declared pnpm version and frozen lockfile:

```powershell
npm install --global pnpm@9.11.0
pnpm.cmd --version
pnpm.cmd install --frozen-lockfile
```

The first install downloads the packages listed in the lockfile. A successful install returns to the prompt without an error.

## 6. Environment configuration

No environment file, database, or API credential is required for the local development workflow documented by the project.

## 7. Run locally

Run from the cloned `it-tools` folder:

```powershell
pnpm.cmd dev
```

Keep the terminal open and use the local URL printed by Vite (normally [http://localhost:5173](http://localhost:5173)). Press **Ctrl+C** to stop the server.

## 8. Verify the app

- Open the Vite URL and confirm the IT Tools home page loads.
- Open a tool and try a sample input.
- Confirm the terminal has no startup error.
- If the port differs from 5173, use the address Vite prints.

## 9. Project structure

| Path | Purpose |
| --- | --- |
| `src/tools/` | Existing tool implementations and the place to add a tool. |
| `src/tools/index.ts` | Imports tools and groups them into categories. |
| `locales/` | Translation resources. |
| `Dockerfile` | Optional production container build. |

## 10. Start developing a feature

Generate a starter tool from the project root:

```powershell
pnpm.cmd run script:create:tool my-first-tool
```

The generator creates files under `src/tools/my-first-tool/` and adds an import to `src/tools/index.ts`. Follow the existing tools' patterns, add the new tool to an appropriate category in `src/tools/index.ts`, and keep `pnpm.cmd dev` running while you develop. The generator does not add the tool to a category for you.

## 11. Test, build, and deploy

Run the unit tests once and run the linter:

```powershell
pnpm.cmd run test:unit -- --run
pnpm.cmd lint
```

The upstream `test` script starts Vitest in watch mode; use the one-shot command above so it exits after the run.

Build the static site with `pnpm.cmd build`. The upstream build script sets `NODE_OPTIONS` using POSIX shell syntax; if that script fails in PowerShell, run its steps with PowerShell syntax:

```powershell
$env:NODE_OPTIONS = "--max_old_space_size=4096"
pnpm.cmd exec vue-tsc --noEmit
if ($LASTEXITCODE -eq 0) { pnpm.cmd exec vite build }
```

The build output is `dist/`. You can preview it locally with:

```powershell
pnpm.cmd preview
```

Docker is optional. To build the team's checked-out source and serve it with Nginx:

```powershell
docker build -t my-it-tools .
docker run --rm -p 8080:80 my-it-tools
```

Open [http://localhost:8080](http://localhost:8080). The upstream README also documents prebuilt images; those show the original app, not your changes.

## 12. Troubleshooting and submission

- **`node`, `npm`, Git, or pnpm is not recognized:** Install the missing tool, reopen PowerShell, and rerun the version checks. For PowerShell script-policy errors, use `pnpm.cmd`.
- **Install fails:** Confirm you are in the cloned project folder and using pnpm 9.11.0, then retry `pnpm.cmd install --frozen-lockfile`.
- **Build fails on `NODE_OPTIONS`:** Use the PowerShell build commands above.
- **The app does not open:** Keep the dev server running and use the exact URL Vite prints.
- **A port is busy:** Stop the other process or use the alternate URL Vite reports.

For event work, fork the original project, create a feature branch, commit and push to your fork, then follow the organizers' announced submission process. Open an upstream pull request only if the maintainers accept contributions. Do not push directly to the original repository.
