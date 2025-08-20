# Setup
- I had ChatGPT generate  a React starter app **rbg-pulseid-widget-react**.
	- Includes:
		- The React frontend with preview functionality
		- Netlify proxy setup and netlify.toml
		- Placeholder for your `pulseid-proxy.js` function. I will replace this with my old one under the `pulseid-proxy-netlify` project.
		- package.json - Contains the package dependencies for react and vite
		- vite.config.js
	- Unzip file from ChatGPT to rbg-pulseid-widget-react
- **Important** - Disable PC Matic antivirus
	- Right click icon PC Matic icon on the mac menu bar
	- Settings > Pause for 1 hour.
	- Icon should turn red.
- Initialize node.js packages
  
  ```bash
  nvm use 20.19.4
  npm install
  
  // Start server to test
  npm run dev
  ```


- GitHub Repo Setup
	- Go to [https://github.com/new](https://github.com/new) and create a repo called `rbg-pulseid-widget-react`.
	- Open terminal window at the new project - `rbg-pulseid-widget-react`
	- git init
	- git remote add origin https://github.com/lansingsp-dev/rbg-pulseid-widget-react.git
	- git add .
	- git commit -m "Initial commit"
	- git push -u origin main
- Open new project in WebStorm
- Update `pulseid-proxy.js` with my old one under the `pulseid-proxy-netlify` project.
- Commit and push changes.
- Create .gitignore file and commit and push.
- In Neflify dashboard, unlink Old Repository for - `pulseid-proxy-netlify`
- Create New Netlify Site From Git
	- Choose your new repo: `rbg-pulseid-widget-react`
	- Set build command
		- `npm run build`
	- Set publish directory
		- `dist`
	- Netlify will auto-detect your netlify.toml and pick up the netlify/functions folder

# NPM Commands

- npm install - install need packages defined in package.json
- npm run dev - Starts the Vite development server with hot reloading for local development. Gives you a fast, live-reloading dev environment.
- npm run build - Generates a production-ready, static bundle in the dist/ folder. Only run this when you’re ready to deploy to production (e.g., Netlify).

**npm run dev**
Starts the Vite development server:
	•	Instant server start
	•	Hot module replacement (HMR)
	•	Fast updates in the browser

**npm run build**
Triggers Vite’s build process, which uses Rollup under the hood:
	•	Bundles your app for production
	•	Outputs static assets to the dist/ directory
	•	Applies optimizations like minification and tree shaking

**npm run preview**
Runs a local static server to preview the production build:
	•	Serves files from the dist/ folder
	•	Lets you test the final result before deploying

# What is Vite?

**Vite** (pronounced like "veet", from the French word for *fast*) is a **modern front-end build tool** designed to be extremely fast and developer-friendly. It was created by Evan You, the creator of Vue.js, but supports a wide range of frameworks, including:

- React
- Vue
- Svelte
- SolidJS
- Preact
- Vanilla JS

---

## What Does Vite Do?

Vite is used to:

- 🚀 Serve your app in development (`npm run dev`)
- 📦 Bundle and optimize your app for production (`npm run build`)
- 🔁 Enable Hot Module Replacement (HMR) for real-time updates during development
- ✅ Use modern ES Modules natively, reducing the need for bundling during development

---

## Why Use Vite Over Webpack or Create React App?

| Feature                 | **Vite**                         | **Webpack / CRA**              |
|-------------------------|----------------------------------|--------------------------------|
| Dev server startup time | ⚡ Instant (native ESM)          | 🐢 Slower                      |
| HMR speed               | 🔁 Fast                          | 🕒 Slower                      |
| Config simplicity       | 🧼 Minimal setup                 | ⚙️ Often complex               |
| Build performance       | 🔨 Uses Rollup internally (fast) | 🧱 Slower builds               |

---

## Typical NPM Scripts in a Vite Project

```json
"scripts": {
  "dev": "vite",           // Starts local dev server
  "build": "vite build",   // Creates production build
  "preview": "vite preview"// Previews the production build locally
}

```

 So, when you run npm run dev, build, or preview, you’re running **Vite under the hood**.
# Vite and npm Scripts

# Vite Commands Explained (`npm run dev`, `npm run build`, `npm run preview`)

## `npm run dev`
- **Purpose**: Starts a local development server.
- **Use case**: Used while developing your app.
- **Features**:
  - Hot Module Replacement (HMR) — updates the browser instantly as you make changes.
  - Fast startup and rebuilds.
- **Runs**: `vite` in development mode.

---

## `npm run build`
- **Purpose**: Builds the app for production.
- **Use case**: When you’re ready to deploy your app (e.g., to Netlify or Vercel).
- **Features**:
  - Bundles all JavaScript, CSS, and assets.
  - Minifies and optimizes for performance.
- **Runs**: `vite build`
  - Outputs files to the `dist/` folder by default.

---

## `npm run preview`
- **Purpose**: Serves the production build locally.
- **Use case**: To test how the built app behaves in a production-like environment before deploying.
- **Features**:
  - Serves files from the `dist/` folder.
  - Helps identify issues that don’t appear during development (e.g., asset paths, routing).
- **Runs**: `vite preview`

---

## Summary Table

| Command           | Purpose                         | When to Use               |
| ----------------- | ------------------------------- | ------------------------- |
| `npm run dev`     | Starts dev server with HMR      | While actively developing |
| `npm run build`   | Builds optimized production app | Before deployment         |
| `npm run preview` | Serves built app locally        | Test production build     |
# Netlify

```bash
cd ~/dev/projects/rbg-pulseid-widget-react
netlify dev
```

This will:
	•	Serve your app at http://localhost:8888
	•	Make this available: `http://localhost:8888/.netlify/functions/pulseid-proxy`

