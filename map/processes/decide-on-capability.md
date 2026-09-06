---
type: process
status: verified
verified_at: 2026-09-05
cluster: human-gated
phase: Decide
trigger: End of each distill-cycle (manual — Dan action, not cron)
consumes:
  - objects/distillation-cycle-002.md (or latest)
  - objects/roadmap.md
produces:
  - capabilities/<id>.md (for SHIP)
  - parking-lot.md (for DEFER)
  - archive/<id>.md (for REJECT)
---

# decide-on-capability

The human gate that converts "open capability in ROADMAP" into a concrete disposition. After every distill-cycle writes a new distillation file, Dan reviews each surfaced capability and marks one of: SHIP, DEFER, REJECT.

## Input → Movement → Output

The latest distillation file lists every open capability that the forcing prompt surfaced. Dan opens `../../ROADMAP.md` (which the cron has updated with the new "Open capabilities" entries) and the matching section of the latest distillation file (which has the citations).

For each capability, Dan makes one of three decisions:

- **SHIP** — the capability moves from "Open" to "Shipped this cycle". A `capabilities/<id>.md` file is created with: title, layer, effort, the "what" (one paragraph), the "why" (links to distillation + NotebookLM sources), status (planned / in-progress / shipped), links to GitHub issues / skills / MCP servers / cron jobs created.
- **DEFER** — the capability stays as "Open" but moves to a separate "Deferred" section in ROADMAP.md, with a `parking-lot.md` entry giving the revisit date (typically the next monthly big-cycle, per PROTOCOL.md cadence).
- **REJECT** — the capability moves to `archive/<id>.md` with a one-line rationale, and is removed from "Open" in ROADMAP.md.

The actual build pattern for SHIPped capabilities follows PROTOCOL.md Phase 4 (GitHub issue / new skill / new MCP / new cron). The decide-on-capability process is the *gate* before that build starts.

## Steps

1. Distill cycle completes — `distillation/<date>.md` exists, ROADMAP.md updated with new "Open capabilities"
2. Dan opens ROADMAP.md and reviews the "Open capabilities" section
3. For each capability, Dan picks one disposition:
   - SHIP → write `capabilities/<id>.md` (per PROTOCOL.md Phase 4 schema) + move to "Shipped this cycle"
   - DEFER → write `parking-lot.md` entry with revisit date + move to "Deferred" in ROADMAP
   - REJECT → write `archive/<id>.md` with one-line rationale + remove from "Open"
4. (Optional) After all dispositions are made, the `close-cycle` process card triggers — ROADMAP.md gets the cycle summary, audio overview gets generated, WhatsApp summary goes out

## If you change this

- **Hits:** the disposition format (`capabilities/<id>.md`, `parking-lot.md`, `archive/<id>.md` — see PROTOCOL.md §"Phase 3 — Decide"); ROADMAP.md "Open capabilities" / "Shipped this cycle" / "Deferred" / "Rejected" sections; the next cycle's distillation forcing prompt (which picks up where this cycle's dispositions left off)
- **Does not hit:** the notebook itself (Decide operates on the distillation output, not on notebook sources); the cron schedule (Decide is manual, not cron-driven); the audio overview artifact (that's a separate Reflect-phase process)

## Surfaces

| Surface | Role |
|---|---|
| Dan (reviewer) | runs (human action) |
| `../../ROADMAP.md` | writes (mutates disposition sections) |
| `../../capabilities/` | writes (for SHIP) — *planned-empty directory* (referenced in PROTOCOL.md, will land on first SHIP) |
| `../../parking-lot.md` | writes (for DEFER) — *planned-empty file* (will land on first DEFER) |
| `../../archive/` | writes (for REJECT) — *planned-empty directory* (will land on first REJECT) |

## See

- Process spec: `../../PROTOCOL.md` §"Phase 3 — Decide"
- Input source: `../../distillation/2026-08-30.md` — cycle 002 distillation with 18 capability entries
- Status legend: `../../ROADMAP.md` §"Capability seed (14 capabilities from initial brainstorm)" — the ⚪/🟢/🟡/🔵/🔴 legend
- Workspace lifecycle: the `icm-workspace-design` skill — for SHIPped capabilities that warrant their own workspace folder
