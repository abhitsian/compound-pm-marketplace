---
name: pm:segment
description: Create needs-based user segments using motivations and behaviors, not demographics
argument-hint: "[product or feature area to segment]"
---

# Needs-Based Segmentation

## Purpose

Segmentation is the foundation of strategy. Bad segmentation (demographics, personas, gut feel) leads to bad strategy. This command builds needs-based segments using motivations and behaviors — the only segmentation that actually predicts product decisions.

Your segments are stored and referenced by every downstream command: `/pm:spec` maps journeys per segment, `/pm:simulate` runs per segment, `/pm:measure` breaks metrics by segment.

## Input

<segment_input> #$ARGUMENTS </segment_input>

**If empty:** Ask "What product or feature area do you want to segment users for?"

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
```

Load existing segments if any:
```bash
ls docs/segments/ 2>/dev/null
```

Load research if available:
```bash
ls docs/research/interviews/ docs/research/signals/ docs/research/synthesis/ 2>/dev/null
```

## Step 1: Identify Jobs to Be Done

Start with the foundational question: **What jobs does this product do for customers?**

For each job:
- **Functional job:** What task are they trying to accomplish?
- **Emotional job:** How do they want to feel?
- **Social job:** How do they want to be perceived?
- **Consumption context:** When and where does this job arise?

List 5-8 distinct jobs. Don't combine — keep them separate.

## Step 2: Choose Segmentation Dimensions

The primary segmentation should be based on **motivations and behaviors**, not demographics.

Use these heuristic dimensions (in priority order):

### Primary: Needs-Based (Most Important)
- What specific problems do customers need to solve?
- What are their core functional requirements?
- Which jobs matter most to them?

### Secondary: Behavioral
- How do they currently solve this problem?
- What's their usage pattern? (frequency, depth, context)
- What's their decision-making process?

### Tertiary: Context of Use
- What environment are they in? (team size, company stage, industry)
- What constraints do they operate under?
- What other tools are they using?

**AVOID as primary dimensions:**
- Demographics (age, gender, location)
- Psychographics (personality types)
- Composite personas (marketing fiction)
- Generic market categories (SMB/Enterprise)

## Step 3: Define Segments

Create 3-5 mutually exclusive segments based on motivations and behaviors.

For each segment:

```markdown
### Segment: [Descriptive Name]

**Core motivation:** [The primary job they're hiring the product for]
**Motivation type:** [Functional | Social | Emotional | Personal]
**Current behavior:** [How they solve this today]
**Key friction:** [What makes their current solution painful]
**Willingness to switch:** [High | Medium | Low]
**Sophistication level:** [Novice | Intermediate | Expert]
**Value sensitivity:** [Price-sensitive | Value-driven | Premium-willing]
```

Name segments by their motivation, not their demographics:
- "Speed optimizers" not "millennials"
- "Risk-averse decision-makers" not "enterprise buyers"
- "Social validators" not "Gen Z users"

## Step 4: Validate with the 5-Point Test

For each segment, verify:

| Test | Question | Pass/Fail |
|------|----------|-----------|
| **Consistent needs** | Do customers in this segment share similar core needs? Are they distinctly different from other segments? | |
| **Product-specific** | Does this segmentation align with our specific product? Is it relevant to our category? | |
| **Targetable** | Can we predictably identify these customers? Do we have a clear way to reach them? | |
| **Prioritizable** | Can we rank segments by ability to differentiate, ease of targeting, and potential impact? | |
| **Winnable** | Can we realistically win in this segment? Do we have the resources to serve them well? | |

**If a segment fails any test:** Revise or merge it.

## Step 5: Score and Prioritize

For each validated segment:

| Segment | Reach | Underserved Degree | Differentiation Potential | Ease of Targeting | Total Score |
|---------|-------|--------------------|--------------------------|-------------------|-------------|
| [Name] | H/M/L | H/M/L | H/M/L | H/M/L | [sum] |

**Scoring:**
- **Reach:** How large is this segment? (H=large addressable, M=moderate, L=niche)
- **Underserved degree:** How poorly served are they by current alternatives? (H=very underserved, M=partially served, L=well served)
- **Differentiation potential:** Can we build something meaningfully better for them? (H=strong advantage, M=moderate, L=marginal)
- **Ease of targeting:** Can we find and reach them efficiently? (H=clear channels, M=some channels, L=hard to reach)

**Choose 1-2 priority segments.** Not all of them. Strategy is about choosing where NOT to play.

## Step 6: Answering the Critical Questions

For each priority segment:

1. **Can we differentiate quickly?** What can we build in 3-6 months that no alternative offers?
2. **Is our differentiation sustainable?** Can competitors copy it easily?
3. **Can we reach them cost-effectively?** What's the acquisition channel?
4. **Is there a clear growth path?** Does winning here open adjacent segments?
5. **Does it align with our product strategy?** (Reference `/pm:strategy` if it exists)

## Step 7: Generate Segmentation Document

Write to `docs/segments/YYYY-MM-DD-<product-area>.md`:

```markdown
---
date: YYYY-MM-DD
product_area: "[area]"
segments_defined: [count]
priority_segments: ["segment1", "segment2"]
segmentation_dimensions: ["needs", "behavior", "context"]
status: "active"
---

# Segmentation: [Product Area]

## Jobs to Be Done
[List of 5-8 jobs identified]

## Segmentation Dimensions
[Primary, secondary, tertiary dimensions chosen and why]

## Segments

### [Priority 1] — [Segment Name]
- **Core motivation:** [job]
- **Motivation type:** [type]
- **Current behavior:** [how they solve today]
- **Key friction:** [pain with current solution]
- **Willingness to switch:** [H/M/L]
- **Why this is priority:** [differentiation potential, reach, underserved degree]
- **How to reach them:** [channels]
- **Growth path:** [adjacent segments this unlocks]

### [Priority 2] — [Segment Name]
[Same structure]

### [Lower Priority] — [Segment Name]
[Same structure, with note on why it's lower priority]

## 5-Point Validation
[Results of validation test for each segment]

## Scoring Matrix
[Table with reach, underserved, differentiation, targeting scores]

## What This Means for Product
- **Build for:** [priority segments]
- **Monitor:** [lower priority segments for changes]
- **Ignore for now:** [segments we're deliberately not serving]

## Review Trigger
Revisit this segmentation when:
- [Specific condition that would change priorities]
- [Market shift that would invalidate segments]
```

## Step 8: Update PM Profile

Add to `active_segments` in pm-profile.yaml:
```yaml
segments:
  product_area: "[area]"
  date: "YYYY-MM-DD"
  priority:
    - name: "[segment name]"
      motivation: "[core motivation]"
      type: "[functional | social | emotional | personal]"
    - name: "[segment name]"
      motivation: "[core motivation]"
      type: "[functional | social | emotional | personal]"
  lower_priority:
    - name: "[segment name]"
```

## Post-Segmentation Options

Use **AskUserQuestion tool**:

**Question:** "Segmentation complete. What's next?"

**Options:**
1. **Run `/pm:differentiate`** — Analyze competitive differentiation for priority segments
2. **Run `/pm:strategy`** — Build full strategy using these segments
3. **Run `/pm:opportunity`** — Evaluate an opportunity for a specific segment
4. **Run `/pm:simulate`** — Simulate a feature for these segments
