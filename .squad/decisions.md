# Squad Decisions

## Active Decisions

### 2026-04-20 — README kept short (Mouth)
Detailed content delegated to `/docs/`. README now serves as entry point only — links to individual doc files. No `/docs/index.md` created; can be added later if docs grow.

### 2026-04-20 — Donation and personal sections removed from README (Mouth)
Upstream author's donation links and personal disclaimer are not appropriate for CIvanPiMa's fork. Archive section (references gloomhaven-secretariat.de version history) also removed as irrelevant to the fork.

### 2026-04-20 — Architecture documented without changes (Mikey)
No architectural changes introduced; `docs/architecture.md` reflects existing code exactly. Key patterns noted: plain-class singletons, signal-as-pulse (`uiChangeSignal`), underutilized command layer, silent storage migration, last-write-wins revision conflict model, edition extension graph.

### 2026-04-20 — data-format.md recommended as companion doc (Mikey)
`docs/data-format.md` identified as a needed companion to architecture docs for JSON field-level documentation. Delivered by Mouth in same sprint.

## Governance

- All meaningful changes require team consensus
- Document architectural decisions here
- Keep history focused on work, decisions focused on direction
