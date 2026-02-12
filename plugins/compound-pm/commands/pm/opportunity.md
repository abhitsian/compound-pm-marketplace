---
name: pm:opportunity
description: Transform a raw insight or idea into a structured, evaluated opportunity
argument-hint: "[data insight, user insight, or opportunity description]"
---

# Opportunity Evaluation

## Purpose

Take a raw signal — a data insight, user complaint, competitive move, or strategic initiative — and run it through your PM framework to produce a structured opportunity document with clear business context, customer problem framing, and prioritization.

## Input

<opportunity_input> #$ARGUMENTS </opportunity_input>

**If empty:** Ask "What opportunity are you evaluating? Describe the signal — a data insight, user feedback, competitive move, or strategic initiative."

## Step 0: Load PM Profile

```bash
cat pm-profile.yaml 2>/dev/null
```

**If profile exists:** Use the PM's preferred frameworks, vocabulary, and past patterns throughout.

**If no profile:** Use sensible defaults and suggest running `/pm:onboard` after.

## Step 1: Classify the Signal

Determine the type of input:

| Signal Type | Starts With | Need to Figure Out |
|-------------|-------------|-------------------|
| **User insight** | What (observed behavior) | Is this a real problem? Who, where, why? |
| **Data insight** | Where (metric anomaly) | What's causing it? Who, why? |
| **Competitive move** | External pressure | Is this relevant? Should we react? |
| **Strategic initiative** | Business direction | What customer problem maps to this? |

Use **AskUserQuestion tool** if the signal type is ambiguous.

## Step 2: Research Phase (Parallel)

Launch these agents **in parallel**:

- Task **opportunity-researcher**: Search `docs/opportunities/` and `docs/compounds/` for similar past opportunities. What did we learn? What worked?
- Task **competitive-landscape**: If relevant, research competitive positioning and market context.

## Step 3: Frame the Customer Problem

Use the PM's preferred problem framing (from `pm-profile.yaml`). Default: 5-question framework.

Ask and answer (collaboratively with the user):

1. **What is the problem?** — Observable pain, not assumed need
2. **Who are we solving it for?** — Specific persona and segment
3. **How does it impact strategy?** — Connection to business mission/growth model
4. **How do we know this is a problem?** — Evidence (data, user quotes, support tickets)
5. **Why do we think this is happening?** — Root cause hypothesis

Frame as a **How Might We** statement:
> "How might we [enable/improve/reduce] [outcome] for [persona] by [approach]?"

## Step 4: Evaluate Business Context

Assess along three dimensions:

### Monetization Potential
- Revenue opportunity (quantify if possible)
- Retention impact
- Expansion/upsell potential
- Cost reduction

### Strategic Fit
- Alignment with product vision
- Platform/cross-BU leverage
- Defensibility contribution (reference Hamilton 7 Powers if PM uses them)

### Competitive Pressure
- Competitor activity in this space
- Market timing
- Risk of NOT doing this

## Step 5: Prioritize the Opportunity

Evaluate using the PM's preferred framework. Default:

| Dimension | Assessment |
|-----------|-----------|
| **Impact potential** | How big is the expected return? |
| **Time to return** | How quickly will we see results? |
| **Compounding vs linear** | Does this enable future bets? |
| **Multi-outcome impact** | Does it serve multiple business objectives? |
| **Differentiation value** | Differentiator, MMR, or Neutralizer? |
| **Order of operations** | Must this happen before other things? |

### Risk vs Impact Classification
- **High Risk, High Impact** — Big Bets
- **High Risk, Low Impact** — Duds (avoid)
- **Low Risk, High Impact** — No Brainers
- **Low Risk, Low Impact** — Quick Wins

## Step 6: Reference Past Patterns

**If PM profile has `project_patterns`:**
- Find the most similar past opportunity
- Show: "This looks similar to [past project]. That one achieved [outcome]. Key learning: [insight]."

**If no past patterns:** Skip this step.

## Step 7: Generate Opportunity Document

Write to `docs/opportunities/YYYY-MM-DD-<kebab-case-name>.md`:

```markdown
---
date: YYYY-MM-DD
signal_type: [user_insight | data_insight | competitive | strategic]
persona: "[target persona]"
business_objective: "[primary business objective]"
classification: "[differentiator | mmr | neutralizer]"
impact_estimate: "[high | medium | low]"
confidence: "[high | medium | low]"
status: "evaluated"
---

# [Opportunity Title]

## Signal
[What triggered this opportunity — the raw insight]

## Customer Problem
[5-question framework output]

### How Might We
> [HMW statement]

## Business Context

### Monetization
[Revenue opportunity, retention impact, expansion potential]

### Strategic Fit
[Vision alignment, platform leverage, defensibility]

### Competitive Pressure
[Market context, competitor activity]

## Prioritization
[Impact, time to return, compounding potential, differentiation]

### Risk vs Impact: [Big Bet | No Brainer | Quick Win]

## Past Patterns
[Similar past opportunities and what we learned — or "First opportunity in this space"]

## Open Questions
[What we still need to validate]

## Next Steps
→ `/pm:solution` to design and evaluate solutions
→ `/pm:spec` if solution is already known
```

## Post-Generation Options

Use **AskUserQuestion tool**:

**Question:** "Opportunity evaluated. What's next?"

**Options:**
1. **Run `/pm:solution`** — Design and evaluate solution approaches
2. **Refine the opportunity** — Adjust framing, add context
3. **Park it** — Save for later consideration
4. **Compare with other opportunities** — See all evaluated opportunities side by side
