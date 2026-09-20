# ROADMAP — Research an AI Agent Can Do For the User

Rolling status across cycles. Updated by the Sunday distillation cron.

## Current cycle

- **Cycle started**: 2026-09-20 (cycle 004 — third weekly distillation)
- **Phase**: Distill → (Dan to run Phase 3 Decide)
- **Notebook**: https://notebooklm.google.com/notebook/b9d347f7-62ff-4999-a65d-a0b59d16bf77
- **Notebook sources**: 12 (unchanged from cycle 003; no new Phase 1 seeds this week)
- **Distillation cadence**: weekly (Sun 18:00 UTC)
- **Latest distillation**: [`distillation/2026-09-20.md`](distillation/2026-09-20.md)
- **Hermes-native S-only shortlist** (concrete Phase 3 SHIP candidates, no external infra needed):
  - `cap-009` Publication-ready Markdown report template w/ Limitations + Open Questions
  - `cap-010` One-page scope card pre-flight gate
  - `cap-012` Claims verification table (claim / evidence / quote / source / confidence + "no evidence found" rows)
  - `cap-016` Dynamic search query sequence shuffling
  - `cap-017` Timestamp-anchored summarization (locator coords on every summary point)
  - `cap-018` Standardized metadata tagging schema (`method`, `dataset`, `limitation`, `open_question`)

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
- ⚪ `cap-009` Publication-ready Markdown report generation (with Limitations + Open Questions sections) — Effort: S (Hermes-native prompt+skill)

### HITL (3)
- ⚪ `cap-010` Mandatory scope card before any research run — Effort: S
- ⚪ `cap-011` Interactive suspend/resume workflow checkpoints — Effort: M (external infra: Mastra vNext orchestrator)
- ⚪ `cap-012` Automated claims verification table — Effort: S

### Durability (2)
- ⚪ `cap-013` Persistent project workspaces — Effort: M
- ⚪ `cap-014` Shadow agent CRUD on its own notes — Effort: M

## Cycle 002 additions (4 new capabilities surfaced by distillation 2026-08-30)

The first weekly distillation surfaced 16 distinct capabilities (vs. 14 in the seed). Four were new.
Added here as `cap-015` … `cap-018`. All ⚪ OPEN pending Phase 3 decision.

### Data acquisition (extended)
- ⚪ `cap-015` Realistic header & behavioral spoofing (rotating UAs, locale match, randomized human-delay generator) — Effort: M (external infra)
- ⚪ `cap-016` Dynamic query sequence shuffling (randomize bulk keyword order before execution) — Effort: S (Hermes-native prompt+skill)

### Processing (extended)
- ⚪ `cap-017` Timestamp-anchored summarization (force extraction of source locator coordinates — timestamps / page numbers — in summaries) — Effort: S (Hermes-native prompt+skill)
- ⚪ `cap-018` Consistent metadata-based tagging (standardize note tags: `method`, `dataset`, `limitation`, `open_question` for cross-file search) — Effort: S (Hermes-native prompt+skill)

## Shipped this cycle

(none yet — first cycle is the foundation; Phase 3 Decide has not run)

## Open capabilities (need SHIP/DEFER/REJECT decision)

All 18 above are ⚪ OPEN. No Phase 3 dispositions have been made by Dan in any cycle to date (cycles 002, 003, 004). Cron-only cycles — the Phase 3 Decide step is a Dan action.

## Deferred

(none yet)

## Rejected

(none yet)

## Audio digests

- 2026-08-31 (cycle 002 audio): artifact_id `edfbb206-8675-4c30-9a24-25a8af8f76ed` — "How AI Agents Beat Digital Bouncers" — deep_dive, ~6.5 min wall-clock, completed 09:08:09Z.
- 2026-09-14 (cycle 003 audio): artifact_id `6f9a451e-7a23-4e19-8be0-da7c1619e2f8` — "AI agents versus the web blockade" — deep_dive, ~5.5 min wall-clock, completed 09:06:31Z.

## Skipped cycles

- 2026-09-07 (Monday audio digest): SKIPPED — no distillation for 2026-09-06. Latest distillation on disk is `distillation/2026-08-30.md`. Root cause: the 2026-09-06 18:00Z `agent-research-distill` cron ran but aborted at the sidecar health probe (NotebookLM MCP sidecar unreachable at `10.0.3.1:8765`). Re-verified 2026-09-07 09:0xZ — still `Connection refused` (curl rc=7). No `studio_create` call was made; notebook `b9d347f7-62ff-4999-a65d-a0b59d16bf77` untouched.

## Cross-cycle trends

- 2026-08-30 (cycle 002): first weekly distillation ran cleanly; notebook returned 16 capabilities (4 new beyond seed), all ⚪ OPEN. No SHIP/DEFER/REJECT decisions this cycle (Phase 3 is a Dan action, not a cron action). Hermes-native share of new entries: 2/4 (cap-017, cap-018 are prompt+skill; cap-015, cap-016 need external infra).
- 2026-09-13 (cycle 003): second weekly distillation after a one-cycle skip (sidecar offline 2026-09-06). Notebook returned 18 capabilities — same universe as cycle 002, with **cleaner tags** (cycle 002 had ambiguous Hermes-native fit on cap-005, cap-008, cap-011, cap-013, cap-014; cycle 003 locked them all to "Needs external infra" or "Hermes-native (Prompt/Skill)"). **No new capabilities surfaced** because no new sources were seeded this cycle. The big unlock this cycle is the **Hermes-native S-only shortlist** (6 caps ready to SHIP as prompt+skill with zero external infra): cap-009, cap-010, cap-012, cap-016, cap-017, cap-018. Phase 3 Decide target for next session: pick at least one off the shortlist to exercise Phase 4 Build. Total capability count across both cycles: 18 unique.
- 2026-09-20 (cycle 004): third weekly distillation — universe still 18 capabilities, **no new sources seeded this cycle so no new entries and no retired entries**. Cycle 004's verbatim answer surfaces the same 18 caps as cycle 003 with cleaner citations on cap-009 (Timestamp & Page-Anchored Summarization, locator-coords rule) and cap-018 (Metadata Tagging Schema, full taxonomy `method`/`dataset`/`limitation`/`open_question`/`assumption`/`decision` expanded from cycle 003's 4-tag list). **All 18 remain ⚪ OPEN** — Phase 3 Decide has not been exercised by Dan in any of the 3 cycles to date. The `capabilities/` directory still doesn't exist; first Phase 4 build is blocked on a Phase 3 SHIP. Recommended SHIP for next session (small judgment call, see distillation "Suggested next action"): `cap-009` Publication-Ready Markdown Reports — S effort, Hermes-native, addresses the overconfidence pattern that recurs across cap-013/015/018. Total cycle count: 3 (002, 003, 004), 18 unique capabilities, 0 SHIPPED, 0 DEFERRED, 0 REJECTED.
- (First quarterly review: 2026-11-29)
