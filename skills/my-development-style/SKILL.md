---
name: my-development-style
description: Plan-tree driven development workflow. Use when starting a new project or feature, breaking an app into components, implementing planned work, or when the user asks what is built, what the status is, or has lost track of the codebase.
---

# Development

Every component that exists in code exists **first** as a plan the user has reviewed. The plan tree is the single map of what the app is, what exists, and what's next. Never invent components silently.

All planning artifacts live in ONE folder — `docs/plan/` — never anywhere else:

```
docs/plan/
├── ABSTRACTION.md    ← the user's mental model, written down
├── CONTEXT.md        ← domain glossary (domain-modeling skill)
├── adr/              ← decision records (domain-modeling skill)
├── MASTER.md         ← component tree + build order
├── components/       ← one PLAN.md per component; nesting = sub-components
├── prototypes/       ← sketches, demos
└── records/          ← append-only build records, numbered
```

If `docs/plan/` exists, read `MASTER.md` before anything else. The `domain-modeling`, `prototype`, and `handoff` skills default to repo-root paths — here the one-folder rule wins: glossary → `docs/plan/CONTEXT.md`, ADRs → `docs/plan/adr/`, sketches and demos → `docs/plan/prototypes/`, handoffs → `docs/plan/records/`.

## Stages

New work runs 1→5; otherwise jump to the stage the request belongs to. Announce the stage.

1. **Abstraction** — run a `grilling` session; write nothing until the frontier is empty. Then write ABSTRACTION.md ([format](./ABSTRACTION-FORMAT.md)) and get the user's sign-off. Any later decision that changes it updates it the same session.
2. **Sketch** — agree what it looks like with ASCII wireframes ([conventions](./SKETCH.md)); questions a sketch can't settle → the `prototype` skill. Link the winner from ABSTRACTION.md.
3. **Model** — pin vocabulary with `domain-modeling`; use `codebase-design` language (module, interface, seam, depth) for all structure talk.
4. **Decompose** — propose the tree as component names + one-liners first; agree the shape, **then** plan one component at a time (short grill → draft PLAN.md → user reviews → `agreed`). Never bulk-generate plans. Split into sub-components lazily — only when a component is about to be built and won't fit on one page. Formats: [PLAN-FORMAT.md](./PLAN-FORMAT.md).
5. **Build** — per component: read its plan (+ parent + MASTER) → status `building` → code only inside its `owns:` paths → status `built`, `verified` once checked → append a [record](./RECORD-FORMAT.md). Anything outside `owns:` or the tree: **stop, surface, plan it first.** Divergence goes in the plan's Deviations section, never silently absorbed.

## Status & audit

- **Status**: read each plan's frontmatter, render the tree with statuses. Frontmatter is the only source of truth.
- **Audit**: map every source file against all `owns:` globs. Unowned files are **orphans** — the "unknown component" smell. Report each; the user adopts, plans, or deletes it.
