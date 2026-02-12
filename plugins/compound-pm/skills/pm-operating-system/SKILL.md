---
name: pm-operating-system
description: Load and apply the PM's personalized operating system from pm-profile.yaml. Use when any /pm: command needs to adapt to the PM's frameworks, vocabulary, and past patterns.
---

# PM Operating System Skill

## Purpose

Read the PM's profile and adapt all outputs to their preferred frameworks, vocabulary, and learned patterns. This is the personalization engine that makes every command work differently for every PM.

## When to Use

This skill is loaded automatically by every `/pm:` command. It reads `pm-profile.yaml` and provides context-specific guidance.

## How Personalization Works

### Framework Adaptation

When the PM profile specifies a framework preference, use it:

| Profile Field | Adapts |
|--------------|--------|
| `frameworks.opportunity_evaluation` | How `/pm:opportunity` frames problems |
| `frameworks.solution_classification` | How `/pm:solution` classifies solutions |
| `frameworks.metrics_hierarchy` | How `/pm:spec` and `/pm:measure` structure metrics |
| `frameworks.activation_funnel` | Activation stage names and definitions |
| `frameworks.user_segmentation` | User segment names and definitions |
| `frameworks.engagement_metrics` | Engagement dimension names |
| `frameworks.buy_in_techniques` | Which techniques `/pm:buyin` prioritizes |

### Vocabulary Adaptation

When the PM profile specifies vocabulary preferences, use their terms:

| Profile Field | Replaces |
|--------------|----------|
| `vocabulary.primary_metric_term` | "outcome metric" / "north star" / "KPI" |
| `vocabulary.problem_framing` | "HMW" / "problem statement" / "JTBD" |
| `vocabulary.roadmap_lens` | Roadmap evaluation dimensions |

### Threshold Pre-filling

When `thresholds` exist in the profile:
- Pre-fill activation targets in `/pm:measure`
- Suggest metric targets based on past averages
- Flag when current predictions deviate significantly from historical patterns

### Past Pattern References

When `project_patterns` exist in the profile:
- Surface similar past projects during `/pm:opportunity`
- Reference past metric actuals during `/pm:measure`
- Flag when current approach resembles a past failure
- Suggest approaches that worked for similar projects

### Decision Log References

When `decision_log` exists in the profile:
- Surface past decisions during `/pm:solution`
- Flag when a similar trade-off was made before
- Show outcomes of past similar decisions

## Profile Growth

The profile grows through usage:

| Action | Profile Update |
|--------|---------------|
| `/pm:compound` after a project | Adds project pattern, updates thresholds, adds to decision log |
| PM skips a framework during a command | Notes which frameworks PM actually uses vs skips |
| PM modifies a suggestion | Learns PM's preferences for future suggestions |

## Minimal Profile Behavior

When no profile exists or profile is minimal:
- Use sensible defaults
- Don't reference past patterns (none exist)
- Don't pre-fill thresholds (no history)
- Suggest running `/pm:onboard` once enough cycles have passed

## Profile Schema

```yaml
name: string
role: string
domain: string
experience_level: string
created: date
last_updated: date

frameworks:
  opportunity_evaluation: string
  solution_classification: string
  metrics_hierarchy: string
  activation_funnel: string
  user_segmentation: string
  engagement_metrics: string
  buy_in_techniques: [string]

vocabulary:
  primary_metric_term: string
  problem_framing: string
  roadmap_lens: [string]

project_patterns:
  - project: string
    date: date
    domain: string
    outcome_metric: string
    predicted: string
    actual: string
    delta: string
    key_learning: string
    activation: {setup: string, aha: string, habit: string}
    engagement: {casual_pct: string, core_pct: string, power_pct: string}
    business_impact: string

thresholds:
  avg_activation_setup: string
  avg_activation_aha: string
  avg_activation_habit: string
  avg_estimation_accuracy: string

decision_log:
  - date: date
    feature: string
    decision: string
    rationale: string
    outcome: string
    would_decide_differently: string

framework_notes: [string]

stakeholders: {}
```
