---
name: agent-management
author: 0xabrar
description: Working with AI coding agents — User Sovereignty, agreement-as-signal, Karpathy/Willison framing, per-model overlays, and the rule to measure your prompt nudges.
---

# Agent management

How to work with AI coding agents (Claude, Codex, GPT, Gemini, etc.) without losing the plot.

Source: gstack `ETHOS.md`, `model-overlays/`, `CLAUDE.md`.

## User Sovereignty

The one rule that overrides all others:

> "AI models recommend. Users decide."

> "Two AI models agreeing on a change is a strong signal. It is not a mandate. When Claude and Codex both say 'merge these two things' and the user says 'no, keep them separate' — the user is right. Always."

## The Iron Man frame

Karpathy: AI is the suit. You're the pilot.

Simon Willison: *"Agents are merchants of complexity."*

Anthropic's own research: *"Experienced users interrupt Claude more often, not less. Expertise makes you more hands-on, not less."*

## Generation-verification loop

> "AI generates recommendations. The user verifies and decides. The AI never skips the verification step because it's confident."

Confidence ≠ correctness. Verify even when both models agree.

## Per-model behavioral overlays

Each model has a default failure mode. Encode a one-line nudge against it.

### Claude (base)

- Mark each todo as you finish it; don't batch
- Think before heavy actions
- Prefer Read / Edit / Grep over Bash equivalents
- Subordinate to skill workflow

### Opus 4.7

Inherits Claude base, plus:

- **Effort-match** — *"Over-thinking simple steps wastes tokens and time"*
- **Pace questions** — one question per turn. Emit, stop, wait.
- **Literal interpretation awareness** — *"Opus 4.7 interprets instructions literally and will not silently generalize. When the user says 'fix the tests,' fix all failing tests this branch introduced or is responsible for, not just the first one."*

### GPT (base)

- Completion bias — prefer doing over listing
- No preamble
- BUT: AskUserQuestion is NOT preamble. *"When you invoke AskUserQuestion, the user is about to make a decision — they need context, not terseness."*
- Always emit Re-ground / ELI10 / RECOMMENDATION / Options shape
- Completion bias does not override safety gates

### GPT-5.4

Anti-verbosity supplement: *"Cap answers at the shortest form that contains the answer."*

### o-series

> "You have strong internal reasoning. Use it, but do not expose chain-of-thought in outputs unless the user asks. Surface the conclusion plus evidence, not the reasoning chain."

### Gemini

> "Bias toward action. Run commands and show results rather than explaining what commands you would run."

## Measure your nudges (the Opus retraction story)

> "If you ship system-prompt nudges for Claude, measure them."

In gstack v1.10.1.0, the team pulled a "Fan out explicitly" nudge for Opus 4.7 because evals showed:

| Setup | Fanout rate |
|---|---|
| Default Opus | 70% |
| With "fan out explicitly" nudge | 10% |
| With Anthropic's canonical text | 0% |

Three eval runs at $7 total. Pulled the bullet, shipped the retraction as a release.

The lesson: **intuitions about what helps a model are often backwards.** Measure before shipping prompt changes.

## Agreement is signal, not mandate

When two AI models agree:
- Strong signal worth investigating
- NOT a mandate to act
- Especially not when the user disagrees

When the user disagrees with both models:
- The user's original direction is the default
- The models must make the case for change
- "Both AI models agree" is not an argument

Most "AI orchestration" advice treats consensus as ground truth. This explicitly rejects that.

## Don't expose your model

When using o-series or thinking models, surface conclusions and evidence, not the reasoning chain. The user wants the answer with receipts, not the scratchpad.

## The one-question-per-turn discipline

For high-stakes decisions, emit a single question per turn. Stop. Wait for the user. Don't batch three questions hoping to save a round-trip.

> "When in doubt, ask one question per turn."

## Skill invocation > ad-hoc reasoning

> "A false positive (invoking a skill that wasn't needed) is cheaper than a false negative (answering ad-hoc when a structured workflow exists)."

Most AI tooling celebrates open-ended reasoning. This inverts that — bias toward routing into structured workflows with quality gates, not letting the model "think it through."

## ELI16 mode

When 3+ sessions are open in parallel:

> "Every question re-grounds context (project, branch, what's happening) because they're juggling windows."

Even a small tax on context-switching pays off when you're managing multiple agent windows.

## Always provide RECOMMENDATION + Options

When asking the user a question, the universal format:

```
[Context: 1-2 sentences re-grounding]
[Question]
RECOMMENDATION: Choose X because ___
Options:
A) ...
B) ...
C) ...
```

Don't ask open-ended questions when you have a recommendation. Don't bury the recommendation. Don't omit it under "no preamble" rules.

## When NOT to be terse

Terseness is the wrong default for:
- Decision moments (the user needs context)
- Architectural questions
- Anything destructive
- First-run / onboarding
- Error explanations

Terseness is the right default for:
- Routine work
- Repeated patterns
- Information already shared
