# Project Briefs — CreatrWeb 12-Application Plan

One-paragraph description per project. See stack-guide.md for
stack assignments and model-inventory.md for confirmed free models.

---

## #1 — Boycott & Ethical Consumption App
**Stack:** Multi-tool orchestration (PRC-clean)
**Status:** In progress — Phase 1 complete (Codex), Phase 3 in progress (Gemini CLI)

A web application that lets users search products, brands, and companies
to surface sourced data on labor practices, environmental impact, political
contributions, and human rights records — with specific coverage of
Palestine, Sudan, Congo, and Uyghur issues. RAG indexing runs locally via
Mistral embeddings. Groq (Compound) handles real-time user-facing queries.
The full development toolchain is PRC-clean by design — a deliberate
architectural decision documented in DECISIONS.md and discussed in the
case study writeup. Each tool has a non-redundant phase role mapped to its
natural strength.

---

## #2 — Consolidated Open Source Showcase
**Stack:** Open Source
**Proposed project:** Policy Argument Mapper

A Node.js tool that accepts a policy topic and a corpus of uploaded
documents or URLs, then produces a structured argument map — claims,
evidence, counterarguments, and source citations — rendered as an
interactive web page. GLM-5.1 handles multi-file agentic sessions.
Kilo Code manages interactive UI decisions. Groq Compound handles
fast real-time query responses. OpenRouter free models serve as
fallback inference. Draws on political science minor and data
analysis experience.

---

## #3 — Free Stack Showcase
**Stack:** Free
**Proposed project:** Art Style Classifier

A web interface that accepts an image upload and returns an art
historical reading — period, movement, stylistic influences, and
comparable works — using Kilo Code's multimodal free models
(Qwen2.5 VL 72B via OpenRouter). Opencode Zen handles agentic
backend sessions. Groq Compound handles fast query responses.
Zero cost throughout development and at runtime. Draws on studio
art background and data analysis experience.

---

## #4 — OpenRouter Standalone
**Stack:** OpenRouter
**Proposed project:** Model Comparison Dashboard

A web interface that accepts a prompt and routes it simultaneously
to gpt-oss-120b, qwen2.5-coder-32b, and minimax-m2.5 via OpenRouter,
displaying responses side by side with latency and token metrics.
The only project that makes sense exclusively with OpenRouter's
multi-model routing. Demonstrates the free model landscape and
provides a practical evaluation tool for future stack decisions.

---

## #5 — Kilo Code Standalone
**Stack:** Kilo Code
**Proposed project:** Personal Reading Log with microformats2

A minimal publishing tool for logging books, articles, and other
reading with h-entry microformats2 markup, making content
machine-readable and IndieWeb-compatible. Kilo Auto routes each
task to the best available free model. The case study question
is whether Kilo Auto makes good routing decisions without
explicit guidance — the DECISIONS.md log documents each
automatic routing choice for evaluation.

---

## #6 — Groq Standalone
**Stack:** Groq
**Proposed project:** Real-Time Text Annotation Tool

A web interface that accepts pasted text and returns instant
entity recognition, sentiment tagging, and key phrase extraction.
Groq's inference speed is the visible feature — latency is part
of the UX story. Compound handles complex multi-entity annotation.
Compound Mini handles single-pass tagging where speed matters more
than depth. Draws directly on data analysis core competency.

---

## #7 — Opencode Go Standalone
**Stack:** Opencode Go
**Proposed project:** Studio Art Process Journal

A minimal publishing tool for documenting art practice — image
uploads, process notes, material logs, and a gallery view — built
entirely with GLM-5.1 as the agentic engine and MiniMax M2.7 for
lighter tasks. Non-sensitive personal content with no political
dimension. Draws on studio art background. Demonstrates
GLM-5.1's multi-file agentic strength on a visually rich project.

---

## #8 — Paid Stack Showcase
**Stack:** Paid (all six tools via creatr routing)
**Proposed project:** Resume Website Enhancement

Targeted improvements to an existing codebase using the creatr()
routing script to assign each task to the right tool. Codex
handles any schema or structural changes. Claude Code handles
spec routes and security. Gemini CLI handles UI components.
Cursor handles feature iteration. Vibe CLI handles bulk build
phases. Copilot handles inline mechanical edits. The case study
demonstrates the routing script in action with a before/after
that any portfolio viewer immediately understands.

---

## #9 — Claude Code Standalone
**Stack:** Paid — Claude Code only
**Proposed project:** Personal Data Observatory

A personal IndieWeb site that ingests exported personal data —
Spotify listening history, reading logs, GitHub commits, or any
CSV — and renders it as a living dashboard with microformats2
markup, rel=me links, Webmention support, and GET /export.json
and GET /feed.xml endpoints. Demonstrates Claude Code's multi-file
IndieWeb spec reliability. Draws on data analysis experience
applied to personal data.

---

## #10 — Codex CLI Standalone
**Stack:** Paid — Codex CLI only
**Proposed project:** Business Intelligence Brief Builder

A tool that ingests structured business data (sales CSVs, survey
exports, financial summaries), applies configurable analysis
templates, and outputs a formatted one-page HTML brief ready to
print or share. Demonstrates Codex's schema-first Phase 1
scaffolding strength. Draws on business minor and data analysis
experience.

---

## #11 — Gemini CLI Standalone
**Stack:** Paid — Gemini CLI only
**Proposed project:** Data Story Generator

A web interface that accepts a CSV upload, runs descriptive
statistics and trend detection server-side, and returns a
structured narrative alongside auto-generated chart embeds.
Demonstrates Gemini CLI's rapid UI iteration on a data-rich
interface. Draws on data analysis core competency and makes
analytical output accessible to non-technical audiences.

---

## #12 — Replit Standalone
**Stack:** Replit
**Proposed project:** Comparative Political Data Explorer

A browser-based tool that visualizes comparative datasets across
countries or time periods — electoral systems, policy indicators,
human rights indices — with filters, annotations, and an
embeddable chart export. No local setup required. Shareable link
from day one. Draws on political science minor and data analysis
background. The embeddable export gives it a clear, demonstrable
use case for any portfolio viewer.