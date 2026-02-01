# Requirements: Maestro GSD Integration

**Defined:** 2026-02-01
**Core Value:** One-click batch execution of PRD queue items through Maestro

## v1 Requirements

### PRD Queue UI

- [ ] **UI-01**: PRD Queue tab in RightPanel showing items from server gsd-system/
- [ ] **UI-02**: Folder view: inbox/ → scoped/ → running/ → completed/
- [ ] **UI-03**: Multi-select items with checkboxes
- [ ] **UI-04**: Status badges per item (pending/scoping/scoped/running/done)
- [ ] **UI-05**: "Scope Selected" button triggers GSD planning
- [ ] **UI-06**: "Run All Scoped" button triggers batch Auto Run
- [ ] **UI-07**: Refresh button to reload queue from server

### Scoping Engine

- [ ] **SCOPE-01**: Convert raw inbox notes to markdown checklists
- [ ] **SCOPE-02**: GSD-style task breakdown in checklist format
- [ ] **SCOPE-03**: Move scoped files from inbox/ to scoped/
- [ ] **SCOPE-04**: Batch scoping (process multiple items)
- [ ] **SCOPE-05**: Progress indicator during scoping

### Execution Integration

- [ ] **EXEC-01**: Scoped PRDs load into Auto Run as documents
- [ ] **EXEC-02**: Run triggers existing Maestro batch processor
- [ ] **EXEC-03**: Move files to running/ when execution starts
- [ ] **EXEC-04**: Move files to completed/ when execution finishes
- [ ] **EXEC-05**: Execution status reflected in queue UI

### Server Connection

- [ ] **SSH-01**: Connect to gsd-system/ via existing SSH remote (gigabrands-dev)
- [ ] **SSH-02**: Read/write files in gsd-system/inbox/, scoped/, running/, completed/
- [ ] **SSH-03**: Watch for new files (polling or notify)
- [ ] **SSH-04**: Handle connection errors gracefully

### IPC Layer

- [ ] **IPC-01**: `window.maestro.prdQueue.list()` - List items by folder
- [ ] **IPC-02**: `window.maestro.prdQueue.read(path)` - Read item content
- [ ] **IPC-03**: `window.maestro.prdQueue.move(from, to)` - Move between folders
- [ ] **IPC-04**: `window.maestro.prdQueue.scope(paths)` - Trigger scoping
- [ ] **IPC-05**: `window.maestro.prdQueue.watch()` - Subscribe to changes

### Telegram Integration (Server-side)

- [ ] **TG-01**: "📋 Queue" button shows pending items inline
- [ ] **TG-02**: Multi-select via inline keyboard
- [ ] **TG-03**: "Scope Selected" triggers server-side scoping
- [ ] **TG-04**: "Run All" triggers maestro-cli from server
- [ ] **TG-05**: Status updates sent back to Telegram

## v2 Requirements

### Advanced Features

- **ADV-01**: Priority ordering for queue items
- **ADV-02**: Tags/categories for filtering
- **ADV-03**: Estimated effort per item
- **ADV-04**: Queue statistics dashboard
- **ADV-05**: Archive search

### Automation

- **AUTO-01**: Auto-scope on arrival (optional)
- **AUTO-02**: Scheduled batch runs
- **AUTO-03**: Webhook triggers

## Out of Scope

| Feature | Reason |
|---------|--------|
| Real-time collaboration | Single-user system |
| Custom AI models | Use existing Claude/Anthropic via Maestro |
| Mobile app | Telegram + Obsidian mobile covers capture |
| Voice commands | Text-based workflow |
| Inline editing of queue items | Edit in Obsidian, not Maestro |

## Traceability

| Requirement | Phase | Status |
|-------------|-------|--------|
| UI-01 | Phase 1 | Pending |
| UI-02 | Phase 1 | Pending |
| UI-03 | Phase 1 | Pending |
| UI-04 | Phase 1 | Pending |
| UI-05 | Phase 2 | Pending |
| UI-06 | Phase 3 | Pending |
| UI-07 | Phase 1 | Pending |
| SCOPE-01 | Phase 2 | Pending |
| SCOPE-02 | Phase 2 | Pending |
| SCOPE-03 | Phase 2 | Pending |
| SCOPE-04 | Phase 2 | Pending |
| SCOPE-05 | Phase 2 | Pending |
| EXEC-01 | Phase 3 | Pending |
| EXEC-02 | Phase 3 | Pending |
| EXEC-03 | Phase 3 | Pending |
| EXEC-04 | Phase 3 | Pending |
| EXEC-05 | Phase 3 | Pending |
| SSH-01 | Phase 1 | Pending |
| SSH-02 | Phase 1 | Pending |
| SSH-03 | Phase 4 | Pending |
| SSH-04 | Phase 1 | Pending |
| IPC-01 | Phase 1 | Pending |
| IPC-02 | Phase 1 | Pending |
| IPC-03 | Phase 2 | Pending |
| IPC-04 | Phase 2 | Pending |
| IPC-05 | Phase 4 | Pending |
| TG-01 | Phase 5 | Pending |
| TG-02 | Phase 5 | Pending |
| TG-03 | Phase 5 | Pending |
| TG-04 | Phase 5 | Pending |
| TG-05 | Phase 5 | Pending |

**Coverage:**
- v1 requirements: 27 total
- Mapped to phases: 27
- Unmapped: 0 ✓

---
*Requirements defined: 2026-02-01*
*Last updated: 2026-02-01 after initial definition*
