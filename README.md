# GH Tracker

![Screenshot](./resources/Screenshot.png)

> Scenario 1 of Gloomhaven with starting classes of different editions

**Table of Contents**:

- [Introduction](#introduction)
- [Quick Start](#quick-start)
- [Features](#features)
  - [Scenario Tracking](#scenario-tracking)
- [Install](#install)

## Introduction

*GH Tracker* is a **companion app** for Gloomhaven-based board games.
It manages scenario play by tracking initiative, health, conditions, and monster standees Automates attack modifier and loot decks;
Applies scenario-specific rules; and
Tracks full character, party, and campaign progression across **Gloomhaven**, **Frosthaven**, **Jaws of the Lion**, **Forgotten Circles**, **Gloomhaven 2nd Edition**, **Button & Bugs**, **The Crimson Scales**, **Trail of Ashes**, and more.

It runs in any modern browser with no install required, supports multi-client sync via [GHS Server](https://github.com/Lurkars/ghs-server), and can be installed as a PWA or Electron app for offline use.

This is a fork of [Lurkars/gh-tracker](https://github.com/Lurkars/gh-tracker) maintained by CIvanPiMa.

> [!WARNING]
>
> **SPOILER WARNING:** The `label/spoiler` folder in `data/` — and therefore the compiled edition files in `src/assets/data/` — contains spoilers. See [upstream discussion #103](https://github.com/Lurkars/gh-tracker/discussions/103) for details.

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
- **Electron:** Download from the [latest release](https://github.com/Lurkars/gh-tracker/releases/latest) assets (Linux, Mac, Windows)
- **Self-host:** Unzip the release zip onto your web server, or run `docker compose up -d`
- **Build from source:** `npm run build` — output at `./dist/gh-tracker`
