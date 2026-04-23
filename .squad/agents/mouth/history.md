# Mouth — History

## Project Seed (2026-04-20)

**Project:** gh-tracker — Angular companion app for Gloomhaven board games
**User:** CIvanPiMa
**Stack:** Angular 17+, TypeScript, Node.js, JSON data, Docker
**Repo:** https://github.com/CIvanPiMa/gh-tracker
**Editions:** GH, FH, JotL, FC, CS, ToA, BB, GH2e + community editions
**Key paths:** `README.md`, `docs/`, `resources/`

## Learnings

### 2026-04-20 — Initial docs creation

**Architecture insights:**
- `scripts/build-data.js` compiles `data/{edition}/` into `src/assets/data/{edition}.json` — all source data is in `data/`, never edit compiled output
- Pre/post build hooks are wired into npm scripts: `prestart`, `prebuild`, `postbuild`, `pretest` all run the data build script automatically
- `branded: false` in environment files removes all upstream (Lurkars/gloomhaven-secretariat.de) references from UI
- nodemon (`npm run watch`) watches `data/` for JSON changes and re-runs `build-data.js`
- Angular SPA — catch-all server config needed for self-hosting

**File paths and structures learned:**
- `data/gh/base.json` — edition metadata (`edition`, `conditions`, `worldMap`, `logoUrl`)
- `data/gh/character/{name}.json` — character stats (per level 1–9), perks with `type: "remove|replace|add"` and card definitions
- `data/gh/monster/{name}.json` — stats for normal + elite per level 0–7, optional `actions` array on elite stats
- `data/gh/monster/deck/` — ability card deck definitions
- `data/gh/scenarios/{number}.json` — room definitions with per-player-count standee placement (`player2`, `player3`, `player4` keys)
- `data/gh/label/en.json` — flat key→string map; `spoiler/` subfolder for spoiler labels
- `data/schema.json` — JSON schema for compiled edition format
- `src/environments/` — 4 environment files: dev, prod, electron, unbranded

**Conventions and patterns found:**
- Monster stat entries use `"type": "elite"` to distinguish from normal; no type key = normal
- Scenario room monster entries support conditional spawning per player count
- Edition identifiers must match folder names exactly (`base.json#edition === folder name`)
- Pre-commit hook auto-formats `data/` files — use `--no-verify` to skip when making local-only data changes
- Community/optional content is enabled via **Data Management** in-app, not by default
- `docs/` folder did not exist before — created by this task
