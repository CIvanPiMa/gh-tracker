# Installation Guide

This guide covers all ways to install or deploy GH Tracker.

---

## Prerequisites

- **Node.js** — current LTS release (v20+). Download at [nodejs.org](https://nodejs.org).
- **npm** — bundled with Node.js (v10+).
- **Git** — for cloning the repository.

Verify your versions:

```bash
node --version   # v20.x or newer
npm --version    # 10.x or newer
```

---

## Development Setup

Clone the repository and start the dev server:

```bash
git clone https://github.com/CIvanPiMa/gh-tracker.git
cd gh-tracker
npm install
npm run start
```

The dev server is available at [http://localhost:4200](http://localhost:4200).

`npm run start` runs `scripts/build-data.js` automatically (via `prestart`) to compile the JSON data files in `data/` into `src/assets/data/` before launching the Angular dev server.

To watch for data file changes while developing:

```bash
npm run watch
```

This uses [nodemon](https://nodemon.io/) to re-run `build-data.js` whenever any file under `data/` changes.

### Docker (dev mode)

If you prefer Docker for development:

```bash
docker compose -f docker-compose.dev.yaml up -d
```

---

## Production Build

```bash
npm run build
```

The `prebuild` hook runs `build-data.js` and `pre-build.js` automatically. The output is placed in `./dist/gloomhavensecretariat/`.

To serve the build locally for testing:

```bash
npx serve ./dist/gloomhavensecretariat
```

> The default production build sets the base URL to `/`. To use a different base path (e.g. for hosting at `example.com/gh-tracker/`), pass `--base-href`:
>
> ```bash
> npm run build -- --base-href /gh-tracker/
> ```

---

## Docker

### Production (Docker Compose)

```bash
docker compose up -d
```

This uses `docker-compose.yaml` and serves the app on port 80.

### Development (Docker Compose)

```bash
docker compose -f docker-compose.dev.yaml up -d
```

### Standalone Docker

```bash
docker pull gloomhavensecretariat/ghs
docker run --rm -p 80:80 --name ghs gloomhavensecretariat/ghs
```

---

## Self-Hosting

Two options:

**Option A — Pre-built release:**  
Download the zip from the [latest release](https://github.com/Lurkars/gloomhavensecretariat/releases/latest) and unzip it into your web server's document root (nginx, Apache, Caddy, etc.).

**Option B — Build from source:**  
Follow the [Production Build](#production-build) steps above, then copy `./dist/gloomhavensecretariat/` to your web server.

The app is a static Angular SPA. Configure your web server to serve `index.html` for all routes (catch-all / try_files).

---

## PWA (Install as App)

GH Tracker is a Progressive Web App — it can be installed on any device that supports PWAs:

- **Chrome (desktop/Android):** [Instructions](https://support.google.com/chrome/answer/9658361)
- **Safari (iOS/iPadOS):** [Instructions](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Installing#safari_for_ios_iphoneos_ipados)
- **Firefox (Android):** [Instructions](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Installing#firefox_for_android)
- Other browsers: search for "install PWA \<your browser\>"

Once installed, the app works fully offline.

---

## Electron (Standalone Desktop App)

An Electron build is available for Linux, Mac, and Windows.

**Download a pre-built binary:**  
Get the appropriate file from the [latest release](https://github.com/Lurkars/gloomhavensecretariat/releases/latest) assets.

> Linux: AppImage format. Make executable with `chmod +x <file>.AppImage` before running.

**Build from source:**

```bash
npm run electron:build
# then run:
electron . --no-sandbox
# or shortcut:
npm run electron
```

---

## Environment Configuration

Environment files are in `src/environments/`:

| File | Used for |
|---|---|
| `environment.ts` | Development (`ng serve`) |
| `environment.prod.ts` | Production builds |
| `environment.electron.ts` | Electron builds |
| `environment.unbranded.ts` | Unbranded/fork builds |

### Disabling upstream branding

If you are running a fork and want to hide references to `gloomhaven-secretariat.de`, `Lurkars`, feedback dialogs, and public server lists, set `branded: false` in the relevant environment file:

```typescript
// src/environments/environment.prod.ts
export const environment = {
  production: true,
  branded: false,   // <-- set this
  // ...
};
```

This removes upstream help links, feedback dialogs, and the public GHS server list from the UI.
