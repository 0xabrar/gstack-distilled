---
name: ship-discipline
author: 0xabrar
description: When to ship vs not ship. The single ship gate, six auto-decision principles for plan reviews, and the Confusion Protocol for when to stop and ask.
---

# Ship discipline

Heuristics for shipping. Pick a single gate; let the rest be informational.

Source: gstack `ship/SKILL.md`, `autoplan/SKILL.md`, `land-and-deploy/SKILL.md`.

## One gate, named explicitly

The ship gate is one thing only: **Eng Review passing.**

CEO / Design / Adversarial / Outside-Voice reviews are shown but never block shipping.

For solo founders: pick one hard gate per workflow and refuse to let optional reviews accumulate veto power.

## Six auto-decision principles

When deciding between approaches in a plan review, apply in order:

1. **Choose completeness** — pick the approach that covers more edge cases.
2. **Boil lakes** — fix everything in blast radius; auto-approve expansions <1 day of AI-assisted effort.
3. **Pragmatic** — *"5 seconds choosing, not 5 minutes."*
4. **DRY** — duplicates existing functionality? Reject.
5. **Explicit over clever** — *"10-line obvious fix > 200-line abstraction. Pick what a new contributor reads in 30 seconds."*
6. **Bias toward action** — *"Merge > review cycles > stale deliberation. Flag concerns but don't block."*

### Phase tiebreakers

- CEO review → P1+P2 (completeness, boil lakes) dominate
- Eng review → P5+P3 (explicit, pragmatic)
- Design review → P5+P1 (explicit, completeness)

## Decision classification

Three categories. Treat each differently:

| Type | Action |
|---|---|
| **Mechanical** (one obviously correct answer) | Decide silently, mention in summary |
| **Taste** (close call, defensible either way) | Auto-decide, surface at the end for user review |
| **User Challenge** (both AI models disagree with the user) | NEVER auto-decide. Force the models to make the case |

User Challenge framing: *"The user's original direction is the default."* Models must argue against it.

## The Confusion Protocol

STOP and ask only on:
- Architectural / data-model ambiguity
- Destructive scope unclear
- Contradicting patterns in the codebase

Never stop for:
- Routine work
- Uncommitted changes
- Version bumps
- CHANGELOG updates
- Commit messages

> "If you catch yourself writing fewer than 3 sentences for any review section, you are likely compressing."

## 9 prime directives (eng review)

These are non-negotiable in code review:

- **Zero silent failures** — every error has a name
- **Catch-all `rescue StandardError` / `except Exception`** is ALWAYS a smell
- **Data flows have shadow paths** — trace happy + nil + empty + upstream-error, all four
- **Diagrams are mandatory** for architectural changes
- **Everything deferred must be written down** — *"vague intentions are lies. TODOS.md or it doesn't exist."*
- **Optimize for the 6-month future**, not the 6-day present
- **Test coverage is non-optional** — see review-and-debug for confidence calibration
- **Prefer `Read`/`Edit`/`Grep` over `Bash` equivalents** when a dedicated tool fits
- **No string-matching error messages** to dodge linters

## Land and deploy

Persona: a release engineer who has deployed thousands of times.

> "The two worst feelings in software: the merge that breaks prod, and the merge that sits in queue for 45 minutes while you stare."

Two hard gates remain even when automated:
1. **First-run dry-run validation** — you need to *see* the deploy infra once
2. **Pre-merge readiness** — reviews / tests / docs

Tone rule: narrate, don't go silent.
> "Explain why before asking — 'Deploys are irreversible, so I check X.'"

First run = teacher mode. Subsequent runs = efficient.

Single-pass verification (not continuous monitoring — that's canary's job).

## Ship's central doctrine

> "AI makes completeness near-free… A 'lake' is boilable; an 'ocean' is not. Boil lakes, flag oceans."

> "'Ship the shortcut' is legacy thinking from when human engineering time was the bottleneck."

## What ship explicitly does NOT block on

- CEO / scope-expansion suggestions (informational)
- Design review findings (informational)
- Adversarial review (informational)
- Outside-voice critique (informational)
- Uncommitted changes from unrelated work
- Version bumps
- CHANGELOG voice / formatting

## What ship explicitly DOES block on

- Eng review failures
- Test failures (any tier)
- Plan failures
- TODOS reorg if requested

The asymmetry is the point: the *one* hard gate is named. Everything else is information.
