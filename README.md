# GDG Featureathon

## Repository 2: IT Tools

This guide explains how to download, install, run, test, and deploy **IT Tools**. It is written for people who are new to Git and web development.

**Source repository:** [CorentinTh/it-tools](https://github.com/CorentinTh/it-tools)  
**Try the hosted app:** [it-tools.tech](https://it-tools.tech)

IT Tools is a collection of handy utilities for developers and people working in IT. See the [upstream feature list and roadmap](https://github.com/CorentinTh/it-tools#functionalities-and-roadmap).

## What you need to install

Install the required tools before following the setup steps:

| Software | Recommended version | Download / installation | Why it is needed |
| --- | --- | --- | --- |
| Git | Current stable version | [Install Git](https://git-scm.com/downloads) | Downloads the project source code |
| Node.js | 22.x LTS | [Install Node.js](https://nodejs.org/en/download) | Runs the development server and builds the website; npm is included |
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

## Run IT Tools on your computer

### 1. Open a terminal

On Windows, open **PowerShell**. On macOS or Linux, open your terminal application.

### 2. Download the project

Run:

```powershell
git clone https://github.com/CorentinTh/it-tools.git
```

This creates a folder named `it-tools`. Move into it:

```powershell
cd it-tools
```

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

Keep the terminal open. Open the local address printed in the terminal, usually <http://localhost:5173>. To stop the server, return to the terminal and press **Ctrl+C**.

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

To preview the production build locally:

```powershell
pnpm preview
```

Open the address printed by the command (the project normally uses <http://localhost:5050>). Press **Ctrl+C** to stop the preview.

## Deploy with Docker

Docker is optional. Make sure Docker Desktop (or Docker Engine on Linux) is installed and running first.

You can run the prebuilt image from Docker Hub:

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

### Build and deploy the static site yourself

If you do not want to use the prebuilt Docker image, create a production build:

```powershell
pnpm install
pnpm build
```

Upload the contents of the resulting `dist` folder to a static web host. If the host connects directly to the GitHub repository, use `pnpm build` as the build command and `dist` as the output directory.

## Troubleshooting

- **`git`, `node`, `npm`, or `pnpm` is not recognized:** Install the missing tool using the links above, then open a new terminal and check its version.
- **The install command fails:** Make sure you are inside the `it-tools` folder, have internet access, and installed Node.js and pnpm. Then try `pnpm install` again.
- **The local page does not open:** Make sure `pnpm dev` is still running, and use the exact URL printed in the terminal.
- **Port 5173 or 5050 is already in use:** Stop the other program using that port, then restart the development server or preview.
- **Docker says the daemon is unavailable:** Start Docker Desktop or the Docker Engine service, then retry the command.
- **Port 8080 is already in use:** Change the host port in the Docker command, for example use `-p 8081:80`, then open <http://localhost:8081>.

## Contributing

To suggest a feature, use the project's [feature request page](https://github.com/CorentinTh/it-tools/issues/new/choose). You can also check the [open issues](https://github.com/CorentinTh/it-tools/issues) for planned or requested features.

For code contributions, the upstream project recommends Visual Studio Code with [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar), [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint), and [i18n Ally](https://marketplace.visualstudio.com/items?itemName=lokalise.i18n-ally).

## License

IT Tools is distributed under the [GNU GPLv3 license](https://github.com/CorentinTh/it-tools/blob/main/LICENSE). Review the license before redistributing a modified copy.