# `personal_starter/` — personal (IndieWeb) context

A complete, self-contained agentic markdown system. Copy this folder's contents
into a repo root and you have everything — no second file to apply on top, and
nothing pointing back at the Creatrweb repo.

**Use this context for** any repo implementing `rel=me`, microformats2, Webmention, IndieAuth, Micropub, WebSub, or POSSE syndication.

**Use this variant** when the repo already has its own agentic markdown — an `AGENTS.md` someone else wrote, a `process.md`, a task template, coursework rubrics, a mature `MEMORY.md`/`DECISIONS.md` pair. It reads what's there first and creates only what's missing. It also works fine on an empty repo; it simply finds nothing to reconcile.

---

## Implementation

### 1. Copy the files

Copy this folder's files into your repo root. Copy the loose markdown files
first — but read Step 1a before copying `AGENTS.md`, since your repo may
already have one. The skill directories are Step 1b, and are deliberately
separate.

Do not copy this file (`SYSTEM-README.md`) into the target repo unless you want
the install instructions to live there; it has no role once the system is
installed.

```
AGENTS.md            Orchestrator — read first, every session, by every tool
LOOP-AGENTS.md       Single-service process — Merge Protocol, loop, roster, stops
GRAPH-AGENTS.md      Multi-service process — install only if you coordinate several
START-HERE.md        The adaptive install prompt (see Step 3)
SYSTEM-README.md     This file — steps + both setup prompts
.claude/skills/      The 9 skills
.agents/skills/      Identical mirror of the above
```

Everything else the system needs — `CLAUDE.md`, `GEMINI.md`, the four memory
files, `.github/copilot-instructions.md`, `.gemini/settings.json` — is
generated during install from bodies embedded in `START-HERE.md`. That is why
they aren't sitting here as files.


### 1a. If your repo already has an `AGENTS.md`

**Do not replace it.** `AGENTS.md` in this folder is built to work either way:

- **No existing `AGENTS.md`** — copy this folder's file in as-is. It's complete
  on its own.
- **An existing `AGENTS.md`** — open this folder's `AGENTS.md`, copy everything
  from the `<!-- ===== BEGIN CREATRWEB ORCHESTRATOR ===== -->` marker to the end
  of the file, and paste it at the **end** of your existing `AGENTS.md`. Leave
  everything already in your file untouched, above the pasted block.

The block is written to be appended safely. It opens with a single
`## Creatrweb Agentic Workflow System` heading rather than a second `#` title,
so it nests cleanly under whatever is already there. It declares its own
precedence: anything above it is your repo's standing instruction set and wins
by default. And it scopes its own numbering — "Section 9" means Section 9 of
the pasted block, never of your file — so your existing section numbers keep
working untouched.

Where one of your rules and one of the block's rules disagree, the agent is
instructed to follow yours, name the conflict, and let you decide. It will not
resolve the conflict silently, and it will not delete either rule.

`LOOP-AGENTS.md` and `GRAPH-AGENTS.md` are new filenames in almost every repo,
so they install as ordinary files with no merge to worry about.

### 1b. Copy the skills one at a time

**Do not copy `.claude/` or `.agents/` as whole directories.** If your repo
already has skills, a directory-level copy can replace the whole folder and
take yours with it. Copy each skill's own folder individually instead:

```
personal_starter/.claude/skills/gallery-format/  →  <your repo>/.claude/skills/gallery-format/
personal_starter/.agents/skills/gallery-format/  →  <your repo>/.agents/skills/gallery-format/
```

…and so on for each of the 9 skills. Your existing skill folders sit
untouched alongside them. If a name collides with one of yours, stop and decide
which you want before copying that one — the install prompt can help you
compare them, and nothing here should overwrite a skill you wrote.

Both mirrors matter: `.claude/skills/` is what Claude Code reads, `.agents/skills/`
is what other agent runners read, and they must stay byte-identical.

### 2. Decide single- or multi-service

One codebase with one deploy target is single-service: keep
`LOOP-AGENTS.md`. More than one repo or deploy
target coordinated together is multi-service: keep both, and note that each
node still runs its own loop.

If the answer is genuinely unclear — a monorepo with independently deployed
packages, say — that's a Rule 1 question. Ask your agent rather than guessing.

### 3. Paste the install prompt

Open a **fresh session** in your agent — not one already mid-task — and paste
the entire contents of `START-HERE.md`.

`START-HERE.md` is the right prompt for this folder. It reads whatever agentic
markdown your repo already has before writing anything, distills the rules out
of it, and creates only what's missing. The two prompts at the end of this
README are alternatives for specific situations, not replacements:

| Situation | Paste this |
|---|---|
| Normal install, any repo | `START-HERE.md` |
| You want the classic one-shot installer, or you're only refreshing the model roster | Prompt A below |
| The project spans several repos and you're setting up the coordination layer | Prompt B below |

### 4. Answer the roster questions

The prompt asks which tools and models you actually have for issue scoping,
mechanical implementation, complex-logic implementation, QA self-review, and
the production-readiness gate. Answer at whatever granularity you like — a
service name ("Claude Pro") or a specific model ID. Anything you leave blank
stays flagged as unconfirmed rather than being invented.

The readiness gate never gets a cheap-tier model. If your roster has no
frontier-tier option for it, the prompt will say so rather than quietly
downgrading.

### 5. Review before you build

The prompt stops at the end of the documentation pass and shows you what it
did. Check three things: that no rule from your old files went
missing, that every skill you already had is still there and now has a load
trigger, that `DESIGN.md` is still empty rather than filled with the agent's guesses about
your taste, and that anything it flagged as a conflict gets your decision
rather than its own.

Then start work in a **new** session. Documentation passes and feature work
don't share a session.

---

## After install

Session start needs no prompt. `AGENTS.md` Section 0 routes the session, and
`LOOP-AGENTS.md` Section 0 classifies the repo. Some people still open with a
constraints block to pull the rules into active context:

> "Starting a new session. SESSION CONSTRAINTS: follow all rules in AGENTS.md
> for every prompt in this conversation. Are you ready?"

If the agent skips a rule mid-session, stop it immediately — "Stop. Check
AGENTS.md Rule 2 before proceeding." At the end of anything significant, run
the Post-Session Eval in `AGENTS.md` Section 12.

**Skills** (the five base skills plus `indieweb-specs`, `indieweb-principles`, `posse-syndication`, `security`) load on demand and are never pre-loaded. Each costs
300–2,400 tokens; on rate-limited models, load one only when its work is the
focus of the current exchange.

**Memory files** fill in during work, on confirmation, never speculatively. An
empty `DESIGN.md` is a correct state — a fabricated one poisons every gallery
that follows.

---

# Prompt A — Single-Service Setup

Copy everything between the two markers below into your agent.

<!-- ===== BEGIN PROMPT A ===== -->

# Documentation Overhaul Prompt — Single-Service Loop Engineering (personal)

> **Context: personal (IndieWeb).** Installs the `personal` markdown system — IndieWeb obligations — rel=me, microformats2, Webmention, IndieAuth, Micropub, WebSub, POSSE.
> Self-contained: everything this prompt needs to build a complete system is in this file.

**Use this once** when installing or updating the Loop Engineering scheme in a
repo — not at the start of every coding session. Once this overhaul is
complete, `AGENTS.md`'s Section 0 routing and `LOOP-AGENTS.md`'s Section 0 Merge Protocol handle per-session loading
automatically; you don't need to re-paste this prompt to start work.

Run this whenever: setting up a fresh repo, retrofitting an existing repo onto
this scheme (empty or mature, static or database-backed, documented or not —
including repos with a rich pre-existing documentation network like task
trackers, process docs, or coursework rubrics), or updating the Model Routing
roster after a subscription/tool change. **This prompt is idempotent** — safe
to re-run any time, including just to change the roster with no other changes.

**Important — the tool you use to run this overhaul does not need to match
the roster you're writing.** You can execute this entire prompt in Claude Pro
while the roster below assigns Opencode Go to implementation roles, or in
Antigravity while specifying GPT-5.6 Luna at medium thinking effort for a
role — the executing tool and the roster are two separate things. State which
tool you're using to run this overhaul (for the record in `DECISIONS.md`)
separately from the roster you're populating.

---

You are performing a documentation overhaul on this repo, not implementing a
feature. Your job is to install or update the Loop Engineering scheme.

**Step 1 — Audit.** Check the repo root, `.github/`, `.claude/`, `.agents/`,
and `docs/` for any existing markdown. Classify what you find using
`LOOP-AGENTS.md` Section 0's four cases:
- **Case A** — no markdown at all.
- **Case B** — some markdown, but unrelated to agent governance (README,
  CHANGELOG, etc.) — not a blocker, leave untouched.
- **Case C** — a single existing `AGENTS.md` with its own rules.
- **Case D** — a rich, pre-existing documentation network (multiple
  interlocking files like `process.md`, `plan.md`, `task-template.md`,
  a live `tasks.md`, benchmark/audit docs, or team docs that already encode
  their own working process — e.g., coursework or an established team
  workflow). Report the case, and for Case D, do **not** propose any
  restructuring yet — proceed to Step 1.5 first.

Report back what you found before changing anything.

**Step 1.5 — Case D only: Goal Extraction and Reconciliation Proposal.**
If Case D applies, read through the existing documentation network and:
1. Summarize each file's original purpose in one line (read-only — no edits).
2. Map each file to the closest concept in this scheme (e.g., a `process.md`
   describing issue lifecycle maps to `LOOP-AGENTS.md` Section 1; a large,
   actively-updated tracker maps to "live work log," not a template to rewrite).
3. Propose, in gallery format, exactly one of three outcomes per file: keep
   as-is and cross-link; lightly annotate without rewriting; or fold in and
   deprecate (only for small files clearly superseded by this scheme — never
   for large or actively-used ones).
4. Wait for my explicit confirmation on the proposal before touching any file.
   The original documents' goals must survive the restructuring, not be
   replaced by this scheme's default vocabulary.

**Step 1.6 — Distill rules out of existing agent files, then reduce them.**
Tool entry points accumulate real rules. A `CLAUDE.md` carrying six months of
corrections is not boilerplate, and turning it into a pointer without rescuing
its content destroys the reasoning this scheme exists to preserve.

For every existing `CLAUDE.md`, `GEMINI.md`, `.github/copilot-instructions.md`,
`.cursorrules`, `.windsurfrules`, `.aider.conf.yml`, and any pre-existing
`AGENTS.md`, build a rule inventory: quote every normative statement (must,
never, always, don't, prefer, or a standing imperative) with its source, and
assign each exactly one destination —

- general behavioral rule → `AGENTS.md` Section 13, Project Specific Rules
- process mechanic → `LOOP-AGENTS.md` Section 1 (or `GRAPH-AGENTS.md`)
- must-never-do-to-this-codebase → `LOOP-AGENTS.md` Section 3, Irreversible Decisions
- binding project constraint → `CONSTRAINTS.md`
- taste or aesthetic preference → `DESIGN.md`, Declared Preferences
- past architectural choice with reasoning → `DECISIONS.md`
- durable lesson from a past failure → `MEMORY.md`
- genuine tool-specific quirk that cannot generalize → stays put, with a
  comment saying why
- redundant with the new system → dropped, naming the rule that supersedes it

Show me the inventory and **wait for approval**. This is an Irreversible
Decision. Only after approval: write each rule to its destination, then reduce
the entry points to pointers — `CLAUDE.md` and `GEMINI.md` to a reference to
`AGENTS.md` and nothing else, `.cursorrules` and friends to a one-line
instruction to read `AGENTS.md` (reduce, never delete — a tool that finds
nothing falls back to its own defaults), and `.gemini/settings.json` merged
rather than replaced.

Nothing is deleted that has not been rehomed. Before Step 5, verify every
inventoried rule appears in exactly one destination and report any that don't.

**Existing skills are preserved.** Never delete, overwrite, or move an existing
`SKILL.md`. Evaluate each one, register it in `AGENTS.md` Section 9 with an
explicit load trigger, mirror it across `.claude/skills/` and `.agents/skills/`
if it exists in only one, and adapt it only far enough to fit — front matter, a
trigger, a cross-reference. If an existing skill shares a name with one this
prompt installs, show both, say where they differ, and ask which survives.
Never merge them silently or assume the shipped one wins. Normative statements
inside a skill stay in that skill; they do not go through the rule inventory.


**Step 2 — Apply the Merge Protocol** from `LOOP-AGENTS.md` Section 0 per the
case identified in Step 1 (and the confirmed proposal from Step 1.5 if Case D):
- Case A or B → create `AGENTS.md` (whole file) and `LOOP-AGENTS.md` at repo
  root from the canonical templates, plus empty stub files for `MEMORY.md`, `DECISIONS.md`, and
  `CONSTRAINTS.md`.
- Case C → never overwrite the existing `AGENTS.md`. Append the Creatrweb
  orchestrator block (from its `BEGIN CREATRWEB ORCHESTRATOR` marker to the end)
  at the end of that file, leaving everything already there above it, and
  install `LOOP-AGENTS.md` alongside. The block defers to the existing rules and
  scopes its own section numbering, so nothing above it needs renumbering. Flag
  every direct rule conflict to me instead of resolving it yourself.
- Case D → apply only the confirmed Step 1.5 proposal, file by file.
- Existing `DECISIONS.md`/`MEMORY.md` → append, never truncate.
- **Existing populated Model Routing Plan (`LOOP-AGENTS.md` Section 2)** → this is the one
  section that gets *replaced*, not appended to — see Step 4.

**Step 2a — Install the `personal` context payload.**

This prompt ships with a complete `personal` markdown system. If the other
files from the `personal` folder are already sitting alongside this prompt in
the repo root, they *are* the payload — verify each is present and skip to
Step 2b. If this prompt was pasted in on its own, create the following at the
repo root:

| File | Source |
|---|---|
| `AGENTS.md` | The orchestrator — precedence, routing, Six Rules, Brainstorm Mode, Pre-Write Check, Core Constraints, skills, memory ownership, eval. **If the repo already has an `AGENTS.md`, never replace it** — append only the block from its `BEGIN CREATRWEB ORCHESTRATOR` marker onward, and leave the existing content above it untouched. |
| `LOOP-AGENTS.md` | The `personal` single-service process file — Merge Protocol (its Section 0 governs how everything lands), the loop, model roster, Irreversible Decisions |
| `GRAPH-AGENTS.md` | The `personal` graph-engineering file — install only if this repo coordinates more than one service |
| `CLAUDE.md` | Pointer to `AGENTS.md`. No unique rules. |
| `GEMINI.md` | Pointer to `AGENTS.md`. No unique rules. |
| `.github/copilot-instructions.md` | Copilot entry point; priority order + memory-file table |
| `.gemini/settings.json` | Gemini context array — must list `AGENTS.md`, `LOOP-AGENTS.md`, `DECISIONS.md`, `CONSTRAINTS.md`, `DESIGN.md`, `MEMORY.md` |
| `MEMORY.md` `DECISIONS.md` `CONSTRAINTS.md` `DESIGN.md` | Header-only scaffolds. Never pre-populate — the `memory-files` and `design-workflow` skills fill them on confirmation. |
| `.claude/skills/<name>/SKILL.md` + `.agents/skills/<name>/SKILL.md` | The 9 skills listed in `AGENTS.md` Section 9. Bodies are in the Appendix below. Write each skill folder individually — never replace `.claude/skills/` or `.agents/skills/` wholesale. Both mirrors must be written and byte-identical. Existing skills are registered and kept, never replaced. |

This folder ships no `ADAPTATION.md`, and none should be created in the target
repo — the context's specializations are already baked into `AGENTS.md` and
`LOOP-AGENTS.md`.

**Step 2b — Verify self-containment.** Before proceeding, confirm no installed
file references a path outside the target repo. If any does, that file was
installed wrong — stop and say so.

**Step 3 — Populate the Model Routing Plan (`LOOP-AGENTS.md` Section 2) using this roster.**
For each role, state a subscription/service name (e.g., "Claude Pro," "Codex,"
"Replit Core") or a specific model name (e.g., "Claude Sonnet 5,"
"gpt-5.2-codex," "qwen3-coder:cloud") — either is acceptable, and you can add
an optional reasoning-effort or thinking-level qualifier to either (e.g.,
"GPT-5.6 Luna at medium thinking"). If I only give a service name, use its
current default/recommended model for that role and note that the specific
model may shift as the service updates its lineup — don't hardcode a model I
never named.

```
Role: Issue scoping / spec drafting
  Service or Model (+ optional effort/thinking level): ____________________

Role: Implementation — mechanical / boilerplate
  Service or Model (+ optional effort/thinking level): ____________________

Role: Implementation — complex logic (auth, data layer, migrations)
  Service or Model (+ optional effort/thinking level): ____________________

Role: Second-opinion patch review (optional)
  Service or Model (+ optional effort/thinking level): ____________________

Role: QA self-review
  Service or Model (+ optional effort/thinking level): ____________________

Role: Production-readiness gate
  Service or Model (+ optional effort/thinking level): ____________________
```

**Step 4 — Write the roster, replacing any prior table.** Write my answers
into `LOOP-AGENTS.md` Section 2 in the existing `Provider / Model ID / Reason`
block format, using exactly the granularity I gave you (don't invent a
specific model I didn't name). If that section already contains a populated
table from a prior run, replace it entirely — do not leave the old table in
place or append a second one. Log the change as one line in `DECISIONS.md`
(or, for Case D repos, that network's own equivalent log/plan file). If I
leave a role blank, keep the template's existing example for that role and
flag it as unconfirmed.

**Step 5 — Confirm and stop.** Show me, in this order: the rule inventory
from Step 1.6 with each rule's final destination, confirming none was lost;
any tool-specific rule left in place, with the reason it can't generalize;
and the final diff of every file changed or created. Do not begin any feature implementation in this same session —
this is a documentation-only pass.


---

# Appendix — Skill Bodies

Write each block below to **both** `.claude/skills/<name>/SKILL.md` and
`.agents/skills/<name>/SKILL.md`, verbatim and byte-identical. Skip this
appendix entirely if the skill directories already arrived with the payload.

## `gallery-format`

```markdown
---
name: gallery-format
description: >
  Formats and governs the presentation of design and architectural
  options before any significant build decision. Load this skill
  whenever Rule 2 applies — before committing to any design choice,
  architectural direction, or feature approach. Also load when Rule 6
  applies and alternatives to non-functional technology must be shown.
---

# Gallery Format — Show Options Before Building

## Purpose

The gallery is not an approval mechanism. It is a reflection instrument.
Viewing meaningfully different alternatives improves decision quality
even when none of the presented options are chosen. The goal is to make
the person's actual preference legible — to themselves — before anything
is built.

## Structure

Every gallery contains three option entries plus one Reframe entry.
No more, no fewer, unless the person explicitly requests otherwise.

### Option Entry Format
[Label — one word, not "Option A"]
- Approach: Two sentences describing what this is and how it feels.
- Trade-off: One sentence — what this gives, and what it costs.
- Example: A concrete illustration — URL pattern, schema snippet,
UI sketch, or code fragment. Never omit this.

### Reframe Entry Format
[Reframe]
- One sentence restating the underlying problem differently.
- Challenge: What this reframing reveals about the original request.
- Closing question: "Does this change what you want to build?"


---

## Rules for All Four Entries

**The three option entries:**
- Must be meaningfully divergent — different in approach, not just
  in implementation detail. If all options feel similar, they are
  not divergent enough. Start over.
- Must include at least one option you would not recommend. Do not
  signal which one this is.
- Do not signal a preference. Use identical formatting and length
  for all entries. Let the person's reaction drive the choice.
- The implied option — the one that surfaces a direction not yet
  consciously articulated — must be traceable to specific signals
  from this user's conversation, DESIGN.md References, Derived
  Identity, or Observed Taste. If DESIGN.md is empty or absent,
  name that gap before presenting the gallery:
  "I don't have your design references yet, so the implied option
  below is drawn from the conversation rather than your DESIGN.md.
  It may be less accurate than usual."

**The Reframe entry:**
- Does not propose an implementation. It reframes the problem.
- Must challenge the premise of the request — not just offer a
  different solution to the same problem.
- Always ends with a closing question. Never omit it.
- If the person dismisses the Reframe without engaging with it,
  note it once: "The reframe is still open if you want to return
  to it." Do not push further.

**In auto/build mode:**
- Select the conservative default from the three options.
- Log all three options and the Reframe in DECISIONS.md with the
  default selected noted.
- Do not present the gallery to the user — they are not available
  to respond. Surface the full gallery at the next interaction.

---

## When to Load This Skill

Load on any of the following triggers:
- Rule 2 applies — a significant design or architectural choice
  is about to be made.
- Rule 6 applies — a specified technology is non-functional and
  alternatives must be shown.
- The person asks to see options, compare approaches, or is
  uncertain between directions.
- Brainstorm Mode is exiting and a direction is being confirmed
  for the first time.

Do not load for mechanical changes. Do not load for decisions
already made and logged in DECISIONS.md unless the person
explicitly requests reconsideration.

---

## Example Gallery

**Context:** Person is deciding on URL structure for a personal blog.

---

**Dated**
- Posts live at `/YYYY/MM/DD/slug`, making time of writing part of
  the permanent address. Feels archival, like a newspaper morgue.
- Trade-off: Gives immediate temporal context and is the most
  durable IndieWeb convention; costs flexibility if you want to
  de-emphasize when something was written.
- Example: `/2026/04/10/why-i-left-twitter`

**Topical**
- Posts live at `/writing/slug`, grouping by content type rather
  than time. Feels more like a book than a diary.
- Trade-off: Cleaner for evergreen content; loses the temporal
  signal that makes a personal site feel lived-in over time.
- Example: `/writing/why-i-left-twitter`

**Flat**
- Posts live at `/slug` with no subdirectory. Maximum brevity,
  minimal hierarchy.
- Trade-off: Simplest to type and share; provides no structural
  signal about content type or time, which complicates future
  reorganization.
- Example: `/why-i-left-twitter`

**Reframe**
- The URL structure question assumes the site's primary identity
  is as a publishing archive. But what if the primary identity
  is as a presence — a place that says who you are right now,
  with the archive as a secondary layer?
- Challenge: If the front door is the person, not the posts, the
  URL structure matters less than what lives at `/` and how posts
  are linked from there.
- Does this change what you want to build?

---

> The gallery is how the person discovers what they actually want.
> Your job is to make the options real enough to react to.
```

## `socratic-depth`

```markdown
---
name: socratic-depth
description: >
  Provides question taxonomy, sequencing rules, and framing
  protocols for assumption-surfacing dialogue. Load this skill
  whenever Rule 1 applies — before any significant change — and
  at every Brainstorm Mode entry. Also load when the person
  appears certain but the basis for that certainty is unstated.
---

# Socratic Depth — Surfacing Assumptions Before Acting

## Purpose

The goal of a question is not to confirm permission. It is to make
visible what the person assumes is already true — before that
assumption gets built into something permanent. The user who most
needs their assumptions examined is also the most likely to feel
they have already examined them. Questions are the only reliable
external signal.

---

## Question Taxonomy

Five types of questions, each targeting a different kind of
invisible assumption. Use the type that fits the moment — do not
rotate through all five mechanically.

### 1. Premise
Surfaces what the person assumes must be true for their direction
to be correct.
- "What would have to be true for this to be a bad idea?"
- "What are you most certain about here — and what makes you
  certain?"
- "What is this decision assuming about your users that you
  haven't said out loud?"

### 2. Consequence
Traces downstream effects before a decision becomes load-bearing.
- "If this works exactly as planned, what becomes harder in
  six months?"
- "Who else is affected by this choice that we haven't
  mentioned yet?"
- "What does this decision make difficult to change later?"

### 3. Inversion
Finds the shape of what's wanted by describing its failure state.
- "What's the worst version of this feature? What makes it bad?"
- "If this shipped and you were embarrassed by it, what would
  be the reason?"
- "What would a person you respect find wrong with this
  direction?"

### 4. Scope
Challenges whether the feature or decision needs to exist at all.
- "What would happen if you didn't build this?"
- "Is there a smaller version of this that would answer the
  same need?"
- "What problem does this solve that isn't already solved
  by what exists?"

### 5. Definition
Exposes vague terms before they become bad schemas, wrong routes,
or unmaintainable code.
- "When you say '[term]', what breaks if that definition
  changes later?"
- "Is '[term]' one thing or several things with the same name?"
- "Who else uses the word '[term]' differently than you do?"

---

## Sequencing Rules

Sequence matters as much as question type. The wrong question at
the wrong moment produces defensiveness, not reflection.

**Earliest in any conversation or feature discussion:**
Use Definition and Premise questions first. Vague terms and
unexamined assumptions compound — catch them before momentum builds.

**Before any irreversible decision:**
Use Consequence questions. The person may be fully committed; the
goal is not to stop them but to ensure the trade-off is named
out loud before it becomes invisible infrastructure.

**Mid-Brainstorm, when a partial direction has emerged:**
Use Inversion questions. The person has enough of a direction to
react to its failure state, but hasn't committed far enough to
be defensive about it.

**When the person appears about to approve without engaging:**
Use Scope questions. They interrupt the approval motion without
challenging the person's competence — they challenge the
necessity of the action, which is easier to examine without
ego involvement.

**Never:**
- Ask two question types in the same turn. One question at a time.
- Ask a permission-seeking question when an assumption-surfacing
  question is available. "Should I proceed?" is not Socratic.
- Ask about what the person doesn't know. Ask about what they
  are certain of — certainty is where unexamined assumptions live.

---

## The Hypothesis Restate Protocol

Use this at every Brainstorm Mode exit, and whenever a person
expresses a direction with embedded assumptions.

**Format:**
"It sounds like your hypothesis is [restate their direction].
That assumes [name the load-bearing assumption].
Does that hold?"

**Rules:**
- Restate their direction accurately before naming the assumption.
  Do not lead with the challenge.
- Name exactly one assumption — the most load-bearing one.
  Do not list multiple assumptions in a single restate.
- End with a closed question ("Does that hold?") not an open one.
  The goal is confirmation or correction, not elaboration.
- If they confirm, proceed. If they correct, update your
  understanding and restate once more before proceeding.
- If they dismiss the assumption without engaging, note it once:
  "That assumption is still open if you want to return to it."
  Do not push further.

---

## The Creative Permission Protocol

For users who appear to be limiting their own vision — proposing
ideas that are technically valid but aesthetically cautious,
generic, or smaller than their stated goals — apply this protocol
instead of a standard Socratic question.

These questions are not about assumptions. They are about
expanding what the person believes they are allowed to want.

- "Why does this have to look like other sites you've seen?"
- "What would the version of this look like that you'd be
  slightly embarrassed to propose — and why?"
- "If you had no concern about whether this was conventional,
  what would you actually build?"
- "What are you holding back, and why?"

**When to use:**
When DESIGN.md exists and the person's stated direction is
inconsistent with their Derived Identity or Observed Taste —
specifically when their proposal is more conservative than
their references suggest they actually want.

When DESIGN.md is empty, use only if the person's conversation
signals suggest self-limitation rather than genuine preference
for the cautious direction.

**Never use these questions:**
- To push the person toward unconventional choices they have
  genuinely rejected.
- More than once per session on the same topic.
- In auto/build mode.

---

## The Assumption Gradient

Not all assumptions carry equal weight. Before asking a question,
locate the assumption on this gradient and prioritize accordingly:

| Weight | Type | Example |
|--------|------|---------|
| **Highest** | Irreversible if wrong | URL structure, schema design, identity claims |
| **High** | Expensive to undo | Vendor dependency, authentication approach |
| **Medium** | Recoverable with effort | Component structure, naming conventions |
| **Low** | Easily changed | Color choices, copy, layout details |

Ask Premise and Consequence questions for High and Highest weight
assumptions. Ask Definition and Scope questions for Medium weight.
Reserve Inversion and Creative Permission questions for moments
when the person is engaged and reflective — they require more
trust than the other types.

---

## What This Skill Is Not

- It is not a checklist to complete before building.
- It is not a way to slow down users who have already thought
  carefully.
- It is not a substitute for the person's own judgment.

The goal is that when something is built, the person can say:
"I knew what I was deciding, and I decided it." The questions
exist to make that true — not to make the agent feel thorough.

---

> Ask what the person is certain of.
> Certainty is where the unexamined assumptions live.
```

## `design-workflow`

```markdown
---
name: design-workflow
description: >
  Governs how the agent populates, reads, and maintains DESIGN.md.
  Load this skill when DESIGN.md is empty or incomplete and the
  person is ready to work on it, when a gallery option needs to
  reference Derived Identity or Observed Taste, or when a session
  produces new signals about the person's aesthetic that should be
  recorded. Do not load for routine implementation work where
  DESIGN.md is already populated and stable.
---

# Design Workflow — Populating and Maintaining DESIGN.md

## What DESIGN.md Is For

DESIGN.md makes the person's aesthetic identity legible to the
agent across sessions. Without it, every gallery option is drawn
from the conversation alone — accurate only to the current session,
with no memory of what the person has consistently responded to
over time.

A fully populated DESIGN.md has three sections:

- **References** — specific works, sites, designers, or artifacts
  the person has named or linked as influences, aspirations, or
  touchstones. These are chosen by the person, not inferred.
- **Derived Identity** — the agent's synthesis of what the
  References reveal about the person's aesthetic. This is a
  hypothesis, not a fact, and the person may correct it.
- **Observed Taste** — patterns the agent has noticed in this
  person's actual decisions across sessions. Not what they said
  they like — what they consistently chose, rejected, or returned
  to when given options.

These three sections serve different purposes and are populated
differently. Do not conflate them.

---

## When DESIGN.md Is Empty

An empty DESIGN.md is not a problem to solve immediately. It is
a gap to name honestly and begin filling only when the person
is ready.

**Name the gap first:**
"Your DESIGN.md doesn't have any references yet. The gallery
options I show you will be drawn from our conversation, which
means they'll reflect what you've said today — not a longer
pattern of what you're drawn to. If you'd like, I can ask a
few questions to start populating it. Or we can build first
and return to it later."

Wait for a response. Do not begin the population workflow
without explicit interest. Do not make "filling DESIGN.md" feel
like homework the person must complete before building.

---

## The Population Workflow

Run this workflow only when the person has indicated they want
to populate DESIGN.md. Do not run it speculatively, and do not
run it in auto/build mode.

Work through the three sections in order. Ask one question at
a time. Record the answer before moving to the next question.

### Section 1: References

The goal is to collect 3–7 specific, named references. Vague
genre references ("I like minimal design") are not useful here —
named works, sites, designers, or artifacts are.

**Opening question:**
"Can you name a website, app, book, poster, building, or any
other designed thing that feels like it's pointing in the
direction you want this site to go? It doesn't have to be
directly related to what we're building — anything that
captures the feeling."

After each answer:
- Confirm the reference by restating it back.
- Ask one follow-up: "What specifically draws you to that one?"
  Record the answer alongside the reference — not as a separate
  entry, but as a note on the reference itself.
- Then ask: "Is there another one, or does that feel like enough
  to start with?"

Continue until the person indicates they are done or until 7
references are collected. Do not push for more than 7 in a
single session. Quality and specificity matter more than quantity.

**Format for each Reference entry:**
- [Name or URL] — [person's own words about what draws them to it]


Never paraphrase the person's words in a Reference entry.
Use their exact language, even if it is informal.

---

### Section 2: Derived Identity

After References are collected, synthesize them into a
Derived Identity paragraph. This is the agent's work, not
the person's — but it must be presented as a hypothesis
and confirmed before being written.

**How to synthesize:**
Look across the References for recurring signals:
- Aesthetic registers (spare, dense, warm, severe, playful,
  institutional, handmade, technical)
- Structural preferences (hierarchy, flatness, rhythm, surprise)
- Relationship to convention (subverts it, refines it,
  ignores it, celebrates it)
- Tone (earnest, ironic, direct, lyrical, dry)

Identify the 2–3 most consistent signals. Ignore signals that
appear only once — a single outlier reference does not define
a pattern.

**Format:**
Write 3–5 sentences in plain language. No jargon. No design
buzzwords. The person should be able to read this and say
"yes, that's me" or "that's not quite right."

**Present it as a hypothesis:**
"Based on your references, here's what I think your aesthetic
direction is. Tell me if any of this is off:

[Derived Identity paragraph]

Does this feel accurate, or is something missing or wrong?"

Wait for a response. Apply corrections immediately. Re-present
once if corrections were substantial. Do not re-present more
than twice — if the second version still doesn't feel right,
note it as unresolved and return to it in a future session.

**Write to DESIGN.md only after confirmation.**

---

### Section 3: Observed Taste

Observed Taste is never populated during the initial population
workflow. It can only be written after the person has made
real decisions — chosen between options, rejected a direction,
or expressed a strong reaction to something in a session.

The first entry in Observed Taste should appear after the first
gallery the person responds to. The agent observes the reaction
and proposes an entry at the end of the session:

"I noticed you responded strongly to [option] and moved past
[option] quickly. Based on that, I'd add this to Observed Taste:
[proposed entry]. Does that feel like a stable preference worth
recording, or was it specific to this decision?"

Write to Observed Taste only on confirmation.

**Format for each Observed Taste entry:**
- [Pattern observed] — first seen [date], [context]


Entries in Observed Taste describe behavior, not stated
preferences. The distinction matters:
- WRONG: "Prefers minimal design" (stated preference)
- RIGHT: "Consistently chose the most typographically spare
  option when given three alternatives — 2026-04-10, URL
  structure gallery; 2026-04-15, homepage layout gallery"

---

## Reading DESIGN.md During a Session

Load DESIGN.md at session start whenever a gallery will be
presented or a significant design decision is approaching.

**If DESIGN.md is populated:**
- Read Derived Identity and Observed Taste before generating
  any gallery option.
- The implied gallery option must be traceable to a specific
  signal in one of these two sections. If it cannot be traced,
  it is not the implied option — it is a generic suggestion
  masquerading as one. Start over.
- If the person's stated direction in the current session
  conflicts with their Observed Taste, name the conflict once:
  "This direction is more [X] than what you've tended toward
  in previous sessions — you've usually [describe pattern].
  Is that a shift, or is this decision different for a reason?"
  Then proceed with the current session's stated direction.

**If DESIGN.md has References but no Derived Identity:**
- Derive it now, silently, before generating the gallery.
- Present it to the person after the gallery: "I also synthesized
  a Derived Identity from your references — want me to show you
  what I came up with before writing it to DESIGN.md?"

**If DESIGN.md is completely empty:**
- Name the gap as described above.
- Draw gallery options from the current session's conversation.
- Note which option would have been the implied option if
  DESIGN.md were populated: "The third option is drawn from
  what you said about [X] earlier — I'd normally trace this
  to your DESIGN.md references, but since we haven't built
  that yet, it's based on today's conversation only."

---

## Maintaining DESIGN.md Over Time

**Update References when:**
The person names a new influence, responds to a gallery with
"that's exactly the direction I want," or links something
with aesthetic intent. Ask before adding: "Should I add that
to your References in DESIGN.md?"

**Update Derived Identity when:**
Three or more new References have been added since the last
synthesis, or the person says the current Derived Identity
no longer feels accurate. Re-run the synthesis and re-present
as a hypothesis. Never update Derived Identity silently.

**Update Observed Taste when:**
A session produces a clear, repeatable pattern — the person
chose the same kind of option twice or more, rejected
the same kind of option twice or more, or expressed a strong
reaction they connected to a longer-standing preference.
Propose the entry at the end of the session, using the
MEMORY.md proposal moment: "I'd also add this to Observed
Taste in DESIGN.md — [entry]. Should I write it?"

**Never update DESIGN.md without confirmation in interactive mode.**
In auto/build mode, do not update DESIGN.md at all — log
a proposed update in DECISIONS.md and surface it at the
next interaction.

---

## DESIGN.md File Format

```markdown
# Design References and Identity

## References
<!-- Named by the person. Never inferred or added without confirmation. -->

- [Name or URL] — [person's own words]
- [Name or URL] — [person's own words]

## Derived Identity
<!-- Agent synthesis, confirmed by person before writing. -->

[3–5 sentences in plain language describing aesthetic direction.]

Last updated: [date]

## Observed Taste
<!-- Behavioral patterns, not stated preferences. Written after
observed decisions, proposed before writing. -->

- [Pattern] — first seen [date], [context]
- [Pattern] — first seen [date], [context]
```

---

## What This Skill Is Not

- It is not a design brief or requirements document.
- It is not a checklist the person must complete.
- It is not static — it is updated as the person's taste
  becomes clearer through actual decisions.
- Derived Identity is not the agent's aesthetic preference
  projected onto the person. It is a hypothesis derived
  entirely from the person's own stated references.

---

> DESIGN.md is how the agent remembers who this person is
> between sessions. The gallery is only as good as this file.
```

## `testing`

```markdown
---
name: testing
description: Test scope, trigger conditions, external integration tests, and pre-merge checklist for IndieWeb spec routes.
trigger: Before releasing any spec route or merging any branch.
---

# Testing

## When to Run What

| Scope | Trigger | Action |
|---|---|---|
| Any file edit | After saving | Run lint. Fix all errors before the next edit. |
| Logical unit of work | Before moving to the next feature, route, or schema change | Run unit tests. Fix failures before continuing. |
| Spec route release | Before releasing a Webmention, Micropub, IndieAuth, or WebSub change | Run the corresponding external integration test. |
| Merge | Before merging any branch | Complete the pre-merge checklist below. |

A logical unit of work is describable in a single commit message — a new
route, spec endpoint, schema change, or component. A typo fix, comment,
style tweak, or single-file rename does not qualify. Do not accumulate
failures across units.

> The applicable lint and test commands are in the nearest framework
> AGENTS.md. Check there before running any check.

## External Integration Tests

Run these against the corresponding spec routes before any release:

- Webmention — [webmention.rocks](https://webmention.rocks)
- Micropub — [micropub.rocks](https://micropub.rocks)
- IndieAuth — [indieauth.rocks](https://indieauth.rocks)

## Pre-Merge Checklist

- [ ] `rel=me` is bidirectional for all configured profiles
- [ ] Every post has `h-entry` with `u-url`, `dt-published`, `e-content`
- [ ] `POST /api/webmention` returns 202 for valid source/target
- [ ] `/.well-known/oauth-authorization-server` returns valid IndieAuth metadata
- [ ] `GET /api/micropub?q=config` returns valid config
- [ ] Atom feed has `rel=hub` and `rel=self`
- [ ] Export endpoints return valid output
- [ ] No new vendor dependency without `docs/dependencies.md` entry
- [ ] No active constraint in CONSTRAINTS.md violated
- [ ] DECISIONS.md updated with any autobuild-mode choices this session
- [ ] Corrections and confirmed preferences recorded in MEMORY.md
```

## `memory-files`

```markdown
---
name: memory-files
description: Rules for reading, writing, and maintaining MEMORY.md, DECISIONS.md, CONSTRAINTS.md, and DESIGN.md across sessions.
trigger: End of session; proposing MEMORY.md or DECISIONS.md updates.
---

# Memory Files

## File Responsibilities

| File | Written by | Read every session |
|---|---|---|
| AGENTS.md | Human only | Yes |
| MEMORY.md | Agent (on confirmation) | Yes |
| DECISIONS.md | Agent | Yes |
| CONSTRAINTS.md | Agent (on statement) | Yes |
| DESIGN.md | Human + agent | Only when design work occurs |

## Creating Files

- **Interactive mode** — ask before creating MEMORY.md or DESIGN.md for
  the first time.
- **Auto Build mode** — create DECISIONS.md at session start without
  asking; note it in build output. Ask before creating MEMORY.md even
  in auto mode.
- **CONSTRAINTS.md** — create at the project root the first time a
  constraint is stated in any session. Always required; not conditional
  on whether AGENTS.md is read-only.

## MEMORY.md Rules

- Write only confirmed, repeated, or clearly stable lessons.
- Keep under 150 lines. When near the limit, ask the person to review;
  move older entries to `docs/memory-archive.md`.
- No secrets, tokens, or personal data.
- Flag contradictions — do not silently overwrite existing entries.
- When a DECISIONS.md entry becomes stable and user-confirmed, summarize
  it as a DECISION entry here.

**Entry format** — one line per lesson, optional note on the next line:
YYYY-MM-DD CATEGORY Lesson in one sentence.
Optional one-line note with context or source decision.


**Valid categories:** `PREFERENCE` `CORRECTION` `CONSTRAINT` `DECISION` `STACK`

## CONSTRAINTS.md Format

One entry per constraint, recorded immediately when stated:
CONSTRAINT plain-language description
SCOPE what it applies to
SET date or "this session"


Constraints are permanent until explicitly lifted. When a person says
something that could lift a constraint, confirm before acting:
> "Are you removing this constraint permanently, or just for this feature?"

## End-of-Session Requirement (Interactive Mode)

Before the final response of any session:

1. Propose 1–3 MEMORY.md entries in the standard format above.
2. Propose any queued DESIGN.md Observed Taste entries.
3. Ask: "Should I write these to MEMORY.md and DESIGN.md?"
4. Do not write either without confirmation.

If the session ends without this step, log both as unresolved checkpoints
in DECISIONS.md.

## AGENTS.md Safeguard

- Never edit without explicit human instruction.
- If AGENTS.md is non-empty when first read, it is the standing
  instruction set. Never replace its contents — only append.
- Present any change as a clearly marked diff; wait for approval before
  applying.
- After any approved change, log what changed in DECISIONS.md and
  summarize in MEMORY.md.
- This file is owned by the person, not the session.
```

## `indieweb-specs`

```markdown
---
name: indieweb-specs
description: >
  Reference for implementing IndieWeb specifications in priority order. Load this
  skill when implementing or modifying rel=me, microformats2, Webmention,
  IndieAuth, Micropub, or WebSub — or when the person asks about IndieWeb
  building blocks, spec compliance, or interoperability. Do not load for
  general design questions or non-spec work.
---

# IndieWeb Specifications — Implement in Priority Order

## Core Principle

Build only what a real UX need demands. A **real UX need** exists
when the person has described a workflow or outcome the spec would
enable. If none is stated, ask before implementing:
*"What would you want users to be able to do that this enables?"*

Higher-priority specs make lower-priority ones more useful, but
they are not always strict dependencies. Do not implement a spec
speculatively — UX before plumbing.

---

## Priority 1 — Identity and Markup

### `rel=me` — Identity Verification
**Advertise:** `<link rel="me" href="…" />` in `<head>`
Also add as `<a rel="me">` on every visible profile link.

**Purpose:** Bidirectional verification that this domain belongs
to the same person as the linked profiles.

**Acceptance criterion:** `npx indiekit check <url>` passes.

**Ask first:** "Which profiles do you want to claim from this
domain?" Confirm each one — rel=me is a public identity statement
and appears in the Irreversible Decisions table.

**Key notes:**
- Verification is bidirectional — the linked profile must also
  link back to this domain.
- Common targets: GitHub, Mastodon, LinkedIn, micro.blog.
- Never add a rel=me link to a profile the person did not name.

---

### microformats2 — Semantic Markup
**Advertise:** Server-rendered HTML only. No `use client`.

**Purpose:** Machine-readable layer on top of human-readable HTML.
Enables Webmention display, IndieAuth authorship, feed readers,
and cross-site interactions.

**Acceptance criterion:** A microformats2 parser extracts a valid
`h-entry` from every post page.

**Ask first:** "Which post types exist on this site?" Build only
the classes the actual post types require.

**Key classes by context:**

| Context | Classes |
|---------|---------|
| Person / site identity | `h-card`, `u-url`, `u-photo`, `p-name` |
| Every post | `h-entry`, `u-url`, `dt-published`, `e-content` |
| Author attribution | `p-author`, nested `h-card` |
| Feed / list page | `h-feed`, contains `h-entry` items |
| Reply / mention | `h-cite`, `u-in-reply-to` |
| Syndication link | `u-syndication` |

**Critical rules:**
- Never remove a microformats2 class without checking which spec
  depends on it. Webmention display, IndieAuth, and feed readers
  all consume these classes.
- microformats2 must be server-rendered. A page that hydrates
  client-side will fail parser checks.
- `e-content` must contain the full post content, not a summary.

---

## Priority 2 — Interaction Infrastructure

### Webmention — Cross-Site Notifications
**Advertise:** `<link rel="webmention" href="/api/webmention" />`

**Purpose:** Receive notifications when other sites link to your
content. Enables cross-site replies, likes, and reposts to appear
on your posts.

**Acceptance criterion:** webmention.rocks tests 1–23 pass.
Run at: https://webmention.rocks/

**Ask first:** "How do you want to handle incoming mentions —
display them automatically, queue for moderation, or ignore them
for now?" Do not build display logic until this is answered.

**Key notes:**
- Validate webmentions asynchronously. Never block the response.
- Sanitize all external `e-content` before rendering — treat it
  as untrusted HTML.
- Sending webmentions must be human-initiated or explicitly
  scheduled. Never auto-send on publish without confirmation.
- Source URL must return a valid page containing a link to target.

---

### IndieAuth — Decentralized Authentication
**Advertise:**
```html
<link rel="authorization_endpoint" href="/auth" />
<link rel="token_endpoint" href="/token" />
```

**Purpose:** Makes this domain an identity provider. Allows the
person to log into other IndieWeb sites using their own URL.

**Acceptance criterion:** indieauth.rocks authorization code
flow passes.
Run at: https://indieauth.rocks/

**Ask first:** "Do you plan to use external publishing clients
or log into other IndieWeb sites?" IndieAuth is in the Irreversible
Decisions table — confirm before activating.

**Key notes:**
- PKCE is mandatory. No exceptions.
- Issue opaque tokens only — no JWTs.
- Exact `redirect_uri` match required on every request.
- `/.well-known/oauth-authorization-server` must return valid
  IndieAuth server metadata.

---

## Priority 3 — Publishing Protocol

### Micropub — External Publishing API
**Advertise:** `<link rel="micropub" href="/api/micropub" />`

**Purpose:** Allows external clients (mobile apps, desktop
editors, CLIs) to create, update, and delete content on this site.

**Acceptance criterion:** micropub.rocks tests 100–300 pass.
Run at: https://micropub.rocks/

**Ask first:** "What is your publishing workflow — do you want
to post from a mobile app, a desktop editor, a CLI, or just
this site's interface?" Build only the post types the person
actually uses. Micropub is in the Irreversible Decisions table.

**Key notes:**
- Verify `delete` scope explicitly before any destructive action.
- Build only the post types the person has described needing.
  Do not scaffold speculative post types.
- `q=config` endpoint must return valid configuration including
  supported post types.

---

## Priority 4 — Real-Time Distribution

### WebSub — Live Feed Updates
**Advertise:**
```html
<link rel="hub" href="[hub-url]" />
<link rel="self" href="[feed-url]" />
```

**Purpose:** Pushes feed updates to subscribers in real time
rather than requiring polling.

**Acceptance criterion:** A subscribed feed reader receives a
new post within 30 seconds of publish.

**Ask first:** "Do you have subscribers who need real-time
updates, or is polling acceptable for now?" WebSub adds
operational complexity — only implement when the UX need is real.

**Key notes:**
- Ping the hub after every publish.
- Both `rel="hub"` and `rel="self"` must appear in the Atom feed.
- The hub URL is typically a third-party service (e.g.
  WebSub.rocks for testing). Document it in docs/dependencies.md.

---

## Spec Dependency Map

Before removing or modifying any spec implementation, check this
dependency chain:

rel=me
└── IndieAuth (uses rel=me for profile discovery)
└── Micropub (requires IndieAuth token validation)

microformats2
└── Webmention display (parses h-entry, h-cite from source)
└── IndieAuth authorship (parses h-card for identity)
└── Feed readers (parse h-feed, h-entry)

WebSub
└── Atom feed (must contain rel=hub and rel=self)


**Never remove a microformats2 class without tracing this map.**
A class that appears unused in the template may be consumed by
an external parser, feed reader, or Webmention handler.

---

## External Test Suite

Run the appropriate test before releasing any spec endpoint:

| Spec | Test suite |
|------|-----------|
| Webmention | https://webmention.rocks/ — tests 1–23 |
| IndieAuth | https://indieauth.rocks/ — auth code flow |
| Micropub | https://micropub.rocks/ — tests 100–300 |
| General | `npx indiekit check <url>` |

These tests are mandatory before merge for any spec route release.
See the Testing and Compliance section of AGENTS.md for the
full pre-merge checklist.

---

## In-Development Specs — Use With Caution

The following specs are undergoing active development and are not
yet broadly implemented [web:1]. Do not implement unless the
person explicitly requests them and understands the stability risk:

- **post-type-discovery** — implied post type inference
- **Microsub** — reader subscription protocol
- **fragmentions** — deep linking into page content
- **salmentions** — salmon-protocol webmentions

Ask the Socratic ownership question before implementing any of
these: "What happens to this feature if the spec changes
significantly before it stabilizes?"

---

> Build only what a real UX need demands.
> UX before plumbing — always.
```

## `indieweb-principles`

```markdown
---
name: indieweb-principles
description: >
  Reference for IndieWeb philosophy and principles as they apply
  to implementation decisions. Load this skill when a decision
  touches data ownership, content portability, site identity,
  or long-term longevity — or when the person asks why IndieWeb
  recommends a particular approach. Do not load for routine
  implementation work where the principle is already clear from
  AGENTS.md context.
---

# IndieWeb Principles — Reference During Implementation

## How to Use This Skill

These principles are not rules. They are lenses for evaluating
decisions that have no single technically correct answer. When a
decision feels close — two approaches seem equally valid — check
it against the relevant principle below before presenting a gallery.

They are also not equally weighted in all contexts. The first
three principles (own your data, humans first, make what you need)
are load-bearing for every IndieWeb site. The remaining seven
are more contextual — apply them when the situation calls for them.

---

## The Principles

### 1. Own Your Data
**What it means:** Content lives on the person's domain. Canonical
URLs point here. No third party controls access to the content or
can make it inaccessible by changing their terms or shutting down.

**Agent behavior:**
- Flag any dependency that makes content inaccessible if the
  service shuts down. Ask the Socratic ownership question:
  "Who controls this content if that service disappears?"
- Never store canonical content in a third-party system without
  an export path. Document the export path in docs/dependencies.md.
- Syndicated copies must link back to the canonical URL here.

**Apply when:** Evaluating any vendor dependency, database choice,
hosting decision, or syndication target.

---

### 2. Humans First
**What it means:** Human-readable HTML is the primary layer.
Machine-readable markup (microformats2, JSON-LD, RSS) is built
on top of it — never as a replacement.

**Agent behavior:**
- Readable HTML ships first. Parseable markup is added to it,
  never substituted for it.
- A page that works only for machines — or only for machines
  after hydration — violates this principle.
- microformats2 classes are attributes on visible, human-readable
  elements. Do not create hidden elements solely for parser
  consumption.

**Apply when:** Designing templates, adding semantic markup,
evaluating server vs. client rendering choices.

---

### 3. Make What You Need
**What it means:** Build for stated use cases only. Do not scaffold
features the person has not described needing.

**Agent behavior:**
- Ask before building anything not explicitly requested.
- "The person might want this later" is not a justification for
  building it now.
- Speculative scaffolding creates maintenance burden and encodes
  assumptions about what the person values.

**Apply when:** Deciding scope at the start of any feature,
evaluating whether to add a post type, route, or endpoint that
wasn't explicitly requested.

**Connects to:** The Scope question in the socratic-depth skill —
"What would happen if you didn't build this?"

---

### 4. Use What You Make
**What it means:** Test the site as the site owner would use it.
If it doesn't work for the owner, it doesn't ship.

**Agent behavior:**
- Test every feature from the perspective of the person posting,
  editing, and reading their own content — not from the
  perspective of an external visitor or parser.
- A feature that passes external tests but is frustrating for
  the owner to use is not done.

**Apply when:** Reviewing any publishing flow, editor experience,
or admin interface before marking a feature complete.

---

### 5. Document
**What it means:** Every non-obvious decision gets a comment or
a docs/ entry. The site should be understandable to its owner
after a six-month gap.

**Agent behavior:**
- Any decision that would not be immediately obvious to the
  person six months from now gets a comment in the code or
  an entry in docs/.
- DECISIONS.md is the primary record for architectural choices.
  Code comments handle implementation-level decisions.
- "This is standard" is not a substitute for documentation when
  the standard is not something the person would know.

**Apply when:** Writing non-trivial logic, making a choice
between two valid approaches, adding any IndieWeb spec endpoint.

---

### 6. UX Before Plumbing
**What it means:** Do not implement a spec until a real UX need
depends on it. Protocol infrastructure without a user-facing
reason to exist is waste.

**Agent behavior:**
- A real UX need exists when the person has described a workflow
  or outcome the spec would enable. If none is stated, ask.
- Building Micropub before the person has described a publishing
  workflow they're frustrated by is plumbing before UX.
- This principle overrides the spec priority table in
  indieweb-specs when no UX need is present.

**Apply when:** Evaluating whether to start implementing a new
IndieWeb spec, or when a spec endpoint is requested without a
stated reason.

---

### 7. Modularity
**What it means:** Each web feature is isolated. Replacing or
removing one must not cascade into breaking others.

**Agent behavior:**
- Webmention, IndieAuth, Micropub, and WebSub endpoints are
  independent. Removing one must not break the others.
- Use the spec dependency map in indieweb-specs to check for
  hidden dependencies before modifying any spec feature.
- microformats2 classes are the most common source of hidden
  coupling — a class removed from a template may break a spec
  feature that depends on it elsewhere.

**Apply when:** Refactoring, removing a feature, or evaluating
whether a change to one spec endpoint could affect another.

---

### 8. Longevity
**What it means:** The site should still work and still be
readable in ten years. URLs are permanent. Implementation
details do not leak into public addresses.

**Agent behavior:**
- No database IDs in public URLs. No framework internals
  in public URLs. No post type names in public URLs —
  types change; URLs must not.
- Permanent redirects for any moved content. Never a 404
  for a URL that was once public.
- Prefer formats with long track records: HTML, Atom, JSON.
  Avoid formats tied to a single framework or vendor.

**Apply when:** Designing URL structure, evaluating format
choices, moving or renaming content.

**Connects to:** The Consequence question in socratic-depth —
"What becomes harder to change in six months?"

---

### 9. Pluralism and Voice
**What it means:** The web is most valuable when it contains
distinct, irreplaceable personal voices. Generic patterns
produce a less valuable web.

**Agent behavior:**
- The gallery protocol exists partly to counteract AI averaging.
  The implied option must surface this specific person's
  direction — not the most common direction for someone with
  similar stated preferences.
- DESIGN.md exists to make the person's aesthetic identity
  legible to the agent across sessions. Use it.
- AI-generated prose for publication must be marked as a draft
  for human review. The person is always the named author.
- Research on human-AI collaboration (Walton et al., 2026,
  doi:10.1145/3773292) found human-steered sessions produce
  outcomes 2–4× better than passive ones. The protocols here
  are not friction — they are what makes the output good.

**Apply when:** Generating any content draft, choosing between
a conventional and unconventional design option, evaluating
whether a feature reflects the person's voice or a generic
pattern.

---

### 10. Have Fun
**What it means:** Personality and joy are features. Do not
sand them down in pursuit of convention or correctness.

**Agent behavior:**
- An unconventional choice that the person loves is better
  than a conventional choice they tolerate.
- "That's not how most sites do it" is not a reason to
  discourage a direction the person is excited about.
- Support unconventional choices fully. Rule 4 of AGENTS.md —
  the person owns everything — includes the right to build
  something strange, playful, or deliberately imperfect.
- If the person's DESIGN.md Observed Taste signals joy or
  humor, the gallery options should reflect that register —
  not neutralize it.

**Apply when:** Any moment where a technically correct but
joyless choice is about to be presented as the only option.

---

## Principle Conflict Resolution

When two principles appear to conflict, resolve in this order:

1. **Own your data** overrides convenience. A simpler solution
   that compromises ownership is not simpler — it is worse.

2. **Humans first** overrides machine optimization. A page that
   is more parseable but less readable has made the wrong trade.

3. **Make what you need** overrides completeness. An unbuilt
   feature cannot break.

4. **Have fun** overrides convention. The person's enjoyment
   of their own site is a feature, not a vanity.

If a conflict cannot be resolved with this ordering, present it
to the person as a gallery with one option per principle. Let
them choose which value takes precedence for this project.

---

> These are not checkboxes.
> They are the reason the checkboxes exist.
```

## `posse-syndication`

```markdown
---
name: posse-syndication
description: >
  Reference for POSSE (Publish on Own Site, Syndicate Elsewhere)
  implementation, URL slug conventions, syndication target
  configuration, and export endpoint maintenance. Load this skill
  when finalizing URL structure, configuring a syndication target,
  building or auditing export endpoints, or when the person asks
  about canonical URLs, slug generation, or cross-posting strategy.
---

# POSSE and Data Ownership — Syndicate Without Surrendering

## Core Principle

**Publish on Own Site, Syndicate Elsewhere.**

Content lives here first. The canonical URL always points to this
domain. Syndicated copies exist to extend reach — they are not
the record of truth. Every syndicated copy must link back to the
canonical URL on this domain.

Syndication is an act of choice, not an act of delegation.
The person decides where their content goes, when it goes there,
and whether it goes at all. The agent never configures a
syndication target the person did not explicitly name, and never
auto-syndicates without confirmation.

---

## URL Conventions

URL structure is an irreversible decision. Always present a gallery
and ask the person to confirm the slug before finalizing any new
URL. Once a URL is public and linked, it is a permanent promise
to everyone who links to it.

### Choose the Pattern by Content Type

**Time-stamped content** (blog posts, articles, notes, journals) 
/YYYY/MM/DD/<slug> 
Use when the date of writing is part of the permanent identity
of the content. The date is canonical metadata — it belongs in
the URL. Do not use for evergreen pages, reference sections,
or features where "when this was written" is irrelevant.

---

**Evergreen pages** (about, contact, uses, now, colophon)
/<slug>
Use for single pages with no temporal identity and no
meaningful parent section. The page is its own thing.
Example: `/about`, `/uses`, `/now`

---

**Structured collections** (projects, work, talks, recipes)
/<section>/<item-slug>
Use when content belongs to a named category and the
category relationship is part of how the person thinks
about and navigates the content.
Example: `/projects/garden-tracker`, `/talks/indieweb-2026`

---

**Nested sub-items** (iterations, versions, chapters)
/<section>/<parent-slug>/<child-slug>
Use sparingly. Only when the parent-child relationship is permanent and meaningful — not for organizational convenience
that might change.
Example: `/projects/garden-tracker/v2`

---

### Slug Confirmation Protocol

Before finalizing any new URL, present the person with the
proposed slug and a brief explanation of why it was chosen.
Do not silently generate and commit a slug.

**Format:**
Proposed URL: /[path]
Pattern used: [which pattern above and why]
Slug derived from: [title, section, or description]
Alternative: /[alternative] — [one sentence on the trade-off]


Then ask: "Does this feel right, or would you like a different
slug?" Wait for confirmation before creating any file, route,
or redirect that uses this URL.

---

### Slug Pushback Rules

Push back on a proposed slug when it creates a mismatch between
the address and what a visitor would expect to find there.
Do this before building — not after.

**Triggers for pushback:**
- The slug implies a different content type than the actual
  content. Example: `/about` for a page hosting a chatbot,
  `/blog` for a page that is actually a portfolio.
- The slug encodes a temporary state. Example: `/new-projects`,
  `/current-work` — "new" and "current" will be wrong soon.
- The slug is so generic it could mean anything.
  Example: `/stuff`, `/things`, `/page2`
- The slug encodes implementation details.
  Example: `/react-app`, `/v2-beta`, `/temp`

**How to push back:**
State the mismatch in one sentence, then offer a corrected
alternative and ask which the person prefers. Do not refuse
to proceed — surface the issue and let the person decide.

Example:
"The slug `/about` typically signals a personal or team
biography page, but this endpoint is meant to host a chatbot.
A visitor arriving at `/about` would likely expect something
different. An alternative might be `/assistant` or `/chat`.
Which feels right for what you're building?"

---

### Slug Generation Rules
- Source: page title, section name, or explicit description —
  normalized to kebab-case
- Remove stop words only if the slug exceeds 60 characters
- Never truncate in a way that changes meaning
- Notes and untitled posts: use first 5 significant words,
  or a content hash if no meaningful words exist
- Implement in `lib/slug.ts` or `app/utils/slug.py`
  (create if absent, following the active framework profile)

### What Must Never Appear in a Public URL
| Prohibited | Why |
|-----------|-----|
| Database IDs (`/posts/1234`) | Leaks implementation; breaks on migration |
| Post type names in time-stamped URLs (`/articles/`) | Types change; URLs must not |
| Framework internals (`/_next/`) | Breaks on framework change |
| Temporary state (`/new-`, `/current-`, `/temp-`) | Will be wrong soon |
| Session or auth tokens | Security |
| Inconsistent trailing slashes | Causes duplicate content |

### Slug Stability Rule
Once a URL is public — reachable at a domain by anyone with
network access — it must never return a 404. If content moves,
implement a permanent (301) redirect. If content is deleted,
return 410 Gone, not 404 Not Found.

---

## Syndication Targets

### Supported Targets
Configure only targets the person has explicitly named.
Never add a target speculatively.

```json
// config/syndication.json
{
  "targets": [
    {
      "uid": "https://mastodon.social/@user",
      "name": "Mastodon",
      "service": "mastodon",
      "domain-restriction": null
    },
    {
      "uid": "https://bsky.app/profile/user",
      "name": "Bluesky",
      "service": "bluesky",
      "domain-restriction": null
    },
    {
      "uid": "https://micro.blog/user",
      "name": "Micro.blog",
      "service": "microblog",
      "domain-restriction": null
    },
    {
      "uid": "https://linkedin.com/in/user",
      "name": "LinkedIn",
      "service": "linkedin",
      "domain-restriction": "articles-only"
    }
  ]
}
```

### Syndication Link Markup
Every syndicated copy must be linked from the canonical post
using the `u-syndication` microformats2 class:

```html
<a class="u-syndication"
   href="https://mastodon.social/@user/123456">
  Also on Mastodon
</a>
```

This link must be:
- Visible to human readers — not hidden or aria-hidden
- Added after syndication completes, not speculatively
- Present on the canonical post page, not only in feeds

### Syndication Is Human-Initiated
Never auto-syndicate on publish without explicit confirmation.
The mandatory question before configuring any new target:

"This will send your content to [platform name]. Once sent,
[platform] controls the copy — you can delete it there, but
you cannot fully retract it. [Platform]'s terms govern the
syndicated copy. Should I configure this target and document
it in docs/dependencies.md?"

Ask this even when the person appears to have already decided.
Each syndication target is an entry in the Irreversible
Decisions table.

### Per-Post Syndication Control
The person must be able to choose, per post, whether to
syndicate and to which targets. Never build a system that
syndicates all posts to all configured targets automatically.

Implement syndication control as a post-level field:
syndicate-to: mastodon, bluesky

or via Micropub's `mp-syndicate-to` property if Micropub
is implemented.

---

## Export Endpoints

These three endpoints must always be functional. They are
the person's guarantee that their content is portable
regardless of what happens to the platform, framework,
or hosting provider.

Test all three before every merge.

### `GET /export/json` → mf2-JSON
Full site export in microformats2 JSON format. Every post,
every post type, every piece of metadata. This is the
migration path to any other IndieWeb-compatible platform.

```json
{
  "items": [
    {
      "type": ["h-entry"],
      "properties": {
        "name": ["Post title"],
        "content": [{"html": "…", "value": "…"}],
        "url": ["https://example.com/2026/04/10/post-slug"],
        "published": ["2026-04-10T20:00:00Z"],
        "syndication": ["https://mastodon.social/@user/123"]
      }
    }
  ]
}
```

### `GET /feed.xml` → Atom
Standards-compliant Atom feed. Must include `rel="hub"` and
`rel="self"` link elements if WebSub is implemented.

```xml
<feed xmlns="http://www.w3.org/2005/Atom">
  <link rel="self" href="https://example.com/feed.xml" />
  <link rel="hub" href="https://hub.example.com" />
  <!-- entries -->
</feed>
```

### `GET /feed.json` → JSON Feed 1.1
JSON Feed spec version 1.1. Human-readable alternative to
Atom for feed readers that prefer JSON.

```json
{
  "version": "https://jsonfeed.org/version/1.1",
  "title": "Site Name",
  "home_page_url": "https://example.com",
  "feed_url": "https://example.com/feed.json",
  "items": [
    {
      "id": "https://example.com/2026/04/10/post-slug",
      "url": "https://example.com/2026/04/10/post-slug",
      "title": "Post title",
      "content_html": "…",
      "date_published": "2026-04-10T20:00:00Z"
    }
  ]
}
```

### Export Endpoint Rules
- All three endpoints must return valid output before any merge.
  Add to the pre-merge checklist in AGENTS.md.
- Pagination is acceptable for large archives — but the first
  page must include a `next` link and the full export must
  be reachable by following pagination links.
- Authentication must never be required to access these endpoints.
  Export is a public right, not a logged-in feature.
- Never remove or gate these endpoints. If a framework migration
  would break them, fix the endpoints before completing the
  migration.

---

## POSSE vs. PESOS

**POSSE** (Publish Own Site, Syndicate Elsewhere) — correct.
Content originates here. Canonical URL is here. Syndicated
copies link back.

**PESOS** (Publish Elsewhere, Syndicate Own Site) — avoid.
Content originates on a third-party platform. The person's
site becomes a mirror of someone else's infrastructure.
PESOS is acceptable only as a temporary bridge during
migration away from a platform.

If the person proposes a workflow that is PESOS rather than
POSSE, name the distinction and ask:
"This would make [platform] the origin of your content rather
than your site. That means [platform] controls the canonical
version. Is that the relationship you want with this content?"

---

## SEO and Canonical URLs

Dated, descriptive slugs for time-stamped content satisfy
contemporary SEO guidance and IndieWeb longevity requirements
simultaneously. Evergreen and hierarchical slugs do the same
for their respective content types. There is no structural
conflict between good URL design and search visibility when
the URL follows the pattern appropriate to its content type.

The canonical URL on this domain is the SEO-authoritative URL.
Syndicated copies should use `rel="canonical"` pointing back
to this domain where the platform supports it. Where it does
not, the `u-syndication` link on the canonical post is the
cross-reference record.

Do not modify URL structure to chase algorithmic signals.
URL structure is permanent. SEO guidance is not.

---

## Self-Hosting and Dependency Documentation

Before adding any third-party syndication service or feed
infrastructure, document in `docs/dependencies.md`:

```markdown
## [Service Name]
- Purpose: [what it does in this project]
- Sends data off-domain: yes
- Self-hosting alternative: [name and URL]
- Cost: [free tier / paid tier / open source]
- What breaks if this shuts down: [description]
- Added: [date]
```

This documentation is mandatory. The Socratic ownership
question applies to every syndication dependency:
"What happens to this part of the site if that service
changes its API, pricing, or shuts down?"

---

> Content originates here.
> Everything else is a copy that points home.
```

## `security`

```markdown
---
name: security
description: IndieWeb endpoint security requirements for Webmention, IndieAuth, Micropub, and media upload handlers.
trigger: Writing any Webmention, IndieAuth, Micropub, or media upload handler.
---

# Security

Apply these requirements to every handler in scope. None are optional.

## Webmention
- Validate asynchronously — never block the HTTP response on verification.
- Sanitize all external `e-content` before display. Treat it as untrusted HTML.

## IndieAuth
- PKCE is mandatory. No JWTs as tokens.
- Exact `redirect_uri` match required — no prefix matching, no wildcards.

## Micropub
- Verify `delete` scope explicitly before any destructive action.
- Do not infer delete permission from write scope.

## Media Uploads
- Validate MIME type by magic bytes, not `Content-Type` header.
- Serve uploaded files outside `public/` or `static/`. Never serve from a
  path the web server exposes directly.

## All Inbound Endpoints
- Rate-limit every inbound endpoint.
- Implement in `lib/ratelimit.ts` or `app/utils/ratelimit.py`.
  Create the file if absent, following the active framework profile in
  DECISIONS.md.

## Pre-Write Reminder
Before writing any handler covered by this skill, confirm:
- Is this endpoint in the Irreversible Decisions table in AGENTS.md?
  If yes, stop and get explicit sign-off before proceeding.
- Does `docs/dependencies.md` need updating for any new package this
  handler introduces?
```

<!-- ===== END PROMPT A ===== -->

---

# Prompt B — Multi-Service Setup

Copy everything between the two markers below into your agent. Use this at the
coordination layer; it delegates per-node installation back to Prompt A.

<!-- ===== BEGIN PROMPT B ===== -->

# Documentation Overhaul Prompt — Multi-Service Graph Engineering (personal)

> **Context: personal (IndieWeb).** Installs the `personal` graph system — IndieWeb obligations — rel=me, microformats2, Webmention, IndieAuth, Micropub, WebSub, POSSE.
> Per-node installation is delegated to `DOC-OVERHAUL-SINGLE-SERVICE.md`
> (personal), which carries the skill bodies; run it once per node.

**Use this once** when installing or updating the Graph Engineering scheme
across a multi-repo/multi-node project — not at the start of every coding
session. Once complete, `GRAPH-AGENTS.md` and each node's `LOOP-AGENTS.md`
handle per-session loading automatically.

Run this whenever: standing up a new multi-service project, registering a new
node into an existing graph (including nodes with a rich pre-existing
documentation network), or updating the roster after a subscription/tool
change — reuse it any time the roster or node list needs revising, not just at
project start. **This prompt is idempotent** — safe to re-run with a partial
change (e.g., just swapping one node's implementation model) without
disturbing anything else.

**Important — the tool you use to run this overhaul does not need to match
the roster you're writing.** You can execute this prompt in Claude Pro while
the roster assigns Opencode Go to per-node implementation, or in Antigravity
while specifying GPT-5.6 Luna at medium thinking for the coordinator role —
state which tool you're using to run this overhaul (for the record) separately
from the roster you're populating below.

---

You are performing a documentation overhaul, not implementing a feature. Your
job is to install or update the Graph Engineering scheme.

**Step 1 — Audit.** Check the coordinating repo root for `GRAPH.md` and
`GRAPH-AGENTS.md`. For each node repo, classify its markdown state using
`LOOP-AGENTS.md` Section 0's four cases (A: none, B: unrelated-only, C: single
existing `AGENTS.md`, D: rich pre-existing documentation network such as
process/plan/task-tracker docs or coursework rubrics). Report the case per
node before changing anything.

**Step 1.5 — For any node classified Case D, run Goal Extraction first.**
Do not restructure that node's docs yet. Summarize each of its existing
files' original purpose in one line, map them to the closest concept in
`LOOP-AGENTS.md`/`GRAPH-AGENTS.md`, and propose (gallery format) keep-as-is,
annotate, or fold-in-and-deprecate per file — fold-in only for small,
clearly superseded files. Wait for my confirmation before touching anything
in that node. If a Case D node's proposal would affect a shared contract or
another node's documentation, flag it for graph-level review before proceeding.

**Step 1.6 — Distill rules out of existing agent files, then reduce them.**
Tool entry points accumulate real rules. A `CLAUDE.md` carrying six months of
corrections is not boilerplate, and turning it into a pointer without rescuing
its content destroys the reasoning this scheme exists to preserve.

Per node, for every existing `CLAUDE.md`, `GEMINI.md`, `.github/copilot-instructions.md`,
`.cursorrules`, `.windsurfrules`, `.aider.conf.yml`, and any pre-existing
`AGENTS.md`, build a rule inventory: quote every normative statement (must,
never, always, don't, prefer, or a standing imperative) with its source, and
assign each exactly one destination —

- general behavioral rule → `AGENTS.md` Section 13, Project Specific Rules
- process mechanic → `LOOP-AGENTS.md` Section 1 (or `GRAPH-AGENTS.md`)
- must-never-do-to-this-codebase → `LOOP-AGENTS.md` Section 3, Irreversible Decisions
- binding project constraint → `CONSTRAINTS.md`
- taste or aesthetic preference → `DESIGN.md`, Declared Preferences
- past architectural choice with reasoning → `DECISIONS.md`
- durable lesson from a past failure → `MEMORY.md`
- genuine tool-specific quirk that cannot generalize → stays put, with a
  comment saying why
- redundant with the new system → dropped, naming the rule that supersedes it

Show me the inventory and **wait for approval**. This is an Irreversible
Decision. Only after approval: write each rule to its destination, then reduce
the entry points to pointers — `CLAUDE.md` and `GEMINI.md` to a reference to
`AGENTS.md` and nothing else, `.cursorrules` and friends to a one-line
instruction to read `AGENTS.md` (reduce, never delete — a tool that finds
nothing falls back to its own defaults), and `.gemini/settings.json` merged
rather than replaced.

Nothing is deleted that has not been rehomed. Before Step 5, verify every
inventoried rule appears in exactly one destination and report any that don't.

**Existing skills are preserved.** Never delete, overwrite, or move an existing
`SKILL.md`. Evaluate each one, register it in `AGENTS.md` Section 9 with an
explicit load trigger, mirror it across `.claude/skills/` and `.agents/skills/`
if it exists in only one, and adapt it only far enough to fit — front matter, a
trigger, a cross-reference. If an existing skill shares a name with one this
prompt installs, show both, say where they differ, and ask which survives.
Never merge them silently or assume the shipped one wins. Normative statements
inside a skill stay in that skill; they do not go through the rule inventory.


**Step 2 — Apply the Merge Protocol** from `GRAPH-AGENTS.md` Section 0:
- No coordination file exists → create `GRAPH.md` and `GRAPH-AGENTS.md` at the
  root of the primary/coordinating repo, and register every known node in the
  Section 3 node table, including each node's markdown_case.
- A node has no governance markdown (Case A/B) → register it as a node in
  `GRAPH.md`, then give it a minimal `LOOP-AGENTS.md` before it's folded into
  graph work.
- A node is Case C → leave its `AGENTS.md` untouched; this overhaul only
  touches graph-level files for that node.
- A node is Case D → apply only the confirmed Step 1.5 proposal.
- **Existing populated node/edge manifest or Model Routing Plan** → these get
  *replaced* where changed, not duplicated — see Steps 3 and 5.

**Step 3 — Update the node/edge manifest (Section 3)** if nodes, contracts,
execution order, or markdown_case values have changed. Confirm the current
node list and their contracts with me before writing. Replace only the
entries that changed; leave unaffected nodes/edges as-is.

**Step 4 — Confirm role scope.** This scheme has two role tiers — confirm
with me which tier applies before filling the roster:
- **Core roles (required for every graph):** coordinator, per-node
  implementation (mechanical), per-node implementation (complex logic),
  per-node QA, cross-node production-readiness gate.
- **Optional roles (add only if relevant):** second-opinion/independent
  contract review, live prototyping node. Skip these unless the project has a
  specific need (e.g., only add "live prototyping node" if a node has a
  visual/UI component).

**Step 5 — Populate the Model Routing Plan (Section 5) using this roster.**
For each role, state a subscription/service name (e.g., "Claude Pro," "Ollama
Cloud," "Replit Core") or a specific model name (e.g., "Claude Opus 5,"
"qwen3-coder:cloud," "Gemini 3 Pro") — either is acceptable, and either can
carry an optional reasoning-effort/thinking-level qualifier (e.g., "GPT-5.6
Luna at medium thinking"). You can mix granularity across roles in the same
pass. If a role is service-only, use that service's current default/
recommended model and note it may shift as the service's lineup changes;
don't hardcode a model I never named. If a role needs per-node assignment
rather than one global choice (e.g., different implementation models for the
frontend node vs. the backend node), list it that way.

```
Role: Graph coordinator (cross-node decisions, sequencing, contract review)
  Service or Model (+ optional effort/thinking level): ____________________

Role: Per-node implementation — mechanical/boilerplate
  Default (all nodes): ____________________
  Overrides (node: service/model), if any: ____________________

Role: Per-node implementation — complex logic
  Default (all nodes): ____________________
  Overrides (node: service/model), if any: ____________________

Role: Per-node QA
  Service or Model (+ optional effort/thinking level): ____________________

Role: Cross-node production-readiness gate
  Service or Model (+ optional effort/thinking level): ____________________

--- Optional roles (fill in only if included per Step 4) ---

Role: Second-opinion / independent contract review
  Service or Model (+ optional effort/thinking level): ____________________

Role: Live prototyping node
  Service or Model (+ optional effort/thinking level): ____________________
```

**Step 6 — Write the roster, replacing any prior table.** Write my answers
into `GRAPH-AGENTS.md` Section 5 in the existing `Role / Provider / Model ID /
Reason` block format, preserving whichever granularity I gave you per role.
If Section 5 already contains a populated roster from a prior run, replace it
entirely — do not append a duplicate table. Log the change as one line in
`GRAPH-MEMORY.md` (e.g., "Roster updated: coordinator moved from Antigravity/
gemini-3-pro to Claude Pro/opus-5"). Flag any role I leave blank as unconfirmed
rather than guessing. Omit optional roles entirely from the written table if
Step 4 confirmed they aren't in scope for this project.

**Step 7 — Confirm and stop.**
Show me the rule inventory from Step 1.6
with each rule's final destination, confirming none was lost, and any
tool-specific rule left in place with the reason it can't generalize. Show me the final diff of every file changed
or created across all affected repos. Do not begin feature implementation in
this same session — this is a documentation-only pass.

<!-- ===== END PROMPT B ===== -->
