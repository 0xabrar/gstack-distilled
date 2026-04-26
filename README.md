# gstack-distilled

The strategy and decision-making frameworks from Garry Tan's [gstack](https://github.com/garrytan/gstack), as focused standalone skills.

## What this is

[gstack](https://github.com/garrytan/gstack) is Garry Tan's open-source Claude Code config — 60+ skills encoding how YC's president builds. The skills are large because they include their full operational layer: bash preambles, telemetry, gbrain memory sync, voice rules, model-specific patches, completion protocols.

This repo extracts the strategy and judgment layer on its own. Just the frameworks. No setup script, no install, no telemetry.

Useful when you want to:
- Read Garry's decision-making frameworks as plain markdown
- Drop a few focused skills into your own Claude Code setup
- Paste specific frameworks into any agent's system prompt

## What's in it

Seven decision-making frameworks, each a standalone skill:

- **[what-to-build](skills/what-to-build/SKILL.md)** — YC office-hours' six forcing questions, the four CEO scope modes, anti-sycophancy rules, cognitive patterns
- **[estimate-and-scope](skills/estimate-and-scope/SKILL.md)** — Boil the Lake, AI compression ratios, three layers of search, the eureka moment
- **[ship-discipline](skills/ship-discipline/SKILL.md)** — The single ship gate, six auto-decision principles, the Confusion Protocol
- **[review-and-debug](skills/review-and-debug/SKILL.md)** — Confidence calibration, root-cause iron law, alert-on-changes, the pre-existing blame protocol
- **[ux-bar](skills/ux-bar/SKILL.md)** — Krug's three laws, Goodwill Reservoir, eight DevEx first principles, time-to-hello-world tiers
- **[agent-management](skills/agent-management/SKILL.md)** — User Sovereignty, agreement-as-signal, per-model overlays, measure-your-nudges
- **[learning-loop](skills/learning-loop/SKILL.md)** — Plan-tune dual-track profile, retro philosophy, the keep-or-toss test

Plus **[doctrine.md](doctrine.md)** — the whole thing in one file for the impatient.

## Install

### Claude Code (plugin marketplace)

```
/plugin marketplace add 0xabrar/gstack-distilled
/plugin install gstack-distilled@gstack-distilled
```

This installs all seven skills as a managed plugin. Updates via `/plugin update`.

### Cross-agent (skills.sh)

For Cursor, Gemini, or any agent that supports the [Agent Skills standard](https://skills.sh/):

```bash
npx skills add 0xabrar/gstack-distilled
```

### Read or paste

Each `skills/<name>/SKILL.md` is plain markdown. Browse the repo, open `doctrine.md` for the single-file version, or copy any section into an agent's system prompt. The doctrine is model-agnostic.

### Manual install (no plugin manager)

```bash
git clone https://github.com/0xabrar/gstack-distilled.git ~/.gstack-distilled
ln -sf ~/.gstack-distilled/skills/* ~/.claude/skills/
```

Update later with `cd ~/.gstack-distilled && git pull`.

## Source and attribution

100% derived from [gstack](https://github.com/garrytan/gstack) (MIT, © Garry Tan). Original frameworks, principles, and quoted text are Garry's. This repo organizes and condenses them.

Each skill file lists the gstack source files it harvests from. See [ATTRIBUTION.md](ATTRIBUTION.md) for the full mapping.

For the live tooling — the headless browser daemon, gbrain memory layer, multi-host installer, parallel-Conductor workflow — use [gstack](https://github.com/garrytan/gstack) directly.

## License

MIT. See [LICENSE](LICENSE).
