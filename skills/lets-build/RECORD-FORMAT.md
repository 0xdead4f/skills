# Record Format

Append-only history of what actually happened, in `docs/plan/records/`. Numbered: `0001-slug.md`, `0002-slug.md` (scan for the highest, increment).

One record per work session or phase — whenever code lands.

```md
---
date: 2026-08-12
components: [core/scheduler, cli]
---

# {What happened, one line}

## Built
{What was created or changed, by component. Short.}

## Deviations
{Where reality disagreed with the plans, or "none". Details live in each
plan's Deviations section — reference, don't duplicate.}

## Verified
{How: tests run, user checked, or "not yet".}

## Next
{The single most useful thing for whoever picks this up.}
```

Records never get edited after the fact — corrections go in a new record.
