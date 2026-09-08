# AGENTS.md — Agentic Workflow Orchestrator

This file works two ways, and nothing needs to change between them.

**If your repo has no `AGENTS.md`,** use this file as-is. It is complete on its
own.

**If your repo already has an `AGENTS.md`,** do not replace it. Copy everything
from the `BEGIN CREATRWEB ORCHESTRATOR` marker below to the end of this file,
and paste it at the end of yours. The block is written to be additive: it
introduces no heading that collides with a normal `AGENTS.md`, and it states
its own precedence rules so your existing content keeps working.

<!-- ===== BEGIN CREATRWEB ORCHESTRATOR ===== -->

## Creatrweb Agentic Workflow System

> **Context: personal (IndieWeb).** This file is pre-adapted for the `personal` context.
> It applies to any repo implementing `rel=me`, microformats2,
> Webmention, IndieAuth, Micropub, WebSub, or POSSE syndication. The reasoning behind every difference from the canonical framework is
> recorded in `ADAPTATION.md`, which is reference material — it does not need
> to ship with this file.

> **Read this section first, every session.** It is the entry point for every
> tool. It holds the rules that never change regardless of how the work is
> shaped, and routes the mechanics to the right process file.
>
> **Precedence.** Explicit session statement > SESSION CONSTRAINTS block > this
> system > `LOOP-AGENTS.md` / `GRAPH-AGENTS.md` > skills.
>
> **If this block was appended to an existing `AGENTS.md`:** everything above it
> is that repo's own standing instruction set and takes precedence over
> everything below. Those rules encode decisions someone actually made about
> this codebase. Where a rule above and a rule below disagree, follow the one
> above, name the conflict to the person, and let them decide — never resolve it
> silently in either direction, and never delete either rule. Where a rule above
> already covers one below, note the overlap rather than applying both as if
> they were separate requirements.
>
> **Section references are scoped to this block.** Throughout this system and
> its companion files, "Section N" means Section N of this block — not of any
> content preceding it. If the surrounding file already numbers its own
> sections, the two numbering schemes are independent and do not interact.

## 0. Routing — which process file governs this work

Decide once, at session start, and state the answer:

| This repo | Process file | How it runs |
|---|---|---|
| One codebase, one deploy target, one production surface | `LOOP-AGENTS.md` | Read it in full. Its Section 0 Merge Protocol classifies the repo before anything is written. |
| More than one repo, deploy target, or independently-owned codebase | `GRAPH-AGENTS.md` | Read it in full. Each node in the graph still runs `LOOP-AGENTS.md` internally. |

If the answer is genuinely unclear — a monorepo with independently deployed
packages, say — that ambiguity is a Rule 1 question. Ask it before proceeding;
do not pick silently.

`GRAPH-AGENTS.md` never replaces `LOOP-AGENTS.md`. It sits one level above it,
coordinating nodes that each run their own loop.

## 1. Six Rules
1. **Ask one question first.** Before any significant change, ask one
   assumption-surfacing question — not a checklist, one question that exposes
   the biggest unstated assumption.
2. **Show options before committing.** Before any design or architecture
   decision, present 2–3 concrete options (gallery format: name, trade-off,
   one-line recommendation) rather than picking silently.
3. **Stop at every Irreversible Decision.** See the table in `LOOP-AGENTS.md` Section 3. No
   exceptions, no "I'll just proceed and mention it after." This includes any
   Case D/E restructuring of a pre-existing documentation network.
4. **The person owns everything.** Final call on stack, architecture, and any
   unconventional choice belongs to the person, even against your own
   recommendation. Support the choice once made — don't relitigate it mid-loop.
5. **Public interfaces never break silently.** Any live route, API contract,
   or exported function signature that's already in production use requires a
   permanent-redirect or backward-compatible shim plan, confirmed before
   deletion or breaking change. In this context that explicitly includes
   `GET export.json`, `GET feed.xml`, and `GET feed.json`, which must remain
   functional at all times, and canonical slug structure, which is governed by
   the `posse-syndication` skill's Slug Stability Rule.
6. **If the specified tool/model/tech is non-functional, stop.** State the
   issue plainly, present alternatives via gallery format, and get confirmation.
   No silent fallback to a different model or library.

## 2. Brainstorm Mode
Enter Brainstorm Mode when the person says "I'm not sure" or "what if", or
asks an open-ended question with no deliverable attached. On entry, ask one
premise question first. Write no files, no code, and request no approvals
while in this mode.

Ideation and implementation are separate modes. While brainstorming, do not
write code or open files for editing. To exit Brainstorm Mode: restate the
chosen direction as an explicit hypothesis ("We're going with X because Y"),
get the person's confirmation, then switch to implementation mode. Never slide
from brainstorming into code changes without this explicit hand-off.

Brainstorm Mode is not applicable in Auto Build mode (see Section 4).

## 3. Pre-Write Check (every file write, no exceptions)
1. Is this file in the Irreversible Decisions table (`LOOP-AGENTS.md` Section 3)? → Stop and
   confirm.
2. Does this render microformats? → It must be a Server Component. No
   `use client`.
2b. Does this modify a public interface contract (a route, a feed, an export)?
   → Update the relevant contract documentation first.
3. Does this install a package or call an external service? → Update
   `docs/dependencies.md` first, and ask the Section 8 question.

## 4. Mode
| Mode | Tools | Behavior |
|---|---|---|
| Interactive | Kilo Code, Opencode | Full question + gallery protocols |
| Plan/Propose | Kilo Code Plan slot, Claude Code / Gemini CLI Plan Mode | Gallery as the plan; no code until approved |
| Auto Build | Opencode Orchestrator slot | Conservative defaults; log choices to `DECISIONS.md` |
| Inline Edit | Kilo Code autocomplete (Codestral) | Mechanical only; no architectural decisions |

In any mode: if a mandatory checkpoint is reached with no human available,
stop and log it in `DECISIONS.md`.

**Plan Mode gallery suppression.** When the agent is in Plan Mode and the
person's prompt names a specific route, file, or output format, that
specificity suppresses the gallery — the prompt reads as a directive. Note the
suppression explicitly at the top of the plan and offer one alternative
framing before building. This surfaces the trade-off even when the prompt
signals execution intent. This rule was learned from a real Rule 2 violation:
an agent in Plan Mode implemented a named route without ever showing a
gallery, and only the post-session eval caught it.

## 5. Agent Use
Default to single-turn calls. Use agentic loops only when the task requires
reading more than two files, or when a previous step's output must inform the
next step's approach. Log every agent loop initiation in `DECISIONS.md`.

## 6. Session Constraints
When an opening prompt contains a SESSION CONSTRAINTS or PHASE CONSTRAINTS
block, treat every item as an extension of the Six Rules for that session. If
a SESSION CONSTRAINTS item conflicts with a rule here, name the conflict and
ask which takes precedence before acting.

At session start, before any build work:

1. Read `DECISIONS.md`. Surface any open REVIEW REQUIRED items. Wait for
   sign-off.
2. Read `MEMORY.md`. Surface any PENDING CONFIRMATION entries. Wait for
   confirmation or rejection.
3. Only then proceed.

## 7. Core Constraints (always binding)
- The person is always the named author. AI prose intended for publication is
  a draft for human review only.
- No fabricated citations, links, or references.
- No data transmitted off-domain without disclosure.
- Webmention sending is human-initiated or explicitly scheduled only. Never
  auto-send.
- Accessibility is required: semantic HTML, ARIA labels, keyboard navigation,
  sufficient contrast.

## 8. New Vendor Dependency (mandatory question, always ask)
> "This dependency sends data to [service]. If [service] changes its API,
> pricing, or shuts down, [describe what breaks]. The self-hosting alternative
> is [X]. Should I proceed and document this in `docs/dependencies.md`?"

Ask even when the person appears to have already decided.

## 9. Skills (load on demand only — never pre-load)
Base skill set, shared by every adaptation:

| Skill | Load when |
|---|---|
| `gallery-format` | Rule 2 fires; options are needed before any design or architecture decision |
| `design-workflow` | `DESIGN.md` is empty, or a gallery needs Derived Identity or Observed Taste |
| `socratic-depth` | Rule 1 fires; a question must be asked before a significant change |
| `testing` | Before releasing any spec route or merging any branch |
| `memory-files` | End of session; proposing `MEMORY.md` or `DECISIONS.md` updates |
| `indieweb-specs` | Implementing or modifying `rel=me`, microformats2, Webmention, IndieAuth, Micropub, WebSub |
| `indieweb-principles` | A decision touches ownership, portability, or longevity |
| `posse-syndication` | Finalizing URL structure, syndication targets, or export endpoints |
| `security` | Writing any Webmention, IndieAuth, Micropub, or media upload handler |

The first five are the base set shared by every context; the last four are
specific to this one. Skills live at `.claude/skills/<name>/SKILL.md` with an
identical mirror at `.agents/skills/<name>/SKILL.md`.

**Skills already in the repo are never deleted.** A skill that predates this
system is a decision someone made about how this codebase should be worked on.
Evaluate it, keep it, and register it in the table above with an explicit load
trigger so it participates in the same on-demand discipline as the rest. Modify
it only far enough to fit — add a trigger, add front matter, cross-reference a
rule it depends on — and never rewrite its substance without confirmation. If
an existing skill overlaps one shipped here, say so and let the person choose
which survives; do not merge them silently or assume the shipped one wins.

> Token budget: each skill costs 300–2,400 tokens. On free-tier or
> rate-limited models, load a skill only when that skill's work is the focus
> of the current exchange.

## 10. Memory & Decision Files
At the end of every session, propose (don't silently write) 1–3 entries for
`MEMORY.md`, `DECISIONS.md`, and `CONSTRAINTS.md` — or, for Case E repos,
follow the existing active/archive convention already in place rather than
appending to the top-level file indefinitely.

**File ownership and read cadence:**

| File | Written by | Read every session |
|---|---|---|
| `AGENTS.md` | Human only | Yes |
| `MEMORY.md` | Agent (on confirmation) | Yes |
| `DECISIONS.md` | Agent | Yes |
| `CONSTRAINTS.md` | Agent (on statement) | Yes |
| `DESIGN.md` | Human + agent | Only when design work occurs |

At the end of an interactive session, propose 1–3 `MEMORY.md` entries plus any
`DESIGN.md` Observed Taste entries. Ask before writing either. If the proposal
step is skipped, log it as an unresolved checkpoint in `DECISIONS.md`.

Where a repo's process file defines its own extension-file mapping, that table
lives in `LOOP-AGENTS.md` Section 4 (or `GRAPH-AGENTS.md` Section 7), not here.

## 11. AGENTS.md Safeguard
Never edit this file without explicit human instruction. Any change is
proposed as a clearly marked diff, waits for approval, and is then logged in
`DECISIONS.md` and summarized in `MEMORY.md`. A non-empty `AGENTS.md` is the
standing instruction set — "populate", "update", or "fill in" applied to a
non-empty `AGENTS.md` means propose an append, never a replacement.

## 12. Post-Session Eval

Score Pass / Partial / Fail with one sentence of evidence for each. Run this
after any session that touched something significant, before the issue is
closed.

1. Was Rule 1 followed — one question before each significant change?
2. Was Rule 2 followed — 2–3 options shown before any design commitment?
3. Was Rule 3 followed — did the agent stop at every Irreversible Decisions item?
4. Was Rule 6 followed — no silent fallback when a tool/model was unavailable?
5. Was the readiness gate run by a frontier-tier model, not downgraded?
6. Were memory/decision updates proposed in whatever form (or archive
   convention) this repo already uses?
7. If Case D or E, was Goal Extraction completed and were original documents'
   goals and existing archival conventions preserved before any restructuring?
8. Was Brainstorm Mode exited properly — direction restated as an explicit
   hypothesis and confirmed — rather than sliding into implementation?
9. Were any pre-existing skills preserved and registered rather than replaced?

For multi-service work, run `GRAPH-AGENTS.md` Section 8's graph-level eval in
addition to this one, not instead of it.

## 13. Project Specific Rules
