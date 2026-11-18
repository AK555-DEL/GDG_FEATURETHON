# Tripix

Tripix is a sample travel search and booking application for bus, train, and air trips. Existing flows include city and date selection, search filters, ticket selection, passenger details, review and confirmation screens, booking history, ticket views, and a profile area. It uses local sample data and does not purchase real tickets.

**Upstream repository:** [MiladJoodi/Tripix](https://github.com/MiladJoodi/Tripix)

For event details, see the [central README](../README.md).

## Prerequisites

- [Git](https://git-scm.com/install/)
- [Node.js](https://nodejs.org/en/download) 24 LTS is recommended. The upstream Next.js 16.2.1 dependency requires Node.js `>=20.9.0`.
- npm, included with Node.js.
- No database or API credentials are required; the app uses sample data.
- [Visual Studio Code](https://code.visualstudio.com/download) and [Google Chrome](https://www.google.com/chrome/) are optional.

## Verify the tools

In PowerShell:

```powershell
git --version
node --version
npm.cmd --version
```

On macOS or Linux, run `npm --version` instead of `npm.cmd --version`.

## Clone the project

In PowerShell:

```powershell
git clone https://github.com/MiladJoodi/Tripix.git
cd Tripix
```

## Install dependencies

The repository contains an npm lockfile (`package-lock.json`, lockfile version 3). Run it from the project directory:

```powershell
npm.cmd ci
```

On macOS or Linux, use `npm ci`.

## Environment configuration

No database, API credentials, `.env` file, or environment variables are required. Search and booking data are included locally.

## Start the development server

```powershell
npm.cmd run dev
```

Open [http://localhost:3000](http://localhost:3000). If Next.js reports another port, open the URL it prints.

On macOS or Linux, use `npm run dev`.

## Where to implement features

- `src/app/` — Next.js routes and pages, including search, booking, confirmation, bookings, tickets, and profile.
- `src/features/` — search and booking feature components.
- `src/components/` — shared layout and reusable UI components.
- `src/data/` — local city, provider, and ticket data.
- `src/store/` — application state.
- `src/hooks/` — reusable React hooks.
- `src/types/` and `src/utils/` — types and helper logic.

Before changing code, run through search, result filtering, ticket selection, passenger entry, review, confirmation, and booking history. Useful improvements include clearer validation, richer filters, sorting, accessibility, saved searches, trip comparison, mobile usability, and better empty or error states.

## Troubleshooting

- **Node.js version error:** use Node.js 24 LTS or another version meeting `>=20.9.0`.
- **Port 3000 is busy:** use the alternate URL printed by Next.js.
- **Lockfile mismatch:** the checked-in lockfile names the project `bilit`, while `package.json` names it `tripix`. If `npm ci` reports it as out of sync, ask an organizer rather than changing or regenerating the lockfile.
- **Lint command:** the upstream `lint` script uses `next lint`, which is no longer supported by Next.js 16. Do not rely on this script during the event.
- **Build:** `npm.cmd run build` on Windows or `npm run build` on macOS/Linux exists in the upstream `package.json`. The current install and browser launch were not verified in this documentation audit.

## Final demonstration checklist

- What problem did you identify, and why does it matter to users?
- What improvement did you propose?
- What did you implement?
- Can you demonstrate it end to end on the running application?
- How is the improved experience better than the original?

Present a meaningful implementation or working prototype, not only an idea. A production-ready feature is not required.
