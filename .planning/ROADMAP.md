# Roadmap: Maestro GSD Integration

## Overview

PRD Queue integration for Maestro using local Obsidian vault files. Items sync via Obsidian Sync from server to Mac. Maestro reads/writes local files - no SSH needed. Architecture follows Maestro's IPC-first pattern.

**Vault location:** `/Users/hunterharris/Documents/Gigabrands/gsd-system/`

## Phases

- [ ] **Phase 1: Foundation** - Folder structure + IPC for local gsd-system
- [ ] **Phase 2: Queue UI Shell** - PRD Queue tab with folder navigation
- [ ] **Phase 3: Read-Only Queue** - Display items with status and refresh
- [ ] **Phase 4: Scoping Engine** - Convert inbox notes to executable checklists
- [ ] **Phase 5: Scoping UI** - Scope button and progress indicator
- [ ] **Phase 6: Execution Engine** - Connect scoped PRDs to Auto Run
- [ ] **Phase 7: Execution UI** - Run button and status tracking
- [ ] **Phase 8: File Watching** - Real-time queue updates via fs watch
- [ ] **Phase 9: Telegram Integration** - Server-side remote queue control

## Phase Details

### Phase 1: Foundation
**Goal**: Folder structure exists and IPC handlers read gsd-system
**Depends on**: Nothing (first phase)
**Requirements**: IPC-01, IPC-02
**Success Criteria**:
  1. gsd-system/ folder exists in Obsidian vault with inbox/scoped/running/completed subfolders
  2. `window.maestro.prdQueue.list('inbox')` returns array of file items
  3. `window.maestro.prdQueue.read(path)` returns file content
  4. IPC errors propagate with meaningful messages

Plans:
- [ ] 01-01: Create folder structure and IPC handlers

### Phase 2: Queue UI Shell
**Goal**: PRD Queue tab exists in RightPanel with folder navigation
**Depends on**: Phase 1
**Requirements**: UI-01, UI-02
**Success Criteria**:
  1. "PRD Queue" tab appears in RightPanel alongside Files/History/Auto Run
  2. Folder tabs show inbox/scoped/running/completed
  3. Clicking a folder tab switches the displayed list
  4. Empty state displays when folder has no items

Plans:
- [ ] 02-01: PRDQueuePanel component
- [ ] 02-02: Folder navigation tabs

### Phase 3: Read-Only Queue
**Goal**: Users can view queue items with status indicators
**Depends on**: Phase 2
**Requirements**: UI-03, UI-04, UI-07
**Success Criteria**:
  1. Items display with checkboxes for multi-selection
  2. Status badges show correct state (pending/scoping/scoped/running/done)
  3. Refresh button reloads queue from disk
  4. Clicking an item shows its content in preview

Plans:
- [ ] 03-01: Item list with selection
- [ ] 03-02: Status badges and refresh

### Phase 4: Scoping Engine
**Goal**: Raw inbox notes transform into executable markdown checklists
**Depends on**: Phase 1
**Requirements**: SCOPE-01, SCOPE-02, SCOPE-03, SCOPE-04
**Success Criteria**:
  1. Raw text note converts to markdown with task checkboxes
  2. Tasks follow GSD-style breakdown (actionable, specific)
  3. Scoped file moves from inbox/ to scoped/ folder
  4. Multiple items can be scoped in batch

Plans:
- [ ] 04-01: Scoping transformer logic
- [ ] 04-02: Batch processing and file movement

### Phase 5: Scoping UI
**Goal**: Users can trigger scoping from the queue interface
**Depends on**: Phase 3, Phase 4
**Requirements**: UI-05, SCOPE-05, IPC-03, IPC-04
**Success Criteria**:
  1. "Scope Selected" button appears when items selected in inbox
  2. Button triggers scoping of all selected items
  3. Progress indicator shows during scoping
  4. Items move from inbox to scoped after completion
  5. UI updates to reflect new item locations

Plans:
- [ ] 05-01: Scope button and IPC integration
- [ ] 05-02: Progress indicator and state updates

### Phase 6: Execution Engine
**Goal**: Scoped PRDs can execute through Maestro's Auto Run system
**Depends on**: Phase 4
**Requirements**: EXEC-01, EXEC-02, EXEC-03, EXEC-04
**Success Criteria**:
  1. Scoped PRD loads into Auto Run as a document
  2. Execution triggers Maestro's existing batch processor
  3. File moves to running/ when execution starts
  4. File moves to completed/ when execution finishes

Plans:
- [ ] 06-01: Auto Run integration
- [ ] 06-02: Execution lifecycle and file movement

### Phase 7: Execution UI
**Goal**: Users can trigger and monitor execution from queue interface
**Depends on**: Phase 5, Phase 6
**Requirements**: UI-06, EXEC-05
**Success Criteria**:
  1. "Run All Scoped" button appears in scoped folder view
  2. Button triggers batch execution of all scoped items
  3. Execution status reflects in queue UI (running badge)
  4. Completed items show done badge

Plans:
- [ ] 07-01: Run button and status integration

### Phase 8: File Watching
**Goal**: Queue updates automatically when local files change
**Depends on**: Phase 3
**Requirements**: IPC-05
**Success Criteria**:
  1. New files in inbox/ appear in queue without manual refresh
  2. File movements between folders reflect in UI automatically
  3. Watch uses efficient fs.watch (not polling)
  4. Changes from Obsidian Sync trigger UI updates

Plans:
- [ ] 08-01: File watch IPC and event handling

### Phase 9: Telegram Integration
**Goal**: Users can control queue remotely via Telegram bot (server-side)
**Depends on**: Phase 5, Phase 7
**Requirements**: TG-01, TG-02, TG-03, TG-04, TG-05
**Success Criteria**:
  1. "Queue" button in Telegram shows pending inbox items
  2. User can select multiple items via inline keyboard
  3. "Scope Selected" writes to inbox/ (syncs to Mac via Obsidian Sync)
  4. "Run All" can trigger maestro-cli if Mac is running
  5. Status updates send back to Telegram

Plans:
- [ ] 09-01: Telegram bot queue display
- [ ] 09-02: Selection and action handlers
- [ ] 09-03: Status notification system

## Progress

| Phase | Plans | Status |
|-------|-------|--------|
| 1. Foundation | 0/1 | Not started |
| 2. Queue UI Shell | 0/2 | Not started |
| 3. Read-Only Queue | 0/2 | Not started |
| 4. Scoping Engine | 0/2 | Not started |
| 5. Scoping UI | 0/2 | Not started |
| 6. Execution Engine | 0/2 | Not started |
| 7. Execution UI | 0/1 | Not started |
| 8. File Watching | 0/1 | Not started |
| 9. Telegram Integration | 0/3 | Not started |

**Total:** 9 phases, 16 plans

---
*Roadmap created: 2026-02-01*
*Last updated: 2026-02-01*
