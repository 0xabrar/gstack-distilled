---
name: review-and-debug
author: 0xabrar
description: Code review, debugging, and incident discipline. Confidence calibration, root-cause iron law, alert-on-changes rule, the pre-existing blame protocol.
---

# Review and debug

How to review code, hunt bugs, and verify fixes without creating noise or whack-a-mole loops.

Source: gstack `review/SKILL.md`, `investigate/SKILL.md`, `canary/SKILL.md`, `CLAUDE.md`.

## Investigate's Iron Law

> "NO FIXES WITHOUT ROOT CAUSE INVESTIGATION FIRST. Fixing symptoms creates whack-a-mole debugging. Every fix that doesn't address root cause makes the next bug harder to find."

Four phases, in order:

1. **Investigate** — read the data flow before guessing
2. **Analyze** — what's the actual cause vs the symptom
3. **Hypothesize** — name the hypothesis explicitly
4. **Implement** — only after the first three

## The 3-strike rule

3 failed hypotheses → STOP.

> "This may be an architectural issue rather than a simple bug."

## Recurring-bug heuristic

> "Recurring bugs in the same files are an architectural smell, not a coincidence."

If the same file is on its third bug fix, the next move is a refactor, not another patch.

## Hard rules for fixes

- Never apply a fix you can't verify
- Never say "this should fix it"
- Regression test must fail without the fix and pass with it
- \>5 files touched → blast-radius gate (slow down, get a second look)

### Red flags to slow down

- *"Quick fix for now"* — there is no "for now"
- Proposing a fix before tracing data flow — you're guessing
- Each fix reveals a new problem elsewhere — wrong layer, not wrong code

## Confidence calibration in reviews

Every finding rated 1-10:

- **Below 7** → caveat or suppress
- **1-2** → only report if severity is P0
- **8+** → call out clearly

Stop reporting noise as if it equals bugs.

## Fix-first, not read-only

Reviews auto-fix:
- Dead code
- N+1 queries
- Stale comments

Reviews ask on:
- Architecture changes
- Tradeoffs

Reviews don't report below confidence 7 unless P0.

## Search-before-recommending

Before suggesting a pattern, verify it's still current best practice. Don't recommend yesterday's wisdom.

## Order of operations in review

Critical-pass categories first:

1. SQL / data safety
2. Race conditions
3. LLM trust boundary
4. Shell injection
5. **Enum completeness** — the one category where within-diff-only review is insufficient. Grep siblings, read consumers.

Then informational findings.

## Pre-existing blame protocol

> "'Pre-existing' without receipts is a lazy claim. Prove it or don't say it."

When an E2E test fails, never claim "not related to our changes" without proving it.

Required: run the same test on `main`.
- If it passes on main but fails on branch → it IS your change
- If it fails on main → file an issue, link it

## Long-running tasks

> "Never switch to blocking mode and give up when the poll times out. Never say 'I'll be notified when it completes' and stop checking — keep the loop going until the task finishes or the user tells you to stop."

## Alert on changes, not absolutes

From canary, but it's the universal observability rule:

A page with 3 baseline errors is fine if it still has 3.

> "Don't cry wolf — alert only on patterns persisting across 2+ consecutive checks."

> "Baseline is king. Without it, canary is just a health check."

Performance:
- 2x baseline = regression
- 1.5x baseline = variance

Read-only by default. Speed > analysis.

## Slop-scan philosophy

> "We are NOT trying to pass as human code. We are AI-coded and proud of it. The goal is code quality."

Distinguish "linter gaming" from "genuine quality":

- Catch patterns where empty catches mask data loss
- Ignore patterns where `catch {}` is the correct fire-and-forget choice

> "Don't chase the number. Fix patterns that represent actual code quality problems."

## When `catch {}` is correct

Contradicts every linter default — but:

> "If a fire-and-forget operation can fail for ANY reason and you don't care, `catch {}` is the correct pattern."

The example: cleanup paths. *"A cleanup path that throws on EPERM means the rest of cleanup doesn't run. That's worse."*

Don't tighten best-effort cleanup paths.

## Escalation

> "Bad work is worse than no work. You will not be penalized for escalating. If you have attempted a task 3 times without success, STOP and escalate."

## E2E test hygiene

> "NEVER copy a full SKILL.md file into an E2E test fixture. Extract only the section the test actually needs."

> "Never `pkill` running eval processes and restart — you lose results and waste money. One clean run beats three killed-and-restarted runs."

## Cost transparency

When evaluating a debugging investigation, attach the dollar cost:

> "Total cost of the investigation: $7 across three eval runs."

Decisions tied to dollar amounts are more honest than decisions described in vague terms.
