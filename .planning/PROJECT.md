# Maestro GSD Integration

## What This Is

A private Maestro fork with PRD Queue integration. Items flow from Obsidian Inbox through GSD scoping into Maestro for batch execution. Captures ideas anywhere (Telegram/Slack/iPhone), scopes them into executable PRDs, and runs them in parallel through Maestro agents.

## Core Value

One-click batch execution: queue items from anywhere, scope them all into PRDs, run them all through Maestro simultaneously.

## Requirements

### Validated

(None yet — ship to validate)

### Active

- [ ] QUEUE-01: PRD Queue view in Maestro showing all pending items from gsd-system/inbox/
- [ ] QUEUE-02: Multi-select items in queue view
- [ ] QUEUE-03: "Scope All" button runs GSD planning on each selected item
- [ ] QUEUE-04: "Run All" button triggers Maestro auto-run on all scoped PRDs
- [ ] FLOW-01: Items flow: inbox/ → scoped/ → running/ → completed/
- [ ] FLOW-02: Queue view shows item status (pending/scoping/scoped/running/done)
- [ ] FLOW-03: Folder structure syncs to Obsidian via existing Obsidian Sync
- [ ] TG-01: Telegram "Queue" button shows all pending inbox items
- [ ] TG-02: Telegram inline selection for batch operations
- [ ] TG-03: "Scope Selected" triggers GSD planning via server
- [ ] TG-04: "Run All" triggers maestro-cli from server
- [ ] SCOPE-01: GSD scoping converts raw notes into PRD markdown with checklists
- [ ] SCOPE-02: PRDs include task breakdown Maestro can process
- [ ] CLI-01: maestro-cli integration for triggering runs from server
- [ ] SYNC-01: Server gsd-system/ accessible from Maestro via SSH

### Out of Scope

- Real-time collaboration — single user system
- Mobile app — Telegram/Obsidian mobile covers capture
- Voice commands — text-based workflow
- Custom AI models — use existing Claude/Anthropic

## Context

**Existing Infrastructure:**
- Server: gigabrands-dev running clawdbot with inbox-watcher skill
- Obsidian vault: /Users/hunterharris/Documents/Gigabrands (synced to server)
- Telegram bot: PRDFactory (8467853296) handles callbacks
- Server gsd-system: /home/dev/gsd-system/ with inbox/ folder
- Maestro: installed at /Applications/Maestro.app, connects via SSH to server

**Already Working:**
- Inbox polling and Telegram notifications
- GSD/Assign/Read buttons on new items
- Single-item queuing to gsd-system/inbox/
- PRD Queue sync to Obsidian (cron job)

**Private Fork:**
- Origin: github.com/Gigabrained/maestro-gsd
- Upstream: github.com/pedramamini/Maestro
- Can pull upstream updates with `git pull upstream main`

## Constraints

- **Tech stack**: Electron/TypeScript/Vite (Maestro's existing stack)
- **Server**: Must work with existing clawdbot/gsd-system on gigabrands-dev
- **Privacy**: All customizations stay in private repo
- **Updateability**: Must be able to merge upstream Maestro updates

## Key Decisions

| Decision | Rationale | Outcome |
|----------|-----------|---------|
| Private mirror over fork | GitHub doesn't allow private forks of public repos; need to keep customizations private | — Pending |
| Separate PRDFactory bot | Avoids Telegram polling conflicts with main clawdbot | — Pending |
| GSD scoping on server | Keeps AI processing centralized, Maestro just executes | — Pending |
| Folder-based state machine | inbox→scoped→running→completed is simple and visible in Obsidian | — Pending |

---
*Last updated: 2026-02-01 after initialization*
