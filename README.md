# skills

Personal skill set for plan-tree driven development. The core problem it solves: **losing custody** of what the AI builds — unknown components, plans that live only in the AI's head.

## Install

### Claude Code

```
/plugin marketplace add 0xdead4f/skills
/plugin install dev-skills@0xdead4f
```

### Codex, and other agents

```sh
npx skills@latest add 0xdead4f/skills
```

Add `-s <name>` to pick specific skills.

## Skills

| Skill | What it does |
| --- | --- |
| `lets-build` | The workflow: Abstraction → Model → Sketch → Decompose → Build. Every phase is brainstormed and refined with the human until approved. One `docs/plan/` tree per project, one PLAN.md per component, custody rules, orphan audit. |
| `grilling` / `grill-me` | Relentless interview to pull the idea out of your head. |
| `domain-modeling` | CONTEXT.md glossary + ADRs. |
| `codebase-design` | Module / interface / seam / depth vocabulary. |
| `prototype` | Throwaway UI variants and logic demos that answer one question. |
| `handoff` | Compact a session into a doc the next agent can pick up. |
| `skills-best-practices` | Author new skills per the agentskills.io spec. |

## The workflow

Every phase: **propose → human reviews → refine → refine → approved**, then the next phase.

```
lets-build ── docs/plan/ tree in each project + custody rules
 ├─ 1. Abstraction  → grilling          (pull the idea out of your head,
 │                                       write ABSTRACTION.md)
 ├─ 2. Model        → domain-modeling   (CONTEXT.md glossary, ADRs)
 │                    codebase-design   (module/interface/seam language)
 ├─ 3. Sketch                           (ASCII wireframes, 2–3 options)
 ├─ 4. Decompose                        (MASTER.md + one PLAN.md per
 │                                       component, agreed one by one)
 └─ 5. Build        → handoff           (custody loop, records/, status,
                                         orphan audit)
```

Everything a project accumulates lives in one folder: `docs/plan/`.

## Credits

`grilling`, `grill-me`, `domain-modeling`, `codebase-design`, `prototype`, and `handoff` are from [mattpocock/skills](https://github.com/mattpocock/skills) (MIT). `skills-best-practices` is from [mgechev/skills-best-practices](https://github.com/mgechev/skills-best-practices).
