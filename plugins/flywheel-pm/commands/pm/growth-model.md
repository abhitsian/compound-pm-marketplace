---
name: pm:growth-model
description: Design and analyze growth loops — acquisition, engagement, monetization, and viral mechanics
argument-hint: "[product to model growth for]"
---

# Growth Model

## Purpose

Growth isn't a department — it's a system of loops. This command maps your product's growth engine: how users discover you, why they stay, how they bring others, and how revenue funds more growth. Without understanding these loops, you're optimizing tactics without a system.

Draws from Reforge growth frameworks and viral loop mechanics.

## Input

<growth_input> #$ARGUMENTS </growth_input>

**If empty:** Ask "What product do you want to model growth for?"

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
```

Load segments and strategy:
```bash
cat docs/segments/*.md 2>/dev/null
cat docs/strategy/*.md 2>/dev/null
```

## Step 1: Identify Your Growth Loops

A growth loop is a closed system where the output of one cycle becomes the input of the next. Map ALL loops that exist (or should exist):

### Acquisition Loops

| Loop Type | How It Works | Your Product |
|-----------|-------------|-------------|
| **Viral loop** | Users invite/share → new users join → they invite/share | [Exists? Describe] |
| **Content loop** | Users create content → content is discovered → new users join to create | [Exists? Describe] |
| **Paid loop** | Revenue → ad spend → new users → revenue | [Exists? Describe] |
| **SEO/AEO loop** | Content indexed → users discover via search/AI → some convert → more content | [Exists? Describe] |
| **Sales loop** | Customers succeed → case studies/referrals → new customers | [Exists? Describe] |
| **Community loop** | Users help users → community grows → community attracts new users | [Exists? Describe] |

### Engagement Loops

| Loop Type | How It Works | Your Product |
|-----------|-------------|-------------|
| **Habit loop** | Trigger → action → variable reward → investment → trigger | [Exists? Describe] |
| **Social loop** | User acts → others are notified → they act → original user is notified | [Exists? Describe] |
| **Progress loop** | User advances → new capabilities unlock → more reasons to return | [Exists? Describe] |
| **Content consumption loop** | User consumes → algorithm learns → better recommendations → more consumption | [Exists? Describe] |

### Monetization Loops

| Loop Type | How It Works | Your Product |
|-----------|-------------|-------------|
| **Expansion loop** | User succeeds → needs grow → upgrades/buys more → more success | [Exists? Describe] |
| **Network pricing loop** | More users → more value → higher willingness to pay → more investment → more users | [Exists? Describe] |

## Step 2: Identify Your Primary Loop

Every product has ONE primary growth engine. The rest are secondary.

Use **AskUserQuestion tool**:

**Question:** "Which loop is your primary growth engine right now?"

**Options:**
1. **Viral/word-of-mouth** — Growth comes from users bringing other users
2. **Content/SEO** — Growth comes from users discovering content
3. **Paid acquisition** — Growth comes from spending money on ads/sales
4. **Product-led** — Growth comes from the product experience itself (freemium, self-serve)

### Primary Loop Deep Dive

Map the complete cycle:
1. **Input:** What enters the loop? (new user, piece of content, dollar spent)
2. **Step 1:** What does the user DO?
3. **Step 2:** What output does that create? (content, invite, data, revenue)
4. **Step 3:** How does that output attract the NEXT user?
5. **Step 4:** What % of new users complete the cycle? (loop efficiency)
6. **Constraints:** What limits the loop? (inventory, quality, trust, saturation)

## Step 3: Viral Factor Calculation (If Applicable)

If your product has any viral/sharing/invite mechanics:

### Basic Calculation
```
Viral Factor = New users acquired through existing users / Original user cohort
```

Take a cohort of users from a specific time period. Count how many new signups have those users as their referrer/sharer. The ratio is your viral factor.

| Metric | Value |
|--------|-------|
| Cohort size (users in period) | [N] |
| Invites/shares sent per user | [N] |
| Conversion rate on invites | [%] |
| New users attributed to cohort | [N] |
| **Viral factor** | [ratio] |

### Interpretation
- **>1.0:** Self-sustaining viral growth (rare and powerful)
- **0.5-1.0:** Meaningful viral contribution (amplifies other channels)
- **0.1-0.5:** Some organic sharing (nice to have)
- **<0.1:** Not meaningfully viral (don't invest here)

### Viral Factor Optimization Levers
- **Increase invites sent:** Make sharing easier, more contextual, incentivized
- **Increase conversion rate:** Improve landing page, reduce signup friction, show social proof
- **Reduce time to invite:** Get users to value faster so they share sooner
- **Improve targeting:** Help users share with people most likely to convert

### Warning: Viral Loops and Spam Loops
If you're artificially inflating invites (address book imports, aggressive notifications), you'll get short-term growth that kills long-term reputation. Check:
- Are invitees responding positively?
- Is the conversion rate stable or declining?
- Are you getting spam complaints?

## Step 4: Retention as Growth Foundation

No growth engine works without retention. Check:

### The 10 Stickiness Signals
| Signal | Threshold | Your Product |
|--------|-----------|-------------|
| Cohort retention curves flatten | Yes/No | [status] |
| Actives/Registered > 25% | >25% | [%] |
| Power user curve shows concentration | Healthy shape | [status] |
| Viral factor | >0.5 | [value] |
| DAU/MAU | >50% (consumer), >30% (B2B) | [%] |
| D1/D7/D30 retention | >60/30/15 | [values] |
| Revenue per user expanding | Positive trend | [status] |
| >60% organic acquisition at scale | >60% | [%] |
| Subscription annual retention | >65% | [%] |
| Market-by-market: older = more engaged | Yes/No | [status] |

**Diagnosis:**
- **6+ signals green:** Product has strong retention. Invest in growth loops.
- **3-5 signals green:** Retention is adequate. Fix gaps before scaling acquisition.
- **<3 signals green:** Retention is the problem. Growth investment is premature — it's filling a leaky bucket.

## Step 5: Growth Constraints

For your primary loop, identify:

1. **What's the bottleneck?** The single thing that, if improved, would most accelerate the loop.
2. **What's the ceiling?** The natural limit — market size, saturation, budget.
3. **What's the risk?** What could break the loop? (Platform changes, competitor moves, cost increases)

## Step 6: Growth Model Document

Write to `docs/growth/YYYY-MM-DD-growth-model.md`:

```markdown
---
date: YYYY-MM-DD
product: "[product name]"
primary_loop: "[loop type]"
viral_factor: [number or "n/a"]
retention_signals_green: [count out of 10]
primary_bottleneck: "[bottleneck]"
---

# Growth Model: [Product]

## Growth Loops
[All loops identified — acquisition, engagement, monetization]

## Primary Loop
[Detailed cycle with efficiency metrics]

## Viral Factor
[Calculation and optimization levers — if applicable]

## Retention Foundation
[10 stickiness signals assessment]

## Constraints
[Bottleneck, ceiling, risk]

## Growth Strategy
[Where to invest based on loop strength and retention foundation]

## Key Metrics to Track
| Metric | Current | Target (3mo) | Target (6mo) |
|--------|---------|-------------|-------------|
| [metric] | [value] | [target] | [target] |
```

## Post-Model Options

Use **AskUserQuestion tool**:

**Question:** "Growth model complete. What's next?"

**Options:**
1. **Run `/pm:retention`** — Deep dive on retention analysis
2. **Run `/pm:north-star`** — Define the North Star Metric for this growth model
3. **Run `/pm:strategy`** — Integrate growth model into product strategy
4. **Done** — Growth model documented
