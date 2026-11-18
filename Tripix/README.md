# GDG Featureathon

## Repository 3: Tripix - Travel Booking Platform

This guide shows you how to get Tripix running on your computer and deploy your own copy. Tripix is a travel-booking frontend demo for searching bus, train, and flight trips and walking through a sample booking flow.

**Source project:** [MiladJoodi/Tripix](https://github.com/MiladJoodi/Tripix.git)

The project uses sample ticket data and saves some information in your browser. It is a demo interface, not a connection to real travel providers or a real ticket-purchasing service.

## What you need to install

| Software | Version | Download | What it is for |
| --- | --- | --- | --- |
| Git | Current stable version | [Install Git](https://git-scm.com/downloads) | Downloads the project |
| Node.js | 20.9 or newer | [Install Node.js](https://nodejs.org/en/download) | Runs and builds the app; npm is included |
| npm | Included with Node.js | [npm installation guide](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) | Installs the project's packages |
| Web browser | Current Chrome, Edge, or Firefox | [Chrome](https://www.google.com/chrome/), [Edge](https://www.microsoft.com/edge/download), or [Firefox](https://www.mozilla.org/firefox/new/) | Opens the app |
| GitHub account | Optional, but recommended | [Create a GitHub account](https://github.com/signup) | Lets your team fork the project and publish its changes |

Next.js 16 requires Node.js 20.9 or newer. The repository's Netlify settings select Node.js 20 for deployment. Check your installed versions in PowerShell or a terminal:

```powershell
git --version
node --version
npm --version
```

## Fork and clone the project

Forking gives your team a copy of the project that you can change and push to GitHub.

1. Sign in to GitHub and open the [Tripix repository](https://github.com/MiladJoodi/Tripix.git).
2. Select **Fork** and create the fork under your account.
3. Clone your fork. Replace `YOUR-USERNAME` with the GitHub username that owns your fork:

   ```powershell
   git clone https://github.com/YOUR-USERNAME/Tripix.git
   cd Tripix
   ```

If you only want to explore the original project, clone it directly instead:

```powershell
git clone https://github.com/MiladJoodi/Tripix.git
cd Tripix
```

## Install and run the app

### 1. Install the packages

From inside the `Tripix` folder, run:

```powershell
npm install
```

This downloads the libraries the project needs. It may take a few minutes the first time.

### 2. Start the development server

```powershell
npm run dev
```

Keep the terminal open while the app is running. Open <http://localhost:3000> in your browser. To stop the server, return to the terminal and press **Ctrl+C**.

## Build the production website

When you are ready to deploy, run these commands from the `Tripix` folder:

```powershell
npm install
npm run build
```

The build creates a static website in the `out` folder. This folder is what you deploy. A successful build does not publish the site by itself.

## Test

The repository does not define a dedicated automated test script. Run `npm run build` to check and generate the static site, then manually try the search, results, booking, confirmation, and profile pages in the local app.

## Deploy with Netlify (recommended)

The repository includes a `netlify.toml` file with the build settings, so Netlify can use the project's configured build command and output folder.

1. Push your team's changes to its GitHub fork.
2. Sign in or create an account at [Netlify](https://app.netlify.com/).
3. Choose **Add new site** / **Import an existing project**, connect GitHub, and select your Tripix fork.
4. Confirm the settings from `netlify.toml`:
   - **Build command:** `npm run build`
   - **Publish directory:** `out`
   - **Node.js version:** 20
5. Start the deployment. When it finishes, open the site URL Netlify provides.

Netlify can build and redeploy the site after you push later changes to the connected branch.

## Deploy the static build to another host

You can deploy Tripix to another static hosting service that supports Next.js static exports:

1. Run `npm install` and `npm run build`.
2. Upload the **contents** of the `out` folder to the host.
3. Follow that host's instructions for static sites and custom domains.

The project has static export enabled in `next.config.ts`; deploy the generated `out` folder, not the source folder.

## Optional: Deploy with Diploi

The upstream project also provides a [Diploi launch page](https://diploi.com/launch/MiladJoodi/Tripix).

1. Open the launch page and follow Diploi's steps to create a deployment.
2. In the deployed project's `next.config.ts`, add your Diploi development preview hostname to `allowedDevOrigins`. Use the hostname shown in your Diploi dashboard, without `https://`:

   ```ts
   import type { NextConfig } from "next";

   const nextConfig: NextConfig = {
     reactStrictMode: true,
     output: "export",
     trailingSlash: true,
     images: { unoptimized: true },
     allowedDevOrigins: ["YOUR-PREVIEW-HOSTNAME.diploi.me"],
   };

   export default nextConfig;
   ```

3. Save the change and restart the deployment in the Diploi dashboard.
4. Open the preview URL shown on the deployment page.

Replace `YOUR-PREVIEW-HOSTNAME.diploi.me` with your actual hostname. Do not copy the example hostname literally.

## Troubleshooting

- **`git`, `node`, or `npm` is not recognized:** Install the missing tool, close and reopen your terminal, and check its version again.
- **`npm install` fails:** Make sure your terminal is inside the `Tripix` folder and that you have an internet connection. Check that Node.js is version 20.9 or newer.
- **The app does not open:** Make sure `npm run dev` is still running and visit <http://localhost:3000>.
- **Port 3000 is already in use:** Stop the other app using that port. Next.js may also print a different local URL; use the URL shown in the terminal.
- **Netlify cannot find the build output:** Confirm the build command is `npm run build` and the publish directory is `out`.
