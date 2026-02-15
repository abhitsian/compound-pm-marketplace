---
name: pm:differentiate
description: Analyze competitive differentiation using 7 Powers, unique assets, and segment-specific advantages
argument-hint: "[product or segment to analyze differentiation for]"
---

# Competitive Differentiation Analysis

## Purpose

Differentiation is a function of user needs, alternatives, unique assets, industry direction, creative choices, and chosen segments. This command maps your competitive landscape and identifies where you can actually win vs. where you're playing someone else's game.

## Input

<differentiation_input> #$ARGUMENTS </differentiation_input>

**If empty:** Ask "What product or segment do you want to analyze differentiation for?"

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
```

Load segments if available:
```bash
cat docs/segments/*.md 2>/dev/null
```

Launch research agent in parallel:
- Task **competitive-landscape**: Research competitive positioning and recent moves for the relevant market.

## Step 1: Map the Competitive Landscape

For each significant competitor (3-5 max):

```markdown
### [Competitor Name]

**Who they serve:** [primary segments]
**Core strength:** [what they're genuinely best at]
**Weakness:** [where they're vulnerable]
**Direction:** [where they're heading — based on recent moves, hiring, product changes]
**Threat level:** [High | Medium | Low] for our priority segments
```

Also map:
- **Non-obvious alternatives:** What do customers use INSTEAD of any product in this category? (Spreadsheets, email, manual process, doing nothing)
- **Emerging entrants:** Who might enter this space in 12 months?

## Step 2: Apply the 7 Powers Framework

Evaluate which of Hamilton Helmer's 7 Powers apply to you vs. competitors:

| Power | Definition | Do We Have It? | Do Competitors Have It? |
|-------|-----------|----------------|------------------------|
| **Scale Economies** | Unit cost declines as volume increases | [Y/N — how?] | [Who has it?] |
| **Network Effects** | Product value increases as more users join | [Y/N — what type?] | [Who has it?] |
| **Switching Costs** | Users face cost/friction when leaving | [Y/N — what creates it?] | [Who has it?] |
| **Branding** | Durable attribution of higher value to a brand | [Y/N — why?] | [Who has it?] |
| **Cornered Resource** | Access to a valuable resource others can't get | [Y/N — what resource?] | [Who has it?] |
| **Counter-Positioning** | A new model incumbents can't adopt without damaging their business | [Y/N — what model?] | [Who has it?] |
| **Process Power** | Deep organizational capability that can't be easily copied | [Y/N — what capability?] | [Who has it?] |

**Key question:** Which powers can we BUILD in the next 12-24 months? Powers aren't just things you have — they're things you create through strategic choices.

## Step 3: Segment-Specific Differentiation

For each priority segment (from `/pm:segment` or defined here):

### What they need most
- Top 3 unmet needs for this segment
- How urgently each need is felt

### How alternatives serve them
| Need | Our Product | Competitor A | Competitor B | Non-product Alternative |
|------|------------|-------------|-------------|----------------------|
| [Need 1] | [How well, 1-10] | [How well] | [How well] | [How well] |
| [Need 2] | [score] | [score] | [score] | [score] |
| [Need 3] | [score] | [score] | [score] | [score] |

### Where we can win
- **Unique asset:** What do we have that competitors don't? (data, technology, relationships, domain expertise, distribution)
- **Creative opportunity:** What unconventional approach could leapfrog alternatives?
- **Industry direction:** Which way is the market moving, and does that favor us?

## Step 4: Identify Differentiation Type

For each potential differentiator:

| Differentiator | Type | Defensibility | Time to Build |
|----------------|------|--------------|---------------|
| [Differentiator 1] | [Differentiator / MMR / Neutralizer] | [High / Medium / Low] | [weeks / months / years] |

**Definitions:**
- **Differentiator:** Unique competitive advantage — users choose us BECAUSE of this
- **MMR (Minimum Market Requirement):** Must-have to even compete — users reject us WITHOUT this
- **Neutralizer:** Catches up to competitors — removes a reason to NOT choose us

**Priority order:** Differentiators > MMRs > Neutralizers

## Step 5: Non-Priorities and Trade-offs

Strategy is about what you DON'T do:

- **What are we deliberately NOT competing on?** Why?
- **Which segments are we deliberately NOT serving?** Why?
- **What features are competitors investing in that we're ignoring?** Why is that okay?
- **What market-level changes would force us to reconsider these non-priorities?**

## Step 6: Differentiation Narrative

Write a clear, one-paragraph differentiation statement:

> "For [priority segment], [our product] is the only [category] that [key differentiator] because [unique asset/power]. Unlike [main competitor], we [specific difference that matters to this segment]."

Test this statement:
- Is it true? (Can you prove it?)
- Is it relevant? (Does the segment care?)
- Is it distinctive? (Could a competitor say the same thing?)
- Is it durable? (Will it still be true in 12 months?)

## Step 7: Generate Differentiation Document

Write to `docs/strategy/YYYY-MM-DD-differentiation-<area>.md`:

```markdown
---
date: YYYY-MM-DD
product_area: "[area]"
priority_segment: "[segment]"
differentiation_type: "[differentiator | mmr | neutralizer]"
primary_power: "[7 powers type or none]"
confidence: "[high | medium | low]"
---

# Differentiation Analysis: [Product Area]

## Competitive Landscape
[Competitor profiles with strengths, weaknesses, direction]

## Non-Obvious Alternatives
[What customers use instead of this entire category]

## 7 Powers Assessment
[Table of powers — who has what]

## Segment-Specific Analysis
[Needs matrix for priority segments]

## Our Differentiation
[Type, defensibility, time to build for each differentiator]

## Non-Priorities
[What we're deliberately not competing on and why]

## Differentiation Statement
> [One paragraph statement]

## Risks
- [What could erode our differentiation]
- [What competitor moves to watch]

## Next Steps
→ `/pm:strategy` to build full strategy
→ `/pm:opportunity` to evaluate opportunities through this lens
```

## Post-Analysis Options

Use **AskUserQuestion tool**:

**Question:** "Differentiation analysis complete. What's next?"

**Options:**
1. **Run `/pm:strategy`** — Build full strategy using segments + differentiation
2. **Run `/pm:opportunity`** — Evaluate an opportunity through this competitive lens
3. **Refine segments** — The analysis revealed new segmentation insights
4. **Done** — Analysis documented
