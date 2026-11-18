# Tripix

**Original repository:** [https://github.com/MiladJoodi/Tripix.git](https://github.com/MiladJoodi/Tripix.git)

## 1. Overview

Tripix is a travel-booking frontend demo for searching buses, trains, and flights and walking through a sample booking flow. It uses Next.js, React, TypeScript, and Tailwind CSS.

The app uses sample data and browser storage. It does not connect to real travel providers or purchase real tickets.

## 2. Prerequisites

Required:

- Git.
- Node.js 20.9 or newer (required by Next.js 16).
- npm, included with Node.js.
- A modern browser.

No database, account, or external travel API credential is required for the local demo. A GitHub account is needed only if you want to fork and push your work.

## 3. Verify prerequisites

In PowerShell:

```powershell
node -v
npm -v
git --version
```

Confirm Node reports version 20.9 or newer.

## 4. Fork and clone

For work you plan to push, open the [original repository](https://github.com/MiladJoodi/Tripix.git) on GitHub and select **Fork**. Then clone your fork, replacing `YOUR-USERNAME` with your GitHub username:

```powershell
git clone https://github.com/YOUR-USERNAME/Tripix.git
cd Tripix
```

To explore without pushing changes, clone the original URL instead.

## 5. Install dependencies

Use the committed `package-lock.json`:

```powershell
npm ci
```

This installs the locked dependencies from the project root.

## 6. Environment configuration

No `.env` file or external service is needed to run the local demo. It uses sample travel data and stores some information in the browser.

## 7. Run locally

From the `Tripix` project folder:

```powershell
npm run dev
```

Keep the terminal open and open [http://localhost:3000](http://localhost:3000). Press **Ctrl+C** to stop the server. If Next.js prints a different URL because the default port is busy, use the URL shown in the terminal.

## 8. Verify the app

- Confirm the home page loads.
- Try searching for a trip and opening the results.
- Walk through the sample booking and confirmation flow.
- Check the browser and terminal consoles for errors.
- Remember that searches and bookings are a demo, not live travel inventory or real ticket purchases.

## 9. Project structure

| Path | Purpose |
| --- | --- |
| `src/app/` | Next.js routes and page-level UI. |
| `src/components/` | Shared layout and interface components. |
| `src/features/` | Search and booking feature components. |
| `public/` | Static images and other public assets. |
| `next.config.ts` | Next.js configuration, including static export settings. |
| `netlify.toml` | Netlify build and deployment settings. |

## 10. Start developing a feature

Choose a focused improvement to a search, results, booking, confirmation, or profile view. Follow existing route and component patterns, and keep `npm run dev` running to review the change in the browser. Do not present sample data or booking behavior as a real travel service.

## 11. Test, build, and deploy

The repository does not define a dedicated automated test script. Its `lint` script currently calls `next lint`, which is not supported by the checked-in Next.js 16 version and fails on a clean install. Use the production build as the automated check and manually exercise the app. **NOT TESTED:** manual browser flows were not part of this clean-clone check.

```powershell
npm run build
```

On the Windows clean-clone check with Node.js 24.22.3 and npm 11.19.1, `npm ci` and `npm run build` succeeded; `npm run lint` failed as described above.

The project has static export enabled. A successful build writes the static website to `out/`; `npm run start` is not a local preview command for this static export. Use the development server for interactive local checks. Netlify deployment is configured in `netlify.toml`:

- Build command: `npm run build`
- Publish directory: `out`
- Node.js version: 20

To deploy, push your fork to GitHub, import that fork into Netlify, and confirm those settings. Deployment accounts are optional and are not needed to run the local app.

## 12. Troubleshooting and submission

- **Node version error:** Install Node.js 20.9 or newer, reopen PowerShell, and check `node -v`.
- **Install fails:** Confirm you are in the folder containing `package.json` and `package-lock.json`, then retry `npm ci`.
- **The app does not open:** Keep `npm run dev` running and use the exact URL Next.js prints.
- **Port 3000 is busy:** Stop the other process or open the alternate local URL printed by Next.js.
- **Netlify does not publish the site:** Confirm `npm run build` succeeds and the publish directory is `out`.
- **A booking does not connect to a provider:** This demo uses sample data and does not book real travel.

For event work, fork the original project, create a feature branch, commit and push to your fork, then follow the organizers' announced submission process. Open an upstream pull request only if the maintainers accept contributions. Do not push directly to the original repository.
