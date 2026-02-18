---
name: pm:north-star
description: Design your North Star Metric with ecosystem analysis, guardrails, and team goals
argument-hint: "[product to define NSM for]"
---

# North Star Metric Design

## Purpose

A North Star Metric captures the core value your product delivers. Not a vanity metric, not revenue, not DAU — the single metric that, if it grows, means you're winning for users AND the business.

This command follows the ecosystem-first approach: map all players, identify their value exchange, and derive a metric that captures multi-player value creation.

Based on Ben Erez's analytical thinking framework.

## Input

<nsm_input> #$ARGUMENTS </nsm_input>

**If empty:** Ask "What product do you want to define a North Star Metric for?"

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
```

Load existing metrics and strategy:
```bash
cat docs/strategy/*.md 2>/dev/null
cat docs/measurements/*.md 2>/dev/null
```

## Step 1: Map the Ecosystem

Identify the 3-5 most important ecosystem players:

For EACH player:

```markdown
### [Player Type] (e.g., End Users, Creators, Advertisers, Enterprise Admins)

**Primary value proposition:** What does the product do for them?
**Key actions they must take to realize value:**
1. [Action 1]
2. [Action 2]
3. [Action 3]

**Metrics to track those actions:**
- [# of users who perform Action 1 per DWM (day/week/month)]
- [# of times Action 1 is performed per DWM]
- [Avg Action 1 per user per DWM]
```

**Important:** Always define what "active" means. Not "active users" but "users who completed [specific action] within [time period]."

## Step 2: Design the North Star Metric

Your NSM should meet ALL of these criteria:

| Criteria | Test |
|----------|------|
| **Captures multi-player value** | Does growth in this metric mean BOTH users AND the business are winning? |
| **Can grow continuously** | Is there a natural ceiling, or can it grow as the product succeeds? |
| **Raw count preferred** | Is it a count (total sessions, items created) rather than a percentage? |
| **Per time period** | Is it measured per [day/week/month] rather than cumulative? |
| **Actionable** | Can the team influence this metric through product changes? |
| **Understandable** | Can every team member explain what it means and why it matters? |

### Candidate NSMs

Generate 3 candidate North Star Metrics:

| Candidate | What It Measures | Multi-Player? | Ceiling? | Actionable? |
|-----------|-----------------|---------------|----------|-------------|
| [NSM 1] | [description] | [Y/N] | [Y/N] | [Y/N] |
| [NSM 2] | [description] | [Y/N] | [Y/N] | [Y/N] |
| [NSM 3] | [description] | [Y/N] | [Y/N] | [Y/N] |

### Select and Critique

Choose one NSM. Then critique it honestly:

**Top 2 Strengths:**
1. [Why this is a good NSM]
2. [Why this is a good NSM]

**Top 2 Drawbacks:**
1. [What this metric misses or could be gamed]
2. [What this metric misses or could be gamed]

## Step 3: Design Guardrail Metrics

For EACH drawback of the NSM, create a guardrail metric:

| NSM Drawback | Guardrail Metric | Threshold |
|-------------|-----------------|-----------|
| [Drawback 1 — e.g., "could grow by adding low-quality content"] | [Guardrail — e.g., "% of content with >1 engagement per week"] | [>X%] |
| [Drawback 2 — e.g., "doesn't capture monetization"] | [Guardrail — e.g., "revenue per active user per month"] | [>$X] |

**Guardrail rules:**
- Guardrails use percentages (to counterbalance the raw-count NSM)
- Guardrails represent quality, safety, or sustainability dimensions
- If a guardrail drops below threshold, growth in the NSM is unhealthy — investigate

## Step 4: Choose the Time Period

| Factor | Consideration |
|--------|--------------|
| **Natural usage cadence** | How often do users naturally engage? (Daily app → daily. Monthly tool → monthly) |
| **Signal-to-noise ratio** | Can you detect real changes at this frequency? (Daily may be too noisy for B2B) |
| **Business cycle relevance** | Does this align with how the business makes decisions? |
| **Ability to take action** | Can the team respond at this cadence? |

**Choose:** Daily / Weekly / Monthly

## Step 5: Build the Metrics Hierarchy

From the NSM, build the full hierarchy:

```
North Star Metric
├── L1: [Direct driver 1]
│   ├── L2: [Input metric 1a]
│   └── L2: [Input metric 1b]
├── L1: [Direct driver 2]
│   ├── L2: [Input metric 2a]
│   └── L2: [Input metric 2b]
└── L1: [Direct driver 3]
    ├── L2: [Input metric 3a]
    └── L2: [Input metric 3b]
```

**L1 metrics** directly move the NSM. If L1 improves, NSM improves.
**L2 metrics** are inputs to L1. These are what teams can actually influence.

## Step 6: Set Baselines and Targets

| Metric | Type | Current Baseline | 3-Month Target | 6-Month Target |
|--------|------|-----------------|----------------|----------------|
| [NSM] | North Star | [value] | [target] | [target] |
| [L1-a] | L1 | [value] | [target] | [target] |
| [L1-b] | L1 | [value] | [target] | [target] |
| [L2-a] | L2 | [value] | [target] | [target] |
| [Guardrail 1] | Guardrail | [value] | [>threshold] | [>threshold] |
| [Guardrail 2] | Guardrail | [value] | [>threshold] | [>threshold] |

**If no baseline data:** Set this up as a measurement plan — "first, instrument these metrics. Then set targets after 4 weeks of baseline data."

## Step 7: Generate Document

Write to `docs/metrics/YYYY-MM-DD-north-star.md`:

```markdown
---
date: YYYY-MM-DD
product: "[product name]"
north_star_metric: "[NSM definition]"
time_period: "[daily | weekly | monthly]"
guardrails: ["guardrail1", "guardrail2"]
status: "active"
---

# North Star Metric: [Product]

## Ecosystem Map
[Players, value propositions, key actions, metrics]

## North Star Metric
> [NSM definition — precise, measurable, unambiguous]

### Why This Metric
[Strengths]

### What It Misses
[Drawbacks — addressed by guardrails]

## Guardrails
[Guardrail metrics with thresholds]

## Metrics Hierarchy
[NSM → L1 → L2 tree]

## Baselines and Targets
[Table with current values and targets]

## What Would Make Us Change This NSM
[Conditions under which this metric is no longer the right one]
```

## Post-Design Options

Use **AskUserQuestion tool**:

**Question:** "North Star Metric designed. What's next?"

**Options:**
1. **Run `/pm:goals`** — Set team goals from this NSM
2. **Run `/pm:measure`** — Build full measurement framework with predictions
3. **Run `/pm:growth-model`** — Connect NSM to growth loops
4. **Done** — NSM documented
