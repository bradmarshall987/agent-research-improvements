# objects/_index.md

One line per noun (capability, layer, distillation, cron, notebook, protocol). Status defaults to `stub` until slice 2 fills in object cards.

Updated: 2026-09-05 by Phase 3.1 of the ICM test plan.

| slug | cluster | universe | status | source |
|---|---|---|---|---|
| `cap-001` | data-acquisition | live | stub | `../ROADMAP.md` §"Data acquisition" — Dual-engine API pipeline (SERP + Reader), Effort M |
| `cap-002` | data-acquisition | live | verified | `../ROADMAP.md` — Multi-provider fallback stack (Brave + SerpAPI + Exa), Effort M |
| `cap-003` | data-acquisition | live | stub | `../ROADMAP.md` — Cloud antidetect browser integration, Effort L (cost) |
| `cap-004` | data-acquisition | live | stub | `../ROADMAP.md` — Residential proxy + humanized scraper, Effort L |
| `cap-005` | processing | live | stub | `../ROADMAP.md` — Autonomous memory folding during long sequences, Effort M |
| `cap-006` | processing | live | verified | `../ROADMAP.md` — Tiered caching (web search + URL crawl separated), Effort S |
| `cap-007` | processing | live | stub | `../ROADMAP.md` — Unified reasoning + visual QA model, Effort L (multi-model infra) |
| `cap-008` | delivery | live | verified | `../ROADMAP.md` — Citation-first answer engine routing, Effort S |
| `cap-009` | delivery | live | stub | `../ROADMAP.md` — Publication-ready Markdown report generation, Effort M |
| `cap-010` | hitl | live | verified | `../ROADMAP.md` — Mandatory scope card before any research run, Effort S |
| `cap-011` | hitl | live | stub | `../ROADMAP.md` — Interactive suspend/resume workflow checkpoints, Effort L (workflow engine) |
| `cap-012` | hitl | live | stub | `../ROADMAP.md` — Automated claims verification table, Effort S |
| `cap-013` | durability | live | verified | `../ROADMAP.md` — Persistent project workspaces, Effort M |
| `cap-014` | durability | live | stub | `../ROADMAP.md` — Shadow agent CRUD on its own notes, Effort M |
| `cap-015` | data-acquisition | live | stub | `../ROADMAP.md` §"Cycle 002 additions" — Realistic header & behavioral spoofing, Effort M (external infra) |
| `cap-016` | data-acquisition | live | stub | `../ROADMAP.md` — Dynamic query sequence shuffling, Effort S (external infra) |
| `cap-017` | processing | live | stub | `../ROADMAP.md` — Timestamp-anchored summarization, Effort S (Hermes-native prompt+skill) |
| `cap-018` | processing | live | stub | `../ROADMAP.md` — Consistent metadata-based tagging, Effort S (Hermes-native prompt+skill) |
| `distillation-cycle-002` | infrastructure | live | stub | `../distillation/2026-08-30.md` — the forcing-prompt answer for the active cycle |
| `synthesis-seed` | infrastructure | live | stub | `../synthesis/improvement-roadmap.md` — the 14-capability initial brainstorm |
| `cron-distill` | infrastructure | live | stub | job_id `7a1a02bde863`, `agent-research-distill`, Sun 18:00 UTC |
| `cron-audio-digest` | infrastructure | live | stub | job_id `ed35832d70c0`, `agent-research-audio-digest`, Mon 09:00 UTC |
| `notebook-llm-substrate` | infrastructure | live | stub | NotebookLM notebook `b9d347f7-62ff-4999-a0b59d16bf77` ("Research an AI Agent Can Do For the User") |
| `protocol-5phase` | infrastructure | live | stub | `../PROTOCOL.md` — the 5-phase brainstorm cycle contract |
| `roadmap` | infrastructure | live | stub | `../ROADMAP.md` — rolling status across cycles |

## What this index is

The L1 catalog for the noun set. Per the ICM `references/core.md` library rule: "the catalog holds no books." This file points at everything and stores almost nothing else. Detailed cards live in `objects/<slug>.md` (filled in slice 2).

## Why all stubs right now

Slice 2 (Nouns) is the next task. It will produce real `objects/<slug>.md` cards with citations, the why, and the Hits/Does not hit waterfall. **Until slice 2 lands, treat this index as a placeholder list.** Don't act on a capability based on this row alone — open the corresponding object card or `../ROADMAP.md`.

## Conventions

- `cap-NNN` rows mirror `../ROADMAP.md` exactly. When you flip a status there (SHIP/DEFER/REJECT), update the matching row here too.
- Cluster = layer (data-acquisition / processing / delivery / hitl / durability) + infrastructure for cross-cutting nouns.
- Universe = `live` for everything currently in force (cycle 002 is the active one).


## Verified subset (2026-09-05)

5 of 25 noun cards are full-filled with citations, Hits/Does not hit, and See sections:
- `cap-002` (data-acquisition) — Multi-provider fallback stack
- `cap-006` (processing) — Tiered caching
- `cap-008` (delivery) — Citation-first answer engine routing
- `cap-010` (hitl) — Mandatory scope card before any research run
- `cap-013` (durability) — Persistent project workspaces

The other 20 cards are `status: stub` and will be filled as SHIP/DEFER/REJECT decisions happen. The `../../ROADMAP.md` table remains the source of truth for capability disposition.
