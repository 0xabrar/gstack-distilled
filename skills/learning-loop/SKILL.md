---
name: learning-loop
author: 0xabrar
description: Compound knowledge across sessions. Plan-tune dual-track psychographic profile (declared vs behavior), retro philosophy that demotes LOC, the keep-or-toss test for learnings.
---

# Learning loop

How to compound knowledge across sessions, projects, and time.

Source: gstack `plan-tune/SKILL.md`, `retro/SKILL.md`, `learn/SKILL.md`, `SKILL.md`.

## The dual-track psychographic profile

Track two things separately:

- **Declared profile** — what you say you want
- **Inferred profile** — what your behavior actually shows

Five dimensions, each 0.0–1.0:

- `scope_appetite`
- `risk_tolerance`
- `detail_preference`
- `autonomy`
- `architecture_care`

Gap-band lexicon:
- <0.1 → **close**
- 0.1–0.3 → **drift**
- \>0.3 → **mismatch** — *"your behavior disagrees with your self-description"*

### Iron rule

The user decides whether declared is wrong or behavior is wrong. **Never auto-update declared from observed gap.**

> "One-way doors override never-ask" — destructive / architectural / security questions ALWAYS ask, regardless of preferences.

### Calibration gate

20 events + 3 skills + 8 question-ids + 7 days before showing inferred profile. Don't surface a "vibe profile" until you have signal.

## Retro philosophy

> "Features shipped leads — what users got. Raw LOC is demoted to context because AI inflates it; ten lines of a good fix is not less shipping than ten thousand lines of scaffold."

### Session classification

- 45-min gap = session boundary
- **Deep session**: 50+ min
- **Medium**: 20-50 min
- **Micro**: <20 min ("fire-and-forget")

### Fix-ratio flag

\>50% fix commits = "ship fast, fix fast" pattern signaling review gaps.

### Focus score

% of commits in single most-changed top-level directory. Low score = scattered work.

### Retro tone doctrine

> "Praise should feel like something you'd actually say in a 1:1 — specific, earned, genuine. Growth suggestions should feel like investment advice — 'this is worth your time because…' not 'you failed at…'"

"3 Habits for Next Week" — each must be **<5 minutes to adopt.**

Never compare teammates negatively.

## Six learning types

When capturing a learning, label it:

1. `pattern` — reusable approach
2. `pitfall` — don't-do
3. `preference` — user-stated
4. `architecture` — structural
5. `tool` — tool-specific gotcha
6. `operational` — process / workflow

## Four learning sources

1. `observed` — saw it directly
2. `user-stated` — user said it
3. `inferred` — pattern-matched from behavior
4. `cross-model` — both Claude and Codex agree

## Confidence honesty

| Source | Confidence |
|---|---|
| Observed and verified | 8-9 |
| Explicit user statement | 10 |
| Inference | 4-5 |

Don't inflate. A speculation logged at 9 poisons future sessions.

## The keep-or-toss test

> "Would this insight save time in a future session? Would knowing this save 5+ minutes? If yes, log it."

Don't log:
- Obvious things
- One-time transient errors (network blips, rate limits)
- Things you'll remember anyway

Append-only with latest-wins. Staleness detection via file-existence checks. Conflict detection: same key, different insight = manual review.

## Operational self-improvement loop

End every session by reflecting:

- Did you take a wrong approach and have to backtrack?
- Did you discover a project-specific quirk (build order, env vars, timing, auth)?

> "A good test: would knowing this save 5+ minutes in a future session? If yes, log it."

Future sessions surface the learnings automatically.

## Memory hygiene

Three privacy tiers, opt-in by default:

- **Full** — everything allowlisted
- **Artifacts-only** — plans, designs, retros, learnings (skip behavioral data like timelines)
- **Off**

What deliberately doesn't sync:
- Question-log
- Question-preference

Why: *"Per-machine UX state. Behavioral data should not travel; durable artifacts (decisions, designs, learnings) should."*

## Per-remote trust triad

For consultants juggling multiple clients:

- `read-write` — full sync both ways
- `read-only` — pull learnings, never push
- `deny` — totally isolated

Designed for *"freelance dev working on Client A in the morning and Client B in the afternoon"* — Client A's insights must not bleed into the brain Client B searches.

## Ship velocity, not LOC

> "Features shipped leads. LOC is demoted to context because AI inflates it."

When measuring weekly progress:
- ✅ "Shipped X features, fixed Y bugs"
- ❌ "Wrote 10K lines"

The bug fix that's 10 lines beats the scaffold that's 10,000.

## Closed-loop principle

Every workflow should generate data the next workflow can consume.

- `/ship` → ship log
- ship log → `/retro` velocity trends
- `/retro` → next sprint priorities
- next sprint → `/ship` again

If a workflow doesn't feed the next one, it's a dead end.

## Verdict-style retros

Don't summarize. Lead with a verdict:

- ✅ "We finally killed the staging-env flake. Shipped 3 features. Took 2 detours we should not have taken."
- ❌ "This week we worked on..."

A retro that doesn't take a position is a status update with extra steps.
