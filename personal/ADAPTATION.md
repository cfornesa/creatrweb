# ADAPTATION.md — personal

> **Reference only — this file does not ship.** The differences it describes
> are already baked into the `personal` payload's `AGENTS.md`, `GRAPH-AGENTS.md`,
> and setup prompts. It exists so that anyone maintaining this context can see
> *why* those files differ from the other context, and so a new context can be
> derived the same way. Do not copy it into a target repo, and do not treat it
> as a delta to be applied at install time — that work is already done.

**Use when:** any repo touching the personal IndieWeb site (chris.com.ph) or
its satellites — e.g., `react-resume`, `node-portfolio`, or any project that
implements rel=me, microformats2, Webmention, IndieAuth, Micropub, WebSub, or
POSSE syndication.

## Additional skills auto-loaded (on top of the base set)

| Skill | Trigger |
|---|---|
| `indieweb-specs` | Implementing or modifying rel=me, microformats2, Webmention, IndieAuth, Micropub, WebSub |
| `indieweb-principles` | A decision touches ownership, portability, or longevity |
| `posse-syndication` | Finalizing URL structure, syndication targets, or export endpoints |
| `security` | Writing any Webmention, IndieAuth, Micropub, or media upload handler |

## Rule 3 specialization (Irreversible Decisions)

In addition to root's Section 5 table, the following require explicit sign-off
in a `personal`-adapted repo:

- URL structure changes
- `rel=me` links
- Auth endpoints (IndieAuth, Micropub token endpoints)
- Syndication targets
- Vendor dependencies

## Pre-Write Check specialization (root Section 7, step 2)

If a write renders microformats, it must be a Server Component — no
`use client`.

## Core Constraints addition (root Section 11)

- Webmention sending is human-initiated or explicitly scheduled only. Never
  auto-send.

## Rule 5 specialization (public interfaces never break silently)

Specialized beyond root's generic route/endpoint interpretation: `GET
export.json`, `GET feed.xml`, and `GET feed.json` must remain functional at
all times. POSSE syndication targets and canonical URL structure are treated
with the same never-break standard as any other public route — a change to
slug structure or feed format requires a permanent-redirect plan, per the
`posse-syndication` skill's Slug Stability Rule, before it ships.

## Case D/E extension-file expectations

Repos under this adaptation may accumulate IndieWeb-specific documentation not
covered by the standard six files — a Webmention endpoint spec, a syndication
target list, or a microformats2 compliance checklist. Register these in the
repo's own `AGENTS.md` Section 6 mapping table under Case E, citing
`webmention.rocks` test results or the relevant IndieWeb spec as the
acceptance-criteria source of truth where applicable.

## How this context was derived

Root's Loop structure, Merge Protocol, and Irreversible Decisions table apply
unchanged — this adaptation only adds the IndieWeb-specific skills and
Rule 5 specialization above. A `personal`-adapted repo that also needs
multi-service Graph handling (e.g., splitting the resume site's backend and
frontend into separate repos) uses `GRAPH-AGENTS.md` at the coordination
layer with this adaptation applied per node.
