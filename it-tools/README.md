# IT Tools

**Upstream:** [github.com/CorentinTh/it-tools](https://github.com/CorentinTh/it-tools)

## About the project

IT Tools is a browser-based collection of developer utilities. Add a new tool or improve an existing one.

## Prerequisites

- **Git**: install the [Windows version](https://git-scm.com/install/) with the default options.
- **Node.js**: the repository pins 18.18.2, which is end-of-life. Node 24.22.3 passed the previous install, build, and test audit; prefer Node 24 LTS for the event. npm is included.
- **pnpm 9.11.0**: required by `packageManager` and `pnpm-lock.yaml`. Install from the [official pnpm instructions](https://pnpm.io/installation) using `npm.cmd install --global pnpm@9.11.0`.
- A modern browser. [VS Code](https://code.visualstudio.com/download) and [Chrome](https://www.google.com/chrome/) are optional.

## Verify installation

In PowerShell:

```powershell
git --version
node -v
npm.cmd -v
pnpm.cmd --version
```

Use Node 24 LTS and confirm pnpm prints `9.11.0`. In PowerShell use `pnpm.cmd` to avoid script-policy errors.

## Clone the project

```powershell
git clone https://github.com/CorentinTh/it-tools.git
cd it-tools
```

For push access, fork the upstream repository first and clone your fork instead.

## Install dependencies

The lockfile is for pnpm; do not use npm or yarn:

```powershell
pnpm.cmd install --frozen-lockfile
```

## Run the application

From the project root:

```powershell
pnpm.cmd dev
```

Keep the terminal open and open the Vite URL (normally [http://localhost:5173](http://localhost:5173)). Stop with **Ctrl+C**.

## Where to add features

Generate a starter tool from the project root:

```powershell
pnpm.cmd run script:create:tool my-first-tool
```

Add it to a category in `src/tools/index.ts`, then develop in `src/tools/my-first-tool/`.

## Troubleshooting

- **Node version mismatch:** the repository's 18.18.2 pin is EOL; the previous audit passed on Node 24.22.3. If organizers require the pin, ask before installing an unsupported runtime.
- **pnpm is not found:** reopen PowerShell and check `pnpm.cmd --version`; reinstall the exact version above if needed.
- **Tests:** run once with `pnpm.cmd run test:unit -- --run` (138 tests passed in the previous audit).
- **Build in PowerShell:** the upstream build script uses POSIX `NODE_OPTIONS`. Use:

  ```powershell
  $env:NODE_OPTIONS = "--max_old_space_size=4096"
  pnpm.cmd exec vue-tsc --noEmit
  if ($LASTEXITCODE -eq 0) { pnpm.cmd exec vite build }
  ```

## Submission

Fork, branch, commit, and push to your fork. Follow [the central event instructions](../README.md); submit a pull request only if the maintainers permit it.
