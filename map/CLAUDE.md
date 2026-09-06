# map/CLAUDE.md

The catalog of `/opt/data/agent-research-improvements/`. Subject tree stays authoritative; this map cites it. Map never becomes a second spec.

## What this catalog answers

- **"Where am I?"** → you're in `map/`. Subject root is `../`.
- **"Where do I go to understand X?"** → `objects/` for nouns, `processes/` for verbs, `effects/CONTEXT.md` for change-impact, `_meta/schema.md` for the closed type set.
- **"What else moves if I change X?"** → `effects/CONTEXT.md`. It is a catalog of "if you're changing X, open these cards" — it does not copy waterfalls.
- **"What does this map NOT answer?"** → "what outside this repo points in." Ask the owner. (See `effects/CONTEXT.md` §"External consumers".)

## What lives here

| Path | Holds |
|---|---|
| `CLAUDE.md` | this file (L0 catalog) |
| `CONTEXT.md` | universes + name collisions + how to walk |
| `_meta/schema.md` | closed set of node types |
| `_templates/object.md` | copyable object card starter |
| `_templates/process.md` | copyable verb card starter |
| `objects/` | record library of nouns (one card per noun) |
| `processes/` | real movements only (one card per verb) |
| `effects/CONTEXT.md` | change-impact index |

## Universes

| Universe | Meaning | Files in this repo |
|---|---|---|
| **live** | In force. Implement and cite against these. | `README.md`, `PROTOCOL.md`, `ROADMAP.md`, `distillation/2026-08-30.md`, `synthesis/improvement-roadmap.md`, `synthesis/sources.md`, the 18 capability entries in `ROADMAP.md` |
| **leftover** | Still present, no longer the main path. Touch only if that path is in scope. | (none — repo is small and current) |
| **ghost** | Named or filed, not wired. | `parking-lot.md`, `archive/`, `capabilities/` — *referenced in README/PROTOCOL but not yet created on disk.* These are planned-empty, not ghost-actual. |

## Noun set (preview — full list in `objects/_index.md`)

- **18 capabilities** (`cap-001` … `cap-018`) — see ROADMAP.md
- **5 layers**: data acquisition / processing / delivery / HITL / durability
- **2 distillations** (cycle 002 is the active one)
- **2 cron jobs**: `agent-research-distill` (7a1a02bde863, Sun 18:00 UTC) and `agent-research-audio-digest` (ed35832d70c0, Mon 09:00 UTC)
- **1 NotebookLM notebook**: `b9d347f7-62ff-4999-a65d-a0b59d16bf77` ("Research an AI Agent Can Do For the User")
- **1 protocol**: PROTOCOL.md (5-phase cycle)

## Cross-references

- Subject root: `../README.md`
- Subject tree authoritative source: `../`
- ICM skill this was scaffolded from: `/opt/data/skills/research/icm-workspace-design/`
- The 18 capabilities are tracked (with SHIP/DEFER/REJECT status) in `../ROADMAP.md` — when you change a capability's status there, also update the matching object card here.