# ROADMAP — Research an AI Agent Can Do For the User

Rolling status across cycles. Updated by the Sunday distillation cron.

## Current cycle

- **Cycle started**: 2026-11-09 UTC (cycle 009; executed Monday after the missed Sunday run)
- **Phase**: Distill complete; Phase 3 decisions remain pending.
- **Notebook**: https://notebooklm.google.com/notebook/b9d347f7-62ff-4999-a65d-a0b59d16bf77
- **Notebook sources**: 12, unchanged in count from cycle 008; this query reports using 10. An unchanged count alone does not prove source content is unchanged.
- **Distillation cadence**: weekly (Sun 18:00 UTC)
- **Latest distillation**: [`distillation/2026-11-09.md`](distillation/2026-11-09.md) — the full NotebookLM answer, saved verbatim.
- **Cycle outcome**: the answer enumerates 23 items; deduplication against the existing 18 capabilities identifies six newly surfaced, distinct candidates (`cap-019`–`cap-024`). These are newly surfaced from the existing corpus, not evidence of new source additions. All 24 remain open pending Phase 3 decisions.
- **Classification cautions**: NotebookLM now calls local tiered caching (`cap-006`) prompt/skill-based, reversing its cycle 008 external-infrastructure label. This is an unverified estimate, not evidence of an implementation or a disposition. Likewise, API integrations still depend on external providers even when the answer calls them prompt/skill changes; multiformat generation and immutable audit claims need implementation checks.
- **Hermes-native S-sized candidates to investigate**: `cap-009`, `cap-010`, `cap-012`, `cap-016`, `cap-017`, `cap-018`, and `cap-019`–`cap-021`; the NotebookLM fit labels are estimates, not deployment verification.

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

None. The repository records no SHIP decisions or completed capability files; the GitHub issue/PR list was also empty when checked. Existing Hermes features may overlap candidates but have not been established as completed Phase 4 builds for this roadmap.

## Open capabilities (need SHIP/DEFER/REJECT decision)

### Previously open — status checked this cycle

All 18 pre-existing entries are **STILL OPEN**; no new SHIP, DEFER, or REJECT disposition is recorded.

- **STILL OPEN** `cap-001` — Dual-engine SERP + reader pipeline.
- **STILL OPEN** `cap-002` — Multi-provider search fallback stack.
- **STILL OPEN** `cap-003` — Cloud antidetect browser integration.
- **STILL OPEN** `cap-004` — Residential proxy + humanized scraper.
- **STILL OPEN** `cap-005` — Autonomous memory folding.
- **STILL OPEN** `cap-006` — Separate search and URL caches; native/external classification requires verification.
- **STILL OPEN** `cap-007` — Unified reasoning + visual QA model.
- **STILL OPEN** `cap-008` — Citation-first answer engine routing.
- **STILL OPEN** `cap-009` — Publication-ready Markdown reports, limitations and open questions.
- **STILL OPEN** `cap-010` — Research scope card.
- **STILL OPEN** `cap-011` — Interactive suspend/resume checkpoints.
- **STILL OPEN** `cap-012` — Claims verification table and evidence triangulation.
- **STILL OPEN** `cap-013` — Persistent project workspaces.
- **STILL OPEN** `cap-014` — Shadow-agent note CRUD.
- **STILL OPEN** `cap-015` — Realistic headers and behavioral spoofing; overlaps `cap-004`.
- **STILL OPEN** `cap-016` — Search query sequence shuffling.
- **STILL OPEN** `cap-017` — Timestamp/page-anchored summaries and fine-grained provenance.
- **STILL OPEN** `cap-018` — Standardized research metadata tags.

### Newly surfaced in cycle 009

Each entry is **OPEN**, not an authorization to build. Effort and fit are NotebookLM estimates to verify, not tested implementation facts. Source titles and detailed proposals are in the [verbatim cycle 009 answer](distillation/2026-11-09.md).

- **OPEN `cap-019` — Counterargument and edge-case pressure testing**: prompt a strongest opposing case and test edge cases; uses the triangulation already in `cap-012`. Processing; S; proposed prompt/skill. Source: *How AI Agents Will Change Research: A Human-in-the-Loop Workflow Playbook*.
- **OPEN `cap-020` — Search-result relevance evaluation and learning extraction**: score relevance against the goal, extract learnings and suggest follow-up questions. Processing; S; proposed prompt/skill, integration to verify. Source: *GitHub - mastra-ai/template-deep-research*.
- **OPEN `cap-021` — Two-person evidence verification and decision sign-off**: separate verifier and approver, with verification notes and unresolved uncertainties. HITL; S for a template/workflow, but requires two available human roles. Source: *How AI Agents Will Change Research: A Human-in-the-Loop Workflow Playbook*.
- **OPEN `cap-022` — Multiformat grounded deliverables**: turn checked research into formats beyond `cap-009` Markdown reports, such as audio, HTML slides and mind maps. Delivery; M; NotebookLM suggests skill orchestration, but actual artifact tooling and external services need verification. Sources: *GitHub - mastra-ai/template-deep-research*; *How AI Agents Will Change Research: A Human-in-the-Loop Workflow Playbook*.
- **OPEN `cap-023` — Cross-file grounded knowledge-base Q&A**: retrieve evidence across saved transcripts, PDFs and notes to answer questions and trace decisions. Durability; S estimated; proposed retrieval/skill change, semantic indexing needs verification. Source: *How AI Agents Will Change Research: A Human-in-the-Loop Workflow Playbook*.
- **OPEN `cap-024` — Research reproducibility and audit metadata**: log inputs, prompts, models/tools, timestamps, assumptions and reviewer identity. Durability; S for a metadata template; a generated text block alone is **not** immutable or tamper-evident, so immutable storage would require separate design. Source: *How AI Agents Will Change Research: A Human-in-the-Loop Workflow Playbook*.

### Cycle 009 deduplication crosswalk

The answer's 23 numbered proposals are not 23 new capabilities. Overlaps are treated as existing scopes, not proof that every detail is implemented: 1→`cap-001`/`cap-002`; 2→`cap-002` (Exa semantic search is in the original seed); 3→`cap-008`; 4→`cap-002` (Google-specific SERP features); 5→`cap-002`; 6→`cap-001`; 7→`cap-004`/`cap-015`; 8→`cap-003`; 9→`cap-006`; 10→`cap-005`; 11→`cap-007`; 12→`cap-012`; 13→`cap-019`; 14→`cap-020`; 15→`cap-011`; 16→`cap-010`; 17→`cap-021`; 18→`cap-022` (overlaps `cap-009` for Markdown); 19→`cap-009`; 20→`cap-017`; 21→`cap-013`/`cap-014`/`cap-018`; 22→`cap-023`; 23→`cap-024`. `cap-016` did not appear as a separate item but remains open. Other omitted existing candidates also remain open; the query is not a decision or proof of completeness.

## Deferred

(none yet)

## Rejected

(none yet)

## Audio digests

- 2026-08-31 (cycle 002 audio): artifact_id `edfbb206-8675-4c30-9a24-25a8af8f76ed` — "How AI Agents Beat Digital Bouncers" — deep_dive, ~6.5 min wall-clock, completed 09:08:09Z.
- 2026-09-14 (cycle 003 audio): artifact_id `6f9a451e-7a23-4e19-8be0-da7c1619e2f8` — "AI agents versus the web blockade" — deep_dive, ~5.5 min wall-clock, completed 09:06:31Z.
- 2026-09-21 (cycle 004 audio): artifact_id `3a1a1b62-f60a-4394-a867-b188c86f7eba` — "How AI Agents Beat Anti-Bot Systems" — deep_dive, ~5.1 min wall-clock, completed 09:06:26Z.
- 2026-09-28 (cycle 005 audio): artifact_id `5ef6718e-9533-4a80-9ad1-e07f6e6f3749` — "Why AI agents must mimic human flaws" — deep_dive, ~6.4 min wall-clock, completed 09:08:07Z.
- 2026-10-04 (cycle 006 audio): artifact_id `5af3e74b-8128-4f4b-a4ba-1f453c792013` — "Research an AI Agent Can Do For the User" — deep_dive, ~6.5 min wall-clock, completed 09:01:58Z
- 2026-10-26 (cycle 008 audio): artifact_id `ad930749-b3c7-4691-8829-a635d0b1c93a` — "Research an AI Agent Can Do For the User" — deep_dive, ~6.5 min wall-clock, completed 09:01:58Z

## Skipped cycles

- 2026-09-07 (Monday audio digest): SKIPPED — no distillation for 2026-09-06. Latest distillation on disk is `distillation/2026-08-30.md`. Root cause: the 2026-09-06 18:00Z `agent-research-distill` cron ran but aborted at the sidecar health probe (NotebookLM MCP sidecar unreachable at `10.0.3.1:8765`). Re-verified 2026-09-07 09:0xZ — still `Connection refused` (curl rc=7). No `studio_create` call was made; notebook `b9d347f7-62ff-4999-a65d-a0b59d16bf77` untouched.
- 2026-10-12 (Monday audio digest): SKIPPED — no distillation for 2026-10-11; latest distillation on disk is `distillation/2026-10-04.md`. No `studio_create` call was made; notebook `b9d347f7-62ff-4999-a65d-a0b59d16bf77` untouched.
- 2026-10-23 (Sunday distillation cycle 007): SKIPPED — NotebookLM MCP sidecar IS online (server_info returns version 0.15.6, profile d7319798@gmail.com, 53 visible tools), but **saved Google auth is expired**. `notebook_query` returns "Could not reach NotebookLM while verifying the session"; `refresh_auth` returns `{status: expired, headless_error: "Headless browser refresh failed (OSError)", headless_hint: "Run 'nlm login' in a desktop session to re-authenticate."}`. **Different failure mode from prior skips** (which were sidecar-down, not auth-expired). Remediation is Dan-side: run `nlm login` on the laptop to refresh the cached auth tokens, then the Sunday cron can proceed. No `distillation/2026-10-23.md` written (no query ran). No `studio_create` call was made; notebook `b9d347f7-62ff-4999-a65d-a0b59d16bf77` untouched. WhatsApp digest [SILENT] — nothing new to report since cycle 006.
- 2026-10-23 (Monday audio digest): SKIPPED — no distillation for 2026-10-22; latest distillation on disk is `distillation/2026-10-04.md` (19 days stale, no Sunday cron has run since 2026-10-04). No `studio_create` call was made; notebook `b9d347f7-62ff-4999-a65d-a0b59d16bf77` untouched. Same deadlock pattern as 2026-10-12 — Phase 1 (no new sources seeded) and Phase 3 (no SHIP/DEFER/REJECT decisions) both stalled; the Sunday `agent-research-distill` cron has not produced a distillation in 3 weeks.
- 2026-11-02 (Monday audio digest): SKIPPED — no distillation for 2026-11-01. Latest distillation on disk is `distillation/2026-10-25.md` (8 days stale). No `studio_create` call was made; notebook `b9d347f7-62ff-4999-a65d-a0b59d16bf77` untouched. The Sunday `agent-research-distill` cron has not produced a distillation in 8 days.
- 2026-11-09 (Monday audio digest): SKIPPED — no distillation for 2026-11-08. Latest distillation on disk is `distillation/2026-10-25.md` (15 days stale). No `studio_create` call was made; notebook `b9d347f7-62ff-4999-a65d-a0b59d16bf77` untouched. The Sunday `agent-research-distill` cron has not produced a distillation in 15 days.

## Cross-cycle trends

Historical entries below are preserved as written, but contain inconsistent totals and contradictory `cap-006` classifications; current status is the cycle 009 inventory above, not those historical counts.

- 2026-08-30 (cycle 002): first weekly distillation ran cleanly; notebook returned 16 capabilities (4 new beyond seed), all ⚪ OPEN. No SHIP/DEFER/REJECT decisions this cycle (Phase 3 is a Dan action, not a cron action). Hermes-native share of new entries: 2/4 (cap-017, cap-018 are prompt+skill; cap-015, cap-016 need external infra).
- 2026-09-13 (cycle 003): second weekly distillation after a one-cycle skip (sidecar offline 2026-09-06). Notebook returned 18 capabilities — same universe as cycle 002, with **cleaner tags** (cycle 002 had ambiguous Hermes-native fit on cap-005, cap-008, cap-011, cap-013, cap-014; cycle 003 locked them all to "Needs external infra" or "Hermes-native (Prompt/Skill)"). **No new capabilities surfaced** because no new sources were seeded this cycle. The big unlock this cycle is the **Hermes-native S-only shortlist** (6 caps ready to SHIP as prompt+skill with zero external infra): cap-009, cap-010, cap-012, cap-016, cap-017, cap-018. Phase 3 Decide target for next session: pick at least one off the shortlist to exercise Phase 4 Build. Total capability count across both cycles: 18 unique.
- 2026-09-20 (cycle 004): third weekly distillation — universe still 18 capabilities, **no new sources seeded this cycle so no new entries and no retired entries**. Cycle 004's verbatim answer surfaces the same 18 caps as cycle 003 with cleaner citations on cap-009 (Timestamp & Page-Anchored Summarization, locator-coords rule) and cap-018 (Metadata Tagging Schema, full taxonomy `method`/`dataset`/`limitation`/`open_question`/`assumption`/`decision` expanded from cycle 003's 4-tag list). **All 18 remain ⚪ OPEN** — Phase 3 Decide has not been exercised by Dan in any of the 3 cycles to date. The `capabilities/` directory still doesn't exist; first Phase 4 build is blocked on a Phase 3 SHIP. Recommended SHIP for next session (small judgment call, see distillation "Suggested next action"): `cap-009` Publication-Ready Markdown Reports — S effort, Hermes-native, addresses the overconfidence pattern that recurs across cap-013/015/018. Total cycle count: 3 (002, 003, 004), 18 unique capabilities, 0 SHIPPED, 0 DEFERRED, 0 REJECTED.
- 2026-09-27 (cycle 005): fourth weekly distillation — universe still 18 capabilities, **still no new sources seeded (4 cycles in a row without a Phase 1 seed)**. Cycle 005 verbatim text is identical to cycle 004 except for citation-bracket renumbering and a literal rephrase on cap-009 ("DOIs" added to the locator-coords example). No new entries, no retired entries, no Hermes-native-vs-external-infra reassignments. **All 18 remain ⚪ OPEN**. The cycle-005 shortlist and "Recommended SHIP for next session" carry forward verbatim from cycle 004. The deadlock pattern (0 SHIPPED across 4 cycles) is now visible enough to call out as a meta-finding: a weekly cron with no Phase 1 seed and no Phase 3 action delivers the same 18-cap report every Sunday. Either Phase 1 (add a new source, surface new caps) or Phase 3 (Dan picks one off the shortlist to start Phase 4 Build) needs to break the loop — both are Dan-only actions. Total cycle count: 4 (002, 003, 004, 005), 18 unique capabilities, 0 SHIPPED, 0 DEFERRED, 0 REJECTED.
- 2026-10-04 (cycle 006): fifth weekly distillation — universe still stable (17 caps in the cycles-003+ numbering, 18 in the cycle-002 ROADMAP seed; same gap that's been there since cycle 003). **Still no new sources seeded (5 cycles in a row without a Phase 1 seed)**. Cycle 006 verbatim text is functionally identical to cycle 005; only the rendering of two bullets differs (cycle 006 separates Description from Hermes-Native Fit per the raw NotebookLM response; cycle 005 collapsed them — same capabilities). No new entries, no retired entries, no Hermes-native-vs-external-infra reassignments, no effort reclassifications. **All 17 remain ⚪ OPEN**; the Phase 3 Decide step is still untouched. The cycle-006 distillation explicitly flags this as a **second identical Suggested Next Action** across cycles 004 → 006 — the meta-finding from cycle 005 (cron is functioning, process is stalled on the human step) is now a structural pattern, not a one-off. The "Recommended SHIP for next session" target (cap-009 Publication-Ready Markdown Reports) has been carried forward 3 cycles in a row without action. Either Phase 1 (add a new source) or Phase 3 (Dan runs Phase 3 Decide) needs to break the loop. Total cycle count: 5 (002, 003, 004, 005, 006), 17 unique capabilities surfaced across cycles 003+, 0 SHIPPED, 0 DEFERRED, 0 REJECTED.
- 2026-10-23 (cycle 007 attempted, SKIPPED): sixth weekly distillation aborted at the `notebook_query` step — **different failure mode from prior skips**: NotebookLM MCP sidecar IS online (server_info returns v0.15.6, all 53 tools visible), but cached Google auth for profile `d7319798@gmail.com` is **expired** (`auth_status: stale` from `server_info`; `refresh_auth` reports `Headless browser refresh failed (OSError)`). No `distillation/2026-10-23.md` written. No new sources seeded (still 6 cycles in a row without a Phase 1 seed). No Phase 3 movement. Capabilities universe still 17 unique across cycles 003+, 0 SHIPPED, 0 DEFERRED, 0 REJECTED. **Action item for Dan**: run `nlm login` on the laptop to refresh the cached Google auth tokens — once that's done, the Sunday cron will resume the cycle-007 distillation automatically on the next scheduled run. **Resolved before cycle 008**: cycle 008's `server_info` returns `auth_status: configured`, confirming Dan ran `nlm login` between 2026-10-23 and 2026-10-25; the cron resumed cleanly with no code-side changes. Total cycle count: 6 attempted (002, 003, 004, 005, 006, 007-skipped), 17 unique capabilities, 0 SHIPPED, 0 DEFERRED, 0 REJECTED.
- 2026-10-25 (cycle 008): seventh successful weekly distillation (21 days after cycle 006; first successful run since the cycle 007 auth skip). **Universe stable at 17 capabilities** (same as cycles 003 → 006). **One meaningful delta**: `cap-006` Tiered Ingestion Caching Architecture flipped from **Hermes-native** (cycles 003 → 006) to **Needs external infra** (cycle 008, citing "structured local cache directories and file storage on the hosting server"); effort unchanged at S. Net effect: the Hermes-native S-only shortlist drops to **5** items (cap-009, cap-010, cap-012, cap-016, cap-017, cap-018 — minus cap-006). Phase 3 disposition needed on cap-006's flip. **All 17 still ⚪ OPEN** — Phase 3 Decide has not been exercised by Dan in any of the 8 cycles to date (002 → 008). No new sources seeded (now 7 cycles in a row without a Phase 1 seed). Cycle 008 verbatim is functionally identical to cycle 006; the only cycle-to-cycle delta is the cap-006 flip plus minor citation-bracket renumbering. The "Suggested next action" section is now word-for-word identical across 4 cycles (005 → 008) and the structural deadlock pattern (cron functioning, process stalled on the human step) is now entrenched enough to count as a quarterly-review-worthy finding. Recommended SHIP target unchanged: `cap-009` Publication-Ready Markdown Reports (or `cap-010` One-Page Scope Card as alternative). Total cycle count: 7 successful (002, 003, 004, 005, 006, 008) + 1 skip (007), 17 unique capabilities surfaced across cycles 003+, 0 SHIPPED, 0 DEFERRED, 0 REJECTED.
- 2026-11-09 (cycle 009): 23 proposals deduplicated into six newly surfaced open candidates (`cap-019`–`cap-024`); 18 existing remain open; none shipped or deferred; source count remains 12 and `cap-006` fit flipped back to prompt/skill in the query.
- (First quarterly review: 2026-11-29)
2026-10-04 (cycle 006 audio): artifact_id  — "Research an AI Agent Can Do For the User" — deep_dive, ~6.5 min wall-clock, completed 09:01:58Z