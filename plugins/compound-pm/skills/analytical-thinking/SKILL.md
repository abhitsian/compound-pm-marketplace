---
name: analytical-thinking
description: North Star Metrics, ecosystem analysis, goal-setting, and tradeoff frameworks. Use when defining metrics, setting team goals, or resolving product tradeoffs.
---

# Analytical Thinking Skill

## Purpose

Analytical thinking for PMs is the structured ability to define metrics, build business cases, set goals, and make tradeoffs. This skill provides frameworks for each, based on Ben Erez's PM analytical thinking methodology.

## Ecosystem Analysis

### Why Ecosystem First

Products don't serve one user — they serve an ecosystem of players. A marketplace serves buyers AND sellers. A content platform serves creators AND consumers. A SaaS tool serves end users AND admins AND buyers.

Your metrics must capture value creation for ALL key players, not just the most visible one.

### How to Map an Ecosystem

For each player (3-5 max):
1. **Identify** the player type (end users, creators, admins, buyers, advertisers)
2. **State** the primary value proposition to them
3. **List** the key actions they must take to realize value
4. **Define** metrics to track those actions

**Metric format:**
- `# of [players] who [action] per [day/week/month]` (measures reach)
- `# of [actions] performed per [day/week/month]` (measures volume)
- `Avg [actions] per [player] per [day/week/month]` (measures depth)

**Critical:** Always define what "active" means. Not "active users" but "users who completed [specific action] within [time period]."

## North Star Metric Design

### Selection Criteria

Your NSM must meet ALL of these:

| Criteria | Test |
|----------|------|
| **Multi-player value** | Growth means both users AND business win |
| **No natural ceiling** | Can grow continuously as product succeeds |
| **Raw count preferred** | Total count rather than percentage |
| **Per time period** | Per week/month, not cumulative |
| **Actionable** | Team can influence through product changes |
| **Understandable** | Every team member can explain it |

### NSM Examples by Product Type

| Product Type | Good NSM | Bad NSM |
|-------------|----------|---------|
| Marketplace | Weekly transactions completed | GMV (cumulative, masks problems) |
| Content platform | Weekly content pieces with >1 engagement | Total uploads (ignores quality) |
| SaaS tool | Weekly active teams with >3 members using | MRR (lagging, not actionable) |
| Social network | Weekly connections with bidirectional interaction | Registered users (vanity) |

### Guardrail Design

For every NSM drawback, create a guardrail:

**Pattern:** NSM is a count → Guardrail is a rate/percentage

| NSM Drawback | Guardrail Pattern |
|-------------|------------------|
| Could grow by adding low-quality items | % of items meeting quality threshold |
| Doesn't capture monetization | Revenue per active user |
| Could grow by adding unprofitable users | Unit economics (LTV/CAC) |
| Doesn't capture satisfaction | NPS or satisfaction score |

**Rule:** If guardrail drops below threshold, NSM growth is unhealthy.

### Time Period Selection

| Factor | Daily | Weekly | Monthly |
|--------|-------|--------|---------|
| Consumer social | Often best | Good | Too slow |
| B2B SaaS | Too noisy | Often best | Good for enterprise |
| Marketplace | Good | Often best | Too slow |
| Transactional | Context-dependent | Good | Often best |

Choose based on: natural usage cadence, signal-to-noise ratio, ability to act on data.

## Metrics Hierarchy

```
North Star Metric
├── L1: Direct drivers (team can influence)
│   ├── L2: Input metrics (individual can influence)
│   └── L2: Input metrics
├── L1: Direct driver
│   ├── L2: Input metric
│   └── L2: Input metric
└── Guardrails (quality/safety checks)
```

**L1 metrics** directly move the NSM. If L1 improves, NSM improves.
**L2 metrics** are inputs to L1. These are what individual contributors optimize.

## Goal Setting Framework

### The Altitude Shift

NSM is 50,000 feet. Team goals are ground level. The altitude shift connects them:

1. **Select ONE ecosystem player** to focus on (with rationale)
2. **Map their complete journey** to NSM contribution
3. **Identify conversion rates** between journey steps
4. **Find the biggest drop-off** — that's where goals live
5. **Set 3 candidate goals** as conversion rate improvements
6. **Score** each on Impact (how much it moves NSM) × Ability to Influence (can the team actually move this)
7. **Select ONE primary goal**

### Goal Guidelines

- Goals = **conversion rate improvements** between journey steps
- Do NOT set averages (they hide segment differences)
- Define directionally first ("increase X"), then set specific targets
- Always pair with anti-goals (what shouldn't get worse)

## Tradeoff Framework

### Tradeoff Types

| Type | Tension |
|------|---------|
| Breadth vs Depth | Many features vs few excellent ones |
| Speed vs Quality | Ship fast vs ship right |
| Short-term vs Long-term | Quick win vs lasting investment |
| User A vs User B | Optimize for one segment vs another |
| Build vs Buy | In-house vs third party |
| Simplicity vs Power | Easy to use vs feature-rich |
| Revenue vs Growth | Monetize vs expand the base |

### Analysis Structure

1. **Name the common goal** both options serve
2. **Frame each option** with exactly 2 pros and 2 cons
3. **Assess evidence** for each claim (data vs assumption)
4. **Check strategic alignment** (mission, NSM, segments, pillars)
5. **Make a decisive recommendation** with rationale
6. **State what would change your mind**

### Decision Heuristics

When analysis doesn't clearly favor one option:
- **Choose the most reversible option** — you can always change later
- **Choose the option that generates learning** — data > guessing
- **Choose the option closest to your strategy** — consistency compounds
- **When in doubt, do less** — simplicity is a feature
