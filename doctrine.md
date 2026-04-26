# The Doctrine — single-file harvest

The decision-making frameworks from [gstack](https://github.com/garrytan/gstack), in one file.

For deeper coverage on each topic, see the corresponding skill in `skills/`.

---

## 1. What to build

**Six forcing questions** (YC office hours). Smart-routed by stage:
- Pre-product → Q1, Q2, Q3
- Has users → Q2, Q4, Q5
- Has paying customers → Q4, Q5, Q6

**Q1 Demand reality:** *"Strongest evidence someone would be genuinely upset if it disappeared tomorrow?"* Behavior counts. Money counts. Waitlists don't.

**Q2 Status quo:** *"What are users doing right now to solve this — even badly?"* The status quo is your real competitor.

**Q3 Desperate specificity:** *"Name the actual human."* You can't email a category.

**Q4 Narrowest wedge:** *"Smallest version someone pays for this week, not after the platform."*

**Q5 Observation:** *"Have you watched someone use this without helping? What surprised you?"*

**Q6 Future-fit:** *"In 3 years, does your product become more essential or less?"*

**Anti-sycophancy:** never say "interesting approach" / "you might want to consider" / "that could work." Take a position and state what evidence would change it.

**Four CEO scope modes** (pick before reviewing):
- SCOPE EXPANSION (greenfield)
- SELECTIVE EXPANSION (enhancement)
- HOLD SCOPE (bugfix)
- SCOPE REDUCTION (>15 files)

**Build for yourself.** *"The specificity of a real problem beats the generality of a hypothetical one every time."*

→ See `skills/what-to-build/SKILL.md`

---

## 2. Estimate and scope

**Boil the Lake.** *"AI-assisted coding makes the marginal cost of completeness near-zero. When the complete implementation costs minutes more than the shortcut — do the complete thing. Every time."*

Lake = boilable (full feature, all edge cases). Ocean = not (multi-quarter migrations). Boil lakes, flag oceans.

**AI compression in estimates** — always quote both:

| Type | Compression |
|---|---|
| Boilerplate | ~100x |
| Tests | ~50x |
| Feature | ~30x |
| Bugfix + regression | ~20x |
| Architecture | ~5x |
| Research | ~3x |

Phrase as: *"2 weeks human / ~1 hour AI-assisted."*

**70-line rule:** if approach A covers more edge cases at 70 lines more than B, choose A.

**Three layers of search:**
- Layer 1: Tried-and-true (built-ins, official docs)
- Layer 2: New-and-popular (*"humans are subject to mania. Mr. Market is either too fearful or too greedy."*)
- Layer 3: First-principles — **prized above the others**

Trust ranking: Layer 3 > Layer 1 > Layer 2.

**The eureka moment:** *"The most valuable outcome of searching is finding a clear reason why the conventional approach is wrong."*

→ See `skills/estimate-and-scope/SKILL.md`

---

## 3. Ship discipline

**One gate, named explicitly.** Eng review only. CEO/Design/Adversarial are informational.

**Six auto-decision principles** (autoplan):
1. Choose completeness
2. Boil lakes (auto-approve <1 day AI-assisted expansions)
3. Pragmatic — *"5 seconds choosing, not 5 minutes"*
4. DRY — duplicates? Reject
5. Explicit over clever — *"10-line obvious fix > 200-line abstraction"*
6. Bias toward action — *"Merge > review cycles > stale deliberation"*

**Decision classification:**
- Mechanical → silent
- Taste → auto + surface
- User Challenge → NEVER auto (force models to make the case)

**Confusion Protocol** — STOP only on architectural ambiguity, destructive scope unclear, contradicting patterns. Never on routine work.

**Land-and-deploy** — narrate, don't go silent. *"Explain why before asking — 'Deploys are irreversible, so I check X.'"*

→ See `skills/ship-discipline/SKILL.md`

---

## 4. Review and debug

**Investigate's Iron Law:** *"NO FIXES WITHOUT ROOT CAUSE INVESTIGATION FIRST."*

Four phases: investigate → analyze → hypothesize → implement.

**3-strike rule.** 3 failed hypotheses → STOP. Probably architectural, not a bug.

**Recurring-bug heuristic:** *"Recurring bugs in the same files are an architectural smell, not a coincidence."*

**Hard rules:**
- Never apply a fix you can't verify
- Never say "this should fix it"
- Regression test must fail without the fix and pass with it
- \>5 files touched → blast-radius gate

**Confidence calibration** — every finding 1-10. Below 7 = caveat or suppress. 1-2 = only report if P0.

**Fix-first reviews** — auto-fix dead code, N+1, stale comments. Ask on the rest.

**Pre-existing blame protocol:** *"'Pre-existing' without receipts is a lazy claim. Prove it or don't say it."* Run on main; if it passes there, it IS your change.

**Alert on changes, not absolutes.** A page with 3 baseline errors is fine if it still has 3. Don't cry wolf — alert only on patterns persisting across 2+ checks.

**`catch {}` is sometimes correct.** *"If a fire-and-forget operation can fail for ANY reason and you don't care, `catch {}` is the correct pattern."*

→ See `skills/review-and-debug/SKILL.md`

---

## 5. UX bar

**Krug's three laws:**
1. Don't make me think — self-evident > self-explanatory > requires explanation
2. Clicks don't matter, thinking does — three mindless clicks beat one puzzle
3. Omit, then omit again — happy talk and instructions must die

*"Users scan, they don't read. Designing billboards going by at 60 mph."*

**Goodwill Reservoir** — every friction point depletes it. When zero, they leave.

**Pit of Success:** *"Make the right thing easy, the wrong thing hard."*

**Eight DevEx first principles:**
1. Zero friction at T0
2. Decide for me, let me override
3. Every error = problem + cause + fix
4. Speed is a feature
5. Show, don't explain
6. Composability over completeness
7. Honest about state
8. Chef-for-chefs bar

**Time-to-hello-world tiers:**

| Time | Tier |
|---|---|
| <2 min | Champion |
| 2-5 min | Competitive |
| 5-10 min | Needs Work |
| **>10 min** | **Red Flag (50-70% abandon)** |

**The boomerang:** plan-stage scores predicted N/10 per dimension. Live audit reports actual. Flag any dimension where `live < plan - 2`.

→ See `skills/ux-bar/SKILL.md`

---

## 6. Agent management

**User Sovereignty (the one rule):** *"AI models recommend. Users decide. This is the one rule that overrides all others."*

**Agreement is signal, not mandate.** *"Two AI models agreeing is a strong signal. It is not a mandate. When Claude and Codex both say merge and the user says no — the user is right. Always."*

**Karpathy's Iron Man frame.** Willison: *"Agents are merchants of complexity."* Anthropic's research: *"Experienced users interrupt Claude more often, not less. Expertise makes you more hands-on, not less."*

**Generation-verification loop:** *"AI generates recommendations. The user verifies and decides. The AI never skips verification because it's confident."*

**Per-model overlays:**
- **Opus 4.7:** literal interpretation — *"fix the tests" means all of them*
- **GPT-5.4:** anti-verbosity — *"Cap at the shortest form that contains the answer"*
- **o-series:** *"Surface conclusions and evidence, not the reasoning chain"*
- **Gemini:** *"Bias toward action. Run commands and show results."*

**Measure your nudges.** gstack v1.10.1.0 pulled a "fan out explicitly" prompt for Opus 4.7 because evals showed it dropped fanout from 70% to 10%. Anthropic's canonical version dropped it to 0%. Total cost: $7. Lesson: intuitions about prompts are often backwards.

**Skill invocation > ad-hoc reasoning:** *"A false positive (invoking a skill that wasn't needed) is cheaper than a false negative (answering ad-hoc when a structured workflow exists)."*

→ See `skills/agent-management/SKILL.md`

---

## 7. Learning loop

**Dual-track psychographic profile.** Track *declared* (self-report) vs *inferred* (observed behavior). Five dimensions: scope_appetite, risk_tolerance, detail_preference, autonomy, architecture_care.

Gap-band:
- <0.1 → close
- 0.1–0.3 → drift
- \>0.3 → mismatch — *"your behavior disagrees with your self-description"*

**Iron rule:** the user decides whether declared is wrong or behavior is wrong. **Never auto-update declared from observed gap.**

**Retro philosophy:** *"Features shipped leads — what users got. Raw LOC is demoted to context because AI inflates it. Ten lines of a good fix is not less shipping than ten thousand lines of scaffold."*

**Fix-ratio flag:** >50% fix commits = "ship fast, fix fast" pattern signaling review gaps.

**Keep-or-toss test:** *"Would this insight save time in a future session? Would it save 5+ minutes? If yes, log it."*

**Closed-loop principle.** Every workflow should generate data the next workflow can consume. Ship → ship log → retro velocity trends → next sprint priorities → ship again.

**Memory hygiene.** Sync durable artifacts (decisions, designs, learnings). Don't sync per-machine UX state (question-log, preferences).

→ See `skills/learning-loop/SKILL.md`

---

## The 12 highest-leverage moves

If you only take a dozen things from this whole repo, take these:

1. **Six forcing questions before any feature** — Q1 (demand), Q3 (specific human), Q4 (narrowest wedge) are non-negotiable for solo founders
2. **Boil the Lake estimate format** — always quote human-time AND AI-assisted-time
3. **Single named ship gate** — pick one hard blocker; everything else is informational
4. **Confidence calibration in reviews** — suppress findings <7 unless P0
5. **3-strike escalation** — three failed hypotheses means the bug is architectural
6. **No-fixes-without-root-cause** with regression test (fail without, pass with)
7. **Pre-existing-failure-with-receipts** — prove on main or own it
8. **Alert on changes, not absolutes** — for any monitoring you wire up
9. **TTHW tiers** for the onboarding/claim flow (<2min Champion is the bar)
10. **User Sovereignty** — agreement between models is signal, not mandate
11. **Measure your prompt nudges** — intuitions are often backwards
12. **Plan-tune dual-track profile** — even a markdown file logging declared-vs-behavior gaps would change how you work

The single most quotable line for keeping yourself honest:

> "'Ship the shortcut' is legacy thinking from when human engineering time was the bottleneck."

Tape that to your monitor.
