---
type: process
status: verified
verified_at: 2026-09-05
cluster: cron-driven
phase: Distill
trigger: cron `agent-research-distill` (Sun 18:00 UTC, job_id `7a1a02bde863`)
consumes:
  - objects/protocol-5phase.md
  - objects/notebook-llm-substrate.md
  - objects/roadmap.md
produces:
  - objects/distillation-cycle-002.md (and successors per cycle)
---

# distill-cycle

The weekly forcing-prompt distillation. Run every Sunday 18:00 UTC by the `agent-research-distill` cron job (job_id `7a1a02bde863`). One notebook_query against the active notebook, full answer saved to `../../distillation/<date>.md`, ROADMAP.md updated with cycle outcome.

## Input → Movement → Output

The cron arrives at 18:00 UTC. The cron prompt (stored in `/opt/data/cron/jobs.json` under the job_id) contains the full forcing prompt verbatim from PROTOCOL.md Phase 2: *"List every concrete, shippable capability mentioned across all sessions. Mark each with: layer (data/processing/delivery/HITL/durability), effort (S/M/L), and Hermes-native fit (does this need external infra or is it a prompt+skill change?). Cite source titles."*

The cron agent then calls `mcp__notebooklm__notebook_query` against the active notebook (`b9d347f7-62ff-4999-a0b59d16bf77`), captures the full answer verbatim, and writes it to `../../distillation/YYYY-MM-DD.md` (filename uses the cron-fire date in UTC).

After writing the distillation file, the cron agent updates `../../ROADMAP.md`:
- Move any SHIPped capabilities (already decided in a prior cycle) to a "Shipped this cycle" section with links to `capabilities/<id>.md`
- Add any new un-shipped capabilities to "Open capabilities"
- Mark anything previously open as DECIDED (with disposition) or STILL OPEN

If the notebook hits the per-notebook 50-source cap, the cron ships a fallback "research failed" stub and does NOT update ROADMAP.md (per the cron prompt's cap-preflight step). The notebook needs rotation per `/opt/data/skills/research/notebooklm-rotation/SKILL.md`.

## Steps

1. Cron arrives at Sun 18:00 UTC → reads the forcing prompt from jobs.json
2. Calls `mcp__notebooklm__notebook_query` against `b9d347f7-62ff-4999-a0b59d16bf77` with the forcing prompt
3. Captures the full answer (no truncation, no summarization)
4. Writes `../../distillation/<YYYY-MM-DD>.md` with the answer (existing example: `2026-08-30.md`; the directory grows per cycle)
5. Reads current `../../ROADMAP.md`
6. Updates ROADMAP per the rules above
7. (Optional) Sends a WhatsApp summary if `deliver=whatsapp` is set (currently `deliver=local` for this cron — see `/opt/data/cron/jobs.json`)

## If you change this

- **Hits:** the `agent-research-distill` cron (job_id `7a1a02bde863`); the notebook (`b9d347f7-...`); the `distillation/` directory in this repo; the `ROADMAP.md` file (mutable per cycle); the `notebook-rotation` skill (when cap hit)
- **Does not hit:** the audio overview generation (`generate-audio-overview` is its own process card); the `capabilities/<id>.md` directory (created in Phase 4 ship-capability, not Distill); NotebookLM notebook source content itself (Distill only *reads* the notebook, never writes to it)

## Surfaces

| Surface | Role |
|---|---|
| NotebookLM notebook `b9d347f7-...` | reads |
| `../../distillation/` directory | writes |
| `../../ROADMAP.md` | writes |
| `agent-research-distill` cron | runs |
| Dan (when cap hit, manual rotation) | triggers |
| Sunday 18:00 UTC scheduler | triggers |

## See

- Process spec: `../../PROTOCOL.md` §"Phase 2 — Distill"
- Cron config: `/opt/data/cron/jobs.json` job_id `7a1a02bde863`
- Output example: `../../distillation/2026-08-30.md` — cycle 002 distillation
- Capability drift cap: `/opt/data/skills/research/notebooklm-rotation/SKILL.md` — the per-notebook cap that caused the W35 failure stub
