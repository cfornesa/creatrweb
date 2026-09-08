# ADAPTATION.md — general

> **Reference only — this file does not ship.** The differences it describes
> are already baked into the `general` payload's `AGENTS.md`, `GRAPH-AGENTS.md`,
> and setup prompts. It exists so that anyone maintaining this context can see
> *why* those files differ from the other context, and so a new context can be
> derived the same way. Do not copy it into a target repo, and do not treat it
> as a delta to be applied at install time — that work is already done.

**Use when:** a standalone project with no domain-specific requirements — no
IndieWeb obligations, no specialized handler security concerns. This is the
near-"undecorated" adaptation: root as-is, plus the two conventional
web-application specializations below.

## Additional skills auto-loaded

None. Base skill set only (`gallery-format`, `socratic-depth`,
`design-workflow`, `testing`, `memory-files`) as defined at root.

## Rule 3 specialization (Irreversible Decisions)

In addition to root's Section 5 table, the following require explicit sign-off
in a `general`-adapted repo:

- URL structure changes
- Database schema changes
- OAuth provider configuration
- Public API endpoints
- Vendor dependencies

## Pre-Write Check specialization (root Section 7, step 2)

Generic interpretation of "public interface contract": if a write modifies the
public API contract, update `docs/api.md` before writing.

## Rule 5 specialization (public interfaces never break silently)

Generic interpretation: any live route, API endpoint, or exported function
signature already in production use requires a permanent-redirect or
backward-compatible shim plan, confirmed before deletion or breaking change.
No domain-specific endpoints to enumerate.

## Case D/E extension-file expectations

None beyond what root's Goal Extraction already handles generically. If a
project under this adaptation develops its own recurring extension file
(e.g., an `ALGORITHMS.md` for a specific translation project), register it in
that repo's own `AGENTS.md` Section 6 mapping table per root's Case E
handling — it does not get promoted here unless it turns out to be common
across multiple `general`-adapted repos, at which point it's a candidate for
graduating into this file.

## How this context was derived

This adaptation exists mainly to make explicit that "no adaptation" is itself
a valid, named choice — so that a person picking a profile always makes an
active decision rather than defaulting silently. If a project has zero
domain-specific needs, cite this adaptation and proceed with root unchanged.
