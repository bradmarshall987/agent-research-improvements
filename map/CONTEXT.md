# map/CONTEXT.md

How to walk this map. The subject tree is authoritative; this map cites it.

## How to read the cards

- **Object cards** (`objects/*.md`) — nouns: things, types, artifacts. "What is X?"
- **Process cards** (`processes/*.md`) — verbs: real movements that run. "How does X happen?"
- **Effects** (`effects/CONTEXT.md`) — change-impact index. "If I change X, what else moves?"
- **Schema** (`_meta/schema.md`) — the closed set of node types. When practice and schema disagree, reconcile.

## How to walk it cold

A fresh agent, no memory of this repo, should be able to:

1. Open `CLAUDE.md` → see the L0 catalog (this directory map).
2. Open `CONTEXT.md` → this file. See universes and how to read cards.
3. Pick a noun from `objects/_index.md`. Open that object card. Verify it cites source (path), states the load-bearing why, and gives a Hits / Does not hit waterfall.
4. From `effects/CONTEXT.md`, name what a stated change hits and what it does not.
5. Token check: CLAUDE.md + CONTEXT.md + one card stays in the 2k–8k band.

## Name collisions

| Term | What it means here | What it might also mean |
|---|---|---|
| **capability** | an item in the brainstorm (`cap-001` … `cap-018`), tracked in ROADMAP.md and (when shipped) in `capabilities/<id>.md` | NOT the same as a Hermes "skill" — skills are one delivery vehicle for shipped capabilities |
| **distillation** | a per-cycle `notebook_query` output saved to `distillation/<date>.md` | NOT the same as a "summary" or "brief" — distillations are the forcing-prompt answer, formatted |
| **synthesis** | raw NotebookLM `notebook_query` outputs, in `synthesis/<slug>.md` | NOT the same as a distillation — syntheses are unforced, distillations are forced |
| **layer** | one of data acquisition / processing / delivery / HITL / durability | NOT a folder — the repo does not use `data/`, `processing/`, etc. as directories |
| **cycle** | one full pass through the 5 phases (Seed → Distill → Decide → Build → Reflect) | cycle 002 is the active one (started 2026-08-30) |

## Slices gated (per system-map.md)

- [x] Slice 0 — Inventory done (7 files classified, all live, no leftover/ghost)
- [x] Slice 1 — Catalog done (CLAUDE.md, CONTEXT.md, schema, templates, objects/_index.md)
- [x] Slice 2 — Nouns (object cards) — 5 verified (cap-002, cap-006, cap-008, cap-010, cap-013), 20 stubs
- [x] Slice 3 — Verbs (process cards) — 3 verified (distill-cycle, decide-on-capability, close-cycle), 3 stubs
- [x] Slice 4 — Change-impact index — effects/CONTEXT.md with 7 change entries + external consumers
- [x] Slice 5 — Re-verify — 2026-09-05 21:55 UTC. 36/38 citations resolve, 2 forward references to planned-empty paths clarified inline. ROADMAP.md mentions 18/18 caps, cards on disk 18/18. Cold walk (CLAUDE + CONTEXT + 1 obj + 1 proc) ≈ 3,029 tokens, in 2k-8k target