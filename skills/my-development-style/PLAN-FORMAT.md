# Plan Formats

One `MASTER.md`, one `PLAN.md` per component under `components/`. The directory nesting IS the tree.

## MASTER.md

```md
# {Product} — Master Plan

{One-line pitch.} → [ABSTRACTION.md](./ABSTRACTION.md) · [CONTEXT.md](./CONTEXT.md)

## Component tree
- [cli](./components/cli/PLAN.md) — parses commands, dispatches to core
- [core](./components/core/PLAN.md) — owns domain logic and state
  - [scheduler](./components/core/scheduler/PLAN.md) — decides what runs when

## Build order
1. **Phase 1 — walking skeleton**: core (minimal), cli (one command)
2. **Phase 2**: ...
```

Links + one-liners only. No statuses (they live in plan frontmatter), no detail (that's the plan's job). Each phase should leave the app runnable.

## PLAN.md

```md
---
component: core/scheduler
status: draft            # draft → agreed → building → built → verified
owns:
  - src/core/scheduler/**
depends-on: [core, storage]
---

# Scheduler

## Purpose
{One paragraph. Deletion test: if this vanished, what complexity reappears where?}

## Interface
{What callers see — entry points, invariants, error modes. Codebase-design
vocabulary: small interface, deep implementation.}

## Behaviour
{The states, rules, and edge cases this component owns. Checkable bullets.}

## Decisions
{Local decisions + one-line why. Hard-to-reverse ones graduate to adr/.}

## Deviations
{Append-only during build: date + what reality forced + what changed.}
```

Rules:

- **One page per plan.** Doesn't fit? Split into sub-components, don't write more.
- **`status`**: `draft` (unreviewed) → `agreed` (user signed off — only now buildable) → `building` → `built` → `verified`. Moves forward only, except by explicit user decision logged in Deviations.
- **`owns`**: every source file in the repo matches exactly one component's globs — this is what makes the audit possible. Parent globs shrink when a child splits out.
- **A plan is a contract, not a diary.** Progress notes belong in records.
