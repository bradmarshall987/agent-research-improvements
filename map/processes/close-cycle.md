---
type: process
status: verified
verified_at: 2026-09-05
cluster: cron-driven
phase: Reflect
trigger: Completion of decide-on-capability for a cycle (currently manual; could be cron-driven)
consumes:
  - processes/decide-on-capability.md
  - processes/generate-audio-overview.md
  - objects/roadmap.md
produces:
  - objects/roadmap.md (mutated with cycle summary)
  - WhatsApp message to home channel (210908798259275@lid)
---

# close-cycle

End-of-cycle consolidation. After all SHIP/DEFER/REJECT decisions are made, the cycle is closed: ROADMAP.md gets a "Cycle <NNN>" section with what shipped / what's open / what's parked; the audio overview gets generated; a short WhatsApp summary goes out to Dan's home channel.

## Input → Movement → Output

This is the **Reflect** phase in PROTOCOL.md — the natural endpoint after Decide. Currently triggered manually after Dan finishes the Decide pass; could be automated to fire Monday morning after the Sunday distillation.

The closing pass:
1. Reads the current ROADMAP.md (which has the latest cycle's dispositions in the appropriate sections)
2. Adds a "Cycle NNN (started YYYY-MM-DD)" entry to ROADMAP.md with:
   - Cycle number (002, 003, ...)
   - Distillation input file (link)
   - Audio overview artifact id (if generated)
   - 3 bullets: shipped this cycle / opened this cycle / parked/deferred this cycle
   - Cross-cycle trend note (1-2 sentences on what the cycle taught us)
3. Triggers `generate-audio-overview` (separate process card) if not already done
4. Sends a WhatsApp summary to the home channel with:
   - 1 link to the latest distillation
   - 1 link to the latest audio overview
   - 3 bullets (shipped / opened / parked)

The WhatsApp summary stays short — the canonical "weekly digest" shape lives in `/opt/data/digests/_templates/record-template.md` and the ICM weekly digest cron prompt has its own delivery shape.

## Steps

1. Wait for `decide-on-capability` to finish for all open capabilities in the cycle
2. Read ROADMAP.md
3. Append the cycle summary section
4. Trigger `generate-audio-overview` (it may also be triggered by its own cron)
5. Compose the WhatsApp summary (1 + 1 + 3 shape)
6. Send via `hermes send --to whatsapp -s "[Agent Research Cycle NNN]" --body <summary>` or equivalent

## If you change this

- **Hits:** ROADMAP.md (cycle summary appended); the WhatsApp home channel delivery; the `agent-research-audio-digest` cron (the audio overview is also generated independently by this cron, so close-cycle may duplicate it — coordination needed); the next cycle's input (the "Cross-cycle trend note" feeds into the next distillation's forcing prompt)

- **Does not hit:** the notebook itself; the distillation file (that's frozen at cycle close); the capability decisions (those happen in `decide-on-capability` before close-cycle runs)

## Surfaces

| Surface | Role |
|---|---|
| Dan | reads (WhatsApp summary) |
| `../../ROADMAP.md` | writes |
| WhatsApp home channel `210908798259275@lid` | writes |
| `agent-research-audio-digest` cron | coordination (avoid duplicate audio overview generation) |

## See

- Process spec: `../../PROTOCOL.md` §"Phase 5 — Reflect"
- Companion process: `generate-audio-overview` (separate process card)
- WhatsApp summary shape: `/opt/data/digests/_templates/record-template.md` §"Shape A — Weekly cron digest"
- Status legend (used in cycle summary): `../../ROADMAP.md` §"Capability seed (14 capabilities from initial brainstorm)"
