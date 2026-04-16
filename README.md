# CreatrWeb — Creative Human-AI Collaboration Framework

A portable kit of context files and loadable skills that guides AI coding
agents toward creative, human-steered, IndieWeb-aligned development. Works
across Claude Code, Codex CLI, Cursor, Gemini CLI, GitHub Copilot, Vibe CLI,
Kilo Code, Opencode, and Replit from a single source of truth.

To keep token costs low, this framework uses a single source of truth for all: AGENTS.md.

NOTE: only keep the necessary files from this framework contingent on your own preferred/available model stack. For instance, if you only use Claude Code, you do not need the /.agents, /.gemini, /.github, folders or the GEMINI.md file. You should also remove this file or totally replace the file contents of README.md with contents relevant to your actual project.

---

## What This Is

This framework applies three principles consistently across every AI
tool you use:

- **Human ownership** — the agent asks before building, shows options
  before committing, and stops at irreversible decisions.
- **Distinct voice** — gallery-format choices resist AI averaging.
  Research shows human-steered sessions produce outcomes 2–4× better
  than passive ones (Walton et al., 2026).
- **IndieWeb-inspired longevity** — your content stays portable, your URLs
  never break, and every dependency is documented.

---

## Your Tool Stack

CreatrWeb supports several stacks. Use the one that fits your budget and feel free to mix and match.

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

These tools can work individually or in conjunction, depending on your workflow, preferences, and budget.

### Free stack
These tools and API providers are genuinely free to start with no credit card:

| Tool / Provider | What it is | Install or sign up |
|---|---|---|
| **Kilo Code** | VS Code extension that connects to any model API | Install **Kilo Code** from the VS Code Extensions panel — search "Kilo Code", click the dropdown arrow next to Install, select **Install Pre-Release Version** [web:37] |
| **Opencode** | Terminal-based agent that connects to any model API | Run `curl -fsSL https://opencode.ai/install | bash` in your terminal [web:82] |
| **Groq (free API)** | Extremely fast inference, free tier, no credit card | Sign up at [console.groq.com](https://console.groq.com), go to API Keys, click **Create API Key** [web:83] |
| **OpenRouter (free models)** | Routes requests to free models from many providers | Sign up at [openrouter.ai](https://openrouter.ai), go to API Keys, click **Create API Key** — free models need no credit card [web:85][web:90] |

> **Connecting Kilo Code or Opencode to a free API:**
> Once you have a Groq or OpenRouter API key, open Kilo Code or Opencode,
> go to its API provider settings, paste your key, and select the model
> you want. Both tools support Groq and OpenRouter out of the box.
> On Groq free tier, keep your AGENTS.md and any loaded skills under
> ~4,000 tokens combined to stay within per-minute limits.

---

## Repository Structure

your-project/
├── AGENTS.md               ← Main instruction file (all agents)
├── CLAUDE.md               ← Claude Code entry point
├── CONSTRAINTS.md          ← Active project constraints (starts empty)
├── DECISIONS.md            ← Architecture log (agent fills during sessions)
├── DESIGN.md               ← Your aesthetic references and identity
├── EVAL_PROMPT.md          ← Post-session compliance audit
├── GEMINI.md               ← Gemini CLI entry point
├── KILO.md                 ← Kilo Code entry point
├── OPENCODE.md             ← Opencode entry point
├── .env.example            ← Environment variable reference
├── .agents/
│   └── skills/
│       ├── gallery-format/       SKILL.md ← Options protocol
│       ├── socratic-depth/       SKILL.md ← Assumption-surfacing questions
│       ├── indieweb-specs/       SKILL.md ← IndieWeb specification reference
│       ├── indieweb-principles/  SKILL.md ← IndieWeb philosophy reference
│       ├── posse-syndication/    SKILL.md ← POSSE, URL conventions, exports
│       ├── design-workflow/      SKILL.md ← Populating and maintaining DESIGN.md
│       ├── security/             SKILL.md ← IndieWeb endpoint security rules
│       ├── testing/              SKILL.md ← Test scope and pre-merge checklist
│       └── memory-files/         SKILL.md ← Memory file rules and entry format
├── .claude/skills/         ← Symlink or copy of .agents/skills/ for Claude Code
├── .gemini/
│   └── settings.json       ← Gemini CLI context configuration
├── .github/
│   └── copilot-instructions.md ← GitHub Copilot entry point
└── inactive/               ← Prior AGENTS.md versions (not read by agents)

Files the agent creates during sessions — do not create manually:
MEMORY.md               ← Confirmed lessons (agent proposes, you approve)
docs/dependencies.md    ← Vendor dependency registry (agent maintains)

---

## What Files Do You Actually Need?

Not every file is required for every setup. Use this table to decide:

| File or folder | Required for | Skip if |
|---|---|---|
| `AGENTS.md` | Everyone — all agents read this | Never skip |
| `CLAUDE.md` | Claude Code users | You don't use Claude Code |
| `KILO.md` | Kilo Code users | You don't use Kilo Code |
| `OPENCODE.md` | Opencode users | You don't use Opencode |
| `GEMINI.md` + `.gemini/settings.json` | Gemini CLI users | You don't use Gemini CLI |
| `.github/copilot-instructions.md` | GitHub Copilot users | You don't use Copilot |
| `CONSTRAINTS.md` | Everyone — created on first constraint | Agent creates it; don't make manually |
| `DECISIONS.md` | Everyone — created at session start | Agent creates it; don't make manually |
| `MEMORY.md` | Everyone — created on first confirmed lesson | Agent creates it; don't make manually |
| `DESIGN.md` | Anyone doing visual or UI work | Projects with no visual component |
| `EVAL_PROMPT.md` | Anyone running post-session audits | Optional but strongly recommended |
| `skills/indieweb-specs` | IndieWeb spec implementors | Projects with no IndieWeb features |
| `skills/indieweb-principles` | IndieWeb spec implementors | Projects with no IndieWeb features |
| `skills/posse-syndication` | Anyone implementing POSSE or feeds | Projects with no syndication |
| `skills/security` | Anyone writing IndieWeb endpoints | Projects with no auth or Webmention |
| `skills/testing` | Everyone — pre-merge checklist | Never skip for spec routes |
| `skills/gallery-format` | Everyone — fires with Rule 2 | Never skip |
| `skills/socratic-depth` | Everyone — fires with Rule 1 | Never skip |
| `skills/design-workflow` | Anyone using DESIGN.md | Projects with no visual component |
| `skills/memory-files` | Everyone — fires at session end | Never skip |
| `.env.example` | Projects with environment variables | Fully static projects |
| `inactive/` | Storing old AGENTS.md versions | Not needed in production |

---

## Using AI Chatbots to Fill In Your Markdown Files

Before your first coding session, several files benefit from human-written
content. An AI chatbot — Claude via Perplexity, ChatGPT, Gemini, or any
conversational AI — can help you think through and draft this content
without touching your codebase. This is a preparation step, not a coding step.

### DESIGN.md — References and Declared Preferences

The References section is the most important thing to fill in before any
design work. Use a chatbot to surface what you actually like:

> "I want to fill in the References section of a design identity file.
> Ask me questions about websites, apps, art, or visual work I admire,
> and help me articulate what I find compelling about them.
> Don't suggest anything yet — just ask."

After several exchanges:

> "Based on what I've described, what common threads do you see across
> my references? Present it as a hypothesis, not a conclusion — I'll
> confirm or correct it."

The output becomes your Derived Identity section. Paste it into
DESIGN.md and confirm or edit it before your first session.

### CONSTRAINTS.md — Non-Negotiables

> "I'm starting a web project. Ask me questions to help me identify
> any non-negotiable rules I have about dependencies, data privacy,
> licensing, or technical choices. One question at a time."

Any constraint that surfaces goes into CONSTRAINTS.md before your
first coding session. Agents treat this file as a no-fly zone and
respect a written constraint far more reliably than a verbal one.

### DECISIONS.md — Project Profile

> "I want to build [plain-language description]. Help me articulate
> my stack, deployment target, database approach, and key version
> constraints in plain language — no jargon unless I introduce it first."

Paste the result into the Project Profile section of DECISIONS.md.
If you leave it blank, your coding agent will ask the same questions
at session start — either approach works.

### AGENTS.md — When to Add Something

AGENTS.md is the one file you should not draft with a chatbot from
scratch — the version in this repo is the authoritative template.
The only time to add something before a first session is a
project-specific rule you know in advance will matter. Propose it
as a diff, confirm it, then add it.

---

## Setup — New Project

### Step 1 — Copy the kit

Copy all files from this template into your project root. Remove
the entry point files for tools you don't use (e.g. if you don't
use Gemini CLI, you don't need `GEMINI.md` or `.gemini/settings.json`).

### Step 2 — Fill in DESIGN.md and CONSTRAINTS.md (recommended)

Use the chatbot workflow above before your first coding session.
The more context your agents have on day one, the fewer clarifying
questions they need to ask mid-build.

### Step 3 — Set up your environment

Copy `.env.example` to `.env` and fill in any values your project
needs. Add your Groq or OpenRouter API key here if using the free
stack. Never commit `.env` to version control.

### Step 4 — Start your first session

Open your chosen agent tool in the project directory and begin.
The agent reads `AGENTS.md` automatically.

### Step 5 — Reference AGENTS.md at session start

Start every session with a SESSION CONSTRAINTS block:

> "Starting a new session.
> SESSION CONSTRAINTS: Follow all rules in AGENTS.md when processing
> all prompts in this conversation. Are you ready?"

**If the agent skips a rule mid-session**, stop it immediately:
- "Stop. Check AGENTS.md Rule 2 before proceeding."
- "Wait — did you ask the Rule 1 question for this change?"

<details>
<summary>Hostinger deployment note</summary>

This repo is configured to deploy as a bundled Express app.

- `npm run build` runs esbuild against `server.ts` and emits `server.bundle.js`.
- `npm start` runs `HOST=0.0.0.0 node server.bundle.js`.
- On Hostinger, use the `Other` framework preset, keep the root
  directory at `./`, use Node.js `20.x`, keep the output directory
  empty, and set the entry file to `server.bundle.js`.
- Build settings: `npm` with `npm run build`.
- Runtime env: `NODE_ENV=production`, `HOST=0.0.0.0`, `PORT=5000`.
- Do not use managed Astro / Next.js presets.

`esbuild` is required to create `server.bundle.js` and is kept in
`dependencies` because some hosts install only production deps before
running the build.
</details>

---

## How Skills Work

Skills are focused instruction sets that extend `AGENTS.md` for specific
tasks. They live in `.agents/skills/` and are loaded on demand — the
agent reads a skill's `SKILL.md` only when the situation calls for it,
keeping the active context lean.

### Loading a skill

Reference a skill by name in your session prompt or mid-session:

> "Load `gallery-format` and show me options for the URL structure."

Or, if `AGENTS.md` instructs the agent to load a skill automatically
(e.g. Rule 2 fires), the agent reads it without you needing to ask.

### Skill reference

| Skill | Load when |
|---|---|
| `gallery-format` | Rule 2 fires — options needed before any design or architecture decision |
| `socratic-depth` | Rule 1 fires — a question must be asked before a significant change |
| `indieweb-specs` | Implementing or modifying rel=me, microformats2, Webmention, IndieAuth, Micropub, WebSub |
| `indieweb-principles` | A decision touches ownership, portability, or longevity |
| `posse-syndication` | Finalizing URL structure, syndication targets, or export endpoints |
| `design-workflow` | DESIGN.md is empty, or a gallery needs Derived Identity or Observed Taste |
| `security` | Writing any Webmention, IndieAuth, Micropub, or media upload handler |
| `testing` | Before releasing any spec route or merging any branch |
| `memory-files` | End of session; proposing MEMORY.md or DECISIONS.md updates |

> Token budget: each skill costs 300–2,400 tokens. On free-tier models
> (Groq, OpenRouter), load only when that skill's work is the focus of
> the current exchange. Never pre-load.

---

## File Reference

### `AGENTS.md`
The authoritative instruction file. Read by every agent on every
session start. Contains the Six Rules, Brainstorm Mode, Mode table,
Agent Use gate, Core Constraints, Vendor Dependency question, Skills
table, Memory Files table, and AGENTS.md Safeguard.

**Do not edit during a session.** The agent proposes changes as a
diff and waits for approval.

---

### `CLAUDE.md`
Claude Code's entry point. Imports AGENTS.md so the full ruleset
loads without duplication.

@AGENTS.md
<!-- Claude Code-specific additions below. -->

---

### `KILO.md`
Kilo Code's entry point. Kilo Code is a VS Code extension that
connects to any model API — Groq, OpenRouter, Anthropic, OpenAI,
Google, or local models [web:36]. Use it with free Groq or
OpenRouter keys for a zero-cost setup.

@AGENTS.md
<!-- Kilo Code-specific additions below. -->

> To connect to Groq in Kilo Code: open the Kilo Code panel in VS
> Code, go to API Provider settings, select **Groq**, and paste your
> API key. To use OpenRouter free models, select **OpenRouter**,
> paste your key, and choose a model ending in `:free` [web:90].

---

### `OPENCODE.md`
Opencode's entry point. Opencode is a terminal-based agent —
similar to Claude Code or Codex CLI — that connects to any model
API [web:82]. Install with:

```bash
curl -fsSL https://opencode.ai/install | bash
```

Or via npm: `npm install -g opencode-ai`

@AGENTS.md
<!-- Opencode-specific additions below. -->

> To connect to Groq or OpenRouter: run `opencode` in your project
> directory, open provider settings, and paste your API key.

---

### `CONSTRAINTS.md`
Starts empty. Created by the agent the first time you state a
constraint. Format:

CONSTRAINT  No third-party analytics or tracking scripts
SCOPE       All pages and API routes
SET         YYYY-MM-DD

---

### `DECISIONS.md`
Agent-maintained audit trail for every architectural decision.
Starts as a template. You never need to write to it directly.

---

### `DESIGN.md`
Your aesthetic identity file. Three sections:

- **References** — works, sites, or art you admire. Your words.
- **Derived Identity** — the agent's synthesis, confirmed by you.
- **Observed Taste** — patterns noticed across sessions, proposed
  at session end.

Load `design-workflow` when you're ready to populate this file.

---

### `.agents/skills/`
Loadable instruction sets. Each skill is a directory with a
`SKILL.md` file. Load on demand only — never pre-load.

---

### `.gemini/settings.json`
Required for Gemini CLI. Skills are not listed here — they load
on demand.

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
    "server.bundle.js",
    ".env",
    ".env.*",
    "data",
    "*.tsbuildinfo"
  ]
}
```

---

### `.github/copilot-instructions.md`
Copilot's entry point. Points to `AGENTS.md` and defines chat,
inline, and Workspace plan mode behavior.

---

### `EVAL_PROMPT.md`
Post-session compliance audit. Paste into the tool that just
completed the session. Scores each rule Pass / Partial / Fail with
one sentence of evidence.

---

### `inactive/`
Stores prior versions of AGENTS.md or other files for reference.
Nothing in this folder is read by any agent.

---

## Agent-by-Agent Guide

### Claude Code
**Best for:** Multi-file work, IndieWeb spec implementation, security
hardening, sessions requiring strong instruction-following.

**How it reads context:** Reads `CLAUDE.md` natively, which imports
`AGENTS.md`. Skills load on demand by name.

**Cost:** Paid (Anthropic subscription or API credits).

**Tip:** Reference `@CONSTRAINTS.md` and `@MEMORY.md` in the opening
prompt for full persistent context.

---

### Codex CLI
**Best for:** Phase 1 scaffolding, schema design, strict
question-before-build discipline with full terminal access.

**How it reads context:** Reads `AGENTS.md` natively from the
project root.

**Cost:** Paid (OpenAI API credits).

**Tip:** Start each session with a SESSION CONSTRAINTS block.

---

### Cursor (Chat and Composer)
**Best for:** Day-to-day feature work, inline edits, suggestions
before auto-apply.

**How it reads context:** Reads `AGENTS.md` natively in Chat and
Composer modes. Inline edit is mechanical-only.

**Cost:** Free tier available; Pro plan recommended for heavy use.

**Tip:** In Composer, ask for a plan first. It takes gallery form
naturally when `AGENTS.md` is in context.

---

### Gemini CLI
**Best for:** UI components, interactive feature development, rapid
gallery-style iteration.

**How it reads context:** Requires `.gemini/settings.json`.

**Cost:** Free tier available via Google AI Studio API key.

**Tip:** SESSION CONSTRAINTS is especially important for Gemini —
never skip it.

---

### GitHub Copilot (Chat)
**Best for:** In-editor assistance, targeted help on a single file
or function.

**How it reads context:** Reads `AGENTS.md` as a repository
instruction file, and `.github/copilot-instructions.md` natively.

**Cost:** Paid (GitHub subscription); free tier available with limits.

**Tip:** Treat suggestions as proposals. Review before accepting,
especially for routes or schemas.

---

### Vibe CLI
**Best for:** Autonomous full-stack scaffolding sessions.

**How it reads context:** Reads `AGENTS.md` natively.

**Cost:** Paid (Mistral API key).

**Known limitation:** Auto Build mode does not pause for gallery
confirmation. Review `DECISIONS.md` after every session.

---

### Kilo Code (free stack)
**Best for:** VS Code users who want a full agent experience on a
free API budget.

**What it is:** A VS Code extension — similar to Cursor's Composer
but model-agnostic — that connects to Groq, OpenRouter, Anthropic,
OpenAI, Google, or local models [web:36].

**How it reads context:** Reads `KILO.md`, which imports `AGENTS.md`.
Skills load on demand by name.

**Cost:** Free with Groq or OpenRouter free-tier API keys.

**Install:** In VS Code, open Extensions (`Ctrl+Shift+X`), search
"Kilo Code", click the dropdown arrow next to Install, select
**Install Pre-Release Version** [web:37].

**Tip:** On Groq free tier, keep AGENTS.md plus any loaded skill
under ~4,000 tokens combined. Load one skill at a time.

---

### Opencode (free stack)
**Best for:** Terminal users who want Claude Code or Codex CLI
behavior on a free API budget.

**What it is:** A terminal-based agent — same interaction model as
Claude Code — that connects to any model provider [web:82].

**How it reads context:** Reads `OPENCODE.md`, which imports
`AGENTS.md`. Skills load on demand.

**Cost:** Free with Groq or OpenRouter free-tier API keys.

**Install:**
```bash
curl -fsSL https://opencode.ai/install | bash
```

**Tip:** Run `opencode` from your project root so it picks up
`AGENTS.md` automatically.

---

### Replit Agent
**Best for:** Browser-based full-stack scaffolding, no local setup
required.

**How it reads context:** Reads `AGENTS.md` natively. Skills in
`.agents/skills/` are available automatically.

**Cost:** Free tier available; Core plan recommended for the full
Agent experience [web:56].

**Install:** Sign up at [replit.com](https://replit.com). No
installation needed — everything runs in the browser.

**Known limitation:** Auto Build mode does not pause for gallery
confirmation. Review `DECISIONS.md` at the end of every session.

---

### Vibe CLI
**Best for:** Autonomous full-stack scaffolding sessions where you want
the agent working across the codebase with minimal interruption.

**What it is:** A terminal-based agent by Mistral that reads `AGENTS.md`
natively and applies conservative defaults in Auto Build mode.

**How it reads context:** Reads `AGENTS.md` natively from the project
root. Skills in `.agents/skills/` are discovered automatically.

**Cost:** Paid (Mistral API key required).

**Install:** `npm install -g vibe-cli`

**Known limitation:** Auto Build mode does not pause for gallery
confirmation. Review `DECISIONS.md` after every session to see which
conservative defaults were selected and override any that don't reflect
your direction.

**Tip:** Use `DECISIONS.md` as your review artifact after every Vibe CLI
session, not during it. Start the following session with those unresolved
checkpoints in your SESSION CONSTRAINTS block.

---

## How to use your model API keys with AI coding tools

Claude Code, Codex, Gemini CLI, GitHub Copilot, Cursor, Vibe CLI, and other services allow you to directly login using your login credentials if you have an account with each respective service. However, for most of these services and others, such as Opencode Zen, Groq, and other services, you will need to use your API keys to use coding tools, such as Kilo Code. The following instructions will help you set up your API keys for use with AI coding tools.

1. Copy the shell script from `shell.txt` (change according to your own preferred/available model stack)
2. Paste it into your `.zshrc` or `.bashrc` file on Mac or Windows
3. Replace the placeholder keys with your actual keys
4. Run `source ~/.zshrc` or `source ~/.bashrc` to reload your terminal, or simply restart your terminal

Note that you only need to do this once per computer and only for models requiring API keys to work with external AI coding tools.

---

## How to Load a Skill

1. Copy the skill's `.md` file to `.agents/skills/`
2. Add its name to the SKILLS block in `AGENTS.md`
3. Run the agent

---

## How the Files Work Together Across Sessions

Session 1 (e.g. Codex CLI or Opencode)
└── Reads:    AGENTS.md
└── Creates:  DECISIONS.md, CONSTRAINTS.md (if constraints stated)
└── Proposes: MEMORY.md entries at session end

Session 2 (e.g. Kilo Code or Gemini CLI)
└── Reads:    AGENTS.md + CONSTRAINTS.md + MEMORY.md
└── Appends:  DECISIONS.md
└── Inherits: all constraints and confirmed lessons automatically

Session 3 (e.g. Cursor or Claude Code)
└── Reads:    AGENTS.md + CONSTRAINTS.md + MEMORY.md
└── Resolves: unresolved checkpoints from DECISIONS.md
└── Continues without repeating prior decisions

No tool ever needs to be told what was decided in a prior session —
the memory files carry that context automatically.

---

## Post-Session Compliance Audit (Optional)

1. Open `EVAL_PROMPT.md`
2. Paste its contents into the tool that just completed the session
3. Review the Pass / Partial / Fail scores
4. Apply only changes that would have prevented an actual failure

---

## Known Behavioral Limitation — High-Specificity Prompts

The gallery protocol (Rule 2) fires on open-ended prompts and is
suppressed by specific measurements, file names, or exact values.
This is intentional.

**Prompts that trigger the gallery:**
- "What are some ways to approach X?"
- "I'm not happy with how Y looks — what would you try?"
- "Before you change anything, show me options for Z."

**Prompts that suppress it:**
- Any prompt with exact pixel values, file names, or property names
- "Change X to Y"
- Feedback phrased as a correction rather than a question

---

## IndieWeb Quick Reference

| Priority | Spec | What it does |
|---|---|---|
| 1 | `rel=me` | Links your domain to your profiles elsewhere |
| 1 | microformats2 | Makes your content machine-readable without breaking HTML |
| 2 | Webmention | Lets other sites notify you when they link to you |
| 2 | IndieAuth | Makes your domain an identity provider |
| 3 | Micropub | Lets external apps publish to your site |
| 4 | WebSub | Pushes new content to subscribers in real time |

Build in this order. Load `indieweb-specs` before implementing any
of these.

---

## Personal Note

My name is Chris Fornesa, and as someone with a lifelong passion for
art and creative pursuits, but also knowledge of data science and a
long-term interest in web development, I have felt myself personally
torn between two wants: preserving human creativity and authenticity,
and ensuring that humans don't simply fall behind technological progress
due to our biases about what is or isn't "real."

This framework is all about leveraging what AI does best, while
embedding safeguards to prevent cognitive atrophy and encourage critical
thought in the process. Though agentic AI has made the process of
creating websites, applications, and software more accessible than ever,
the real opportunity is the ability to apply more thought, not less of
it, into your creative programming practice. Whether you're a beginner,
intermediate, or advanced developer, engineer, or AI consumer, this
framework will hopefully encourage you to exercise your creative prowess
as you utilize AI coding tools.

---

> The person owns this site. You hold the brush.
> Ask before you paint. Show before you decide. Stop before you break anything.