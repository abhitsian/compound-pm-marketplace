---
name: pm:simulate
description: Simulate how each user segment will actually react to a product change before shipping it
argument-hint: "[feature or product change to simulate]"
---

# User Simulation

## Purpose

Before shipping a feature, mentally model how real users will actually think, feel, and act. Not "will users like this?" but the hard version: walk through each segment's internal experience using motivation theory, cognitive biases, and behavioral psychology.

Over time, the plugin tracks your simulation accuracy — comparing predictions against actual outcomes — so your judgment compounds.

## Input

<simulation_input> #$ARGUMENTS </simulation_input>

**If empty:** Ask "What feature or product change do you want to simulate user reactions to?"

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
```

Load relevant segments from past `/pm:segment` outputs:
```bash
ls docs/segments/ 2>/dev/null
```

Load the spec if one exists:
```bash
ls docs/specs/ 2>/dev/null
```

## Step 1: Define the Change

Clearly state:
- **What's changing:** [specific feature/change]
- **Who it affects:** [which segments]
- **Current state:** What do users do today?
- **New state:** What will they do after this change?

## Step 2: Select Segments to Simulate

**If segments exist** (from `/pm:segment`): Use them.

**If no segments:** Create lightweight personas:

For each segment, define:
- **Name:** Descriptive label (not a person's name)
- **Context:** What's happening in their life/work
- **Primary motivation type:** Functional, social, emotional, or personal
- **Current behavior:** How they solve this today
- **Sophistication:** Novice, intermediate, expert
- **Attitude toward change:** Eager, neutral, resistant

Simulate at least 3 segments. Always include one resistant segment.

## Step 3: Run the Simulation Per Segment

For EACH segment, walk through:

### A. The "Wake Up in the Morning" Test
"Does [persona] wake up in the morning thinking about this problem?"
- If YES → High intrinsic motivation. Feature will get discovered.
- If NO → You need an extrinsic nudge to drive awareness. What is it?

### B. Motivation Analysis
- **Functional:** Does this make their task faster/easier/better?
- **Social:** Does this change how others perceive them?
- **Emotional:** Does this change how they feel?
- **Personal:** Does this affect their identity or self-image?
- **How urgent is this for them?** (1-10)
- **How good is their current alternative?** (1-10, where 10 = perfect alternative)

### C. Friction Prediction
Walk through the user journey step by step:
1. **Discovery friction:** How do they learn this exists?
2. **Comprehension friction:** Do they understand what it does?
3. **Decision friction:** Can they decide to try it quickly?
4. **Action friction:** How hard is the first use?
5. **Habit friction:** How inconsistent is this with their current behavior?
6. **Switching cost:** What do they lose by adopting this?

### D. Cognitive Bias Check
Which biases will affect this segment's reaction?

| Bias | Effect on This Change |
|------|----------------------|
| **Status quo bias** | Prefer current way of doing things |
| **Loss aversion** | Fear of losing current workflow (2x stronger than gain) |
| **Endowment effect** | Overvalue their existing setup |
| **Ambiguity aversion** (Ellsberg) | Prefer known limitations over unknown improvements |
| **Social proof** | Will adopt if they see others doing it |
| **Anchoring** | First impression of this change will stick |
| **Bandwagon effect** | Will follow majority behavior |
| **Ostrich effect** | Will avoid if it surfaces uncomfortable information |

### E. Nth Order Effects
Think beyond the obvious:
- **1st order:** User uses the feature → [direct effect]
- **2nd order:** Because of 1st order → [what changes in their workflow?]
- **3rd order:** Because of 2nd order → [what breaks? what improves unexpectedly?]

### F. Prediction
For this segment, predict:
- **Awareness rate:** What % will even notice this change? (0-100%)
- **Trial rate:** Of those aware, what % will try it? (0-100%)
- **Adoption rate:** Of those who try, what % will keep using it? (0-100%)
- **Satisfaction:** Of those who adopt, how satisfied? (1-10)
- **Net sentiment:** Positive, neutral, or negative?
- **Biggest risk:** What could go wrong for this segment?

## Step 4: Cross-Segment Patterns

After simulating all segments:

- **Where do segments agree?** These are high-confidence predictions.
- **Where do segments diverge?** These are risk areas — the change helps one segment but hurts another.
- **Who gets worse?** Any segment that's worse off deserves special attention.
- **Is there a "silent majority" problem?** Are you optimizing for a vocal minority?

## Step 5: Overall Adoption Prediction

```
Nudge × (Motivation − Friction)^Satisfaction = Adoption
```

Calculate per segment and aggregate:

| Segment | Motivation | Friction | Nudge | Satisfaction | Predicted Adoption |
|---------|-----------|---------|-------|-------------|-------------------|
| [Seg 1] | [1-10] | [1-10] | [1-10] | [1-10] | [%] |
| [Seg 2] | [1-10] | [1-10] | [1-10] | [1-10] | [%] |
| [Seg 3] | [1-10] | [1-10] | [1-10] | [1-10] | [%] |

**Weighted overall prediction:** [%] adoption at 30 days

## Step 6: Past Pattern Check

**If PM profile has `simulation_log`:**
- Compare this prediction pattern against past simulations
- "Your past simulations for [similar feature type] overestimated adoption by [X%]. Adjusting."
- "You tend to underweight [friction type] for [segment type]. Watch for that here."

## Step 7: Recommendations

Based on the simulation:
- **Ship as-is?** Only if all segments show positive or neutral outcomes.
- **Modify first?** What specific changes would improve predicted adoption?
- **Segment the rollout?** Which segment should get it first?
- **Add nudges?** What extrinsic nudges are needed for low-awareness segments?
- **Monitor what?** What signals will tell you if the simulation was right or wrong?

## Step 8: Generate Simulation Document

Write to `docs/simulations/YYYY-MM-DD-<feature-name>.md`:

```markdown
---
date: YYYY-MM-DD
feature: "[feature name]"
segments_simulated: [count]
predicted_adoption_30d: "[%]"
confidence: "[high | medium | low]"
status: "predicted"
---

# Simulation: [Feature Name]

## The Change
[What's changing, current state → new state]

## Segment Simulations

### [Segment 1 Name]
- **Motivation:** [type, score]
- **Friction:** [key friction points, score]
- **Biases at play:** [list]
- **Nth order effects:** [predictions]
- **Predicted adoption:** [%]
- **Biggest risk:** [what could go wrong]

[Repeat for each segment]

## Cross-Segment Analysis
[Agreements, divergences, who gets worse]

## Overall Prediction
[Adoption formula calculation and aggregate]

## Recommendations
[Ship/modify/segment/nudge decisions]

## What Would Prove This Wrong
[Specific signals that would indicate the simulation was inaccurate]
```

## Step 9: Set Review Trigger

Add to PM profile `simulation_log`:
```yaml
- date: "YYYY-MM-DD"
  feature: "[name]"
  predicted_adoption: "[%]"
  actual_adoption: "pending"
  review_date: "YYYY-MM-DD" # 30 days out
  segments: [count]
  key_assumption: "[the assumption most likely to be wrong]"
```

This is what makes simulation compound. When you run `/pm:compound`, it compares predictions vs actuals and updates your calibration.

## Post-Simulation Options

Use **AskUserQuestion tool**:

**Question:** "Simulation complete. What's next?"

**Options:**
1. **Run `/pm:spec`** — Build the spec with simulation insights baked in
2. **Run `/pm:motivation-map`** — Go deeper on motivation analysis for the top segment
3. **Adjust and re-simulate** — Change the feature based on findings
4. **Done** — Simulation logged for future comparison
