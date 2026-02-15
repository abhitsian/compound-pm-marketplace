---
name: pm:goals
description: Set team goals by connecting team-level metrics to the North Star Metric
argument-hint: "[team or area to set goals for]"
---

# Team Goal Setting

## Purpose

The "altitude shift" — from 50,000-foot product metrics to team-level goals that people can actually influence. This command takes your North Star Metric and translates it into specific, achievable team goals for the next 3-6 months.

Based on Ben Erez's analytical thinking framework.

## Input

<goals_input> #$ARGUMENTS </goals_input>

**If empty:** Ask "What team or product area do you want to set goals for?"

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
```

Load NSM and metrics:
```bash
cat docs/metrics/*north-star*.md 2>/dev/null
cat docs/measurements/*.md 2>/dev/null
```

**If no NSM exists:** Recommend running `/pm:north-star` first.

## Step 1: Select the Ecosystem Player

From your NSM ecosystem map, choose ONE player to focus on:

Use **AskUserQuestion tool**:

**Question:** "Which ecosystem player are you setting goals for?"

Present the players from the NSM ecosystem map, plus:
- **Rationale required:** Why this player? (Biggest lever on NSM? Most underserved? Strategic priority?)

## Step 2: Map the User Journey

For the selected player, map the complete journey that leads to NSM impact:

```
[Entry] → [Step 1] → [Step 2] → ... → [Core Value Action] → [Repeat/Expand]
```

For each step:
- **What % of users progress to the next step?** (conversion rate)
- **What's the average time between steps?**
- **Where's the biggest drop-off?**

This creates a conversion funnel from entry to NSM contribution.

## Step 3: Identify Goal Candidates

Brainstorm exactly 3 potential goals the team can influence in 3-6 months.

**Goal guidelines:**
- Goals should represent **conversion rate improvements** between journey steps
- Do NOT set averages as goals (averages hide segment differences)
- Define goals **directionally** first (e.g., "increase session starts per user") — set specific targets after
- Goals must be things the TEAM can actually move through product/design/engineering work

For each candidate goal:

```markdown
### Goal Candidate [N]: [Description]

**Journey step:** [Step X → Step Y]
**Current conversion:** [%]
**Why this matters for NSM:** [Specific causal chain from this metric to NSM]
**How the team would move this:** [Specific product changes]
**Impact score:** [High | Medium | Low] — How much does this move the NSM?
**Ability to influence score:** [High | Medium | Low] — Can the team actually drive this?
```

## Step 4: Score and Select

| Goal | Impact (1-5) | Ability to Influence (1-5) | Weighted Score |
|------|-------------|--------------------------|----------------|
| [Goal 1] | [score] | [score] | [Impact×2 + Influence×1] |
| [Goal 2] | [score] | [score] | [score] |
| [Goal 3] | [score] | [score] | [score] |

**Select ONE primary goal.** (Maybe one secondary.)

**Explain specifically:** "Improving [goal metric] from [current] to [target] will move the NSM by approximately [X] because [causal chain]."

## Step 5: Define the Goal Precisely

```markdown
## Primary Goal

**Statement:** Increase [metric] from [baseline] to [target] by [date]
**Ecosystem player:** [who this affects]
**NSM connection:** [how this moves the North Star]
**Measurement:** [exactly how to measure — tool, query, cadence]
**Leading indicator:** [what signals progress before the goal metric moves]

## Success Criteria
- **Green:** [metric] ≥ [target]
- **Yellow:** [metric] between [X] and [target]
- **Red:** [metric] < [X]
```

## Step 6: Define Anti-Goals

What should NOT get worse while pursuing this goal?

| Anti-Goal (Guardrail) | Threshold | Why It Matters |
|----------------------|-----------|----------------|
| [Metric that might suffer] | [Don't go below X] | [Consequence of degradation] |

## Step 7: Tradeoff Awareness

Every goal has tradeoffs. Name them:

- "By focusing on [goal], we're NOT focusing on [alternative]"
- "If [goal metric] improves but [guardrail metric] drops, we should [specific action]"
- "This goal optimizes for [segment/player] at the potential expense of [other segment/player]"

## Step 8: Generate Goal Document

Write to `docs/goals/YYYY-MM-DD-<team>-goals.md`:

```markdown
---
date: YYYY-MM-DD
team: "[team name]"
goal_period: "[start date] to [end date]"
primary_goal: "[goal statement]"
nsm_connection: "[how goal connects to NSM]"
baseline: "[current metric value]"
target: "[target metric value]"
---

# Team Goals: [Team] — [Period]

## North Star Metric Reference
[Current NSM, L1/L2 metrics]

## User Journey
[Conversion funnel for selected ecosystem player]

## Goal Candidates Evaluated
[3 candidates with scores]

## Primary Goal
[Precise goal statement with success criteria]

## Anti-Goals
[What shouldn't get worse]

## Tradeoffs
[What we're choosing not to optimize]

## Review Schedule
- Weekly: Check leading indicators
- Bi-weekly: Review goal metric
- End of period: Full retrospective → `/pm:compound`
```

## Post-Goal Options

Use **AskUserQuestion tool**:

**Question:** "Goals set. What's next?"

**Options:**
1. **Run `/pm:measure`** — Build full measurement framework with predictions
2. **Run `/pm:tradeoff`** — Deep dive on a specific tradeoff
3. **Share with team** — Generate goal communication via `/pm:buyin`
4. **Done** — Goals documented
