---
name: pm:measure
description: Create a comprehensive measurement framework with predictions for post-launch tracking
argument-hint: "[spec doc path or feature name]"
---

# Measurement Framework

## Purpose

Generate a complete measurement framework that defines what to track, how to track it, baseline values, targets, and predictions. The predictions are compared against actuals during `/pm:compound` to calibrate the PM's estimation accuracy over time.

## Input

<measure_input> #$ARGUMENTS </measure_input>

**If a file path:** Read the spec document.
**If empty:** Check `docs/specs/` for the most recent spec.

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
```

Extract past metric patterns and learned thresholds.

## Step 1: Define the Metrics Hierarchy

Use the PM's preferred hierarchy. Default: Outcome → Intermediate → Leading.

### Outcome Metrics (Business Impact)
What the business cares about:

| Metric | Formula | Baseline | Target | Confidence |
|--------|---------|----------|--------|-----------|
| [e.g., Revenue impact] | [calculation] | [current] | [goal] | [H/M/L] |
| [e.g., Retention rate] | [calculation] | [current] | [goal] | [H/M/L] |

### Intermediate Metrics (Product Outcomes)
What the product delivers:

| Metric | Formula | Baseline | Target | Confidence |
|--------|---------|----------|--------|-----------|
| [e.g., Self-service rate] | [calculation] | [current] | [goal] | [H/M/L] |
| [e.g., Task completion rate] | [calculation] | [current] | [goal] | [H/M/L] |

### Leading Metrics (User Behavior)
Early signals:

| Metric | Formula | Baseline | Target | Confidence |
|--------|---------|----------|--------|-----------|
| [e.g., Feature adoption rate] | [calculation] | [current] | [goal] | [H/M/L] |
| [e.g., Daily active users] | [calculation] | [current] | [goal] | [H/M/L] |

## Step 2: Activation Funnel

Use the PM's preferred funnel. Default: Setup → Aha → Habit.

**If PM profile has `thresholds`:** Pre-fill targets from past project averages and note: "Based on your past projects, typical activation rates are [X]. Adjust if this context differs."

| Stage | Definition | Predicted Target | Measurement | Timeframe |
|-------|-----------|-----------------|-------------|-----------|
| **Setup** | [criteria] | [%] | [how] | [expected time] |
| **Aha** | [criteria] | [%] | [how] | [expected time] |
| **Habit** | [criteria] | [%] | [how] | [expected time] |

## Step 3: Engagement Framework

### Dimensions

| Dimension | Metric | Definition | Predicted Target |
|-----------|--------|-----------|-----------------|
| **Breadth** | Features used | Avg features per [period] | [target] |
| **Depth** | Frequency | Avg [actions] per [period] | [target] |
| **Intensity** | Time/effort | Avg time per session | [target] |

### User Segmentation

| Segment | Definition | Predicted Distribution |
|---------|-----------|----------------------|
| **Casual** | [frequency] | [%] |
| **Core** | [frequency] | [%] |
| **Power** | [frequency] | [%] |

## Step 4: Business Impact Predictions

Make explicit, falsifiable predictions:

```markdown
## Predictions (to be validated in /pm:compound)

### 30-Day Predictions
- [ ] Adoption rate: [X]% of target users will try the feature
- [ ] Setup completion: [X]% of those who try will complete setup

### 90-Day Predictions
- [ ] Activation: [X]% will reach Aha moment
- [ ] Retention: [X]% will become habitual users
- [ ] Engagement: WAU will reach [X]%

### 6-Month Predictions
- [ ] Business impact: [specific revenue/retention/expansion prediction]
- [ ] Customer outcome: [specific outcome metric prediction]

### Confidence Notes
- Most confident about: [metric] because [reason]
- Least confident about: [metric] because [reason]
```

## Step 5: Continue / Pause / Pivot Criteria

| Timeframe | Continue If | Pause If | Pivot If |
|-----------|-----------|---------|---------|
| **30 days** | [specific thresholds] | [specific thresholds] | [specific thresholds] |
| **90 days** | [specific thresholds] | [specific thresholds] | [specific thresholds] |
| **6 months** | [specific thresholds] | [specific thresholds] | [specific thresholds] |

## Step 6: Generate Measurement Document

Write to `docs/measurements/YYYY-MM-DD-<feature>-measurement.md`:

```markdown
---
date: YYYY-MM-DD
feature: "[feature name]"
spec: "[link to spec doc]"
status: "predictions"
review_dates:
  - "YYYY-MM-DD"  # 30-day review
  - "YYYY-MM-DD"  # 90-day review
  - "YYYY-MM-DD"  # 6-month review
---

# Measurement: [Feature Name]

## Metrics Hierarchy
[Outcome, Intermediate, Leading metrics]

## Activation Funnel
[Setup → Aha → Habit with targets]

## Engagement Framework
[Breadth, Depth, Intensity with segments]

## Predictions
[Explicit 30/90/180 day predictions]

## Continue / Pause / Pivot
[Decision criteria by timeframe]

## Actuals (filled in during /pm:compound)
### 30-Day Review
_To be completed on [date]_

### 90-Day Review
_To be completed on [date]_

### 6-Month Review
_To be completed on [date]_
```

## Post-Generation Options

**Options:**
1. **Set calendar reminders** — Create review dates
2. **Build dashboard** — Outline dashboard requirements for engineering
3. **Run `/pm:compound`** — If this is a post-launch measurement update
4. **Done** — Measurement framework is ready
