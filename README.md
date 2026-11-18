# GDG Featurethon Participant Hub

Welcome to the GDG Featurethon. In this 4-5 hour event, choose one of five open-source projects, build a focused feature, and share your work. This repository is a directory and documentation hub; project source code remains in the original repositories.

## Choose a project

| Project | What it is | Main technologies | Setup notes | Original repository | Setup guide |
| --- | --- | --- | --- | --- | --- |
| **Simple React Ecommerce** | Frontend e-commerce demo with product browsing, cart, wishlist, and simulated account flows. | React, TypeScript, Vite, Tailwind CSS, Redux Toolkit, Cypress | Low: Node.js/npm; internet needed for DummyJSON product data. | [GitHub](https://github.com/alim1496/simple-react-ecommerce.git) | [Guide](./simple-react-ecommerce/README.md) |
| **Tripix** | Travel-booking demo for bus, train, and flight searches and a sample booking flow. | Next.js, React, TypeScript, Tailwind CSS | Low: Node.js 20.9+ and npm; uses local sample data. | [GitHub](https://github.com/MiladJoodi/Tripix.git) | [Guide](./Tripix/README.md) |
| **PancakeMaker** | Offline-first expense tracker with optional cloud sync. | React, TypeScript, Vite, Turborepo, Cloudflare Workers/D1 | Moderate: npm workspaces; local tracking works without cloud accounts. | [GitHub](https://github.com/momentmaker/pancakemaker.git) | [Guide](./pancakemaker/README.md) |
| **IT Tools** | Collection of browser-based utilities for developers and IT professionals. | Vue, TypeScript, Vite, pnpm | Moderate: Node.js 18.18.2 and pnpm 9.11.0. | [GitHub](https://github.com/CorentinTh/it-tools.git) | [Guide](./it-tools/README.md) |
| **myDrive** | Self-hosted file storage with a browser interface. | React, TypeScript, Node.js, Express, MongoDB | Higher: MongoDB and local secrets are required; the guide notes current clean-install backend build and Windows lint issues. | [GitHub](https://github.com/subnub/myDrive.git) | [Guide](./myDrive/README.md) |

## General prerequisites

- [Git](https://git-scm.com/downloads) to clone a project.
- A modern browser.
- The project-specific Node.js and package manager versions listed in its setup guide.
- MongoDB only if you choose myDrive. Docker is optional; the myDrive guide includes a native PowerShell workflow and options for obtaining MongoDB.

Check your tools in PowerShell:

```powershell
node -v
npm -v
git --version
```

Not every project uses npm. IT Tools requires pnpm; follow that project's guide rather than substituting a package manager.

## Participant workflow

1. Select the assigned project and read its setup guide before installing dependencies.
2. On GitHub, fork the original project to your account if you plan to submit code. You can clone the original for read-only exploration.
3. Clone your fork, install dependencies using the project's lockfile, and follow its local verification checklist.
4. Create a feature branch, make a focused change, run the documented checks, and commit your work.
5. Push to your fork. Open a pull request to the original repository only if its maintainers accept contributions and you have followed their contribution rules.

For a typical fork workflow:

```powershell
git clone https://github.com/YOUR-USERNAME/PROJECT.git
cd PROJECT
git switch -c feat/short-feature-name
```

Replace the placeholders with your own fork and project folder. Do not push directly to a repository you do not own.

## Troubleshooting and help

If setup fails, check that the terminal is in the cloned project folder, confirm the required runtime/package-manager versions in its guide, and use the exact install command for its lockfile. Include your operating system, project name, command, and first useful error message when asking for help. Redact passwords, tokens, and private URLs.

Do not delete lockfiles or randomly change dependency versions. Never commit `.env` files, API keys, passwords, or other secrets.

## Submissions

The central repository does not yet specify an event deadline, submission form/channel, judging criteria, or required demo format. Organizers should announce those details separately. Until then, keep your work on your fork and do not assume a pull request or direct push is the event submission method.

## Contributing

For changes to this project hub, fork this repository, create a branch, update only the relevant documentation, check links and commands, and open a pull request.

For feature work, use the selected project's original repository and its contribution instructions. Each project has its own license and review process; a fork and pull request may be required.
