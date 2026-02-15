---
name: pm:strategy
description: Build a complete product strategy — segmentation, differentiation, strategic pillars, non-priorities, and roadmap
argument-hint: "[product or product area]"
---

# Product Strategy

## Purpose

Strategy is a function of segmentation and differentiation. This command produces a complete strategy document that sits ABOVE the opportunity loop — it's the frame that determines which opportunities matter and which don't.

Uses Shreyas Doshi's strategy template: segments, market context, strategic pillars, non-priorities, and roadmap with metrics.

## Input

<strategy_input> #$ARGUMENTS </strategy_input>

**If empty:** Ask "What product or product area are you building a strategy for?"

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
```

Load existing segments and differentiation analysis:
```bash
cat docs/segments/*.md 2>/dev/null
cat docs/strategy/*differentiation*.md 2>/dev/null
```

**If no segments exist:** Recommend running `/pm:segment` first, but offer to do lightweight segmentation inline.

**If no differentiation analysis exists:** Recommend running `/pm:differentiate` first, but offer to do lightweight analysis inline.

## Step 1: One-Sentence Strategy

Before going deep, force clarity:

> "[Our product] wins by [how we differentiate] for [priority segments] against [main alternatives]."

This sentence must be:
- **Specific** — not "by being the best"
- **Choosy** — names WHO we serve (implies who we don't)
- **Actionable** — suggests what to build and what not to build
- **Falsifiable** — we can tell if we're executing on it or not

Test: "If I showed this to anyone on the team, would they know what to build next and what to say no to?"

## Step 2: Target Segments

Reference `/pm:segment` output or build inline:

1. What are the main jobs your product does for customers?
2. What are the most important segmentation dimensions? (Needs-based, behavioral, context)
3. What segments are you prioritizing and why?
4. What segments are you NOT prioritizing and why?

For each priority segment:
- Core motivation and job
- Size and growth trajectory
- Current alternatives and satisfaction level
- Our right to win

## Step 3: Market Context & Map

### Where is this market headed?
- Technology trends that change the game (AI, mobile, platform shifts)
- Buyer behavior shifts
- Regulatory changes
- Pricing model evolution

### Who are the main players?
For each (3-5):
- Who they serve
- Their core strength
- Their strategic direction
- Their vulnerability

### Market map for priority segments
Position competitors on a 2x2 relevant to your market:
- Axes should reflect what priority segments actually care about
- Show where you are and where you're heading

## Step 4: Strategic Pillars / Differentiation

The 2-6 things that define your strategy. Each pillar should:
- Connect to a segment need
- Leverage a unique asset or power
- Be different from what competitors are doing
- Be measurable

For each pillar:

```markdown
### Pillar: [Name]

**Why this matters:** [Connection to segment need]
**How we're different:** [What we do that competitors can't/won't]
**Unique asset leveraged:** [Data, technology, relationships, domain expertise]
**Power being built:** [Which of 7 Powers this contributes to]
**Example initiatives:**
- [Feature/initiative 1]
- [Feature/initiative 2]
- [Feature/initiative 3]
```

## Step 5: Non-Priorities

The most important part of strategy — what you're NOT doing:

### Trade-offs
- "We choose [X] over [Y] because [reason tied to segments and differentiation]"
- "We invest in [X] at the expense of [Y] because [reason]"

### Lower Priority / Not a Priority
| Item | Why It's Not a Priority | What Would Change This |
|------|------------------------|----------------------|
| [Feature/Market/Segment] | [Reason] | [Condition that would reprioritize] |

### Table Stakes & Below Table Stakes
- **Table stakes (MMR):** Things we must do to compete but don't differentiate us
- **Below table stakes:** Things competitors do that we deliberately don't

## Step 6: 1-2 Year Roadmap

### Now (Next 3 months)
| Pillar | Initiative | Expected Outcome | Metric |
|--------|-----------|-------------------|--------|
| [Pillar] | [Initiative] | [What changes for users] | [How to measure] |

### Next (3-12 months)
| Pillar | Initiative | Expected Outcome | Metric |
|--------|-----------|-------------------|--------|
| [Pillar] | [Initiative] | [What changes] | [How to measure] |

### Later (12-24 months)
| Pillar | Direction | Hypothesis | Validation Needed |
|--------|-----------|------------|------------------|
| [Pillar] | [Where we're heading] | [What we believe] | [What we need to learn first] |

### Leading & Lagging Indicators

| Indicator | Type | Current | Target (6mo) | Target (12mo) |
|-----------|------|---------|-------------|--------------|
| [Metric 1] | Leading | [value] | [target] | [target] |
| [Metric 2] | Leading | [value] | [target] | [target] |
| [Metric 3] | Lagging | [value] | [target] | [target] |
| [Metric 4] | Lagging | [value] | [target] | [target] |

## Step 7: Strategy Stress Test

Before finalizing, test:

1. **Is it a real strategy?** Does it make hard choices, or does it say "we'll do everything"?
2. **Can you say no with it?** Give an example of an opportunity you'd reject because of this strategy.
3. **Is it differentiated?** Could a competitor write the same strategy? If yes, it's not a strategy.
4. **Is it achievable?** Do you have the resources and capabilities?
5. **Is it measurable?** Can you tell in 6 months if it's working?

## Step 8: Generate Strategy Document

Write to `docs/strategy/YYYY-MM-DD-strategy-<product-area>.md`:

```markdown
---
date: YYYY-MM-DD
product_area: "[area]"
one_sentence: "[strategy in one sentence]"
priority_segments: ["segment1", "segment2"]
pillars: ["pillar1", "pillar2", "pillar3"]
review_date: "YYYY-MM-DD"
status: "active"
---

# Strategy: [Product Area]

## One-Sentence Strategy
> [The sentence]

## Target Segments
[Priority segments with justification]

## Market Context
[Market direction, competitive map, positioning]

## Strategic Pillars
[2-6 pillars with initiatives and unique assets]

## Non-Priorities
[Trade-offs, what we're NOT doing, table stakes]

## Roadmap
[Now / Next / Later with metrics]

## Leading & Lagging Indicators
[4 key metrics with baselines and targets]

## Strategy Stress Test
[Results of the 5 questions]

## Review Schedule
- Next review: [date, 3 months out]
- Conditions that trigger earlier review: [list]
```

## Post-Strategy Options

Use **AskUserQuestion tool**:

**Question:** "Strategy documented. What's next?"

**Options:**
1. **Share with team** — Generate stakeholder-specific strategy narratives via `/pm:buyin`
2. **Evaluate opportunities** — Use this strategy to filter via `/pm:opportunity`
3. **Set metrics** — Define the North Star Metric via `/pm:north-star`
4. **Done** — Strategy documented and ready for review
