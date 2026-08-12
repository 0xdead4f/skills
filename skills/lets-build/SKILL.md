---
name: lets-build
description: Plan-tree driven development workflow. Use when starting a new project or feature, breaking an app into components, implementing planned work, or when the user asks what is built, what the status is, or has lost track of the codebase.
---

# Let's Build

Every component that exists in code exists **first** as a plan the user has reviewed. The plan tree is the single map of what the app is, what exists, and what's next. Never invent components silently.

All planning artifacts live in ONE folder — `docs/plan/` — never anywhere else:

```
docs/plan/
├── ABSTRACTION.md    ← the user's mental model, written down
├── CONTEXT.md        ← domain glossary (domain-modeling skill)
├── adr/              ← decision records (domain-modeling skill)
├── MASTER.md         ← component tree + build order
├── components/       ← one PLAN.md per component; nesting = sub-components
├── prototypes/       ← sketches
└── records/          ← append-only build records, numbered
```

If `docs/plan/` exists, read `MASTER.md` before anything else. The `domain-modeling` and `handoff` skills default to repo-root paths — here the one-folder rule wins: glossary → `docs/plan/CONTEXT.md`, ADRs → `docs/plan/adr/`, handoffs → `docs/plan/records/`.

## How every phase runs

A phase is a brainstorm with the user, never a generation task. The loop is: **propose → user reacts → refine → refine again** — as many rounds as it takes. A phase is done only when the user explicitly approves its artifact; only then move to the next phase. Never run two phases in one pass, and never advance past an unreviewed artifact.

## Phases

New work runs 1→5; otherwise jump to the phase the request belongs to. Announce the phase.

1. **Abstraction** — run a `grilling` session; write nothing until the frontier is empty. Then draft ABSTRACTION.md ([format](./ABSTRACTION-FORMAT.md)) and refine it with the user. Any later decision that changes it updates it the same session.
2. **Model** — pin vocabulary with `domain-modeling` (CONTEXT.md, ADRs); use `codebase-design` language (module, interface, seam, depth) for all structure talk from here on.
3. **Sketch** — agree what it looks like with ASCII wireframes ([conventions](./SKETCH.md)): 2–3 structurally different options, refined with the user until one wins. Link the winner from ABSTRACTION.md.
4. **Decompose** — propose the tree as component names + one-liners first; refine the shape with the user, **then** plan one component at a time (short grill → draft PLAN.md → refine → user approves → `agreed`). Never bulk-generate plans. Split into sub-components lazily — only when a component is about to be built and won't fit on one page. Formats: [PLAN-FORMAT.md](./PLAN-FORMAT.md).
5. **Build** — per component: read its plan (+ parent + MASTER) → status `building` → code only inside its `owns:` paths → status `built`, `verified` once the user has reviewed the result → append a [record](./RECORD-FORMAT.md). Anything outside `owns:` or the tree: **stop, surface, plan it first.** Divergence goes in the plan's Deviations section, never silently absorbed.

## Status & audit

- **Status**: read each plan's frontmatter, render the tree with statuses. Frontmatter is the only source of truth.
- **Audit**: map every source file against all `owns:` globs. Unowned files are **orphans** — the "unknown component" smell. Report each; the user adopts, plans, or deletes it.
