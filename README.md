# Creatrweb

A framework for meaningful human-AI creative collaboration in software
development. It ships as four complete, self-contained markdown systems — `general/`,
`personal/`, `general_starter/`, and `personal_starter/` — each one a drop-in
payload that integrates loop engineering, graph engineering, and a set of
skills built to keep human judgment, taste, and critical thinking at the center
of the work. Between them they cover a fresh repo, a mature codebase that
already has its own agentic markdown, and everything in between.

This framework applies three principles consistently across every AI tool you use:

1. **Ask before assuming.** Agents surface hidden assumptions with one
   question before any significant change, rather than guessing and hoping.
2. **Show options before committing.** Design and architecture decisions get
   2–3 concrete choices in gallery format, not a single silent pick.
3. **The person owns everything.** Final say on stack, architecture, scope,
   and unconventional choices belongs to the person — always.

## How to use it

Two questions decide which folder you want: **what kind of site is this**, and
**what's already in the repo**.

|  | New or lightly-documented repo | Repo that already has agentic markdown |
|---|---|---|
| **Any site or app** | `general/` | `general_starter/` |
| **Personal / IndieWeb site** | `personal/` | `personal_starter/` |

All four are complete, self-contained embedded systems. Copy a folder's
contents into your repo root and you have everything — no second file to apply
on top, and nothing pointing back at this repo.

**Choosing the context.** Use `personal/` or `personal_starter/` for any repo
implementing `rel=me`, microformats2, Webmention, IndieAuth, Micropub, WebSub,
or POSSE syndication. Use `general/` or `general_starter/` for everything else.
Picking one is a conscious decision, not a default — moving from `general` to
`personal` later is additive, while starting with `personal` on a project that
never needs it loads four skills you'll never trigger.

**Choosing the variant.** The plain folders install a clean system and assume
you want it as written. The `_starter` folders are for repos that already have
something — an `AGENTS.md` someone else wrote, a `process.md`, a task template,
coursework rubrics, a mature `MEMORY.md`/`DECISIONS.md` pair with archive
splits. They swap the full payload for a `START-HERE.md` that reads what's there first, extracts each
existing file's original purpose in its own terms, classifies the repo against
the five Merge Protocol cases, and then creates only what's missing. Existing
files are kept, annotated, or extended — never overwritten, and where existing
rules conflict with the framework's, the existing rules win by default and the
conflict is surfaced rather than resolved silently.

If you're between the two — a repo with a README and little else — either works.
`_starter` is the safer choice, since it degrades to a plain install when it
finds nothing to reconcile.

**Running it.** Open the folder's `SYSTEM-README.md` and follow it — it has the steps
and, at the end, both setup prompts ready to copy. Copying the files in is
already a working install; the prompts populate the model roster and reconcile
anything your repo already had. In a `_starter` folder, `START-HERE.md` is the
prompt to paste for a normal install.

Existing work is never destroyed. An `AGENTS.md` you already have is never
replaced — the orchestrator ships as an appendable block, marked off so you can
paste it at the end of your own file, and it defers to your rules where the two
disagree. Rules found in an old `CLAUDE.md` or `.cursorrules` are inventoried
and rehomed before those files become pointers. Skills already in your repo are
registered with load triggers rather than replaced.

Run the setup prompt **once**. After that, `AGENTS.md` Section 0's routing and
`LOOP-AGENTS.md` Section 0's Merge Protocol handle per-session loading on their own — there is no prompt to re-paste at the start
of a session.

## The three-file structure

Every context installs the same three governance/process files, and the split
between them is the point:

| File | Role |
|---|---|
| `AGENTS.md` | **Orchestrator.** Read first, every session, by every tool. Precedence, routing, the Six Rules, Brainstorm Mode, Pre-Write Check, Mode, Core Constraints, the vendor-dependency question, skills, memory-file ownership, Post-Session Eval. |
| `LOOP-AGENTS.md` | **Single-service process.** The five-case Merge Protocol, the four-stage loop, the Model Routing Plan, the Irreversible Decisions table, extension-file mapping. |
| `GRAPH-AGENTS.md` | **Multi-service process.** Node/edge manifest, coordinator role, cross-node irreversible decisions. Sits above `LOOP-AGENTS.md` — it never replaces it, and each node still runs its own loop. |

`AGENTS.md` Section 0 routes between the two process files at session start.
Governance never lives in a process file; process never lives in the
orchestrator. That separation is what lets loop and graph engineering share one
set of rules instead of drifting into two dialects.

## What's in a context folder

The plain folders ship a complete installed system. The `_starter` folders ship
only what cannot be reconstructed — everything else is generated by
`START-HERE.md` from bodies embedded in it.

```
general/  personal/                    general_starter/  personal_starter/
├── AGENTS.md                          ├── AGENTS.md
├── LOOP-AGENTS.md                     ├── LOOP-AGENTS.md
├── GRAPH-AGENTS.md                    ├── GRAPH-AGENTS.md
├── SYSTEM-README.md (+ prompts)        ├── START-HERE.md
├── CLAUDE.md    (pointer)             ├── SYSTEM-README.md (+ prompts)
├── GEMINI.md    (pointer)             ├── .claude/skills/<name>/SKILL.md
├── MEMORY.md                          └── .agents/skills/<name>/SKILL.md
├── DECISIONS.md
├── CONSTRAINTS.md
├── DESIGN.md
├── ADAPTATION.md  (reference only)
├── .claude/skills/<name>/SKILL.md
├── .agents/skills/<name>/SKILL.md
├── .github/copilot-instructions.md
└── .gemini/settings.json
```

Each folder's own `SYSTEM-README.md` carries the implementation steps **and both
setup prompts inline**, so installing means copying files and pasting one prompt
from one file. It's named that way rather than `README.md` so it never collides
with the README your repo already has. Copy skill folders individually rather than copying `.claude/` or
`.agents/` wholesale — a directory-level copy can take your existing skills
with it.

The four memory files ship as headers only, and a starter install writes them
the same way. They are filled in during work, on confirmation, by the
`memory-files` and `design-workflow` skills — never pre-populated. An empty
`DESIGN.md` is a correct state; a fabricated one poisons every future gallery.

`ADAPTATION.md` is reference material explaining why a context differs from the
other. It does not ship to a target repo, and the starter folders omit it
entirely.

## Skills

`general/` and `general_starter/` carry five: `gallery-format` (Rule 2), `socratic-depth` (Rule 1),
`design-workflow` (`DESIGN.md` work), `testing` (pre-merge), `memory-files`
(session end). `personal/` and `personal_starter/` carry those five plus `indieweb-specs`,
`indieweb-principles`, `posse-syndication`, and `security`.

Skills are loaded on demand and never pre-loaded. Each costs 300–2,400 tokens;
on free-tier or rate-limited models, load one only when its work is the focus
of the current exchange. Every skill exists in two byte-identical copies, under
`.claude/skills/` and `.agents/skills/`, so both Claude Code and other agent
runners find it where they look.

## The five Merge Protocol cases

`AGENTS.md` Section 0 classifies your repo before touching anything, and the
agent states which case applies at session start:

- **Case A** — no markdown at all (fresh repo).
- **Case B** — some markdown, none of it agent-governance related.
- **Case C** — a single existing `AGENTS.md` with its own, differently-authored rules.
- **Case D** — a rich, differently-named documentation network that predates this framework (coursework `process.md`/`plan.md`/`tasks.md`, a team workflow).
- **Case E** — a documentation network whose file names already match this framework, at scale (mature `MEMORY.md`/`DECISIONS.md`, archive splits, one-off extension files like `ALGORITHMS.md` or `BACKLOG.md`).

Cases D and E are Irreversible Decisions under Rule 3 — the agent stops and
waits for you either way.

## If the agent skips a rule mid-session

Stop it immediately:

- "Stop. Check AGENTS.md Rule 2 before proceeding."
- "Wait… did you ask the Rule 1 question for this change?"
- "Stop. Which Merge Protocol case applies here, and did you get confirmation
  before restructuring anything?"

Then run the Post-Session Eval in `AGENTS.md` Section 12 to audit what was and
wasn't followed.

## Documentation

`docs/` is reference material about the framework. It is not part of either
payload and never ships to a target repo.

```
docs/
├── WHY.md, RULES.md, FAQ.md, SKILLS.md, STACK-GUIDE.md,
│   WORKED-EXAMPLE.md, CHANGELOG.md, CONTRIBUTING.md,
│   MODEL-INVENTORY.md, PROJECT-BRIEFS.md
├── instructions/    ROUTING_CONFIG.md, KILO_CODE_CONFIG.md
├── stacks/          Per-provider model routing plans (*.txt)
└── testing/         PLANNING_PROMPTS.md
```

Start with `docs/FAQ.md` for which context to choose and how the Merge
Protocol cases apply to a specific repo, and `docs/WORKED-EXAMPLE.md` for a
real six-day build with every gallery, failure, and correction recorded.
