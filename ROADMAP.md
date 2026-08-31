# ROADMAP — Research an AI Agent Can Do For the User

Rolling status across cycles. Updated by the Sunday distillation cron.

## Current cycle

- **Cycle started**: 2026-08-30 (cycle 002, first weekly distillation)
- **Phase**: Distill → (Dan to run Phase 3 Decide)
- **Notebook**: https://notebooklm.google.com/notebook/b9d347f7-62ff-4999-a65d-a0b59d16bf77
- **Notebook sources**: 12
- **Distillation cadence**: weekly (Sun 18:00 UTC)
- **Latest distillation**: [`distillation/2026-08-30.md`](distillation/2026-08-30.md)

## Capability seed (14 capabilities from initial brainstorm)

The full seed lives in `synthesis/improvement-roadmap.md`. Status legend:
- 🟢 SHIPPED
- 🟡 IN PROGRESS
- ⚪ OPEN (no decision yet)
- 🔵 DEFERRED
- 🔴 REJECTED

### Data acquisition (4)
- ⚪ `cap-001` Dual-engine API pipeline (SERP + Reader) — Effort: M
- ⚪ `cap-002` Multi-provider fallback stack (Brave + SerpAPI + Exa) — Effort: M
- ⚪ `cap-003` Cloud antidetect browser integration — Effort: L (cost)
- ⚪ `cap-004` Residential proxy + humanized scraper — Effort: L

### Processing (3)
- ⚪ `cap-005` Autonomous memory folding during long sequences — Effort: M
- ⚪ `cap-006` Tiered caching (web search + URL crawl separated) — Effort: S
- ⚪ `cap-007` Unified reasoning + visual QA model — Effort: L (multi-model infra)

### Delivery (2)
- ⚪ `cap-008` Citation-first answer engine routing — Effort: S
- ⚪ `cap-009` Publication-ready Markdown report generation — Effort: M

### HITL (3)
- ⚪ `cap-010` Mandatory scope card before any research run — Effort: S
- ⚪ `cap-011` Interactive suspend/resume workflow checkpoints — Effort: L (workflow engine)
- ⚪ `cap-012` Automated claims verification table — Effort: S

### Durability (2)
- ⚪ `cap-013` Persistent project workspaces — Effort: M
- ⚪ `cap-014` Shadow agent CRUD on its own notes — Effort: M

## Cycle 002 additions (4 new capabilities surfaced by distillation 2026-08-30)

The first weekly distillation surfaced 16 distinct capabilities (vs. 14 in the seed). Four were new.
Added here as `cap-015` … `cap-018`. All ⚪ OPEN pending Phase 3 decision.

### Data acquisition (extended)
- ⚪ `cap-015` Realistic header & behavioral spoofing (rotating UAs, locale match, randomized human-delay generator) — Effort: M (external infra)
- ⚪ `cap-016` Dynamic query sequence shuffling (randomize bulk keyword order before execution) — Effort: S (external infra)

### Processing (extended)
- ⚪ `cap-017` Timestamp-anchored summarization (force extraction of source locator coordinates — timestamps / page numbers — in summaries) — Effort: S (Hermes-native prompt+skill)
- ⚪ `cap-018` Consistent metadata-based tagging (standardize note tags: `method`, `dataset`, `limitation`, `open_question` for cross-file search) — Effort: S (Hermes-native prompt+skill)

## Shipped this cycle

(none yet — first cycle is the foundation; Phase 3 Decide has not run)

## Open capabilities (need SHIP/DEFER/REJECT decision)

All 18 above are ⚪ OPEN.

## Deferred

(none yet)

## Rejected

(none yet)

## Audio digests

- 2026-08-31 (cycle 002 audio): artifact_id `edfbb206-8675-4c30-9a24-25a8af8f76ed` — "How AI Agents Beat Digital Bouncers" — deep_dive, ~6.5 min wall-clock, completed 09:08:09Z.

## Cross-cycle trends

- 2026-08-30 (cycle 002): first weekly distillation ran cleanly; notebook returned 16 capabilities (4 new beyond seed), all ⚪ OPEN. No SHIP/DEFER/REJECT decisions this cycle (Phase 3 is a Dan action, not a cron action). Hermes-native share of new entries: 2/4 (cap-017, cap-018 are prompt+skill; cap-015, cap-016 need external infra).
- (First quarterly review: 2026-11-29)
