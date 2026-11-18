# GDG FEATUREATHON
 
# Clone, Run, and Deploy

This guide is for the first of the five project repositories planned for the club event. It explains how to set up the **Shopify** demo on your computer, run it, and deploy it.

## Repository 1: Shopify - Simple eCommerce App

**Source repository:** [alim1496/simple-react-ecommerce](https://github.com/alim1496/simple-react-ecommerce)

Shopify is a frontend-only e-commerce demo built with React, TypeScript, Vite, Tailwind CSS, and Redux Toolkit. You can browse products, search, use categories, manage a cart and wishlist, and try the simulated login experience.

The app gets product data from [DummyJSON](https://dummyjson.com/), so it needs an internet connection. It does not need a database, environment variables, or a separately deployed backend.

## Before you start

Install these tools:

| Tool | Version | Why you need it |
| --- | --- | --- |
| [Git](https://git-scm.com/downloads) | Current stable version | Downloads the project source code |
| [Node.js](https://nodejs.org/en/download) | 20.x LTS | Runs the development server and builds the app |
| [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) | 10.x or newer | Installs the project's packages; npm is included with Node.js |
| Modern browser: [Chrome](https://www.google.com/chrome/), [Edge](https://www.microsoft.com/edge/download), or [Firefox](https://www.mozilla.org/firefox/new/) | Current version | Opens the app |
| [Docker Desktop](https://docs.docker.com/desktop/) (includes Docker Compose) | Optional | Runs the app in a production-like container |

To check whether Git, Node.js, and npm are installed, open PowerShell or a terminal and run:

```powershell
git --version
node --version
npm --version
```

The Node.js version should be 20.x and npm should be 10.x or newer. Docker is only needed if you choose the Docker deployment steps below.

## Run the app on your computer

### 1. Open a terminal

On Windows, open **PowerShell**. On macOS or Linux, open your terminal application.

### 2. Clone the repository

Cloning downloads a copy of the project to your computer:

```powershell
git clone https://github.com/alim1496/simple-react-ecommerce.git
```

Go into the new project folder:

```powershell
cd simple-react-ecommerce
```

### 3. Install project dependencies

Run this from inside the `simple-react-ecommerce` folder:

```powershell
npm ci
```

This installs the exact package versions recorded by the project. It may take a few minutes the first time.

### 4. Start the development server

```powershell
npm run dev
```

Keep this terminal open while you use the app. Open the URL printed in the terminal, usually <http://localhost:5173>.

When you change source files, Vite refreshes the app in the browser. To stop the server, return to the terminal and press **Ctrl+C**.

## Check the project

Run these commands from the project folder:

```powershell
npm run lint
npm run build
```

The build command checks and compiles the app, then puts the deployable files in the `dist` folder.

To preview that production build on your computer:

```powershell
npm run preview
```

Open the URL printed in the terminal, normally <http://localhost:4173>. Press **Ctrl+C** to stop the preview server.

## Run the Cypress tests (optional)

First, start the app in one terminal:

```powershell
npm run dev
```

Keep it running. Open a **second** terminal, go to the `simple-react-ecommerce` folder, and run either:

```powershell
npx cypress open
```

This opens the Cypress test interface. To run the tests in the terminal without opening the interface:

```powershell
npx cypress run
```

The configured test server is <http://localhost:5173/>.

## Deploy with Docker (optional)

Make sure Docker Engine is running, then run this from the project folder:

```powershell
docker compose up --build -d ecommerce-app
```

The production container is available at <http://localhost:3000>.

To view its logs:

```powershell
docker compose logs -f ecommerce-app
```

Press **Ctrl+C** to stop following the logs. The container keeps running until you stop it. To stop and remove the Compose resources:

```powershell
docker compose down
```

The Compose file also provides an optional containerized development server:

```powershell
docker compose --profile dev up --build ecommerce-dev
```

Open <http://localhost:5173/>. Press **Ctrl+C** in that terminal to stop it, then remove the development resources with:

```powershell
docker compose --profile dev down
```

## Deploy to a static hosting service (optional)

Build the production files:

```powershell
npm ci
npm run build
```

Upload the **contents** of the `dist` folder to a static host such as Netlify, Vercel, GitHub Pages, Azure Static Web Apps, or an Nginx server. If the host builds from the repository instead, use `npm run build` as the build command and `dist` as the output directory.

This app uses client-side routes, including `/products`, `/search`, `/wishlist`, and `/account`. Configure your host to serve `index.html` for routes it does not recognize; otherwise, opening or refreshing one of those pages directly may show a 404 error. For Nginx, the fallback rule is:

```nginx
location / {
    try_files $uri $uri/ /index.html;
}
```

## Troubleshooting

- **`git`, `node`, or `npm` is not recognized:** Install the missing tool and reopen your terminal. Check the version with the commands in [Before you start](#before-you-start).
- **`npm ci` fails:** Confirm you are in the `simple-react-ecommerce` folder and using the required Node.js and npm versions. Check your internet connection and try `npm ci` again.
- **The app cannot load products:** Check your internet connection and whether [DummyJSON](https://dummyjson.com/) is reachable.
- **A port is already in use:** Another app may be using port 5173, 4173, or 3000. Stop that app or configure a different port.
- **Docker commands fail:** Confirm Docker Engine is installed and running. For more build detail, try `docker compose build --no-cache ecommerce-app`.
- **A page shows 404 after refresh on a deployed site:** Configure the static host's single-page-app fallback to `index.html`, as described above.

## More event repositories

This README currently covers the first repository. Setup guides for the other four event repositories will be added when they are available.
