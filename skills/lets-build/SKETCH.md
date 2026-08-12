# Sketch

ASCII wireframes in a markdown file — the cheapest way to agree what something looks like before code exists. Works for web UI, TUI, and CLI output alike.

1. **One file per surface**: `docs/plan/prototypes/sketch-{name}.md`. State the question at the top.
2. **Draw 2–3 structurally different options** — different layout, different information hierarchy, different primary affordance. Not the same boxes rearranged.
3. **Iterate.** The user reacts ("header from A, sidebar from B"), you redraw. Keep losers under `## Rejected` with one line on why — that's the design history.
4. **Mark the winner** and link it from ABSTRACTION.md's "How it looks".

## Drawing conventions

Box-drawing characters, every region labelled, interactions annotated beside the frame:

```
┌──────────────────────────────────────────┐
│ ▌app-name          [search…]      (@me) │  ← top bar: always visible
├──────────┬───────────────────────────────┤
│ nav      │  Today                        │
│  ● Inbox │  ┌─────────────────────────┐  │
│  ○ Done  │  │ task title        [btn] │  │  ← one card per task,
│          │  │ meta · meta             │  │    click opens detail
│          │  └─────────────────────────┘  │
└──────────┴───────────────────────────────┘
```

- Real(ish) content in the boxes, not lorem — content decisions are layout decisions.
- One state per frame; a second state (empty, error, expanded) gets a second frame.
- CLI: show the literal command and its output block instead of boxes.
