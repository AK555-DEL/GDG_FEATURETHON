# GDG Featureathon

## Repository 2: IT Tools

This guide explains how to download, install, run, test, and deploy **IT Tools**. It is written for people who are new to Git and web development.

**Source repository:** [CorentinTh/it-tools](https://github.com/CorentinTh/it-tools.git)
**Try the hosted app:** [it-tools.tech](https://it-tools.tech)

IT Tools is a collection of handy utilities for developers and people working in IT. See the [upstream feature list and roadmap](https://github.com/CorentinTh/it-tools#functionalities-and-roadmap).

## What you need to install

Install the required tools before following the setup steps:

| Software | Recommended version | Download / installation | Why it is needed |
| --- | --- | --- | --- |
| Git | Current stable version | [Install Git](https://git-scm.com/downloads) | Downloads the project source code |
| Node.js | 18.18.2 (`.nvmrc`) | [Install Node.js](https://nodejs.org/en/download) | Runs the development server and builds the website; npm is included |
| pnpm | 9.11.0 | [Install pnpm](https://pnpm.io/installation) | Installs the project's JavaScript packages |
| Web browser | Current Chrome, Edge, or Firefox | [Chrome](https://www.google.com/chrome/), [Edge](https://www.microsoft.com/edge/download), or [Firefox](https://www.mozilla.org/firefox/new/) | Opens the app |
| Docker | Optional | [Install Docker Desktop](https://docs.docker.com/desktop/) for Windows/macOS, or [Docker Engine](https://docs.docker.com/engine/install/) for Linux | Runs the prebuilt app container for deployment |
| Code editor | Optional | [Visual Studio Code](https://code.visualstudio.com/download) | Makes it easier to read and edit the project |

The project specifies pnpm 9.11.0. After installing Node.js, open a terminal and install that version of pnpm:

```powershell
npm install --global pnpm@9.11.0
```

Check that the required tools are available:

```powershell
git --version
node --version
npm --version
pnpm --version
```

The pnpm command should report `9.11.0`. If a command is not recognized, finish installing that tool and open a new terminal.

The repository's `.nvmrc` specifies Node.js 18.18.2. Use that version for the closest match to the repository configuration.

## Fork the project for your team

Forking creates your team's own copy of the project on GitHub. You can push your changes to your fork and share its link with the event organizers.

1. Sign in to [GitHub](https://github.com/) or [create an account](https://github.com/signup).
2. Open the [IT Tools repository](https://github.com/CorentinTh/it-tools) and select **Fork**, then create the fork under your GitHub account.
3. Clone **your fork**, replacing `YOUR-USERNAME` with your GitHub username:

   ```powershell
   git clone https://github.com/YOUR-USERNAME/it-tools.git
   cd it-tools
   ```

4. Make changes in this local copy. After committing your work, run `git push` to send it to your fork on GitHub.

## Run IT Tools on your computer

### 1. Open a terminal

On Windows, open **PowerShell**. On macOS or Linux, open your terminal application.

### 2. Open your cloned project

If you followed the fork steps above, your terminal should already be in the `it-tools` folder. If not, open a terminal in that folder or navigate to it with `cd`.

### 3. Install the project packages

Run this from inside the `it-tools` folder:

```powershell
pnpm install
```

This downloads the packages the project needs. It can take a few minutes the first time.

### 4. Start the development server

```powershell
pnpm dev
```

Keep the terminal open. Vite normally serves the development app at <http://localhost:5173>. If that port is busy, Vite may print a different address; use the address shown in your terminal. To stop the server, return to the terminal and press **Ctrl+C**.

## Where do I start?

The existing tool implementations live under `src/tools/`. To create a starter template for a new tool, run this from the project folder (use a short name with lowercase letters and hyphens):

```powershell
pnpm run script:create:tool my-first-tool
```

The script creates starter files in `src/tools/my-first-tool/` and adds an import to `src/tools/index.ts`. Then:

1. Build your tool's interface in `src/tools/my-first-tool/my-first-tool.vue`.
2. Open `src/tools/index.ts` and add the new tool to an appropriate category in `toolsByCategory`; the generator does not do this step.
3. Run `pnpm dev` and open the printed local address to try your tool.

## Run checks (optional)

Run these commands from the `it-tools` folder:

```powershell
pnpm test
pnpm lint
pnpm build
```

- `pnpm test` runs the unit tests.
- `pnpm lint` checks the source code for common problems.
- `pnpm build` type-checks and builds the website. The deployable files are written to the `dist` folder.

On Windows PowerShell, the upstream build script's inline `NODE_OPTIONS` assignment may not run. Use the equivalent PowerShell commands:

```powershell
$env:NODE_OPTIONS = "--max_old_space_size=4096"
pnpm exec vue-tsc --noEmit
if ($LASTEXITCODE -eq 0) { pnpm exec vite build }
```

To preview the production build locally:

```powershell
pnpm preview
```

Open <http://localhost:5050>. The preview command is configured to use port 5050. Press **Ctrl+C** to stop the preview.

## Deploy the app

### Run the upstream app for reference only

These prebuilt images contain the original upstream app, **not your team's changes**. Use them only to see the original app running. For your own version, use the build instructions below.

Docker is optional. Make sure Docker Desktop (or Docker Engine on Linux) is installed and running first. Run the prebuilt image from Docker Hub:

```powershell
docker run -d --name it-tools --restart unless-stopped -p 8080:80 corentinth/it-tools:latest
```

Or use the image from GitHub Packages instead:

```powershell
docker run -d --name it-tools --restart unless-stopped -p 8080:80 ghcr.io/corentinth/it-tools:latest
```

The command downloads the image if needed and starts the app in the background. Open <http://localhost:8080> in your browser.

Useful Docker commands:

```powershell
docker logs -f it-tools
docker stop it-tools
docker rm it-tools
```

Press **Ctrl+C** to stop viewing the logs. The stop and remove commands stop the app and remove its container; run the `docker run` command again to start it later.

### Build and run your team's version with Docker

The repository includes a `Dockerfile` that builds the checked-out project and serves it with Nginx. From the root of your cloned fork, build an image from your team's code:

```powershell
docker build -t my-it-tools .
```

Start your image:

```powershell
docker run -d --name my-it-tools --restart unless-stopped -p 8080:80 my-it-tools
```

Open <http://localhost:8080>. This image is built from your local project folder, so it includes your team's changes.

To stop and remove your team's container:

```powershell
docker stop my-it-tools
docker rm my-it-tools
```

### Deploy your team's static site

From the root of your cloned fork, create a production build:

```powershell
pnpm install
pnpm build
```

Upload the contents of the resulting `dist` folder to a static web host. If the host connects directly to your fork, use `pnpm build` as the build command and `dist` as the output directory. Configure the host to serve `index.html` for app routes if it requires a single-page-app fallback.

## Troubleshooting

- **`git`, `node`, `npm`, or `pnpm` is not recognized:** Install the missing tool using the links above, then open a new terminal and check its version.
- **Node.js version differs from the repository setting:** Install Node.js 18.18.2, as specified by `.nvmrc`.
- **PowerShell says running scripts is disabled when using pnpm:** Try the Windows command wrapper, for example `pnpm.cmd install` or `pnpm.cmd dev`.
- **The install command fails:** Make sure you are inside the `it-tools` folder, have internet access, and installed Node.js and pnpm. Then try `pnpm install` again.
- **The local page does not open:** Make sure `pnpm dev` is still running, and use the exact URL printed in the terminal.
- **Port 5173 or 5050 is already in use:** Stop the other program using that port, then restart the development server or preview.
- **Docker says the daemon is unavailable:** Start Docker Desktop or the Docker Engine service, then retry the command.
- **Port 8080 is already in use:** Change the host port in the Docker command, for example use `-p 8081:80`, then open <http://localhost:8081>.

## Event submission

Each team should submit:

- The URL of its GitHub fork, with the team's latest changes pushed.
- A short demo video showing the new tool and how it works.

The event deadline and submission channel have not been provided yet; the organizers should announce them before submissions are due.

## Contributing

To suggest a feature, use the project's [feature request page](https://github.com/CorentinTh/it-tools/issues/new/choose). You can also check the [open issues](https://github.com/CorentinTh/it-tools/issues) for planned or requested features.

For code contributions, the upstream project recommends Visual Studio Code with [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar), [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint), and [i18n Ally](https://marketplace.visualstudio.com/items?itemName=lokalise.i18n-ally).

## License

IT Tools is distributed under the [GNU GPLv3 license](https://github.com/CorentinTh/it-tools/blob/main/LICENSE). Review the license before redistributing a modified copy.
