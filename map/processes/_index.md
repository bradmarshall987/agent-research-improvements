# processes/_index.md

One line per verb (movement) in this repo. Status defaults to `stub` until slice 3 fills in process cards.

Updated: 2026-09-05 by Phase 3 Task 3.3 of the ICM test plan.

| slug | cluster | phase | trigger | status | source |
|---|---|---|---|---|---|
| `add-source-to-notebook` | manual | Seed | any new source/insight | stub | `../../PROTOCOL.md` §"Phase 1 — Seed" |
| `distill-cycle` | cron-driven | Distill | Sun 18:00 UTC cron `7a1a02bde863` | **verified** | `../../PROTOCOL.md` §"Phase 2 — Distill" |
| `decide-on-capability` | human-gated | Decide | end of distill-cycle (manual) | **verified** | `../../PROTOCOL.md` §"Phase 3 — Decide" |
| `ship-capability` | build | Build | SHIP decision in decide-on-capability | stub | `../../PROTOCOL.md` §"Phase 4 — Build" |
| `generate-audio-overview` | cron-driven | Reflect | Mon 09:00 UTC cron `ed35832d70c0` | stub | `../../PROTOCOL.md` §"Phase 5 — Reflect" |
| `close-cycle` | cron-driven | Reflect | completion of decide-on-capability | **verified** | `../../PROTOCOL.md` §"Phase 5 — Reflect" |

## What this index is

The L1 catalog for the verb set. Per the ICM `references/core.md` library rule: "the catalog holds no books." This file points at every process card and stores almost nothing else.

## Verified subset (2026-09-05)

3 of 6 verb cards are full-filled:
- `distill-cycle` — the weekly forcing-prompt backbone (cron-driven)
- `decide-on-capability` — the human gate that converts "open" to "shipped/deferred/rejected"
- `close-cycle` — the end-of-cycle consolidation that ships the WhatsApp summary

The other 3 cards (`add-source-to-notebook`, `ship-capability`, `generate-audio-overview`) are `status: stub` — they exist in the index because the noun set in `objects/_index.md` references them, but their cards will be filled when those processes become load-bearing for future agents.

## Composition with object cards

Every process card has a `consumes:` and `produces:` list pointing at object cards. Examples:
- `distill-cycle` consumes `protocol-5phase.md`, `notebook-llm-substrate.md`, `roadmap.md`; produces `distillation-cycle-002.md`
- `decide-on-capability` consumes `distillation-cycle-002.md`, `roadmap.md`; produces capability artifacts in `capabilities/`, `parking-lot.md`, `archive/`
- `close-cycle` consumes `roadmap.md` and the audio overview; produces a WhatsApp message

If you change a process, the object's Hits / Does not hit list changes. Update both files.
