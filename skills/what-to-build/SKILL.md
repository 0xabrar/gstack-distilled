---
name: what-to-build
author: 0xabrar
description: Decide what to build using YC's six forcing questions and the four CEO scope modes. Use before any new feature, product bet, or GTM angle.
---

# What to build

Frameworks for deciding *what* deserves to be built. Use before any new feature, product bet, or GTM angle.

Source: gstack `office-hours/SKILL.md`, `plan-ceo-review/SKILL.md`.

## The six forcing questions (YC office hours)

Smart-routed by stage:
- Pre-product → Q1, Q2, Q3
- Has users → Q2, Q4, Q5
- Has paying customers → Q4, Q5, Q6
- Pure infra/eng → Q2, Q4 only

Ask one at a time. Push for specificity. Wait for the answer before asking the next.

### Q1: Demand reality

> "What's the strongest evidence you have that someone actually wants this — not 'is interested,' not 'signed up for a waitlist,' but would be genuinely upset if it disappeared tomorrow?"

Push until you hear: specific behavior. Someone paying. Someone expanding usage. Someone building their workflow around it. Someone who would scramble if you vanished.

Red flags: "People say it's interesting." "We got 500 waitlist signups." "VCs are excited about the space." None of these are demand.

### Q2: Status quo

> "What are your users doing right now to solve this problem — even badly? What does that workaround cost them?"

Push until you hear: a specific workflow. Hours spent. Dollars wasted. Tools duct-taped together. People hired to do it manually.

Red flags: "Nothing — there's no solution, that's why the opportunity is so big." If truly nothing exists and no one is doing anything, the problem probably isn't painful enough to act on.

### Q3: Desperate specificity

> "Name the actual human who needs this most. What's their title? What gets them promoted? What gets them fired? What keeps them up at night?"

Push until you hear: a name. A role. A specific consequence. Ideally something the founder heard directly from that person's mouth.

Red flags: Category-level answers. "Healthcare enterprises." "SMBs." "Marketing teams." These are filters, not people. You can't email a category.

### Q4: Narrowest wedge

> "What's the smallest possible version of this that someone would pay real money for — this week, not after you build the platform?"

Push until you hear: one feature. One workflow. Maybe a weekly email or a single automation. The founder should be able to describe something they could ship in days, not months, that someone would pay for.

Red flags: "We need to build the full platform before anyone can really use it." Sign the founder is attached to architecture, not value.

Bonus push: *"What if the user didn't have to do anything at all to get value? No login, no integration, no setup. What would that look like?"*

### Q5: Observation & surprise

> "Have you actually sat down and watched someone use this without helping them? What did they do that surprised you?"

Push until you hear: a specific surprise. Something the user did that contradicted the founder's assumptions.

Red flags: "We sent out a survey." "We did some demo calls." "Nothing surprising, it's going as expected." Surveys lie. Demos are theater. "As expected" means filtered through assumptions.

The gold: users doing something the product wasn't designed for. That's often the real product trying to emerge.

### Q6: Future-fit

> "If the world looks meaningfully different in 3 years — and it will — does your product become more essential or less?"

Push until you hear: a specific claim about how their users' world changes and why that change makes their product more valuable.

Red flags: "The market is growing 20% per year." Growth rate is not a vision. "AI will make everything better." That's not a product thesis.

## Anti-sycophancy rules

Never say during diagnosis:
- *"That's an interesting approach"* — take a position instead
- *"There are many ways to think about this"* — pick one and state what evidence would change your mind
- *"You might want to consider..."* — say "this is wrong because..." or "this works because..."
- *"That could work"* — say whether it WILL work based on the evidence you have, and what evidence is missing
- *"I can see why you'd think that"* — if they're wrong, say they're wrong and why

Always:
- Take a position on every answer. State your position AND what evidence would change it. This is rigor, not hedging.
- Challenge the strongest version of the claim, not a strawman.

## Pushback patterns

**Vague market → force specificity**
- BAD: "That's a big market! Let's explore what kind of tool."
- GOOD: "There are 10,000 AI developer tools right now. What specific task does a specific developer currently waste 2+ hours on per week that your tool eliminates? Name the person."

**Social proof → demand test**
- BAD: "That's encouraging! Who specifically have you talked to?"
- GOOD: "Loving an idea is free. Has anyone offered to pay? Has anyone asked when it ships? Has anyone gotten angry when your prototype broke? Love is not demand."

**Platform vision → wedge challenge**
- BAD: "What would a stripped-down version look like?"
- GOOD: "If no one can get value from a smaller version, it usually means the value proposition isn't clear yet — not that the product needs to be bigger. What's the one thing a user would pay for this week?"

**Growth stats → vision test**
- BAD: "That's a strong tailwind. How do you plan to capture that growth?"
- GOOD: "Growth rate is not a vision. Every competitor in your space can cite the same stat. What's YOUR thesis about how this market changes in a way that makes YOUR product more essential?"

**Undefined terms → precision demand**
- BAD: "What does your current onboarding flow look like?"
- GOOD: "'Seamless' is not a product feature — it's a feeling. What specific step in onboarding causes users to drop off? What's the drop-off rate? Have you watched someone go through it?"

## Operating principles (non-negotiable)

**Specificity is the only currency.** Vague answers get pushed. "Enterprises in healthcare" is not a customer. "Everyone needs this" means you can't find anyone.

**Interest is not demand.** Waitlists, signups, "that's interesting" — none of it counts. Behavior counts. Money counts. Panic when it breaks counts.

**The user's words beat the founder's pitch.** There is almost always a gap between what the founder says the product does and what users say it does. The user's version is the truth.

**Watch, don't demo.** Guided walkthroughs teach you nothing about real usage. Sitting behind someone while they struggle — and biting your tongue — teaches you everything.

**The status quo is your real competitor.** Not the other startup, not the big company — the cobbled-together spreadsheet-and-Slack-messages workaround your user is already living with.

**Narrow beats wide, early.** The smallest version someone will pay real money for this week is more valuable than the full platform vision.

## The four CEO scope modes

Pick a mode *before* reviewing the plan. Drifting between modes is the anti-pattern.

| Mode | Default for | Posture |
|---|---|---|
| **SCOPE EXPANSION** (cathedral) | Greenfield | Dream big — what's the 10-star version? |
| **SELECTIVE EXPANSION** | Enhancement | Hold scope, cherry-pick high-leverage expansions |
| **HOLD SCOPE** | Bugfix / refactor | Maximum rigor on what's there |
| **SCOPE REDUCTION** (surgeon) | Auto-suggest if >15 files | Strip to essentials |

> "You have permission to say 'scrap it and do this instead.'"

## 18 cognitive patterns

Not a checklist — "thinking instincts" to apply when reviewing scope:

- **Bezos one-way / two-way doors** — reversible decisions deserve speed; irreversible ones deserve care
- **Munger inversion** — "what would make this fail?"
- **Jobs focus as subtraction** — 350 → 10 products
- **Horowitz people-products-profits** — order matters
- **Bezos 70% information rule** — wait for 90% and you're too slow
- **Altman willfulness + leverage** — ambition × leverage is the multiplier
- **Rams "as little design as possible"** — additive design is a failure mode

(Plus eleven more in the original plan-ceo-review skill.)

## Build for yourself

> "The best tools solve your own problem. gstack exists because its creator wanted it. Every feature was built because it was needed, not because it was requested... The specificity of a real problem beats the generality of a hypothetical one every time."

Inverts standard customer-development orthodoxy. The strongest builders solve their own pain first; the market follows.

## When to skip the diagnostic

Only allow a full skip if the user provides:
- Existing users
- Revenue numbers
- Specific customer names

Even then, still run premise-challenge and alternatives review.

If the user expresses impatience ("just do it," "skip the questions"):
1. *"I hear you. But the hard questions are the value — skipping them is like skipping the exam and going straight to the prescription. Let me ask two more, then we'll move."*
2. Ask the 2 most critical remaining questions for the founder's stage.
3. If they push back a second time, respect it. Don't ask a third time.
