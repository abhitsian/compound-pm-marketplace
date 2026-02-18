---
name: pm:tradeoff
description: Structure and resolve product tradeoffs with clear criteria, evidence, and reversibility analysis
argument-hint: "[tradeoff to analyze]"
---

# Tradeoff Analysis

## Purpose

Every product decision is a tradeoff. This command forces explicit analysis rather than implicit compromise. Name the tradeoff, identify what both options serve, frame the evidence, and make a decisive recommendation tied to your strategy and metrics.

Based on Ben Erez's analytical thinking tradeoff framework.

## Input

<tradeoff_input> #$ARGUMENTS </tradeoff_input>

**If empty:** Ask "What tradeoff are you facing? Describe the two (or more) options pulling in different directions."

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
```

Load strategy and goals:
```bash
cat docs/strategy/*.md 2>/dev/null
cat docs/goals/*.md 2>/dev/null
cat docs/metrics/*north-star*.md 2>/dev/null
```

## Step 1: Identify the Tradeoff Type

| Type | Description | Example |
|------|-----------|---------|
| **Breadth vs Depth** | Serve more users lightly or fewer users deeply | Add 5 integrations vs make 1 integration excellent |
| **Speed vs Quality** | Ship faster with lower quality or slower with higher quality | MVP now vs polished product in 2 months |
| **Short-term vs Long-term** | Quick win now vs investment that pays off later | Feature patch vs platform refactor |
| **User A vs User B** | Optimize for one segment at the expense of another | Power users vs new users |
| **Build vs Buy** | Build in-house or use a third-party solution | Custom analytics vs Amplitude |
| **Simplicity vs Power** | Keep it simple or add capabilities | Opinionated defaults vs configuration |
| **Revenue vs Growth** | Monetize now or grow the user base | Paywall vs freemium |
| **Real estate** | Limited space — what gets prominence | Homepage: feature A vs feature B |
| **Required vs Optional** | Force users through a step or make it optional | Onboarding: mandatory tutorial vs skip option |

## Step 2: Clarify the Common Goal

Before analyzing options, answer: **What is the shared goal both options are trying to achieve?**

> "Both options are trying to [common goal]. They differ in [how they approach it]."

This is critical. If options don't share a common goal, it's not a tradeoff — it's a prioritization decision (use `/pm:decide` instead).

## Step 3: Frame Each Option

For each option (2-3 max):

```markdown
### Option [A/B/C]: [Name]

**What it means concretely:** [Specific description]
**Effort/cost:** [Time, resources, complexity]

**Pro 1:** [Specific advantage]
**Pro 2:** [Specific advantage]

**Con 1:** [Specific disadvantage]
**Con 2:** [Specific disadvantage]

**Who benefits:** [Which segments, stakeholders]
**Who is hurt:** [Which segments, stakeholders]
**Reversibility:** [Easy / Hard / Impossible]
```

**Limit to TWO pros and TWO cons per option.** Forces you to identify what matters most.

## Step 4: Evidence Check

For each pro and con, assess the evidence:

| Claim | Evidence Type | Confidence |
|-------|-------------|-----------|
| [Pro/Con statement] | [Data / User research / Expert opinion / Assumption] | [High / Medium / Low] |

**Flag claims with no evidence.** These are assumptions, not facts. Decide if you need to validate before choosing.

## Step 5: Strategic Alignment

Evaluate each option against your strategy:

| Criteria | Option A | Option B |
|----------|---------|---------|
| **Aligns with product mission** | [How?] | [How?] |
| **Moves the North Star Metric** | [How much?] | [How much?] |
| **Serves priority segments** | [Which?] | [Which?] |
| **Supports strategic pillars** | [Which?] | [Which?] |
| **Consistent with non-priorities** | [Y/N] | [Y/N] |

## Step 6: Make a Decision

**Recommend ONE option.** Be decisive.

```markdown
## Recommendation: Option [X]

**Why:** [2-3 reasons tied to strategy, metrics, and evidence]

**Key risk:** [The biggest thing that could go wrong]
**Mitigation:** [How to catch it early]

**What would change my mind:** [Specific conditions or data]
```

**If you truly can't decide:** The options might be too similar to matter. In that case: pick the most reversible one, ship it, and learn.

## Step 7: Generate Document

Write to `docs/tradeoffs/YYYY-MM-DD-<tradeoff-name>.md`:

```markdown
---
date: YYYY-MM-DD
tradeoff: "[description]"
type: "[breadth_vs_depth | speed_vs_quality | etc]"
chosen: "[Option name]"
reversibility: "[easy | hard | impossible]"
confidence: "[high | medium | low]"
---

# Tradeoff: [Description]

## Common Goal
[What both options are trying to achieve]

## Options
[Option A and B with pros, cons, who benefits/hurt]

## Evidence Assessment
[Confidence levels for each claim]

## Strategic Alignment
[How each option maps to strategy, NSM, segments]

## Decision: [Option X]
[Recommendation with rationale]

## What Would Change This
[Conditions for revisiting]

## Review Date
[When to check if the decision was right]
```

## Post-Analysis Options

Use **AskUserQuestion tool**:

**Question:** "Tradeoff analyzed. What's next?"

**Options:**
1. **Run `/pm:decide`** — Full decision framework if this needs more rigor
2. **Run `/pm:simulate`** — Simulate user reaction to the chosen option
3. **Run `/pm:bias-check`** — Check if biases are affecting this tradeoff
4. **Done** — Tradeoff documented
