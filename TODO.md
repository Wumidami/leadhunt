# LeadHunt v2.0 Implementation TODO

Source: "improved PRD n others" (June 2, 2026)

## Execution order

- [x] Phase 1 (P0/P1 launch): F5 -> F1 -> F2
- [x] Phase 2 (core workflow): F4 -> F3 -> F6
- [x] Phase 3 (power features): F7 -> F8
- [x] Phase 4 (polish): F9 -> F10

## Phase 1 - Launch

### F5 - User profile settings (P1)

- [x] Add localStorage helpers: getProfile(), saveProfile()
- [x] Add profile schema: name, brand, phone, pitchLanguage
- [x] Add first-load profile prompt/modal if profile missing
- [x] Add settings entry point (gear icon or Settings tab)
- [x] Replace hardcoded pitch identity with profile fields
- [x] Block pitch send/generate when profile incomplete
- [x] Acceptance test: profile updates affect new pitch previews immediately

### F1 - Dashboard metrics strip (P0)

- [x] Add metrics strip container above lead list
- [x] Render cards: total leads, hot leads (score >= 80), follow-ups due, closed deals
- [x] Ensure metrics rerender after add/edit/status change/import
- [x] Add follow-up due computation guarded for missing followUpDate
- [x] Acceptance test: no network calls, cards are informational only

### F2 - Empty state onboarding (P0)

- [x] Add conditional render when leads.length === 0
- [x] Build 3-step onboarding card:
- [x] Step 1: open Niche Browser tab
- [x] Step 2: open Region Browser tab
- [x] Step 3: open Add Lead modal
- [x] Ensure empty state disappears immediately after first saved lead

## Phase 2 - Core workflow

### F4 - Follow-up date field (P1)

- [x] Extend lead schema with nullable followUpDate (ISO date)
- [x] Add date input in modal (shown only for Contacted/Follow-Up)
- [x] Default follow-up date to tomorrow when visible
- [x] Render due-date pills on cards:
- [x] Future date -> blue date pill
- [x] Today/past date -> red Overdue pill
- [x] Ensure backward compatibility for existing leads without followUpDate
- [x] Wire into dashboard follow-ups due metric

### F3 - Unified filter bar (P1)

- [x] Replace six-filter layout with unified strip
- [x] Add status chip tabs: All/New/Contacted/Follow-up/Closed
- [x] Keep Tier, Niche, Sort as compact dropdowns
- [x] Move Country + Platform into More filters expander
- [x] Add active filter count with clear action: Filters (N) x
- [x] Verify all prior filter combinations still produce same results
- [x] Verify one-row layout on >= 375px width

### F6 - Issue tags on cards (P2)

- [x] Render up to 4 issue pills from lead.issues
- [x] Render +N more overflow label when > 4
- [x] Hide issue row if no issues
- [ ] Validate no card layout regression in list and board mini-cards

## Phase 3 - Power features

### F7 - Card-level WhatsApp send pitch (P2)

- [x] Add Send pitch button on cards with whatsapp number only
- [x] Extract shared pitch-send workflow used by detail panel + card button
- [x] Reuse profile completeness check and prompt
- [x] Copy pitch to clipboard and open WhatsApp deep link
- [x] Acceptance test: no duplicated business logic paths

### F8 - Kanban board view (P2)

- [x] Add List/Board view toggle
- [x] Render 4 columns: New, Contacted, Follow-Up, Closed
- [x] Show lead count per column
- [x] Render mini-cards: name, score, city
- [x] Make columns scrollable for long lists
- [x] Add drag-drop status change using SortableJS
- [x] Lazy-load SortableJS only on first board activation
- [x] Persist selected view for session only
- [x] Verify mobile layout stacks 2x2 at narrow widths

## Phase 4 - Polish

### F9 - CSV import (P3)

- [x] Add Import CSV button beside Export CSV
- [x] Add file picker (.csv only)
- [x] Parse client-side with FileReader + PapaParse
- [x] Preview counts: rows found, valid, duplicates skipped, errors
- [x] Merge valid rows into leads (do not overwrite)
- [x] Deduplicate by Business Name + City
- [x] Add import format guidance in How to Use section

### F10 - localStorage backup warning (P3)

- [x] Show dismissible warning banner when leads.length >= 20
- [x] Banner text includes Export now action
- [x] Persist dismiss state in warnDismissed localStorage key
- [x] Do not show banner again once dismissed

## Cross-cutting engineering checklist

- [ ] Keep single-file architecture (index.html + localStorage only)
- [ ] Preserve backward compatibility for existing leads data
- [ ] Avoid backend dependencies
- [x] Add defensive parsing for localStorage JSON
- [x] Centralize rerender triggers after every leads mutation
- [ ] Keep UI responsive at 375px+ (list, filters, board)
- [ ] Validate generated pitch for all pitch languages

## Definition of done

- [ ] All acceptance criteria F1-F10 satisfied
- [ ] Manual test pass for add/edit/delete/filter/status/pitch/export/import
- [x] No hardcoded identity strings remain in pitch generation
- [ ] Existing lead data loads without migration errors
