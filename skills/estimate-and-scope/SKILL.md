---
name: estimate-and-scope
author: 0xabrar
description: Estimate work and scope decisions in the AI-coding era. Boil the Lake, AI compression ratios, three-layer search before building.
---

# Estimate and scope

How to size work and decide between approaches when AI compresses the cost of completeness.

Source: gstack `ETHOS.md`, `CLAUDE.md`, `ship/SKILL.md`.

## Boil the Lake

> "AI-assisted coding makes the marginal cost of completeness near-zero. When the complete implementation costs minutes more than the shortcut — do the complete thing. Every time."

Lake vs ocean:
- **Lake** = boilable. 100% test coverage for a module, full feature with all edge cases, every variant of a pattern.
- **Ocean** = not boilable. Multi-quarter platform migrations, full rewrites of legacy systems.

Boil lakes. Flag oceans as out of scope.

> "'Ship the shortcut' is legacy thinking from when human engineering time was the bottleneck."

## AI compression in estimates

Always quote both human-time and AI-assisted time:

| Type of work | Compression |
|---|---|
| Boilerplate | ~100x |
| Tests | ~50x |
| Feature | ~30x |
| Bugfix + regression | ~20x |
| Architecture | ~5x |
| Research | ~3x |

Phrase as: *"2 weeks human / ~1 hour AI-assisted."*

When evaluating "approach A (full, ~150 LOC) vs approach B (90%, ~80 LOC)" — almost always choose A.

### Anti-patterns in estimation

- *"Choose B — it covers 90% with less code."* (If A is 70 lines more, choose A.)
- *"Let's defer tests to a follow-up PR."* (Tests are the cheapest lake to boil.)
- *"This would take 2 weeks."* (Say: "2 weeks human / ~1 hour AI-assisted.")

## Search before building

> "The 1000x engineer's first instinct is 'has someone already solved this?' not 'let me design it from scratch.'"

### Three layers of knowledge

**Layer 1: Tried and true** — built-ins, official docs, well-established libraries.
> "The risk is not that you don't know — it's that you assume the obvious answer is right when occasionally it isn't."

**Layer 2: New and popular** — recent blog posts, trending patterns, popular libraries.
> "Humans are subject to mania. Mr. Market is either too fearful or too greedy. Search results are inputs to your thinking, not answers."

**Layer 3: First principles** — your own reasoning from fundamentals.
> "Prize them above everything else."

**Trust ranking:** Layer 3 > Layer 1 > Layer 2.

Most engineering culture says "don't reinvent the wheel" by default. This inverts that: *"Once in a while, questioning the tried-and-true is where brilliance occurs."*

### Search rubric

1. `{runtime} {thing} built-in`
2. `{thing} best practice {current year}`
3. Check official docs

### The eureka moment

> "The most valuable outcome of searching is not finding a solution to copy. It's finding a clear reason why the conventional approach is wrong... zig while others zag. When you find one, name it. Celebrate it. Build on it."

> "The truly superlative projects are full of these moments — 11 out of 10."

## Anti-patterns in scope decisions

- Rolling a custom solution when the runtime has a built-in
- Accepting blog posts uncritically in novel territory
- Picking the smaller-LOC option when the larger one covers more edge cases
- Deferring tests to a follow-up PR
- Quoting estimates in human-time without the AI-assisted equivalent
- Assuming Layer 2 (new and popular) is a strong signal because something is trending

## The completeness test

When you find yourself thinking "ship the 90% version":

1. How many lines is the gap between 90% and 100%?
2. What's the AI-assisted estimate to fill it?
3. Is this a lake or an ocean?

If it's a lake and the gap is hours not weeks → boil it.
