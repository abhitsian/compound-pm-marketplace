---
name: metrics-design
description: Design complete metrics frameworks with outcome-intermediate-leading hierarchy, activation funnels, and engagement dimensions. Use when defining how to measure product success.
---

# Metrics Design Skill

## Purpose

Provide structured guidance for designing complete, measurable metrics frameworks. Adapts to the PM's preferred hierarchy from their profile.

## Metrics Hierarchy

### Default: Outcome → Intermediate → Leading

**Outcome Metrics** measure business impact:
- Revenue, retention, expansion
- Measured over longer periods (quarterly, annually)
- What the business ultimately cares about

**Intermediate Metrics** measure product outcomes:
- Self-service rate, task completion rate, satisfaction score
- Bridge between user behavior and business impact
- Measured over medium periods (monthly, quarterly)

**Leading Metrics** measure user behavior:
- Feature adoption, session frequency, engagement depth
- Early signals that predict intermediate and outcome metrics
- Measured continuously (daily, weekly)

### Alternative Hierarchies

**North Star → L1 → L2:**
- North Star: Single metric that captures core value delivered
- L1: Direct drivers of the North Star
- L2: Inputs to L1 metrics

**Business → Product → Feature:**
- Business: Revenue and retention metrics
- Product: User outcome metrics
- Feature: Usage and adoption metrics

## Activation Funnel

### Default: Setup → Aha → Habit

| Stage | Definition | How to Measure |
|-------|-----------|---------------|
| **Setup** | User has completed initial configuration and can use the product | % of users who complete setup; time to complete |
| **Aha** | User has experienced the core value for the first time | % of users who perform the key value action; time to Aha |
| **Habit** | User has developed a repeated pattern of value extraction | % of users who perform the value action [X] times in [Y] period |

### Defining Good Thresholds

- Setup completion should be > 80% (if lower, onboarding is broken)
- Aha rate should be > 50% of those who set up (if lower, value prop is unclear)
- Habit rate should be > 30% of those who reached Aha (if lower, value doesn't sustain)
- Time to Aha should be < 1 week for most B2B products

## Engagement Dimensions

### Default: Breadth, Depth, Intensity

| Dimension | What It Measures | Example |
|-----------|-----------------|---------|
| **Breadth** | How many features are used | Avg features used per week |
| **Depth** | How frequently features are used | Avg actions per week |
| **Intensity** | How much time/effort is invested | Avg session duration |

### User Segmentation

| Segment | Default Definition | Implications |
|---------|-------------------|-------------|
| **Casual** | 1-2 sessions per week | At risk of churn, need engagement |
| **Core** | 3-4 sessions per week | Healthy engagement, focus on deepening |
| **Power** | 5+ sessions per week | Champions, leverage for expansion |

## Tradeoff Metrics

Every optimization has a cost. Always define what might get worse:

| If Optimizing | Watch For Decline In |
|--------------|---------------------|
| Adoption rate | Quality of users adopted |
| Engagement depth | Breadth of feature usage |
| Self-service rate | Satisfaction with complex cases |
| Speed to market | Code quality, tech debt |
| Revenue per user | Total addressable users |

## Anti-Patterns

- Metrics without baselines (can't measure improvement)
- Outcome metrics only (no early warning system)
- Vanity metrics (total users, page views without context)
- Too many metrics (if everything is measured, nothing is prioritized)
- Metrics without owners (who acts on this data?)
- Metrics without thresholds (what's good vs bad?)
