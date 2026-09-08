# Frequently Asked Questions

Ideation by: Chris Fornesa, Assisted by: Claude Sonnet via Perplexity, Edits by: Grammarly.

---

## Getting Started

**Q: Do I need to fill in AGENTS.md before my first session?** No.
`AGENTS.md` arrives complete — the Six Rules, Merge Protocol, Loop, and skill
triggers are all already written. The only section left blank for you is
Section 13, Project Specific Rules. If it's empty, the agent asks three
plain-language questions at session start and fills it in for you:

1. "What are you trying to build — a website, an app, a blog, something else?"  
2. "Do you already have any code or files for this project, or are we starting from scratch?"  
3. "Is there a specific tool or service you've been told to use, or should I suggest something?"

**Q: What is the SESSION CONSTRAINTS block, and do I always need it?** It promotes the rules from AGENTS.md's reference sections into the agent's active working context for the duration of the session. Start every session with:

* "Starting a new session. SESSION CONSTRAINTS: Follow all rules in AGENTS.md when processing all prompts in this conversation. Are you ready?"

Without it, the agent may drift toward generic coding defaults as the session progresses.

**Q: Which agent should I start with for a new project?**  
It depends on the AI coding tools that you have access to. As I have access to the Codex CLI, I often use it for Phase 1 scaffolding to follow Rule 1 (ask before building) most consistently. Then, since I have access to Claude Code, I use it for IndieWeb spec implementation or for any work that touches multiple files simultaneously.

---

## Contexts

**Q: I already have an `AGENTS.md`. Will this overwrite it?**  
No. `AGENTS.md` in each context folder is built to be appended. It carries a
`<!-- ===== BEGIN CREATRWEB ORCHESTRATOR ===== -->` marker; everything from
that marker to the end of the file can be pasted at the end of your own
`AGENTS.md`, leaving your content untouched above it. The block opens with a
single `##` heading rather than a second `#` title so it nests cleanly, it
states that your existing rules take precedence over its own, and it scopes its
section numbering to itself — "Section 9" means Section 9 of the block, so your
file's numbering is unaffected. If your repo has no `AGENTS.md`, copy the file
in whole instead; it works standalone with no edits.

**Q: Why is it called `SYSTEM-README.md` and not `README.md`?**  
Because almost every repo already has a `README.md`, and a folder you copy
wholesale into a repo root shouldn't collide with it. `SYSTEM-README.md` holds
the install steps and both setup prompts; it has no role once the system is
installed, so there's no need to copy it into the target repo at all.

**Q: Which context do I start with?**  
There are two, and picking one is a conscious decision rather than a default.
Use `general/` for a standalone project — a conventional web app, a tool, a
client site. Use `personal/` for anything touching the personal IndieWeb site
or its satellites: any repo implementing `rel=me`,
microformats2, Webmention, IndieAuth, Micropub, WebSub, or POSSE syndication.
If you're unsure, start with `general` — moving up to `personal` later is
additive and costs nothing, while starting with `personal` on a project that
never needs it loads four skills you'll never trigger.

**Q: What is a context, exactly? Is it a separate framework?**  
No — it's the same framework, pre-adapted. Each context folder is a complete,
self-contained markdown system: copy its contents to your repo root and you
have everything, with no second file to apply on top and nothing pointing back
at the Creatrweb repo. The `ADAPTATION.md` in each folder is reference material
explaining why that context's files differ from the other's; it does not need
to travel with them.

**Q: Why is there a `general` context if it barely adds anything?**  
So that "no domain-specific needs" is a named, active choice rather than a
silent default. It does carry real specializations — an Irreversible Decisions
table covering URL structure, schema changes, OAuth provider configuration and
public API endpoints, plus a Pre-Write step requiring `docs/api.md` to be
updated when the public API contract changes.

**Q: Where do skills live?**  
Inside whichever context folder you installed, at `.claude/skills/<name>/SKILL.md`
with a byte-identical mirror at `.agents/skills/<name>/SKILL.md`, declared in
that context's `AGENTS.md` Section 9. `general/` ships five (`gallery-format`,
`socratic-depth`, `design-workflow`, `testing`, `memory-files`); `personal/`
ships those five plus `indieweb-specs`, `indieweb-principles`,
`posse-syndication`, and `security`. They're declared in `AGENTS.md` Section 9,
and the setup prompts also carry every skill body inline, so a prompt-only
install produces the same files.

**Q: How do the five Merge Protocol cases apply to my repo?**  
`LOOP-AGENTS.md` Section 0 classifies the target repo before touching
anything, and the agent must state which case applies at session start:

| Case | Your repo looks like | What happens |
|---|---|---|
| A | No markdown at all | `AGENTS.md` created verbatim, plus empty `MEMORY.md`/`DECISIONS.md`/`CONSTRAINTS.md` stubs |
| B | Only `README.md`/`CONTRIBUTING.md`/`CHANGELOG.md` | Those left untouched; `AGENTS.md` created alongside |
| C | One existing `AGENTS.md` with different rules | Never overwritten — the Creatrweb orchestrator block is appended to the end of your file, your rules take precedence, and any direct contradiction is flagged rather than silently resolved |
| D | A rich, differently-named doc network (`process.md`, `plan.md`, `tasks.md`) | Goal Extraction → Mapping → gallery proposal → your explicit confirmation, before anything moves |
| E | Already Creatrweb-lineage, but mature and large | Adopt, don't duplicate; follow the repo's existing archive conventions; register one-off files like `ALGORITHMS.md` rather than folding them in |

Cases D and E are both Irreversible Decisions under Rule 3 — the agent stops
and waits for you either way.

**Q: Why are there three files — AGENTS.md, LOOP-AGENTS.md, GRAPH-AGENTS.md?**  
Because rules and mechanics change at different rates and for different
reasons. `AGENTS.md` is the orchestrator: every tool reads it first, and it
holds everything true regardless of how the work is shaped — the Six Rules,
Brainstorm Mode, the Pre-Write Check, Core Constraints, skills, memory-file
ownership, the eval. `LOOP-AGENTS.md` holds single-service process: Merge
Protocol, the four-stage loop, the model roster, the Irreversible Decisions
table. `GRAPH-AGENTS.md` holds multi-service process and sits above the loop
rather than replacing it — each node still runs its own. `AGENTS.md` Section 0
routes between them at session start. If you're ever unsure where something
belongs: a rule goes in the orchestrator, a mechanic goes in a process file.

**Q: Do I always need GRAPH-AGENTS.md?**  
No. Install it only when more than one repo or deploy target is genuinely
coordinated. A single-service repo that carries it anyway is just noise the
agent has to read every session. If the answer is unclear — a monorepo with
independently deployed packages, say — that ambiguity is a Rule 1 question, and
the agent should ask rather than decide for you.

**Q: What's the difference between `general/` and `general_starter/`?**  
What they assume about your repo. The plain folder installs a clean system and
assumes you want it as written — right for a fresh or lightly-documented repo.
The `_starter` folder carries only what can't be reconstructed — the three
governance/process files, the two setup prompts, and the skills — plus
`START-HERE.md`, an adaptive install for a repo that already has agentic
markdown: it reads everything first, states each existing
file's original purpose in that file's own terms, classifies the repo against
the five Merge Protocol cases, and then creates only what's missing. Existing
files get kept, annotated, or extended — never overwritten. The same split
applies to `personal/` and `personal_starter/`. The skills, rules, and payload
are otherwise identical.

**Q: What happens if existing rules contradict the framework's?**  
Under a `_starter` install, the existing rules win by default — they encode
decisions someone actually made about that codebase — and the conflict is
surfaced for you to decide rather than resolved silently. The one exception is
an `AGENTS.md` that is empty or a bare placeholder heading; that counts as
absent. Anything with real content is Case C, which appends rather than
replaces.

**Q: I already have a `CLAUDE.md` full of rules. Will the install delete it?**  
It will rewrite it, but only after rescuing everything in it. The setup prompts
build a rule inventory first: every normative statement in `CLAUDE.md`,
`GEMINI.md`, `.cursorrules`, `copilot-instructions.md` and any existing
`AGENTS.md` is quoted with its source and assigned exactly one destination — a
behavioral rule to `AGENTS.md`, a process mechanic to `LOOP-AGENTS.md`, a
must-never to the Irreversible Decisions table, a version pin to
`CONSTRAINTS.md`, a taste preference to `DESIGN.md`, a past choice to
`DECISIONS.md`, a hard-won lesson to `MEMORY.md`. You approve that inventory
before anything is written. Only then do the entry points become pointers, and
the install verifies afterward that every inventoried rule landed somewhere.
Nothing is deleted that has not been rehomed.

**Q: What if a rule really is tool-specific?**  
It stays in that tool's file — the one documented exception — with a comment
saying why it can't generalize. The test is simple: if the rule would matter to
any other agent, it belongs in `AGENTS.md`. Most rules that look tool-specific
aren't; the Plan Mode gallery-suppression rule started life in `CLAUDE.md` and
turned out to apply to every tool with a plan mode.

**Q: Will a `_starter` install invent MEMORY.md or DESIGN.md entries?**  
No, and this is deliberate. Those files are created as headers only. An empty
`DESIGN.md` is a correct state; a fabricated one poisons every future gallery
by making guesses look like your stated taste.

**Q: Do I have to use the setup prompt at all?**  
No. Copying the context folder's contents into your repo root is a complete
install on its own. The prompt exists for two cases: you'd rather not copy
files by hand, or your repo already has documentation and you want the
five-case Merge Protocol applied so nothing gets overwritten.

**Q: Do I run the DOC-OVERHAUL prompt every session?**  
No. It's a one-time, idempotent install. Once `AGENTS.md` (or `GRAPH-AGENTS.md`) is in the repo, it handles per-session loading on its own.
Re-run the overhaul prompt only when your model roster changes or the repo's
documentation shape changes enough to warrant reclassification.

---

## The Gallery Protocol

**Q: Why isn't the gallery showing up when I ask for changes?** The gallery is suppressed by specific prompts. If you wrote "Change X to Y" or included exact pixel values, file names, or property names, the agent read that as a directive and executed. To get options, use an  
open prompt instead:

* "The terminal dialog feels cramped on mobile. What are some approaches?"  
* "I'm not happy with how Y looks. What would you try?"  
* "Before you change anything, show me options for Z."

**Q: The gallery options don't match my taste.**  
Populate DESIGN.md. Gallery options must be traceable to your specific References, Derived Identity, or Observed Taste entries, not to generic defaults. An empty DESIGN.md means the agent is guessing based on statistical patterns from other users, not yours.

**Q: What is the Reframe entry in a gallery?**  
It challenges the premise of the request itself, not a variation on your approach, but a question about whether the approach is the right one. If you asked for a nav redesign, the Reframe might ask whether the nav is the right solution to the navigation problem at all. You can ignore it, but it exists to surface directions you might not have considered.

**Q: Can I skip the gallery for a session?**  
You can suppress it by writing specific prompts (see above). If you want to work without it for a whole session, add a SESSION CONSTRAINTS item: \`Skip gallery protocol this session — execute on specific instructions.\` The eval prompt at session end will still flag missed opportunities, so DECISIONS.md stays accurate.

---

## Agent-Specific Issues

**Q: Gemini is ignoring AGENTS.md.**  
Gemini requires \`.gemini/settings.json\` to read the framework. Without it, Gemini uses its own defaults. Verify that the file exists at the project root and that it lists AGENTS.md in the context array. Also note that Gemini reads reference sections at session start but doesn't actively consult them during code generation — use a SESSION CONSTRAINTS block to promote critical rules into the active context.

**Q: Claude Code stopped following a rule mid-session.**  
Stop the session immediately:

* "Stop. Check AGENTS.md Rule \[N\] before proceeding."  
* "Wait… did you ask the Rule 1 question for this change?"

For persistent drift, start the next session with the full SESSION CONSTRAINTS block. Reference @CONSTRAINTS.md and @MEMORY.md explicitly in the opening prompt.

**Q: The agent edited AGENTS.md without my permission.**  
This is a safeguard violation. AGENTS.md is owned by the person, not the session. If AGENTS.md is non-empty when first read, the agent must never replace its contents. "Populate", "update", or "fill in" applied to a non-empty AGENTS.md means propose an append as a clearly marked diff, never a replacement. If this happens, restore the previous version from git and add an explicit CONSTRAINT: "Never modify AGENTS.md without explicit written instruction."

**Q: Replit auto-applied changes without gallery confirmation.**  
Replit in auto/build mode does not pause for gallery confirmation — this is expected behavior. Review DECISIONS.md at the end of every Replit session to see which conservative defaults were selected and override any that don't reflect your direction.

**Q: Two agents gave me conflicting recommendations across sessions.**  
The memory files exist to prevent this. Check DECISIONS.md for the prior decision and MEMORY.md for any confirmed lessons. If neither file records the relevant decision, the session that made the choice didn't log it — add it manually, and it will carry forward into all future sessions.

---

## The Personal (IndieWeb) Context

> Everything in this section applies only to repos installed from `personal/`.
> Under `general/`, none of these skills ship and none of these rules exist.

**Q: I don't know what POSSE means. Do I need to?**  
POSSE stands for Publish on Own Site, Syndicate Elsewhere. The short version: write everything on your own domain first, then share it to other platforms. This means you always own the original. Load \`posse-syndication\` for the full URL conventions and syndication rules.

**Q: Which IndieWeb spec should I implement first?**  
\`rel=me\` and microformats2. Both have zero server-side requirements and make everything else easier. Don't implement Webmention until you have a real use case for cross-site replies. Don't activate IndieAuth or Micropub until those features are directly needed.

**Q: How does the Creatrweb idea differ from the Indieweb?**  
The Creatrweb also shares the ideals of decentralization, content ownership, and the desire for alternatives to the “corporate web” that the Indieweb community holds at its core. However, the Creatrweb also understands the corporate realities of the modern internet: there is no such thing as a website that falls outside the grasp of big tech corporations. It also recognizes that human-tool collaboration can foster creativity, even when the tool is rooted in generative AI. However, ownership of identity rules has been integrated into [AGENTS.md](http://AGENTS.md) and other documentation, as these should be normalized components of the basic experience of owning content on the internet.

**Q: How does the Creatrweb idea approach accessibility?**  
I modeled the idea of the Creatrweb in part on my experiences with ableism and gatekeeping. Coming from the contexts of neurodivergence, physical disability, and chronic pain, I have often needed to exclude myself from many normal parts of life. At the same time, even when I have wanted to include myself, things have not always gone well. This is why I stand for accessibility beyond vague statements about what I believe accessibility to be. As someone who has dealt with access issues throughout my entire life, whether it be due to disability, socioeconomic status, or identity-based discrimination, accessibility is about acceptance as the norm, not just diversity for quotas. Accessibility is not an afterthought but rather the implicit focus that defines all that I do, including with this framework, starting with the acceptance that access to generative AI tools can ethically, morally, and authentically uphold creativity. 

**Q: Why does the agent stop and ask before I add a package?**  
New vendor dependencies are Irreversible Decisions. Once a service is woven into your project, you depend on its continued availability, pricing, and API stability. The mandatory question,  "The self-hosting alternative is X. Should I proceed?", ensures that the trade-off is named out loud before it becomes invisible infrastructure. The exact wording is in `AGENTS.md` Section 8.

---

## Memory and Session Continuity

**Q: How does the agent remember decisions across sessions?**  
Three files automatically carry context: MEMORY.md (confirmed durable lessons), DECISIONS.md (architectural choices and unresolved checkpoints), and CONSTRAINTS.md (binding constraints). A fourth, DESIGN.md, is read only when design work occurs. `AGENTS.md` Section 10 records who writes each file and which are read every session. Any
agent that reads these files at session start picks up the full project
history without being told explicitly.

**Q: What is an unresolved checkpoint?**  
A decision that needed to be made but couldn't be completed in the session — usually because the session ended before a question was answered. The agent logs these in DECISIONS.md and halts at the relevant point in the next session.

**Q: MEMORY.md is getting long.**  
Keep it under 150 lines. When near the limit, review it with the agent and move older entries to docs/memory-archive.md. Never delete entries without reviewing them — a "stale" lesson may still be relevant. Think of this as akin to the concept of memory vs storage (RAM vs SSD) wherein memory is meant to be short-term and immediately accessible, while storage is meant to be long-term but stored out of sight until you need it.

---

## AI Authorship and Ethics

**Q: Is AI-assisted code still "my" code?**  
Firstly, code is not truly owned. Code relies on dependencies to run (e.g., JavaScript on a website requires a web browser for interactivity), and code elements, such as functions, cannot (and should not) be subject to copyright. Subjecting these elements to copyright would be akin to allowing a single artist to copyright an art style and deeming it illegal for another artist to draw or paint in that style. Secondly, code is functional for software, akin to how words are functional for essays, and medium and canvas are functional for art. Functional building blocks are the backbone of any practice. Thus, while code can be bought and sold (as software), words can be sold as news articles, and media and canvases can be sold as art, it is unethical to disallow functional building blocks from being limited beyond reasonable bounds. Thirdly, the root of all practice is the novel idea. Personally, I believe that allowing an idea a chance to develop will always be preferable to not allowing it to be executed. Life is too short, and the world is too big for our ideas to fall to the wayside just because of a lack of skill, connections, or resources.

**Q: But isn’t AI unethical?**  
We need to understand this question from a broader perspective, rather than oversimplified ideas of ownership. Firstly, the technology is now available to non-technical people, enabling them to bring their vision to life. Some people, like myself, would see it as unethical to prioritize someone else’s discomfort (no matter how justified) over bringing a non-technical creative’s vision to life. Secondly, the global supply chain is notorious for unethical practices, and, more specifically, in the tech industry, unethical model training has occurred throughout the rise of social media, as highlighted in [this article](https://www.sciencedirect.com/science/article/abs/pii/S0736585325001030). But why the spotlight on generative AI? It is simply a matter of the times that we live in. It is extremely easy to scapegoat a technology, such as generative AI, as the global economic system runs in such opaque ways that true transparency is often fleeting. As a result, individuals tend to draw on what they know, and, in the present day, the idea that generative AI is unethical prevails, as the carceral public consciousness does not easily draw the line between AI corporations and AI technologies. At the same time, [as early as 2020](https://crcs.seas.harvard.edu/news/10-wonderful-examples-using-artificial-intelligence-ai-good), researchers have been using AI technologies for positive use cases, while [MIT](https://mitsloan.mit.edu/ideas-made-to-matter/machine-learning-and-generative-ai-what-are-they-good-for) emphasizes that generative AI is best used for “dealing with everyday language or common images” as it is difficult for other AI techniques, such as traditional machine learning, to meaningfully work with unstructured data (data that isn’t formatted in a tabular format). For instance, a notable use case of generative AI is [generating synthetic data](https://pmc.ncbi.nlm.nih.gov/articles/PMC12614387/) to accelerate breast cancer research, leading to improved models that translate into more accurate breast cancer detection technologies. In short, while AI companies should absolutely train AI models, we need not forget that social media companies have been unethically training their own algorithms for decades. Also, while AI companies should find ways to make training more environmentally conscious and resource-efficient, this is a matter of what AI companies believe they can get away with, rather than an inherent flaw in the ethics of generative AI and other AI technologies.

**Q: What is the proper way to attribute AI-generated content?**  
There is no widely accepted standard for attributing AI-generated content as of April 2026\. However, explicitly citing a specific chatbot may be a good place to start. If AI-generated content is created using something that you wrote as source material, it may be best to state something of this nature. For instance, I explicitly state “Assisted by…” in the tagline of the FAQ as Claude Sonnet via Perplexity utilized my stated philosophy as context to generate many parts of this document. While not usually demanded, doing this helps to normalize how AI-generated content is perceived and may also help to specify where human creativity and ingenuity is present in a given work. This also helps us to get an accurate inventory of how we are using generative AI technologies and outputs, hopefully ensuring that we are leveraging generative AI effectively while duly developing our ideas, creativity, and ingenuity, rather than replacing this crucial aspect of human creation.