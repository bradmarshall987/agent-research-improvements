# effects/CONTEXT.md — change-impact index

This file is a **catalog**, not a copy of waterfalls. For each kind of change in this repo, it points at the object + process cards that need to be opened and re-verified. It does not duplicate the Hits / Does not hit lists that live in each card.

Per `references/system-map.md` §"Slice 4 — Change-impact index": "if you're changing X, open these cards." The index answers "I am changing X, what inside the tree moves." It does NOT answer "what outside the tree points in" — for that, see "External consumers" below.

## Walks it backwards (the slice 4 discipline)

For each entry below, the test is: "if I make this change and forget to update the listed cards, what breaks?" The cards listed are the ones whose state is implicitly coupled to the changed thing.

---

## Change: flip a capability's disposition in ROADMAP.md (OPEN → SHIPPED / DEFERRED / REJECTED)

**Cards to open and re-verify:**
- `objects/cap-NNN.md` (the specific capability card) — bump `disposition:` frontmatter, update "Connected to" if the new disposition creates new joins
- `objects/_index.md` — the row's status mirrors ROADMAP, so it stays in sync (currently both say "OPEN" for all 18; first SHIP will desync)
- `processes/decide-on-capability.md` — the process card's "Steps" section documents the disposition; if a NEW disposition type is added (e.g. "PAUSE"), update the process card too
- `processes/ship-capability.md` — for SHIP dispositions, this card describes the build pattern that follows; check that PROTOCOL.md Phase 4 patterns still apply

**Cards NOT affected:**
- The notebook itself
- Distillation / synthesis files
- Cron schedule / config
- WhatsApp delivery (unless the SHIPped capability creates a new cron with `deliver=whatsapp`)

---

## Change: add a new source to the NotebookLM notebook

**Cards to open and re-verify:**
- `objects/notebooklm-substrate.md` — the source list changes; if the substrate card lists "12 sources" or similar, update the count
- `processes/add-source-to-notebook.md` — currently a stub; once full-filled, its Steps section will document the exact behavior; update if it changes
- `objects/synthesis-seed.md` — if the new source changes the brainstorm seed (e.g. introduces a new capability), re-verify

**Cards NOT affected:**
- The 18 capability object cards directly (only via indirect distillation impact)
- Cron jobs (the notebook adds sources; it doesn't change cron behavior)

**Watch for:** per-notebook 50-source cap. If the notebook is approaching the cap, also open `/opt/data/skills/research/notebooklm-rotation/SKILL.md` and consider rotating before adding more.

---

## Change: edit ROADMAP.md directly (not via a Decide pass)

**Cards to open and re-verify:**
- All 18 capability object cards — they cite `../../ROADMAP.md` as the source. If ROADMAP reorganizes, batch-update the Citations lines.
- `processes/decide-on-capability.md` — the process references ROADMAP; if the schema (status legend, section names) changes, the process card's "Steps" section needs updating.
- `processes/close-cycle.md` — the closing pass appends to ROADMAP; if the cycle summary section changes shape, update this card.

**Cards NOT affected:**
- The notebook itself
- Synthesis / distillation files
- Cron schedule

---

## Change: modify PROTOCOL.md (the 5-phase cycle)

**Cards to open and re-verify:**
- All 6 process cards in `processes/` — each one cites `../../PROTOCOL.md` for its phase spec. Re-verify every "Steps" section.
- `objects/protocol-5phase.md` (when full-filled) — the protocol card itself.
- `map/CLAUDE.md` — if the phase ordering changes, update the slice gate comments in `CONTEXT.md` too.

**Cards NOT affected:**
- Object cards directly (they describe nouns, not phases)
- Cron schedule (the cron prompts are separate from PROTOCOL.md, though related)

**Watch for:** PROTOCOL.md changes are the highest-impact edits in this repo. Plan to re-run the full slice 5 re-verify after any non-trivial protocol change.

---

## Change: rotate the NotebookLM notebook (per `notebooklm-rotation` skill)

**Cards to open and re-verify:**
- `objects/notebooklm-substrate.md` — update the notebook ID in frontmatter
- `objects/cap-002.md`, `objects/cap-006.md`, `objects/cap-008.md` (and any other card that references the notebook's content)
- `processes/distill-cycle.md` — the cron prompt's TARGET NOTEBOOK field

**Cards NOT affected:**
- Capability cards that don't cite the notebook directly
- The PROTOCOL.md itself
- Cron job IDs / schedule

**Watch for:** the cron prompt `deliver=whatsapp` carries the notebook URL in step 5's "Open notebook" link. After rotation, the digest's URL points at the wrong notebook until the cron is updated.

---

## Change: edit the cron schedule (`jobs.json`)

**Cards to open and re-verify:**
- `objects/cron-distill.md` and `objects/cron-audio-digest.md` — their `entity:` frontmatter points at jobs.json
- `processes/distill-cycle.md` and `processes/generate-audio-overview.md` — their `trigger:` frontmatter says "cron X at time Y"
- The cron-job-health-audit skill (`/opt/data/skills/cron-job-health-audit/SKILL.md`) — different scope but related

**Cards NOT affected:**
- Object cards for capabilities
- The notebook itself
- PROTOCOL.md (unless the schedule change requires protocol change)

---

## Change: edit the cron prompt text (`jobs.json` `prompt` field)

**Cards to open and re-verify:**
- The process card corresponding to that cron's verb (e.g. `distill-cycle.md` for the distill cron)
- The handoff doc that documented the prompt's original design (`/opt/data/handoffs/2026-09-05-icm-test-phase-1-handoff.md` references the cron-prompt template)

**Cards NOT affected:**
- Object cards (unless the prompt change introduces new noun references)
- The cron schedule itself

**Watch for:** cron prompt edits are common but rarely re-verified. The fact that the ICM weekly digest shipped "research failed" stubs for weeks (Phase 1) was in part because nobody re-read the prompt after the notebook rotated.

---

## External consumers (NOT covered by this index)

Things outside this repo's tree that point in:

- **`/opt/data/cron/output/dd5d79f8799a/`** — the wiki-lint watchdog reads this. Not affected by anything in this repo (different scope).
- **`/opt/data/skills/research/notebooklm-rotation/SKILL.md`** — references the old notebook `ba1e5fee-...` in its docs as the "abandoned" example. Update if you rotate again.
- **`/opt/data/handoffs/2026-09-05-icm-test-phase-*.md`** — the ICM test handoffs. Update if a Phase 4 patch changes the skill itself.
- **NotebookLM notebook `b9d347f7-...`** — outside this tree, but is the substrate. Source additions / reindexing doesn't show up here.
- **WhatsApp home channel `210908798259275@lid`** — receives `close-cycle` summaries. The summary shape lives in `/opt/data/digests/_templates/record-template.md`.

Ask the owner (Dan) before assuming any of these are wired safely.

---

## Slice 5 (re-verify) gate

After making any change above, walk the changed cards end-to-end:

1. Open each opened card. Confirm Citations still resolve (`../../` paths exist).
2. Confirm frontmatter `consumes:` / `produces:` still point at cards that exist.
3. Confirm "If you change this" lists are still accurate.
4. Confirm no orphan cards (every noun in `_index.md` still has a card; every verb in `_index.md` still has a card).

The full slice 5 re-verify (cross-checking the 8 full-filled cards against ROADMAP.md and PROTOCOL.md) is captured separately in the Phase 3 Task 3.4 handoff doc.