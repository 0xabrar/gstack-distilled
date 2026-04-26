---
name: ux-bar
author: 0xabrar
description: UX quality bar — Krug's three laws of usability, the eight DevEx first principles, time-to-hello-world tiers, the Goodwill Reservoir, the Pit of Success.
---

# UX bar

What "good" feels like for users. Use when reviewing flows, onboarding, error messages, and dev experience.

Source: gstack `design-review/SKILL.md`, `devex-review/SKILL.md`, `qa/SKILL.md`.

## Krug's three laws of usability

1. **Don't make me think** — self-evident > self-explanatory > requires explanation
2. **Clicks don't matter, thinking does** — three mindless clicks beat one puzzle
3. **Omit, then omit again** — happy talk and instructions must die

Supporting doctrine:
- *"Users scan, they don't read… designing billboards going by at 60 mph."*
- *"Users satisfice — pick first reasonable, not best."*
- *"Clarity trumps consistency."*

## The Goodwill Reservoir

Every user starts with a finite reservoir of goodwill. Every friction point depletes it. When it hits zero, they leave.

Friction points that drain it:
- Error messages without fixes
- Required fields with no explanation
- "Click here to continue" buttons that lead to dead ends
- Slow loads
- Forms that lose state on error

Goodwill restorers:
- Errors that include the fix
- Defaults that just work
- Speed
- Surprise-and-delight moments

## Pit of Success

> "Make the right thing easy, the wrong thing hard."

If users keep doing the wrong thing, the design is wrong, not the users.

## Eight DevEx first principles

For tools where your users are themselves builders:

1. **Zero friction at T0** — first-run should require nothing the user doesn't already have
2. **Decide for me, let me override** — opinionated defaults, escape hatches everywhere
3. **Every error = problem + cause + fix** — never just "something went wrong"
4. **Speed is a feature** — latency in dev tools compounds
5. **Show, don't explain** — examples beat docs
6. **Composability over completeness** — a sharp tool you combine beats a Swiss Army knife
7. **Honest about state** — if the tool is in a weird mode, say so
8. **Chef-for-chefs bar** — *"your users build products for a living, the bar is higher"*

## Time-to-hello-world (TTHW) tiers

| Time | Tier | What it means |
|---|---|---|
| <2 min | **Champion** | Best-in-class. Users will recommend. |
| 2-5 min | **Competitive** | Acceptable. Most successful tools live here. |
| 5-10 min | **Needs Work** | Friction is hurting conversion. |
| **>10 min** | **Red Flag** | 50-70% abandonment. Fix this before anything else. |

If you can't measure TTHW for your product, you're flying blind on conversion.

## The boomerang (DevEx review)

At plan stage, score predicted N/10 on each UX dimension.

After ship, do a live audit and score actual.

**Flag any dimension where `live < plan - 2`.**

This forces honesty about the gap between what you intended and what you shipped.

## First Impression rule

When designing for review:

> "A designer doesn't hedge, they react. The first impression is gut-reaction first."

Don't ask reviewers what they think — watch them load the page and listen to the first thing they say.

## Trunk test

For any nav: if a user lands on a sub-page from search, can they figure out where they are and where to go in 2 seconds?

If not, the nav is broken.

## Errors are for AI agents now

> "Every error message must be actionable. The agent should be able to read the error and know what to do next without human intervention."

In an AI-first world, error messages aren't just for humans — they're inputs to a fix loop. "Something went wrong" wastes both human and agent time.

## Reproduce or it didn't happen (QA)

> "Repro is everything. Every issue needs a screenshot. No exceptions."

> "Depth over breadth — 5-10 well-documented issues > 20 vague descriptions."

> "Test like a user. Never read source code."

> "Never refuse to use the browser." — even backend-only diffs ship through the browser

## Three QA tiers

| Tier | Time | Scope |
|---|---|---|
| **Quick** | ~30s | Smoke test, top 5 nav |
| **Full** | 5-15 min | 5-10 well-evidenced issues |
| **Exhaustive** | Open-ended | Cosmetic + edge cases |

Triage tier dictates fix scope:
- Quick fixes critical + high
- Standard adds medium
- Exhaustive does cosmetic too

## Common UX anti-patterns

- "Click to continue" with no preview of what's next
- Errors without fixes
- Required fields with no inline validation
- Forms that clear on error
- Modals that block primary actions
- Onboarding that requires completing X steps before showing value
- Default opt-in for things that should be opt-out (and vice versa)
