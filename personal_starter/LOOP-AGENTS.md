# LOOP-AGENTS.md — Single-Service Loop Engineering

> **Context: personal (IndieWeb).** This file is pre-adapted for the `personal` context.
> It applies to any repo implementing `rel=me`, microformats2,
> Webmention, IndieAuth, Micropub, WebSub, or POSSE syndication.
> Installed via `START-HERE.md`, which adapts to whatever agentic markdown the
> repo already has and creates only what is missing.
>
> **This file is process, not governance.** The Six Rules, Brainstorm Mode,
> Pre-Write Check, Core Constraints, skills, and memory-file ownership all live
> in `AGENTS.md`, which is the orchestrator every tool reads first. This file
> defines how a single service's work actually runs: how the scheme merges into
> a repo, the four-stage loop, the model roster, and what stops the loop.
>
> For work spanning more than one repo or deploy target, `GRAPH-AGENTS.md`
> sits above this file — each node still runs this loop internally.

## 0. Merge Protocol (read this first, every session)
Before doing anything else, check the repo root and `.github/`, `.claude/`,
`.agents/`, and `docs/` directories for any existing markdown.

- **Case A — No markdown at all (fresh repo):** install this file as
  `LOOP-AGENTS.md` at repo root verbatim, alongside `AGENTS.md`, and create empty stub files for
  `MEMORY.md`, `DECISIONS.md`, and `CONSTRAINTS.md` (headers only — filled in
  during Phase 1 and at session end).
- **Case B — Some markdown, none of it agent-governance related** (e.g., just
  a `README.md`, `CONTRIBUTING.md`, or `CHANGELOG.md`): leave those files
  untouched and create `LOOP-AGENTS.md` alongside them exactly as in Case A.
- **Case C — A single existing `AGENTS.md` with its own, differently-authored
  rules:** do not overwrite it. Append the Creatrweb
  orchestrator block from `AGENTS.md` (everything from its
  `BEGIN CREATRWEB ORCHESTRATOR` marker onward) to the end of that file, then
  install this file alongside it. Reconcile numbering — treat this
  file's Six Rules as additive/confirmatory if the existing file already has a
  similar rule list. Flag any direct contradiction to the person instead of
  silently picking a winner.
- **Case D — A rich, differently-named pre-existing documentation network**
  (e.g., `process.md`, `plan.md`, `task-template.md`, `tasks.md`, benchmark/
  audit docs, or team docs — a network whose file names don't already match
  this scheme's, typically because it predates this scheme entirely, e.g.
  coursework or a pre-existing team workflow):
  1. **Goal Extraction (read-only):** summarize each existing file's original
     purpose in one line before proposing any change. Do not restructure yet.
  2. **Mapping:** map each file to the closest concept in this scheme.
  3. **Reconciliation proposal (gallery format, Rule 2):** propose exactly one
     of three outcomes per file — keep as-is and cross-link; lightly annotate
     without rewriting; or fold in and deprecate (only for small files clearly
     superseded — never for large or actively-used ones).
  4. **Explicit confirmation required** before touching any file. The original
     document's intent must survive even if its form is reorganized.
  5. Only after confirmation, apply the agreed restructuring.
- **Case E — The file names already match this scheme, at scale** (e.g., an
  existing `AGENTS.md`/`MEMORY.md`/`DECISIONS.md`/`CONSTRAINTS.md`/`DESIGN.md`
  family that's already Creatrweb-lineage, but mature — large
  files, an active/archive split like a `docs/decisions-archive.md`, or
  repo-specific extension files with no scheme equivalent, e.g. `ALGORITHMS.md`,
  `BACKLOG.md`, `SETUP.md`, or a `scratch_*.md` working file):
  1. **Adopt, don't duplicate.** Treat the existing `AGENTS.md` (and its
     siblings) as canonical content already. Never create a
     second, parallel file or append a redundant "imported" section — diff
     against `AGENTS.md` Sections 1–2 only to confirm the Six Rules and
     Brainstorm Mode already present are equivalent, and flag drift instead of
     silently overwriting.
  2. **Detect and follow existing archival conventions.** If `MEMORY.md` or
     `DECISIONS.md` already has a companion archive file, follow that repo's
     existing split (e.g., prune the active file into the archive at whatever
     cadence the repo already uses) rather than imposing Section 6's simple
     append rule from scratch.
  3. **Register, don't restructure, one-off extension files.** For any file
     with no equivalent in this scheme (`ALGORITHMS.md`, `BACKLOG.md`,
     `SETUP.md`, `scratch_*.md`, etc.), add a one-line purpose note to
     this file's Section 4 mapping table rather than folding its content
     in or renaming it. A file like `ALGORITHMS.md` — a business-logic spec —
     becomes a **required citation source** for any issue whose acceptance
     criteria depend on preserving existing behavior (this matters directly
     for PHP→React/Node translation issues: cite the relevant `ALGORITHMS.md`
     section, and treat any mismatch between the doc and the actual code as a
     Rule 1 question — which one is source of truth?).
  4. State explicitly which extension files you found and how each was
     registered.
- **If `DECISIONS.md` / `MEMORY.md` already exist and are simple (not Case
  E-scale):** append, never truncate.

State explicitly at the start of the session which case applies and what you
did (or, for Case D/E, what you found and proposed) about it.

## 1. The Loop
Every unit of work in this repo runs through four stages, tracked as one
GitHub issue per loop. This applies equally to a repo's very first issue and
its thousandth. If a Case D/E network already has its own loop description or
backlog (e.g., a `process.md`, or a `BACKLOG.md` staging issues before they're
filed), this section is cross-referenced to it rather than duplicating it.

1. **Issue creation** — scope written as a single testable outcome, not a
   feature bundle. Include acceptance criteria and which files/modules are
   expected to change. For translation/migration work, cite the relevant
   section of `ALGORITHMS.md` (or equivalent) as part of the acceptance
   criteria if one exists.
2. **Implementation** — scoped strictly to the issue. If the work reveals a
   need to touch something outside scope, stop and open a new issue (Rule 1
   applies: ask before expanding scope).
3. **QA self-review** — the implementing agent (or a different model, see
   Section 2) re-reads the diff against the issue's acceptance criteria,
   checks for regressions in adjacent code, and runs the test suite.
4. **Production-readiness gate** — a frontier-tier model evaluates: does this
   pass QA, does it touch anything in the Irreversible Decisions table, is
   documentation (`MEMORY.md`/`DECISIONS.md`, or the mapped equivalent)
   updated, is it safe to merge? This step never gets downgraded to a
   cheap-tier model regardless of how simple the issue looked.

## 2. Model Routing Plan
> This table reflects the **current** roster only. It is populated and
> replaced (never duplicated) via the Documentation Overhaul Prompt (`DOC-OVERHAUL-SINGLE-SERVICE.md`).

```
Stage: Issue scoping / spec drafting
  Provider: Claude Code or Codex
  Model ID: sonnet-5 (Claude Code) or gpt-5.2-codex (Codex)
  Reason: Needs judgment about scope boundaries and acceptance criteria,
          not raw throughput.

Stage: Implementation — mechanical / boilerplate
  Provider: Opencode Go
  Model ID: kimi-k2.5 (frontend/React) or qwen3.6-plus (backend/API)
  Reason: Flat $10/mo, strong enough for scoped file-level work, cheapest
          lane for volume.

Stage: Implementation — complex logic (auth, data layer, migrations)
  Provider: Ollama Cloud
  Model ID: qwen3-coder:cloud
  Reason: Stronger reasoning than the Go bundle without frontier pricing;
          also reachable through Claude Code's Anthropic-compatible endpoint.

Stage: Second-opinion patch review (optional, terminal-native)
  Provider: Mistral Vibe
  Model ID: devstral-2
  Reason: Independent model family catches blind spots the primary
          implementer might share with its own QA pass.

Stage: QA self-review
  Provider: Claude Code
  Model ID: sonnet-5
  Reason: Balanced cost/reasoning for diff review against acceptance criteria.

Stage: Production-readiness gate
  Provider: Claude Code
  Model ID: opus-5
  Reason: Highest-stakes checkpoint in the loop. Never downgrade this stage.
```

## 3. Irreversible Decisions Table
| Action | Required before proceeding |
|---|---|
| Schema migration on a production or shared database | Show migration diff + rollback plan |
| Deleting or renaming a live route/endpoint | Redirect/shim plan confirmed |
| Force-push, history rewrite, or branch deletion | Explicit confirmation, no exceptions |
| Deploying to production | QA + readiness gate both passed |
| Removing a dependency or swapping a core library | Gallery of alternatives shown first |
| Any write to a production database (not staging) | Confirmed scope + backup verified |
| Rotating or exposing secrets/credentials | Explicit confirmation |
| Changing URL or canonical slug structure | Redirect plan confirmed; Slug Stability Rule applied |
| Adding, changing, or removing a `rel=me` link | Explicit sign-off — identity consolidation depends on it |
| Changing an auth endpoint (IndieAuth, Micropub token) | Explicit sign-off |
| Adding or removing a syndication target | Explicit sign-off; export contract re-verified |
| Changing a feed or export format (`feed.xml`, `feed.json`, `export.json`) | Backward-compatible plan confirmed first |
| Adding a vendor dependency | Section 12 question asked and answered |
| Restructuring/folding any Case D file, or any Case E extension file (`ALGORITHMS.md`, `BACKLOG.md`, etc.) | Goal Extraction + Mapping + gallery proposal completed first |
| Treating code as source-of-truth over a conflicting `ALGORITHMS.md` (or equivalent) during translation | Rule 1 question asked and answered explicitly |

## 4. Extension File Mapping

**Extension file mapping table** (populate for Case D/E repos):

| File | Original purpose (one line) | Relationship to this scheme |
|---|---|---|
| e.g. `ALGORITHMS.md` | e.g. "authoritative business-logic spec" | e.g. "required citation for translation issue acceptance criteria" |
