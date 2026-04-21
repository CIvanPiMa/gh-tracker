# GH Tracker

<img width="776" alt="image" src="./resources/Screenshot.png">

> Scenario 1 of Gloomhaven with starting classes of different editions

**Table of Contents**:

- [Introduction](#introduction)
- [Quick Start](#quick-start)
- [Features](#features)
  - [Scenario Tracking](#scenario-tracking)
- [Install](#install)
- [Contributing](#contributing)
- [Privacy](#privacy)
- [Copyright / License](#copyright--license)

## Introduction

*GH Tracker* is a **companion app** for Gloomhaven-based board games.

It manages scenario play by tracking initiative, health, conditions, and monster standees

Automates attack modifier and loot decks;

Applies scenario-specific rules; and

Tracks full character, party, and campaign progression across **Gloomhaven**, **Frosthaven**, **Jaws of the Lion**, **Forgotten Circles**, **Gloomhaven 2nd Edition**, **Button & Bugs**, **The Crimson Scales**, **Trail of Ashes**, and more.

It runs in any modern browser with no install required, supports multi-client sync via [GHS Server](https://github.com/Lurkars/ghs-server), and can be installed as a PWA or Electron app for offline use.

This is a fork of [Lurkars/gloomhavensecretariat](https://github.com/Lurkars/gloomhavensecretariat) maintained by CIvanPiMa.

> [!WARNING]
>
> **SPOILER WARNING:** The `label/spoiler` folder in `data/` — and therefore the compiled edition files in `src/assets/data/` — contains spoilers. See [upstream discussion #103](https://github.com/Lurkars/gloomhavensecretariat/discussions/103) for details.

## Quick Start

```bash
git clone https://github.com/CIvanPiMa/gh-tracker.git
cd gh-tracker
npm install
npm run start      # dev server at http://localhost:4200
```

For Docker: `docker compose up -d`

See [docs/installation.md](./docs/installation.md) for full installation options including Docker, PWA, Electron, and self-hosting.

## Features

### Scenario Tracking

- **Initiative** sorting for all figures
- **Health** — automatic exhaust/dead, per-level max values

## Install

See [docs/installation.md](./docs/installation.md) for the full guide. Quick options:

- **PWA:** Open in browser → install via browser menu. [Chrome](https://support.google.com/chrome/answer/9658361) · [Safari iOS](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Installing#safari_for_ios_iphoneos_ipados) · [Firefox Android](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Installing#firefox_for_android)
- **Electron:** Download from the [latest release](https://github.com/Lurkars/gloomhavensecretariat/releases/latest) assets (Linux, Mac, Windows)
- **Self-host:** Unzip the release zip onto your web server, or run `docker compose up -d`
- **Build from source:** `npm run build` — output at `./dist/gloomhavensecretariat`

## Contributing

See [docs/contributing.md](./docs/contributing.md). All data is in `data/` as human-readable JSON — data fixes and translations are especially welcome.

For translations, use [Weblate](https://i18n.gloomhaven-secretariat.de/) (log in with GitHub).

<img src="https://i18n.gloomhaven-secretariat.de/widget/gloomhavensecretariat/multi-auto.svg" alt="Translation status" />

## Privacy

This application does NOT collect any personal data. Everything runs and stays in your browser/local memory. For the server component, see [GHS Server#Privacy](https://github.com/Lurkars/ghs-server#privacy).

## Copyright / License

Gloomhaven and all related properties, images and text are owned by [Cephalofair Games](https://cephalofair.com).

Assets/Data used:

- [Creator Pack by Isaac Childres](https://boardgamegeek.com/thread/1733586/files-creation) CC BY-NC-SA 4.0
- [Worldhaven](https://github.com/any2cards/worldhaven)
- [Nerdhaven Images](https://drive.google.com/drive/folders/16wSfzvrSlpbGY8l4eWn8dnHjDUF7A2_e)
- [X-haven Assistant](https://github.com/Tarmslitaren/FrosthavenAssistant)
- [Gloomhaven Item DB](https://github.com/heisch/gloomhaven-item-db)
- [Virtual Gloomhaven Board](https://github.com/PurpleKingdomGames/virtual-gloomhaven-board)
- [Frosthaven - Previously On](https://github.com/jenkinsonc/frosthaven-previouslyon)
- Some other assets are licensed under public domain

Source code is licensed under [AGPL](/LICENSE)
