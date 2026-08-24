# Protocol — the 5-phase brainstorm cycle

This is the operational contract for `Research an AI Agent Can Do For the User`. The cycle
runs weekly (mini) and monthly (big) and is owned by the cron job `agent-research-distill`
(Sundays 18:00 UTC, deliver to WhatsApp home channel).

## Phase 1 — Seed

**Trigger**: any new source, insight, or notebook_query output.

**What to do**:
- Add the source to the NotebookLM notebook via `mcp__notebooklm__source_add`.
- Save the source URL + title to `synthesis/<topic-slug>-sources.md` (this is the human-readable
  source index; the notebook is the searchable one).
- If the source came from a notebook_query, save the full answer verbatim to
  `synthesis/<topic-slug>.md`.

**Done when**: the source is in NotebookLM, and a markdown mirror exists on disk.

## Phase 2 — Distill

**Trigger**: Sunday 18:00 UTC cron.

**What to do**:
- Run `notebook_query` against the notebook with the forcing prompt:
  *"List every concrete, shippable capability mentioned across all sessions. Mark each with:
  layer (data/processing/delivery/HITL/durability), effort (S/M/L), and Hermes-native fit
  (does this need external infra or is it a prompt+skill change?). Cite source titles."*
- Save the full answer to `distillation/YYYY-MM-DD.md`.
- Update `ROADMAP.md`:
  - Move any SHIPped capabilities to a "Shipped this cycle" section with a link to their
    `capabilities/<id>.md` file.
  - Add any new un-shipped capabilities to "Open capabilities".
  - Mark anything previously open as either DECIDED (with disposition) or STILL OPEN.

**Done when**: `distillation/YYYY-MM-DD.md` exists and `ROADMAP.md` reflects the cycle.

## Phase 3 — Decide

**Trigger**: end of each distillation (the cron, after writing the distillation file).

**What to do** (Dan or designated reviewer):
- For each open capability, mark one of:
  - **SHIP** — moves to backlog as a concrete task. Get a capability id (next sequential
    number: `cap-001`, `cap-002`, ...).
  - **DEFER** — sits in `parking-lot.md` with a revisit date.
  - **REJECT** — gets a one-line rationale in `archive/<id>.md`.

**Done when**: every capability from the latest distillation has a disposition.

## Phase 4 — Build

**Trigger**: a SHIP decision in Phase 3.

**What to do**:
- Create a `capabilities/cap-<NNN>.md` file with:
  - Title
  - Layer (data/processing/delivery/HITL/durability)
  - Effort (S/M/L)
  - The "what" — one paragraph on what gets built
  - The "why" — links back to the distillation and the NotebookLM source(s)
  - Status (planned / in-progress / shipped)
  - Links to any GitHub issues, skills, MCP servers, or cron jobs created
- The actual build follows whatever pattern fits:
  - **Code change in Hermes** → GitHub issue in the relevant repo
  - **New skill** → `/opt/data/skills/<category>/<skill-name>/SKILL.md` (mirrored to this repo's
    `skills/` for reference)
  - **New MCP server** → follow the `hermes-mcp-servers` workflow
  - **New cron / monitoring** → `cronjob` create, with `deliver=whatsapp`

**Done when**: the capability is either live (shipped) or has a tracked build state.

## Phase 5 — Reflect

**Trigger**: end of cycle (immediately after Phase 3 + 4).

**What to do**:
- Generate an audio overview from the notebook via `studio_create(audio)`. Save the audio
  artifact id in `ROADMAP.md`.
- Update `ROADMAP.md` to reflect the cycle's outcome (what shipped, what's open, what's parked).
- Send a short WhatsApp summary to the home channel with: 1 link to the latest distillation,
  1 link to the latest audio overview, 3 bullets (shipped / opened / parked).

**Done when**: the digest is delivered and `ROADMAP.md` is up to date.

## Cadence

- **Weekly mini-cycle**: Sundays 18:00 UTC, run by cron `agent-research-distill`.
- **Monthly big-cycle**: first Sunday of each month, the distillation forcing prompt is replaced
  with a strategic prompt that includes cross-cycle trends.
- **Quarterly strategic review**: in `archive/quarterly-review-YYYY-QN.md`, write a one-page
  summary of what got shipped, what got rejected and why, what new layer is worth investing in.

## Hand-off artifact

If a session ends mid-cycle, write a `HANDOFF-<date>.md` to this repo's root with:
- What phase we ended on
- What's outstanding
- The exact `cronjob` invocation that resumes the cycle
- Any secrets / environment context the next session needs

This file is read by the next agent that runs `agent-research-resume` (a separate cron that
runs on session start).
