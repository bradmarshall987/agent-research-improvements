# Agent Research Improvements

A living brainstorm repository for evolving Hermes (and similar AI agents) into better research assistants.

## What this is

This repo is the durable record of ideas, distillations, and shipped capabilities that come out of the
NotebookLM notebook **`Research an AI Agent Can Do For the User`**
(https://notebooklm.google.com/notebook/b9d347f7-62ff-4999-a65d-a0b59d16bf77).

- **NotebookLM** = "what could be" substrate — grounded reasoning, source citations, audio overviews.
- **This repo** = "what we're doing about it" substrate — decisions, shipped artifacts, parking lot.

## The 5-phase cycle

1. **Seed** — add new sources/insights to the NotebookLM notebook; mirror syntheses to `synthesis/`.
2. **Distill** — every Sunday 18:00 UTC, a cron forces a `notebook_query` and writes `distillation/<date>.md`.
3. **Decide** — for each capability, mark SHIP / DEFER / REJECT.
4. **Build** — shipped capabilities become GitHub issues or `capabilities/<id>.md` files.
5. **Reflect** — `ROADMAP.md` is updated; an audio overview is generated every Monday morning.

## Layout

```
.
├── README.md                    this file
├── PROTOCOL.md                  the 5-phase cycle, in detail
├── ROADMAP.md                   rolling status across cycles
├── distillation/                per-cycle forced-query outputs
│   └── YYYY-MM-DD.md
├── capabilities/                one file per shipped capability
│   └── capability-<id>.md
├── parking-lot.md               deferred ideas with revisit dates
├── archive/                     rejected ideas with rationale
└── synthesis/                   raw NotebookLM notebook_query outputs
    └── <topic-slug>.md
```

## Current seed

The initial brainstorm (14 shippable capabilities across 5 layers: data acquisition, processing,
delivery, HITL, durability) lives in `synthesis/improvement-roadmap.md` and is mirrored at
`/opt/data/research/2026-08-24-research-an-ai-agent-can-do/synthesis-improvement-roadmap.md`.

The protocol in `PROTOCOL.md` came from
`/opt/data/research/2026-08-24-research-an-ai-agent-can-do/BRAINSTORM-REPO.md`.

## How to use this repo

- **Subscribe to issues** — each SHIPped capability becomes an issue.
- **PRs welcome** — if you have hands-on test data on a capability (e.g., you ran Tavily vs Exa
  from your own stack and have timings), drop a `hands-on/<vendor>-<date>.md` file.
- **Audio digests** — auto-generated every Monday. Subscribe to the NotebookLM notebook for the
  audio overview.

## NotebookLM notebook

**Title**: Research an AI Agent Can Do For the User
**URL**: https://notebooklm.google.com/notebook/b9d347f7-62ff-4999-a65d-a0b59d16bf77
**Sources**: 12 (HLE, GAIA, ProxyHat, APIScout, Awesome Agents, Context Studios, Searchcans,
Sendwin, Mastra template, TicNote, DeepAgent DeepWiki, LinkedIn rank-tracker piece)
**Status**: shared, public link
