# ABSTRACTION.md Format

The user's mental model written down — every later plan is checked against it. One page max.

```md
# {Product Name}

## What it is
{One paragraph: what exists when this is done, and for whom.}

## How it is used
{2–5 numbered walkthroughs: "user opens X, types Y, sees Z."
CLI → actual commands. Library → calling code. Scenarios, not adjectives.}

## How it looks
{Link to the winning sketch in prototypes/ + one sentence of intent.
Headless → the shape of the API/output instead.}

## How it works
{Runtime shape, the core data's path from input to output, and the 3–6 key
moving parts by name — these names seed the component tree.}

## Not in scope
{Explicit no-s. This is what stops scope drift during build.}
```

Rules:

- **The user's words win.** This translates their head, not your architecture taste. Fuzzy terms get sharpened with them (domain-modeling), not replaced.
- **Sign-off gate.** No decomposition until the user agrees this is their abstraction.
- **It stays alive.** A decision that changes the abstraction updates this file the same session.
