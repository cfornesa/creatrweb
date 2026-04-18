# CreatrWeb — Creative Human-AI Collaboration Framework

A portable kit of context files and loadable skills that guides AI coding
agents toward creative, human-steered development. Works across Claude Code,
Codex CLI, Cursor, Gemini CLI, GitHub Copilot, Vibe CLI, Kilo Code, Opencode,
and Replit from a single source of truth.

This repository contains two variants of the framework:

- **`general_creation/`** — A domain-agnostic version suitable for any software
  project. IndieWeb-specific skills and rules have been removed or generalized.
  Includes the session-start review loop for DECISIONS.md and MEMORY.md.
- **`personal_creation/`** — The original IndieWeb-aligned version, retaining
  all IndieWeb specs, POSSE syndication, Webmention security, and the full
  personal site skill set.

Use the subfolder that matches your project. Copy its contents into your
project root and remove entry-point files for tools you don't use.

To keep token costs low, this framework uses a single source of truth: `AGENTS.md`.

---

## What This Is

This framework applies three principles consistently across every AI tool you use:

- **Human ownership** — the agent asks before building, shows options before
  committing, and stops at irreversible decisions.
- **Distinct voice** — gallery-format choices resist AI averaging. Research
  shows human-steered sessions produce outcomes 2–4× better than passive ones
  (Walton et al., 2026).
- **Longevity** — your architecture stays portable, your public URLs never
  break, and every dependency is documented.

---

## Your Tool Stack

CreatrWeb supports several stacks. Use the one that fits your budget and feel
free to mix and match.

### Paid stack(s)
These tools have free tiers but perform best on paid plans:

| Tool | What it is | Install |
|---|---|---|
| **Claude Code** | Terminal-based agent by Anthropic | `npm install -g @anthropic-ai/claude-code` |
| **Codex CLI** | Terminal-based agent by OpenAI | `npm install -g @openai/codex` |
| **Cursor** | VS Code fork with built-in AI | Download at [cursor.com](https://cursor.com) |
| **Gemini CLI** | Terminal-based agent by Google | `npm install -g @google/gemini-cli` |
| **GitHub Copilot** | In-editor assistant in VS Code | Install **GitHub Copilot** from the VS Code Extensions panel (`Ctrl+Shift+X`) |
| **Replit** | Browser-based agent and IDE | Sign up at [replit.com](https://replit.com) — no install needed |
| **Vibe CLI** | Terminal-based agent by Mistral AI | `npm install -g @mistral/vibe-cli` |

These tools can work individually or in conjunction, depending on your workflow,
preferences, and budget.

### Free stack
These tools and API providers are genuinely free to start with no credit card:

| Tool / Provider | What it is | Install or sign up |
|---|---|---|
| **Kilo Code** | VS Code extension that connects to any model API | Install **Kilo Code** from the VS Code Extensions panel — search "Kilo Code", click the dropdown arrow next to Install, select **Install Pre-Release Version** |
| **Opencode** | Terminal-based agent that connects to any model API | Run `curl -fsSL https://opencode.ai/install \| bash` in your terminal |
| **OpenRouter (free models)** | Routes requests to free models from many providers | Sign up at [openrouter.ai](https://openrouter.ai), go to API Keys, click **Create API Key** — free models need no credit card |

> **Note on Groq:** Groq advertises a free tier but its per-minute token limits
> are restrictive enough that it may not be reliably free for agentic sessions.
> OpenRouter free models are the more consistent zero-cost path for Kilo Code
> and Opencode.

> **Connecting Kilo Code or Opencode to a free API:**
> Once you have an OpenRouter API key, open Kilo Code or Opencode, go to its
> API provider settings, paste your key, and choose a model ending in `:free`.
> On free-tier models, keep your `AGENTS.md` and any loaded skill under ~4,000
> tokens combined. Load one skill at a time.

---

## Repository Structure

your-project/
├── general_creation/           ← Domain-agnostic framework variant
│   ├── AGENTS.md               ← Main instruction file (all agents)
│   ├── CLAUDE.md               ← Claude Code entry point
│   ├── CONSTRAINTS.md          ← Active project constraints (starts empty)
│   ├── DECISIONS.md            ← Architecture log + review loop
│   ├── DESIGN.md               ← Your aesthetic references and identity
│   ├── EVAL_PROMPT.md          ← Post-session compliance audit
│   ├── GEMINI.md               ← Gemini CLI entry point
│   ├── MEMORY.md               ← Confirmed lessons (agent proposes, you approve)
│   ├── .env.example            ← Environment variable reference
│   ├── .agents/
│   │   └── skills/
│   │       ├── gallery-format/   SKILL.md ← Options protocol
│   │       ├── socratic-depth/   SKILL.md ← Assumption-surfacing questions
│   │       ├── design-workflow/  SKILL.md ← Populating and maintaining DESIGN.md
│   │       ├── testing/          SKILL.md ← Test scope and pre-merge checklist
│   │       └── memory-files/     SKILL.md ← Memory file rules and entry format
│   ├── .claude/skills/         ← Symlink or copy of .agents/skills/ for Claude Code
│   ├── .gemini/
│   │   └── settings.json       ← Gemini CLI context configuration
│   └── .github/
│       └── copilot-instructions.md ← GitHub Copilot entry point
│
├── personal_creation/          ← IndieWeb-aligned framework variant (original)
│   ├── AGENTS.md
│   ├── CLAUDE.md
│   ├── CONSTRAINTS.md
│   ├── DECISIONS.md
│   ├── DESIGN.md
│   ├── EVAL_PROMPT.md
│   ├── GEMINI.md
│   ├── MEMORY.md
│   ├── .env.example
│   ├── .agents/
│   │   └── skills/
│   │       ├── gallery-format/
│   │       ├── socratic-depth/
│   │       ├── indieweb-specs/
│   │       ├── indieweb-principles/
│   │       ├── posse-syndication/
│   │       ├── design-workflow/
│   │       ├── security/
│   │       ├── testing/
│   │       └── memory-files/
│   ├── .claude/skills/
│   ├── .gemini/
│   │   └── settings.json
│   └── .github/
│       └── copilot-instructions.md
│
├── instructions/               ← Supporting reference docs
├── stacks/                     ← Stack-specific configuration notes
├── testing/                    ← Framework test fixtures
└── README.md                   ← This file

Files the agent creates during sessions — do not create manually:
MEMORY.md               ← Confirmed lessons (agent proposes, you approve)
docs/dependencies.md    ← Vendor dependency registry (agent maintains)

---

## What Files Do You Actually Need?

### general_creation (any project)

| File or folder | Required for | Skip if |
|---|---|---|
| `AGENTS.md` | Everyone — all agents read this | Never skip |
| `CLAUDE.md` | Claude Code users | You don't use Claude Code |
| `GEMINI.md` + `.gemini/settings.json` | Gemini CLI users | You don't use Gemini CLI |
| `.github/copilot-instructions.md` | GitHub Copilot users | You don't use Copilot |
| `CONSTRAINTS.md` | Everyone | Agent creates it; don't make manually |
| `DECISIONS.md` | Everyone | Agent creates it; don't make manually |
| `MEMORY.md` | Everyone | Agent creates it; don't make manually |
| `DESIGN.md` | Projects with a visual or UX component | Projects with no visual component |
| `EVAL_PROMPT.md` | Anyone running post-session audits | Optional but strongly recommended |
| `skills/gallery-format` | Everyone — fires with Rule 2 | Never skip |
| `skills/socratic-depth` | Everyone — fires with Rule 1 | Never skip |
| `skills/design-workflow` | Anyone using `DESIGN.md` | Projects with no visual component |
| `skills/testing` | Everyone — pre-merge checklist | Never skip |
| `skills/memory-files` | Everyone — fires at session end | Never skip |
| `.env.example` | Projects with environment variables | Fully static projects |

### personal_creation (IndieWeb / personal site)

Includes everything above, plus:

| File or folder | Required for | Skip if |
|---|---|---|
| `skills/indieweb-specs` | Implementing rel=me, microformats2, Webmention, IndieAuth, Micropub, WebSub | Projects with no IndieWeb features |
| `skills/indieweb-principles` | Decisions touching ownership, portability, or longevity | Projects with no IndieWeb features |
| `skills/posse-syndication` | Finalizing URL structure, syndication targets, or export endpoints | Projects with no syndication |
| `skills/security` | Writing any Webmention, IndieAuth, Micropub, or media upload handler | Projects with no auth or Webmention |

---

## The Review Loop (general_creation)

The `general_creation` variant adds an explicit session-start review loop not
present in the original framework. This ensures that decisions made in Auto Build
mode or incomplete sessions are surfaced to you before new code is written.

### How it works

**In `DECISIONS.md`:** At the end of any Auto Build or incomplete interactive
session, the agent writes a `REVIEW REQUIRED` block using this format:

## REVIEW REQUIRED — Read before starting next session
<!-- Agent writes this block. Confirm or override each item before new code is written. -->
- [ ] [DATE] [TOOL] Conservative default applied: [what was chosen and why]
- [ ] [DATE] Gallery deferred: [what decision was skipped and what options were considered]

Resolved items are marked `[x]` and left in place as an audit trail. They are
never deleted.

**In `MEMORY.md`:** Any lesson the agent proposed but you did not confirm or
reject in the same session is marked `PENDING CONFIRMATION`. The agent surfaces
these at the next session start before proceeding.

**In `AGENTS.md`:** The session-start protocol requires the agent to:
1. Read `DECISIONS.md` — surface any open `REVIEW REQUIRED` items and wait for
   sign-off before any build work.
2. Read `MEMORY.md` — surface any `PENDING CONFIRMATION` entries and wait for
   confirmation or rejection.
3. Only then proceed.

This makes the review loop **agentic** — the agent initiates it, not you. You
don't need to remember to read `DECISIONS.md` after every session.

---

## Using AI Chatbots to Fill In Your Markdown Files

Before your first coding session, several files benefit from human-written
content. An AI chatbot — Claude via Perplexity, ChatGPT, Gemini, or any
conversational AI — can help you think through and draft this content without
touching your codebase. This is a preparation step, not a coding step.

### DESIGN.md — References and Declared Preferences

> "I want to fill in the References section of a design identity file.
> Ask me questions about websites, apps, art, or visual work I admire,
> and help me articulate what I find compelling about them.
> Don't suggest anything yet — just ask."

After several exchanges:

> "Based on what I've described, what common threads do you see across
> my references? Present it as a hypothesis, not a conclusion — I'll
> confirm or correct it."

The output becomes your Derived Identity section. Paste it into `DESIGN.md`
and confirm or edit it before your first session.

### CONSTRAINTS.md — Non-Negotiables

> "I'm starting a software project. Ask me questions to help me identify
> any non-negotiable rules I have about dependencies, data privacy,
> licensing, or technical choices. One question at a time."

Any constraint that surfaces goes into `CONSTRAINTS.md` before your first
coding session. Agents treat this file as a no-fly zone.

### DECISIONS.md — Project Profile

> "I want to build [plain-language description]. Help me articulate my
> stack, deployment target, database approach, and key version constraints
> in plain language — no jargon unless I introduce it first."

Paste the result into the Project Profile section of `DECISIONS.md`. If
you leave it blank, your coding agent will ask the same questions at
session start — either approach works.

### AGENTS.md — When to Add Something

`AGENTS.md` is the one file you should not draft with a chatbot from scratch —
the version in each subfolder is the authoritative template. The only time to
add something before a first session is a project-specific rule you know in
advance will matter. Propose it as a diff, confirm it, then add it.

---

## Setup — New Project

### Step 1 — Choose your variant

Copy the contents of either `general_creation/` or `personal_creation/` into
your project root. If you're building a personal site with IndieWeb features,
use `personal_creation/`. For anything else, use `general_creation/`.

### Step 2 — Prune for your tool stack

Remove entry-point files for tools you don't use (e.g. if you don't use
Gemini CLI, you don't need `GEMINI.md` or `.gemini/settings.json`).

### Step 3 — Fill in DESIGN.md and CONSTRAINTS.md (recommended)

Use the chatbot workflow above before your first coding session. The more
context your agents have on day one, the fewer clarifying questions they
need to ask mid-build.

### Step 4 — Set up your environment

Copy `.env.example` to `.env` and fill in any values your project needs.
Add your OpenRouter API key here if using the free stack. Never commit
`.env` to version control.

### Step 5 — Start your first session

Open your chosen agent tool in the project directory and begin. The agent
reads `AGENTS.md` automatically.

### Step 6 — Reference AGENTS.md at session start

Start every session with a SESSION CONSTRAINTS block:

> "Starting a new session.
> SESSION CONSTRAINTS: Follow all rules in AGENTS.md when processing
> all prompts in this conversation. Are you ready?"

**If the agent skips a rule mid-session**, stop it immediately:
- "Stop. Check AGENTS.md Rule 2 before proceeding."
- "Wait — did you ask the Rule 1 question for this change?"

---

## How Skills Work

Skills are focused instruction sets that extend `AGENTS.md` for specific tasks.
They live in `.agents/skills/` and are loaded on demand — the agent reads a
skill's `SKILL.md` only when the situation calls for it, keeping active context
lean.

### Loading a skill

Reference a skill by name in your session prompt or mid-session:

> "Load `gallery-format` and show me options for the authentication approach."

Or, if `AGENTS.md` instructs the agent to load a skill automatically
(e.g. Rule 2 fires), the agent reads it without you needing to ask.

### Skill reference — general_creation

| Skill | Load when |
|---|---|
| `gallery-format` | Rule 2 fires — options needed before any design or architecture decision |
| `socratic-depth` | Rule 1 fires — a question must be asked before a significant change |
| `design-workflow` | `DESIGN.md` is empty, or a gallery needs Derived Identity or Observed Taste |
| `testing` | Before merging any branch or releasing any feature |
| `memory-files` | End of session; proposing `MEMORY.md` or `DECISIONS.md` updates |

### Skill reference — personal_creation (additional skills)

| Skill | Load when |
|---|---|
| `indieweb-specs` | Implementing or modifying rel=me, microformats2, Webmention, IndieAuth, Micropub, WebSub |
| `indieweb-principles` | A decision touches ownership, portability, or longevity |
| `posse-syndication` | Finalizing URL structure, syndication targets, or export endpoints |
| `security` | Writing any Webmention, IndieAuth, Micropub, or media upload handler |

> **Token budget:** Each skill costs 300–2,400 tokens. On free-tier models
> (OpenRouter), load only when that skill's work is the focus of the current
> exchange. Never pre-load.

---

## How to Add a Custom Skill

1. Create a directory under `.agents/skills/your-skill-name/`
2. Add a `SKILL.md` file describing when to load it and what it governs
3. Add its name and load trigger to the SKILLS table in `AGENTS.md`
4. Reference it in your session prompt to load it: `"Load your-skill-name"`

This is the intended extension point for making `general_creation` domain-specific
to your project without modifying the core framework files.

---

## File Reference

### `AGENTS.md`
The authoritative instruction file. Read by every agent on every session start.
Contains the Six Rules, Brainstorm Mode, Mode table, Agent Use gate, Core
Constraints, Vendor Dependency question, Skills table, Memory Files table,
session-start review loop, and AGENTS.md Safeguard.

**Do not edit during a session.** The agent proposes changes as a diff and
waits for approval.

---

### `CLAUDE.md`
Claude Code's entry point. Imports `AGENTS.md` so the full ruleset loads
without duplication.

@AGENTS.md
<!-- Claude Code-specific additions below. -->

---

### `GEMINI.md`
Gemini CLI's entry point. Requires `.gemini/settings.json`.

---

### `CONSTRAINTS.md`
Starts empty. Created by the agent the first time you state a constraint.

CONSTRAINT  No third-party analytics or tracking scripts
SCOPE       All pages and API routes
SET         YYYY-MM-DD

---

### `DECISIONS.md`
Agent-maintained audit trail for every architectural decision. In `general_creation`,
also contains the `REVIEW REQUIRED` block for the session-start review loop.
Starts as a template. You never need to write to it directly.

---

### `MEMORY.md`
Confirmed lessons that persist across sessions and tools. The agent proposes
entries at session end; you approve or reject before they are written. Entries
marked `PENDING CONFIRMATION` are surfaced at the next session start.

---

### `DESIGN.md`
Your aesthetic identity file. Three sections:

- **References** — works, sites, or art you admire. Your words.
- **Derived Identity** — the agent's synthesis, confirmed by you.
- **Observed Taste** — patterns noticed across sessions, proposed at session end.

Load `design-workflow` when you're ready to populate this file.

---

### `EVAL_PROMPT.md`
Post-session compliance audit. Paste into the tool that just completed the
session. Scores each rule Pass / Partial / Fail with one sentence of evidence.

---

### `.agents/skills/`
Loadable instruction sets. Each skill is a directory with a `SKILL.md` file.
Load on demand only — never pre-load.

---

### `.gemini/settings.json`
Required for Gemini CLI.

```json
{
  "context": [
    "AGENTS.md",
    "DECISIONS.md",
    "CONSTRAINTS.md",
    "DESIGN.md",
    "MEMORY.md"
  ],
  "ignore": [
    "node_modules",
    ".env",
    ".env.*"
  ]
}
```

---

## Agent-by-Agent Guide

### Claude Code
**Best for:** Multi-file work, security hardening, sessions requiring strong
instruction-following.
**How it reads context:** Reads `CLAUDE.md` natively, which imports `AGENTS.md`.
Skills load on demand by name.
**Cost:** Paid (Anthropic subscription or API credits).
**Tip:** Reference `@CONSTRAINTS.md` and `@MEMORY.md` in the opening prompt for
full persistent context.

---

### Codex CLI
**Best for:** Phase 1 scaffolding, schema design, strict question-before-build
discipline with full terminal access.
**How it reads context:** Reads `AGENTS.md` natively from the project root.
**Cost:** Paid (OpenAI API credits).
**Tip:** Start each session with a SESSION CONSTRAINTS block.

---

### Cursor (Chat and Composer)
**Best for:** Day-to-day feature work, inline edits, suggestions before auto-apply.
**How it reads context:** Reads `AGENTS.md` natively in Chat and Composer modes.
Inline edit is mechanical-only.
**Cost:** Free tier available; Pro plan recommended for heavy use.
**Tip:** In Composer, ask for a plan first. It takes gallery form naturally when
`AGENTS.md` is in context.

---

### Gemini CLI
**Best for:** UI components, interactive feature development, rapid gallery-style
iteration.
**How it reads context:** Requires `.gemini/settings.json`.
**Cost:** Free tier available via Google AI Studio API key.
**Tip:** SESSION CONSTRAINTS is especially important for Gemini — never skip it.

---

### GitHub Copilot (Chat)
**Best for:** In-editor assistance, targeted help on a single file or function.
**How it reads context:** Reads `AGENTS.md` as a repository instruction file,
and `.github/copilot-instructions.md` natively.
**Cost:** Paid (GitHub subscription); free tier available with limits.
**Tip:** Treat suggestions as proposals. Review before accepting, especially for
routes or schemas.

---

### Vibe CLI
**Best for:** Autonomous full-stack scaffolding sessions.
**How it reads context:** Reads `AGENTS.md` natively. Skills in `.agents/skills/`
are discovered automatically.
**Cost:** Paid (Mistral API key required).
**Known limitation:** Auto Build mode does not pause for gallery confirmation.
The session-start review loop in `general_creation` will surface deferred
galleries at the next interactive session.

---

### Kilo Code (free stack)
**Best for:** VS Code users who want a full agent experience on a free API budget.
**What it is:** A VS Code extension — similar to Cursor's Composer but
model-agnostic — that connects to OpenRouter, Anthropic, OpenAI, Google, or
local models.
**How it reads context:** Reads `KILO.md`, which imports `AGENTS.md`. Skills
load on demand by name.
**Cost:** Free with OpenRouter free-tier API keys.
**Install:** In VS Code, open Extensions (`Ctrl+Shift+X`), search "Kilo Code",
click the dropdown arrow next to Install, select **Install Pre-Release Version**.
**Tip:** Keep `AGENTS.md` plus any loaded skill under ~4,000 tokens combined.
Load one skill at a time.

---

### Opencode (free stack)
**Best for:** Terminal users who want Claude Code or Codex CLI behavior on a
free API budget.
**What it is:** A terminal-based agent — same interaction model as Claude Code —
that connects to any model provider.
**How it reads context:** Reads `OPENCODE.md`, which imports `AGENTS.md`. Skills
load on demand.
**Cost:** Free with OpenRouter free-tier API keys.
**Install:** `curl -fsSL https://opencode.ai/install | bash`
**Tip:** Run `opencode` from your project root so it picks up `AGENTS.md`
automatically.

---

### Replit Agent
**Best for:** Browser-based full-stack scaffolding, no local setup required.
**How it reads context:** Reads `AGENTS.md` natively. Skills in `.agents/skills/`
are available automatically.
**Cost:** Free tier available; Core plan recommended for the full Agent experience.
**Known limitation:** Auto Build mode does not pause for gallery confirmation.
Review `DECISIONS.md` at the end of every session.

---

## How the Files Work Together Across Sessions

Session 1 (e.g. Codex CLI or Opencode)
└── Reads:    AGENTS.md
└── Creates:  DECISIONS.md, CONSTRAINTS.md (if constraints stated)
└── Proposes: MEMORY.md entries at session end

Session 2 (e.g. Kilo Code or Gemini CLI)
└── Reads:    AGENTS.md + CONSTRAINTS.md + MEMORY.md
└── Surfaces: REVIEW REQUIRED items from DECISIONS.md before building
└── Surfaces: PENDING CONFIRMATION entries from MEMORY.md
└── Appends:  DECISIONS.md
└── Inherits: all constraints and confirmed lessons automatically

Session 3 (e.g. Cursor or Claude Code)
└── Reads:    AGENTS.md + CONSTRAINTS.md + MEMORY.md
└── Resolves: unresolved checkpoints from DECISIONS.md
└── Continues without repeating prior decisions

No tool ever needs to be told what was decided in a prior session —
the memory files carry that context automatically.

---

## How to use your model API keys with AI coding tools

Claude Code, Codex, Gemini CLI, GitHub Copilot, Cursor, Vibe CLI, and other
services allow you to log in directly with account credentials. For tools like
Kilo Code and Opencode connecting to external providers, you will need API keys.

1. Copy the shell script from `shell.txt` (adjust for your own model stack)
2. Paste it into your `.zshrc` or `.bashrc` file
3. Replace the placeholder keys with your actual keys
4. Run `source ~/.zshrc` or `source ~/.bashrc` to reload your terminal

You only need to do this once per computer.

---

## Post-Session Compliance Audit (Optional)

1. Open `EVAL_PROMPT.md`
2. Paste its contents into the tool that just completed the session
3. Review the Pass / Partial / Fail scores
4. Apply only changes that would have prevented an actual failure

---

## Known Behavioral Limitation — High-Specificity Prompts

The gallery protocol (Rule 2) fires on open-ended prompts and is suppressed by
specific measurements, file names, or exact values. This is intentional.

**Prompts that trigger the gallery:**
- "What are some ways to approach X?"
- "I'm not happy with how Y looks — what would you try?"
- "Before you change anything, show me options for Z."

**Prompts that suppress it:**
- Any prompt with exact pixel values, file names, or property names
- "Change X to Y"
- Feedback phrased as a correction rather than a question

---

## Personal Note

My name is Chris Fornesa, and as someone with a lifelong passion for art and
creative pursuits, but also knowledge of data science and a long-term interest
in web development, I have felt myself personally torn between two wants:
preserving human creativity and authenticity, and ensuring that humans don't
simply fall behind technological progress due to our biases about what is or
isn't "real."

This framework is all about leveraging what AI does best, while embedding
safeguards to prevent cognitive atrophy and encourage critical thought in the
process. Though agentic AI has made the process of creating websites,
applications, and software more accessible than ever, the real opportunity is
the ability to apply more thought, not less of it, into your creative
programming practice. Whether you're a beginner, intermediate, or advanced
developer, engineer, or AI consumer, this framework will hopefully encourage
you to exercise your creative prowess as you utilize AI coding tools.

---

> The person owns this project. You hold the brush.
> Ask before you paint. Show before you decide. Stop before you break anything.`