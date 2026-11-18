# Tripix

A travel booking frontend for searching and booking bus, train, and flight tickets.

**Original repository:** [https://github.com/MiladJoodi/Tripix.git](https://github.com/MiladJoodi/Tripix.git)

## Prerequisites

- Git
- Node.js 20 or newer
- npm
- A modern web browser

## Clone the project

In PowerShell:

```powershell
git clone https://github.com/MiladJoodi/Tripix.git
cd Tripix
```

## Install dependencies

```powershell
npm install
```

## Run locally

```powershell
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## Test

The repository does not define a dedicated test script. Build the static site to check compilation:

```powershell
npm run build
```

Then run the app locally and manually check the search, results, booking, confirmation, and profile pages.

## Deployment

The project is configured for static export and Netlify. Connect the GitHub repository to Netlify; the checked-in `netlify.toml` specifies:

- Build command: `npm run build`
- Publish directory: `out`
- Node.js version: 20

The generated `out` directory can also be hosted by another static hosting provider.

## Common issues

- **Wrong or missing Node.js version:** Install Node.js 20 or newer, then verify with `node --version`.
- **Port 3000 is already in use:** Stop the other local server or use the alternate URL shown by Next.js.
- **Build fails after dependencies were changed:** Run `npm install` again and retry `npm run build`.
- **Static deployment shows a blank page:** Confirm that the host publishes `out` and uses the repository's static-site configuration.
