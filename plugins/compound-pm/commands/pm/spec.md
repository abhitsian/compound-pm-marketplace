---
name: pm:spec
description: Transform a solution into a detailed, actionable product specification
argument-hint: "[solution doc path, feature description, or opportunity context]"
---

# Product Specification

## Purpose

Take a recommended solution and produce a detailed spec that engineering, design, and stakeholders can execute against. Adapts to the PM's preferred spec structure, metrics framework, and vocabulary.

## Input

<spec_input> #$ARGUMENTS </spec_input>

**If a file path:** Read the solution or opportunity document.
**If a description:** Use as context.
**If empty:** Check `docs/solutions/` for the most recent solution doc.

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
```

Read solution doc to extract: recommended solution, metrics, risk assessment, validation plan.

## Step 1: Vision Narrative

Write a vision narrative following the PM's preferred structure. Default: 3-part structure.

### Part 1: The Aspirational Problem
Describe the problem in visceral, emotional terms. Lead with the user's pain.
- Use specific numbers and scenarios
- Make the reader feel the problem

### Part 2: The Opinionated Solution
Describe the solution in detail. Be specific and opinionated.
- Walk through the user journey step by step
- Show how each pain point is resolved
- Include key interactions and moments

### Part 3: The User-Centric Resolution
Close with what the user's world looks like after.
- Concrete outcome (time saved, friction removed)
- Emotional resolution (confidence, ease, delight)

## Step 2: Customer Journey Map

Map the end-to-end user journey with friction points:

```markdown
| Step | User Action | Current Experience | New Experience | Friction Removed |
|------|------------|-------------------|----------------|-----------------|
| 1    | [action]   | [pain]            | [improvement]  | [friction type] |
```

Rank friction points by:
- **Intensity** — How painful is this?
- **Frequency** — How often does this happen?
- **Impact** — What's the business impact of solving this?

## Step 3: Solution Details

### Core Capabilities
For each capability in the solution:
- **What it does** — Functional description
- **Why it matters** — User value
- **How it works** — Key interactions
- **Differentiator / MMR / Neutralizer** — Classification

### Trade-offs
Document every trade-off decision:
- **What we chose** vs **What we didn't choose**
- **Short-term** vs **Long-term** implications
- **Rationale** — Why this trade-off is acceptable

### Scope Boundaries
- **In scope** — What we're building
- **Out of scope** — What we're explicitly NOT building and why
- **Future scope** — What comes next if this succeeds

## Step 4: Metrics Framework

Use the PM's preferred metrics hierarchy. Default:

### Outcome Metric
The business outcome this drives. Define:
- Metric name and formula
- Current baseline
- Target
- Measurement methodology

### Activation Funnel
Use the PM's preferred funnel. Default: Setup → Aha → Habit.

| Stage | Definition | Target | Measurement |
|-------|-----------|--------|-------------|
| **Setup** | [What constitutes setup complete] | [%] | [How measured] |
| **Aha** | [First value moment] | [%] | [How measured] |
| **Habit** | [Repeated value — define frequency] | [%] | [How measured] |

**If PM profile has `thresholds`:** Pre-fill targets based on past project averages.

### Engagement Metrics
Use the PM's preferred dimensions. Default: Breadth / Depth / Intensity.

| Dimension | Metric | Definition |
|-----------|--------|-----------|
| **Breadth** | Features used | Average features used per [period] |
| **Depth** | Frequency | Average [actions] per [period] |
| **Intensity** | Time spent | Average time per session |

### User Segmentation
Use the PM's preferred segmentation. Default: Casual / Core / Power.

| Segment | Definition | Target Distribution |
|---------|-----------|-------------------|
| **Casual** | [frequency definition] | [%] |
| **Core** | [frequency definition] | [%] |
| **Power** | [frequency definition] | [%] |

### Business Metrics
- Revenue impact (quantified)
- Retention impact
- Expansion/upsell potential
- Platform value

## Step 5: Pricing & Packaging

Based on the PM's past patterns:
- **Who benefits?** All customers or a segment?
- **Which SKU?** Base, Pro, Add-on, New SKU?
- **Rationale** — Why this packaging decision?
- **WTP analysis** — What are alternatives? What would customers pay?

**If PM profile has past packaging decisions:** Reference them.

## Step 6: Launch Criteria

### Continue / Pause / Pivot Framework
Define criteria for each decision:

| Decision | Criteria |
|----------|---------|
| **Continue investing** | [specific metric thresholds met] |
| **Pause investment** | [metric thresholds not met after X period] |
| **Pivot** | [fundamental assumption invalidated] |

### Positioning
- **Positioning strategy** — Differentiator-based, value-based, or category-based
- **Key message** — One sentence that captures the value
- **Buyer awareness** — What do buyers need to understand?

## Step 7: Generate Spec Document

Write to `docs/specs/YYYY-MM-DD-<kebab-case-name>-spec.md`:

```markdown
---
date: YYYY-MM-DD
opportunity: "[link to opportunity doc]"
solution: "[link to solution doc]"
status: "draft"
outcome_metric: "[primary outcome metric]"
target: "[metric target]"
sku: "[base | pro | add-on | new]"
---

# Spec: [Feature Title]

## Vision Narrative
[3-part narrative]

## Customer Journey
[Journey map with friction points]

## Solution Details
### Capabilities
### Trade-offs
### Scope

## Metrics
### Outcome Metric
### Activation Funnel
### Engagement
### User Segments
### Business Metrics

## Pricing & Packaging
[SKU decision with rationale]

## Launch Criteria
### Continue / Pause / Pivot
### Positioning

## Open Questions
[Unresolved items]

## Next Steps
→ `/pm:review` to get multi-agent spec review
→ `/pm:buyin` to create stakeholder narratives
→ Hand off to engineering for `/workflows:plan`
```

## Post-Generation Options

**Options:**
1. **Run `/pm:review`** — Multi-agent spec review
2. **Run `/pm:buyin`** — Create stakeholder alignment narratives
3. **Refine spec** — Adjust sections
4. **Hand off to engineering** — Generate a `/workflows:plan` compatible plan
