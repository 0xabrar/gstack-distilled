# Attribution

Every framework in this repo is harvested from [gstack](https://github.com/garrytan/gstack), Garry Tan's open-source Claude Code config (MIT-licensed).

## Source mapping

| This repo | gstack source files |
|---|---|
| `skills/what-to-build/SKILL.md` | `office-hours/SKILL.md`, `plan-ceo-review/SKILL.md` |
| `skills/estimate-and-scope/SKILL.md` | `ETHOS.md`, `CLAUDE.md`, `ship/SKILL.md` |
| `skills/ship-discipline/SKILL.md` | `ship/SKILL.md`, `autoplan/SKILL.md`, `land-and-deploy/SKILL.md` |
| `skills/review-and-debug/SKILL.md` | `review/SKILL.md`, `investigate/SKILL.md`, `canary/SKILL.md`, `CLAUDE.md` |
| `skills/ux-bar/SKILL.md` | `design-review/SKILL.md`, `devex-review/SKILL.md`, `qa/SKILL.md` |
| `skills/agent-management/SKILL.md` | `ETHOS.md`, `model-overlays/*.md`, `CLAUDE.md` |
| `skills/learning-loop/SKILL.md` | `plan-tune/SKILL.md`, `retro/SKILL.md`, `learn/SKILL.md`, `SKILL.md` |
| `doctrine.md` | All of the above |

## What's quoted vs paraphrased

Verbatim quotes from gstack are wrapped in `> blockquotes` or surrounded by quotation marks. Everything else is paraphrase or organization.

## Not included

gstack contains 60+ skills, ~90K lines of TypeScript, and operational infrastructure (headless browser daemon, gbrain memory layer, multi-host adapters, telemetry, CI workflows). None of that is in this repo.

This repo extracts only the strategy and decision-making frameworks — the principles, heuristics, and cognitive patterns. For the actual tooling, use gstack directly.

## Credit

If you use any of this, the credit goes to Garry Tan and the gstack contributors.
