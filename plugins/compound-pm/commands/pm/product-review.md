---
name: pm:product-review
description: Generate a weekly/biweekly product review covering shipped work, metrics, decisions needed, and learnings
argument-hint: "[optional: 'weekly', 'biweekly', 'monthly', or specific date range]"
---

# Product Review

## Purpose

PMs run recurring rituals. This command generates a structured product review by pulling from your active bets, recent compounds, measurements, and decisions. Adapts to your audience and cadence.

## Input

<review_input> #$ARGUMENTS </review_input>

**Default:** Weekly review.

## Step 0: Load Everything

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
ls docs/specs/ docs/measurements/ docs/compounds/ docs/decisions/ docs/research/ 2>/dev/null
```

## Step 1: Choose Format

Use **AskUserQuestion tool**:

"Who is this product review for?"

**Options:**
1. **Your team** — Detailed, operational, what's next
2. **Your manager / leadership** — Strategic, metrics-focused, decisions needed
3. **Cross-functional partners** — Dependencies, asks, alignment
4. **All-hands / company** — High-level, impact-focused, narrative

## Step 2: Gather Inputs

### What Shipped (past period)
Scan recent files:
- `docs/specs/` — Specs that moved to "shipped" status
- `docs/compounds/` — Recent learnings
- `docs/decisions/` — Recent decisions made

### Metrics Movement
From `docs/measurements/` and `work-context.yaml`:
- Key metrics and their movement
- Predictions vs actuals where available

### Active Work
From `work-context.yaml`:
- In-flight projects and their status
- Active bets and confidence levels

### Decisions Needed
From `docs/decisions/` with status "pending":
- Open decisions requiring input
- Upcoming decisions on the horizon

### Learnings
From recent `docs/compounds/`:
- Key learnings from recent cycles
- Framework updates

### Risks & Blockers
From `work-context.yaml`:
- Dependencies at risk
- Customer escalations
- Competitive moves

## Step 3: Generate Review

### For Team (detailed, operational)

```markdown
# Product Review — Week of [Date]

## Shipped This Week
- [Feature/change] — [impact in one sentence]
- [Feature/change] — [impact]

## Metrics Snapshot
| Metric | Last Week | This Week | Trend | Target |
|--------|-----------|-----------|-------|--------|
| [Metric 1] | [value] | [value] | [arrow] | [target] |

## Active Work
| Project | Status | Next Milestone | Risk |
|---------|--------|---------------|------|
| [Project 1] | [status] | [milestone] | [risk level] |

## Decisions Made
- [Decision]: Chose [option] because [reason]

## Decisions Needed
- [Decision]: Need input from [who] by [when]

## Learnings
- [Learning from this week]

## Next Week Focus
1. [Priority 1]
2. [Priority 2]
3. [Priority 3]

## Blockers / Help Needed
- [Blocker and what's needed to unblock]
```

### For Leadership (strategic, metrics)

```markdown
# Product Update — [Period]

## Executive Summary
[3 sentences: what happened, what it means, what's next]

## Key Metrics
| Metric | Actual | Target | Status |
|--------|--------|--------|--------|
| [Outcome metric] | [value] | [target] | [on_track/at_risk/off_track] |

## Highlights
- [Biggest win and its business impact]

## Active Bets
| Bet | Confidence | Expected Impact | Status |
|-----|-----------|----------------|--------|
| [Bet 1] | [H/M/L] | [$X / Y%] | [status] |

## Decisions Needed from You
1. [Decision]: [context in 1 sentence]. Options: [A] or [B]. Recommend: [X].

## Risks
- [Top risk and mitigation plan]

## Customer Signal
- [Most important thing we heard from customers this period]
```

### For Cross-functional (dependencies, asks)

```markdown
# Product Sync — [Date]

## What We Shipped (affects your team)
- [Feature] — [how it affects them]

## Coming Next (heads-up)
- [Upcoming change] — [what they need to know]

## Asks from Us
- [What we need from them, by when]

## Asks from You
- [What they've asked for, our timeline]

## Shared Metrics
| Metric | Movement | Notes |
|--------|----------|-------|
| [Shared metric] | [trend] | [context] |
```

### For All-Hands (narrative, impact)

```markdown
# Product Update — [Period]

## The Story
[Narrative: problem we're solving, what we built, what happened — in customer terms, not feature terms]

## By the Numbers
- [Impact metric 1]
- [Impact metric 2]

## What's Next
[One paragraph on where we're headed]

## Team Shoutout
[Credit to people who made it happen]
```

## Step 4: Save and Share

Write to `docs/reviews/YYYY-MM-DD-<type>-review.md`

**Options:**
1. **Copy to clipboard** — Ready to paste into Slack/email
2. **Refine** — Adjust tone, add/remove sections
3. **Generate for another audience** — Create a different version
4. **Done**
