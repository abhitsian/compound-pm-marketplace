---
name: pm:retention
description: Analyze retention with cohort curves, habit loops, and resurrection strategies
argument-hint: "[product or feature to analyze retention for]"
---

# Retention Analysis

## Purpose

Retention is the foundation of all growth. If users don't come back, nothing else matters — acquisition fills a leaky bucket, viral loops decay, and revenue churns. This command provides a structured framework for diagnosing, measuring, and improving retention.

## Input

<retention_input> #$ARGUMENTS </retention_input>

**If empty:** Ask "What product or feature do you want to analyze retention for? Do you have retention data, or is this a framework for planning?"

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
```

Load growth model if available:
```bash
cat docs/growth/*.md 2>/dev/null
```

## Step 1: Define Retention for Your Product

Retention means different things for different products. Define precisely:

### What counts as "retained"?
- **Active definition:** What action constitutes "active use"?
  - Not: "Opened the app"
  - But: "Completed [core value action]"
- **Frequency expectation:** How often should a healthy user engage?
  - Daily product → measure D1, D7, D30
  - Weekly product → measure W1, W4, W12
  - Monthly product → measure M1, M3, M6
  - Transactional product → measure repeat purchase rate

### Retention Segments
| Segment | Definition | Current Estimate |
|---------|-----------|-----------------|
| **New users** | First 7 days | [% retained at D7] |
| **Activated users** | Reached Aha moment | [% of new who activate] |
| **Core users** | Regular usage pattern | [% of activated who become core] |
| **Power users** | Heavy, consistent usage | [% of core who become power] |
| **At-risk users** | Usage declining | [% of core showing decline] |
| **Churned users** | No activity for [X] days | [% who have churned] |
| **Resurrected users** | Returned after churning | [% of churned who return] |

## Step 2: Retention Curve Analysis

### Ideal Retention Curve Shape
```
100% ─┐
      │\
      │ \
      │  \___________  ← curve flattens (healthy)
      │
  0%  └─────────────── time
```

### Retention Curve Diagnosis

| Shape | Diagnosis | Action |
|-------|-----------|--------|
| **Flattens at >30%** | Healthy — you have product-market fit for retained users | Focus on moving the flat line up and getting more users to the flat part |
| **Flattens at 10-30%** | Moderate — PMF for a niche, but most users don't find value | Investigate what retained users do differently. Can you move more users to that behavior? |
| **Flattens at <10%** | Weak — most users don't get value | Product-market fit problem. Fix value delivery before growing. |
| **Doesn't flatten** | Critical — continuous decline | Fundamental value problem. Users try and leave. |

## Step 3: New User Retention Deep Dive

The first 7 days determine everything.

### Day 1 Retention
- What % of new users return on Day 1?
- **Benchmark:** >60% for consumer, >40% for B2B
- If low: The first session doesn't deliver enough value. Users don't see a reason to return.

### Time to Aha
- How long until users experience core value?
- **Benchmark:** <5 minutes for consumer, <1 day for B2B
- If slow: Onboarding is blocking value. Can you skip setup and show value first?

### Activation Rate
- What % of new users complete the activation criteria?
- What's the drop-off at each step of activation?
  1. [Step 1]: [% who complete]
  2. [Step 2]: [% who complete]
  3. [Step 3]: [% who complete]
- **Where's the biggest drop-off?** That's your #1 retention lever.

### New User → Habit Transition
- What behavior predicts long-term retention?
- "Users who [specific action] within [timeframe] retain at [X]% vs [Y]% for those who don't"
- This is your magic number — the behavior to optimize toward.

## Step 4: Engagement Depth Analysis

### Power User Curve
Map the distribution of usage frequency:

| Actions per month | % of users |
|-------------------|-----------|
| 1 | [%] |
| 2-3 | [%] |
| 4-7 | [%] |
| 8-15 | [%] |
| 16-30 | [%] |
| 30+ | [%] |

**Healthy shape:** Smile curve (high at 1, dip in middle, rise at 30+)
**Unhealthy shape:** Decline curve (high at 1, falling to near-zero)

### Engagement Dimensions
| Dimension | Metric | Current | Target |
|-----------|--------|---------|--------|
| **Breadth** | Avg features used per week | [value] | [target] |
| **Depth** | Avg actions per session | [value] | [target] |
| **Intensity** | Avg session duration | [value] | [target] |

## Step 5: Churn Analysis

### Why Users Leave
Map the top churn reasons:

| Reason | % of Churn | Preventable? |
|--------|-----------|-------------|
| Never activated (cold start) | [%] | Yes — fix onboarding |
| Found a better alternative | [%] | Maybe — differentiate |
| Problem went away | [%] | No — natural churn |
| Too complex/difficult | [%] | Yes — simplify |
| Not enough value for the price | [%] | Yes — adjust value/price |
| Changed role/company | [%] | No — natural churn |

### Churn Signals (Early Warning)
What behaviors predict churn BEFORE it happens?
- Decreased login frequency
- Fewer core actions
- Support tickets
- Feature exploration (looking for alternatives)
- Account downgrade consideration

## Step 6: Resurrection Strategies

For users who have churned, what brings them back?

### Resurrection Triggers
| Trigger | Type | Effectiveness |
|---------|------|-------------|
| Product improvement notification | Extrinsic | [H/M/L] |
| Social — friend/colleague joined | Extrinsic | [H/M/L] |
| Problem recurrence — pain returns | Intrinsic | [H/M/L] |
| Win-back offer/discount | Extrinsic | [H/M/L] |
| Seasonal/periodic need | Intrinsic | [H/M/L] |
| New feature announcement | Extrinsic | [H/M/L] |

### AI-Specific Resurrection Tactics
- Personalized re-engagement based on past usage patterns
- "Here's what changed since you left" summaries
- Predictive churn intervention (catch them before they leave)

## Step 7: Retention Action Plan

Prioritize interventions by segment:

| Segment | Problem | Intervention | Expected Impact |
|---------|---------|-------------|----------------|
| New users | [key drop-off] | [specific fix] | [% improvement] |
| Activated users | [barrier to habit] | [specific fix] | [% improvement] |
| At-risk users | [churn signal] | [specific intervention] | [% improvement] |
| Churned users | [reason they left] | [resurrection tactic] | [% improvement] |

## Step 8: Generate Document

Write to `docs/retention/YYYY-MM-DD-retention-analysis.md`:

```markdown
---
date: YYYY-MM-DD
product: "[product name]"
d1_retention: "[%]"
d7_retention: "[%]"
d30_retention: "[%]"
activation_rate: "[%]"
curve_shape: "[flattening | declining | critical]"
top_churn_reason: "[reason]"
---

# Retention Analysis: [Product]

## Retention Definition
[What "active" means, frequency expectations]

## Retention Curve
[Shape, diagnosis, benchmarks]

## New User Retention
[D1, time to Aha, activation rate, drop-off analysis]

## Engagement Depth
[Power user curve, breadth/depth/intensity]

## Churn Analysis
[Top reasons, early warning signals]

## Resurrection Strategies
[Triggers and tactics]

## Action Plan
[Prioritized interventions by segment]
```

## Post-Analysis Options

Use **AskUserQuestion tool**:

**Question:** "Retention analysis complete. What's next?"

**Options:**
1. **Run `/pm:growth-model`** — Integrate retention into growth loop analysis
2. **Run `/pm:north-star`** — Define metrics that drive retention
3. **Run `/pm:motivation-map`** — Map motivation for the activation moment
4. **Done** — Analysis documented
