# Mikey — History

## Project Seed (2026-04-20)

**Project:** gh-tracker — Angular companion app for Gloomhaven board games
**User:** CIvanPiMa
**Stack:** Angular 17+, TypeScript, SCSS, Node.js build scripts, JSON data, Docker
**Repo:** https://github.com/CIvanPiMa/gh-tracker
**Key paths:** `src/app/`, `data/`, `scripts/`, `.squad/`
**Build:** `npm run start` (dev), `npm run build` (prod), `npm run test` (tests)

## Learnings

### 2026-04-20 — Architecture Documentation

**Key architectural patterns observed:**
- `GameManager` is a plain-class singleton (not Angular DI) exported as a module-level const — all managers share a reference to the same `Game` instance passed via constructor
- Angular Signals (`WritableSignal<number>`) used as a "version counter" pulse rather than storing reactive values; all components react to a single `uiChangeSignal` increment
- `GhsManager` is the only Angular `Injectable` in the business logic layer — it bridges the signal system to Angular's DI/effect world and runs cross-cutting reactive logic on every state change
- Command pattern (`CommandManager` + typed `Command` subclasses) provides named, serializable, undoable operations sitting below `StateManager`
- Storage is dual-backend: IndexedDB primary, LocalStorage fallback, with explicit migration on first IndexedDB availability
- `Game.revision` field is used for WebSocket conflict detection (server state wins; client creates backup on downgrade)

**Notable design decisions:**
- Plain class singletons over Angular services keeps business logic framework-independent and testable without Angular TestBed
- `OnPush` change detection throughout the UI means all re-renders are gated on `uiChangeSignal` — predictable and performant
- Edition data is compiled from source JSON at build time (not lazy-loaded individually), giving a single clean JSON blob per edition
- `base.json` in each edition folder is the only required file; all other content files are optional and default to empty arrays

**Important file paths:**
- `src/app/game/model/Game.ts` — single source of truth for all runtime state
- `src/app/game/businesslogic/GameManager.ts` — central coordinator + signal hub
- `src/app/game/businesslogic/GhsManager.ts` — Angular bridge (Injectable, effect-based)
- `src/app/game/businesslogic/StateManager.ts` — undo/redo, WebSocket, permissions
- `src/app/game/businesslogic/StorageManager.ts` — IndexedDB/LocalStorage abstraction
- `src/app/game/commands/CommandManager.ts` — command registry and dispatch
- `scripts/build-data.js` — data pipeline (data/ → src/assets/data/)
- `src/app/game/businesslogic/SettingsManager.ts` — edition URLs, locales, user prefs
- `src/app/ui/main.ts` — root Angular component (figure list, drag-drop, keyboard)
- `docs/architecture.md` — this document
