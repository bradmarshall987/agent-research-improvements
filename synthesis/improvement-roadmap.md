# Brainstorm seed — 14 shippable capabilities for Hermes as a research assistant

Source: forced `notebook_query` against the `Research an AI Agent Can Do For the User`
NotebookLM notebook on 2026-08-24.

The notebook has 12 sources covering HITL workflow playbooks, frontier benchmarks (HLE, GAIA),
Google IP-blocking mechanisms, search API comparison, and headless-browser fingerprinting.

This is the raw synthesis; the ROADMAP.md and PROTOCOL.md in this repo turn it into action.

---

To upgrade **Hermes** into a highly advanced, enterprise-grade research assistant for non-technical
users, we should focus on shifting it from a reactive "one-off chatbot" to a structured, resilient,
and repeatable research system.

The following high-leverage, concrete capabilities are grouped by structural layer.

## 1. Data Acquisition Layer

To prevent Hermes from hitting constant anti-bot blocks and data-access limits, the data
collection infrastructure must be made highly resilient.

- **Implement a Dual-Engine API Pipeline**: Shift away from fragile, custom web scraping setups
  that frequently break due to layout changes. Instead, run a standardized dual-engine pipeline
  that pairs a **SERP API** for link discovery with a specialized **Reader API** (such as Jina
  Reader or Firecrawl) to cleanly extract page content and convert messy HTML into structured,
  LLM-ready Markdown. *Source: "Web Scraping vs API for AI Agents: Which is Better in 2026?"*

- **Establish a Multi-Provider Fallback Stack**: Integrate a multi-vendor fallback system (for
  example, combining Brave Search API for independent index querying and predictability with
  SerpAPI for high-fidelity Google-specific features, or Exa for semantic/neural queries). This
  protects Hermes from supplier concentration risks, index outages, or rate-limit blocks.
  *Source: "Best AI Search APIs for Agents 2026 | Context Studios" & "Tavily vs SerpAPI vs Brave
  Search API 2026 | APIScout"*

- **Deploy Cloud Antidetect Browser Evasion**: When Hermes absolutely must access targets shielded
  by heavy anti-bot software (like Cloudflare, DataDome, or Kasada) where standard APIs do not
  exist, integrate a cloud-based antidetect browser. This runs real, headed browser profiles on
  cloud hardware backed by physical GPU rendering and native TLS handshakes, completely bypassing
  Chrome DevTools Protocol (CDP) detection artifacts. *Source: "Headless Browser Detection Methods:
  Browser Isolation Guide (2026)"*

- **Configure Realistic Scraper Humanization**: For lightweight crawling, implement a proxy
  infrastructure using residential IPs with geographic consistency (matching the IP to query
  localization). Force the scraper to rotate popular, up-to-date User-Agent strings, supply full
  browser header payloads, and calculate realistic "human delays" between searches to avoid IP
  bans. *Source: "Avoid Google Blocks While Scraping SERPs | ProxyHat"*

## 2. Processing Layer

The processing layer should convert raw retrieved text into dense, context-aware reasoning assets
while controlling API costs.

- **Configure Autonomous Thought & Memory Folding**: Activate autonomous memory folding during
  long, multi-step research sequences. This allows Hermes to autonomously compress intermediate
  thinking, keep context sizes manageable, and prevent context window exhaustion. *Source:
  "Deep Research Benchmarks | RUC-NLPIR/DeepAgent | DeepWiki"*

- **Integrate a Tiered Caching Architecture**: Build a dedicated caching architecture that
  splits web search cache directories from URL crawl cache directories. This avoids redundant
  external API calls, significantly driving down operational search costs and reducing latency
  for repetitive queries. *Source: "Deep Research Benchmarks | RUC-NLPIR/DeepAgent | DeepWiki"*

- **Deploy a Unified Reasoning & Visual QA Model Service**: Power the core agent using an
  advanced reasoning model alongside an auxiliary Visual QA model service. This allows Hermes
  to run complex, multi-modal reasoning chains over both textual documents and visual assets,
  such as charts or diagrams in PDF attachments. *Source: "Deep Research Benchmarks |
  RUC-NLPIR/DeepAgent | DeepWiki"*

## 3. Delivery Layer

Non-technical users need highly structured, clean, and pre-verified final deliverables, not
messy raw data dumps.

- **Incorporate Citation-First Answer Engines**: For simple factual lookups, route queries
  directly to answer-first models like Perplexity Sonar or You.com Smart API. This allows Hermes
  to bypass a costly custom search-to-synthesis pipeline for routine facts and immediately deliver
  cited summaries. *Source: "Best AI Search APIs for Agents 2026 | Context Studios" &
  "Search API Pricing Compared 2026 | Awesome Agents"*

- **Generate Publication-Ready Markdown Reports**: Implement an autonomous report generation
  agent designed to transform messy raw findings directly into comprehensive, formatted Markdown
  reports immediately after user sign-off on research quality. *Source: "GitHub -
  mastra-ai/template-deep-research"*

## 4. Human-in-the-Loop (HITL) Layer

To guarantee safety and prevent the "responsibility gap," Hermes must subject its work to
rigorous human constraints and checkpoints.

- **Enforce a Mandatory Scoping Phase**: Before launching any automated research run, force
  the user to fill out a simple **one-page scope card**. This explicitly establishes the core
  research question, decision supported, target audience, and strict **stop rules** (such as a
  60-minute time box or a maximum of 25 sources) to prevent unchecked agent drift. *Source:
  "How AI Agents Will Change Research: A Human-in-the-Loop Workflow Playbook"*

- **Build Interactive Suspend/Resume Workflows**: Re-architect Hermes's background workflows
  to feature strategic suspend and resume gates. Instead of executing a multi-step task end-to-end,
  Hermes must pause at checkpoints and wait for the user to approve, edit, or reject intermediate
  findings. *Source: "GitHub - mastra-ai/template-deep-research"*

- **Enforce an Automated Claims Verification Table**: Force Hermes to extract and map every
  major assertion into a **claims table** containing: (1) the claim, (2) supporting evidence,
  (3) a verbatim quote, (4) a precise provenance pointer, and (5) a confidence tag. Enforce
  triangulation, requiring at least two independent sources for critical claims, and mandate
  "no evidence found" rows to prevent quiet model guesswork. *Source: "How AI Agents Will Change
  Research: A Human-in-the-Loop Workflow Playbook"*

## 5. Durability Layer

Research must carry over between sessions so users can continuously build a structured knowledge
base without starting from scratch.

- **Establish Persistent Project Workspaces**: Organize Hermes's outputs inside bounded project
  spaces. By keeping the initial prompt constraints, transcripts, PDF files, and verified
  claims tables co-located in a single workspace, users can run continuous research loops,
  conduct weekly triages, and safely reuse previous context in later sessions. *Source:
  "How AI Agents Will Change Research: A Human-in-the-Loop Workflow Playbook"*

- **Enable Shadow Agent CRUD Operations**: Allow Hermes to execute direct Create, Read,
  Update, and Delete actions on its own notes in the workspace. This lets the agent dynamically
  "write back" verified chat insights into durable files — such as appending to a living
  bibliography or updating a running literature map — safeguarding valuable work that would
  normally vanish when a chat window is closed. *Source: "How AI Agents Will Change Research:
  A Human-in-the-Loop Workflow Playbook"*

---

## Mapping to effort & Hermes-native fit

| ID  | Capability                                  | Layer      | Effort | Hermes-native fit |
|-----|---------------------------------------------|------------|--------|--------------------|
| 1   | Dual-engine SERP+Reader pipeline            | Data       | M      | Skill + small infra |
| 2   | Multi-provider fallback stack               | Data       | M      | Skill + API keys    |
| 3   | Cloud antidetect browser                    | Data       | L      | External infra ($$) |
| 4   | Residential proxy + humanized scraper       | Data       | L      | External infra ($$) |
| 5   | Autonomous memory folding                   | Processing | M      | Prompt + skill     |
| 6   | Tiered caching (search/crawl separated)     | Processing | S      | Skill + config     |
| 7   | Unified reasoning + VQA model               | Processing | L      | Multi-model infra  |
| 8   | Citation-first answer engine routing        | Delivery   | S      | Skill              |
| 9   | Publication-ready Markdown report generation| Delivery   | M      | Skill + workflow   |
| 10  | Mandatory scope card                        | HITL       | S      | Skill + template   |
| 11  | Interactive suspend/resume checkpoints      | HITL       | L      | Workflow engine    |
| 12  | Automated claims verification table         | HITL       | S      | Skill + template   |
| 13  | Persistent project workspaces               | Durability | M      | Skill + filesystem |
| 14  | Shadow agent CRUD on own notes              | Durability | M      | Skill              |

The four **S-effort** items (6, 8, 10, 12) are the low-hanging fruit — pure skill changes,
no external infra. Recommended starting lineup.
