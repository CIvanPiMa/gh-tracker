# Usage Guide

This guide walks through using GH Tracker to manage your Gloomhaven-based campaign.

---

## First Launch and Initial Setup

1. Open the app at [http://localhost:4200](http://localhost:4200) (dev) or your hosted URL.
2. On first launch, you will see an empty board with a settings menu icon.
3. Open **Settings** (gear icon) to review options. Most features can be toggled on/off here.
4. Open **Data Management** (wrench icon or from the menu) to enable additional content packs (community editions, solo scenarios, Envelope X, etc.).

No account or sign-in is required. All state is stored locally in your browser's `localStorage`.

---

## Selecting an Edition and Starting a Campaign

1. From the main menu, go to **Campaign** → **New Campaign**.
2. Select your edition (Gloomhaven, Frosthaven, Jaws of the Lion, etc.).
3. Add characters using the **+ Add Character** button. Select the class and enter the player name.
4. The party sheet is now active. You can track party gold, achievements, and campaign progress from here.

To manage multiple campaigns, use **Campaign** → **Manage Campaigns**.

---

## Running a Scenario

### Setup

1. From the campaign view, select a scenario from the scenario list or the world map.
2. The app automatically populates monster groups and standees for the first room.
3. Set the **scenario level** (or let the app calculate it based on character levels).

### During a Scenario

**Each round:**

1. Each player enters their initiative (click the character's initiative field).
2. Click **Draw** (or press `n`) to draw monster ability cards and sort all figures by initiative.
3. Take turns in order. Click a figure to open its action menu.

**Initiative:** All figures are sorted automatically. Ties between monsters and characters can be resolved manually.

**Health tracking:** Click a figure → use `+`/`-` arrows (or keyboard `→`/`←`) to adjust HP. Characters auto-exhaust at 0 HP; monsters auto-die.

**Conditions:** Click a figure → toggle condition buttons (stun, muddle, poison, etc.). Conditions auto-expire at the start of the affected figure's turn where applicable.

**Monster standees:** The app automatically places standees when a new room or section opens. You can manually add/remove standees from the monster group menu.

**Elements:** Click element icons to advance them through their states (strong → waning → inert). The app auto-advances all elements at the end of each round.

### Ending a Scenario

Click **Finish Scenario** (or press `Shift+F`). The app applies all rewards:
- XP and gold to characters
- Scenario unlocks to the campaign
- Party achievements

---

## Key Features Walkthrough

### Attack Modifier Decks

- Each character has their own modifier deck, built from their starting deck plus perks.
- Click a character → **AM Deck** to view, draw (`m`), or draw with advantage (`a`) / disadvantage (`d`).
- The monster modifier deck is shared. Blessings and curses are added automatically from scenario rules or manually.
- You can reveal, remove, or rearrange cards in the deck editor.

### Loot Deck

- Enable via Settings → **Loot Deck**.
- Press `l` with a character active to draw a loot card. The app applies enhancements automatically.
- For Frosthaven, the town guard deck is also supported.

### Scenario Rules

- Special rules (e.g., "shuffle X cards into the AM deck", "apply condition to monster", named monsters with bonus abilities) are displayed automatically when the scenario or section loads.
- The app applies many rules automatically; others show a confirmation prompt.

### Character Progression

- Open a character sheet (click character icon or press `s` on a focused character) to view and edit:
  - Level, XP, gold/resources
  - Items (buy, equip, manage item states during scenarios)
  - Perks and their effect on the AM deck
  - Battle goals, masteries
- Retiring a character and creating a new one is handled through the character sheet.

### Frosthaven Outpost

- Between scenarios, manage the outpost: calendar, resource tracking, building upgrades, town guard deck, and outpost attacks.
- Building 81 (Trials) and Building 90 (Challenges) mechanics are automated where possible.

### Party Sheet and Campaign

- Access via `p` (party sheet) or `g` (world map).
- Track party achievements, reputation, donations, scenarios completed.
- The scenario flow chart is accessible via `c`.

---

## Multi-Client Sync with GHS Server

GH Tracker supports synchronizing state across multiple devices/clients via [GHS Server](https://github.com/Lurkars/ghs-server).

### Setup

1. Go to **Settings** → **Server**.
2. Enter a server URL (e.g., `wss://gloomhaven-secretariat.de`) or a self-hosted GHS Server address.
3. Enter or create a game code.
4. All clients connected to the same game code share state in real time.

### Permissions

The server supports per-client permission management. The host can grant or restrict actions (e.g., allow a client to only control specific characters).

### Self-hosting GHS Server

See [GHS Server](https://github.com/Lurkars/ghs-server) for setup instructions.

---

## Settings Overview

Open Settings (gear icon) to configure:

| Setting | Description |
|---|---|
| Scenario Level | Manual override or auto-calculate from character levels |
| Character Items | Enable item state tracking during scenarios |
| Battle Goals | Enable battle goal deck |
| Event Decks | Enable event card management |
| Loot Deck | Enable loot deck |
| Errata Hints | Show errata notifications |
| Display Options | HP display mode, trait display, player number labels |
| Server | GHS Server connection settings |
| Data Management | Enable/disable edition content packs |

Most features that impact physical component replacement can be toggled individually.

---

## Keyboard Shortcuts

GH Tracker has extensive keyboard shortcuts. Press `?` to show the shortcut overlay.

### Global shortcuts

| Key | Action |
|---|---|
| `Ctrl+Z` | Undo |
| `Ctrl+Y` / `Ctrl+Shift+Z` | Redo |
| `n` | Next round / Draw |
| `f` | Toggle fullscreen |
| `↑` / `+` | Zoom in |
| `↓` / `-` | Zoom out |
| `Ctrl+R` | Reset zoom |
| `ESC` / `←` | Open main menu |
| `m` | Draw AM card |
| `a` | Draw AM card with Advantage |
| `d` | Draw AM card with Disadvantage |
| `l` | Draw loot card / Inc. money tokens |
| `Shift+L` | Dec. money tokens |
| `1`–`6` | Toggle element state |
| `h` | Toggle hide absent figures |
| `s` | Select figure by number |
| `x` | Difficulty/level menu |
| `Alt+X` | Inc. XP (active character) |
| `Shift+X` | Dec. XP (active character) |
| `e` | Scenario effects menu |
| `Shift+F` | Finish scenario menu |
| `p` | Open party sheet |
| `g` | Open global map |
| `c` | Open scenario chart |
| `?` | Show keyboard shortcuts |

### Figure menu shortcuts

| Key | Action |
|---|---|
| `→` | Inc. current HP |
| `←` | Dec. current HP |
| `0`–`9` | Toggle condition |
| `x` | Inc. XP |
| `Shift+X` | Dec. XP |
| `l` / `Shift+L` | Inc./Dec. loot |
| `b` / `Shift+B` | Inc./Dec. bless |
| `c` / `Shift+C` | Inc./Dec. curse |
| `k` / `d` | Kill/exhaust |
| `s` | Open character sheet |
| `a` | Toggle character absent |

Full reference: [resources/keyboard-shortcuts.md](../resources/keyboard-shortcuts.md)

---

## Mobile and PWA Tips

- Install as a PWA for the best mobile experience (see [docs/installation.md](./installation.md#pwa-install-as-app)).
- The layout adapts to screen size. Rotate to landscape for more space.
- Use pinch-to-zoom or the `↑`/`↓` keyboard shortcuts to adjust zoom level.
- State is saved locally on the device. Use GHS Server if you want to share a session across devices.
- The app works fully offline once installed as a PWA.
