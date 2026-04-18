# Planning Prompts

These are the starting planning prompts for the projects I want to build with each stack. They are intentionally high-level and open-ended to allow for creative exploration within each stack's capabilities.

From here, I will iterate on the project ideas, defining more specific features, user flows, and technical requirements as I prototype and test each one. The goal is to leverage the unique strengths of each stack while building something that is both useful and showcases the capabilities of the models involved.

## 12 REPLIT: 
I want to build a comparative political data explorer
showing datasets across countries on electoral systems, policy
indicators, and human rights indices with embeddable visualizations.
Stack: Replit Agent (auto-build mode). Note: auto-build does not
pause for gallery confirmation — DECISIONS.md review is required
after every session.
Files: DECISIONS.md (required), DESIGN.md (required), CONSTRAINTS.md
(required), MEMORY.md (if lessons confirmed).
Deliverable: handoff prompt for Replit Agent.

## 6 GROQ: 
I want to build a real-time text annotation tool where
users paste text and instantly receive entity recognition, sentiment
tagging, and key phrase extraction — speed is a visible feature.
Stack: Groq free tier only. Models: compound (multi-tool, 30K TPM
limit), compound-mini (3x faster, single-tool, 14K TPM limit).
Hard limit: 30 req/min total across both models. Scope must fit
within a single compound call per user action.
Files: DECISIONS.md (required), DESIGN.md (required), CONSTRAINTS.md
(required — rate limits are binding constraints), MEMORY.md (if
lessons confirmed).
Deliverable: handoff prompt for Groq Compound.

## 4 OPENROUTER: 
I want to build a model comparison dashboard showing
responses from three OpenRouter free models with latency and token
metrics. Models: gpt-oss-120b:free, qwen2.5-coder-32b:free,
minimax-m2.5:free. Hard constraint: free tier rate limits mean
requests must be sequential, not simultaneous — architecture must
account for this.
Files: DECISIONS.md (required), DESIGN.md (required), CONSTRAINTS.md
(required — sequential-only architecture is a binding constraint),
MEMORY.md (if lessons confirmed).
Deliverable: handoff prompt for Kilo Code (OpenRouter routing).

## 5 KILO CODE: 
I want to build a personal reading log with h-entry
microformats2 markup — title, author, date read, a short note,
and a rating per entry. Stack: Kilo Code native free models only.
Models: kilo-auto/free (auto-routing), nemotron-3-super-120b:free
(120B hybrid MoE), openrouter/free (routes to best available free
model). Note: all three are routing models — actual model served
may change between sessions.
Files: DECISIONS.md (required), DESIGN.md (required), CONSTRAINTS.md
(required), MEMORY.md (if lessons confirmed).
Deliverable: handoff prompt for Kilo Code.

## 10 CODEX: 
I want to build a business intelligence brief builder
where users upload a CSV, select an analysis template, and receive
a formatted one-page HTML brief.
Stack: Paid — Codex CLI, routed via creatr scaffold.
Files: DECISIONS.md (required), DESIGN.md (required), CONSTRAINTS.md
(required), MEMORY.md (if lessons confirmed).
Deliverable: handoff prompt for Codex CLI.

## 11 GEMINI: 
I want to build a data story generator where users
upload a CSV and receive a plain-language narrative with chart
embeds readable by a non-technical audience.
Stack: Paid — Gemini CLI, routed via creatr ui.
Files: DECISIONS.md (required), DESIGN.md (required), CONSTRAINTS.md
(required), MEMORY.md (if lessons confirmed).
Deliverable: handoff prompt for Gemini CLI.

## 9 CLAUDE CODE: 
I want to build a personal data observatory
ingesting my exported data as a living IndieWeb dashboard with
microformats2, rel=me, Webmention, and GET /export.json and
GET /feed.xml endpoints.
Stack: Paid — Claude Code, routed via creatr spec.
Files: DECISIONS.md (required), DESIGN.md (required), CONSTRAINTS.md
(required — IndieWeb spec endpoints are irreversible decisions),
MEMORY.md (if lessons confirmed), EVAL_PROMPT.md (if evaluation
criteria are being revised this session).
Deliverable: handoff prompt for Claude Code.

## 3 FREE STACK: 
I want to build an art style classifier where users
upload an image and receive an art historical reading — period,
movement, influences, and comparable works.
Stack: Free (Kilo Code + Opencode Zen + Groq + OpenRouter free).
Image model: qwen2.5-vl-72b:free via OpenRouter (multimodal input).
Reasoning: gpt-oss-120b:free. Fast queries: compound.
Hard constraint: no batch image processing — single image per
request only. Free tier rate limits apply to all four tools.
Files: DECISIONS.md (required), DESIGN.md (required — art
classification output must be traceable to the user's stated
aesthetic references, not statistical averages), CONSTRAINTS.md
(required — single-image-only rule is binding), MEMORY.md (if
lessons confirmed).
Deliverable: handoff prompt addressed to the lead agent confirmed
during this session (Kilo Code or Opencode Zen).

## 7 OPENCODE GO: 
I want to build a studio art process journal with
image uploads, process notes, material logs, and a gallery view.
Stack: Opencode Go subscription. Models: glm-5.1 (primary, agentic
multi-file), minimax-m2.7 (fallback, lighter tasks), gpt-5-nano
(fast low-stakes tasks via Opencode Zen free).
Hard constraint: all three models are PRC-affiliated — this project
must contain no politically sensitive content of any kind.
Files: DECISIONS.md (required), DESIGN.md (required — gallery
view must reflect the user's own aesthetic, not AI defaults),
CONSTRAINTS.md (required — PRC model restriction is permanent and
binding), MEMORY.md (if lessons confirmed).
Deliverable: handoff prompt for Opencode Go (glm-5.1 as lead).

## 2 OPEN SOURCE: 
I want to build a language learning micro-story
engine where users pick a target language and a vocabulary list
and receive original micro-stories (200–400 words) that embed
the target words naturally in context, with a glossary and
comprehension questions per story.
Stack: Opencode Go + Kilo Code + Groq + OpenRouter free tier.
Models: glm-5.1 (primary agentic lead — multilingual generation
strength), minimax-m2.7 (fallback, narrative generation),
gpt-5-nano via Opencode Zen free (fast low-stakes tasks).
Reasoning: gpt-oss-120b:free via OpenRouter. Implementation:
devstral-small:free or llama-4-scout:free via OpenRouter.
Fast queries: Groq compound, 30K TPM hard limit, 30 req/min
total. Note: all Opencode Go models are PRC-affiliated — this
project must contain no politically sensitive content of any
kind. OpenRouter free tier requests must be sequential, not
simultaneous. Routing models (kilo-auto/free, openrouter/free)
may vary between sessions — record actual model served in
DECISIONS.md each session.
Files: DECISIONS.md (required), DESIGN.md (required — story
output formatting and UI must reflect the user's aesthetic
references, not generic language-app defaults; ask for
References before any interface or output design question),
CONSTRAINTS.md (required — PRC model restriction, sequential
request architecture, and 30K TPM limit are all binding),
MEMORY.md (if lessons confirmed this session).
Deliverable: handoff prompt for Opencode Go (glm-5.1 as lead).

## 8 PAID STACK: 
I want to build a studio art portfolio site where
each piece has a full process journal — materials, stages,
references, and notes — alongside the final work, with
microformats2 h-entry markup, a gallery view that reflects my
confirmed aesthetic identity, and GET /export.json and
GET /feed.xml endpoints.
Stack: All six paid tools via creatr command. Routing:
scaffold→Codex (schema, image data model with placeholder slots,
file structure — no real images required at this phase),
spec→Claude Code (microformats2 h-entry, export and feed
endpoints, irreversible URL structure decisions),
ui→Gemini (gallery view and process journal UI, working against
placeholder assets until Cursor phase),
feature→Cursor (real image integration, materials tagging,
process stage filtering, gallery refinements),
build→Vibe CLI (build pipeline and deployment scaffolding),
inline→Copilot (inline edits and mechanical refinements),
review→Claude Code via EVAL_PROMPT (full spec compliance,
export endpoint validation, pre-merge checklist).
Each tool handles only its designated task type — no
cross-routing. Real images are introduced in the Cursor
feature phase only, not during scaffold, spec, or UI phases.
Files: DECISIONS.md (required — URL structure and h-entry
schema are irreversible decisions requiring explicit sign-off
before Claude Code spec phase begins), DESIGN.md (required —
gallery UI must be derived from confirmed Derived Identity,
not generic portfolio defaults; Gemini UI phase is blocked
until DESIGN.md References and Derived Identity are confirmed),
CONSTRAINTS.md (required — image-last sequencing rule and
URL structure freeze are binding constraints),
MEMORY.md (if lessons confirmed this session),
EVAL_PROMPT.md (required — review criteria must be confirmed
before the Claude Code review step).
Deliverable: handoff prompts for each tool in routing order,
formatted as a numbered sequence.