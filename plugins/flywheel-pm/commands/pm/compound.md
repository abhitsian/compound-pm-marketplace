---
name: pm:compound
description: Capture learnings from a product cycle and update your PM profile — the most important step
argument-hint: "[feature name or measurement doc path]"
---

# Compound — The Most Important Step

## Purpose

After a product cycle (launch, measurement review, or post-mortem), capture what worked, what didn't, compare predictions to actuals, and update your PM profile so the next cycle is faster and better. **This is where the gains accumulate. Skip it, and you've done traditional PM with AI assistance.**

## Input

<compound_input> #$ARGUMENTS </compound_input>

**If a file path:** Read the measurement or spec document.
**If a feature name:** Search `docs/` for all related documents.
**If empty:** Ask what to compound.

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
```

Gather all related documents:
```bash
ls docs/opportunities/*[feature]* docs/solutions/*[feature]* docs/specs/*[feature]* docs/measurements/*[feature]* 2>/dev/null
```

## Step 1: Gather Outcomes

Ask the PM (using **AskUserQuestion tool** where appropriate):

### What happened?
- What was the actual outcome vs predicted?
- Did the feature ship as specced or did scope change?
- What was the business impact?

### Predictions vs Actuals
If a measurement doc exists with predictions, go through each:

| Prediction | Predicted | Actual | Delta | Why |
|-----------|-----------|--------|-------|-----|
| Adoption rate | [X]% | [actual]% | [+/-] | [explanation] |
| Activation | [X]% | [actual]% | [+/-] | [explanation] |
| Retention | [X]% | [actual]% | [+/-] | [explanation] |
| Revenue impact | $[X] | $[actual] | [+/-] | [explanation] |

### Estimation Calibration
- Were you overconfident or underconfident?
- Which metric types do you predict well? Poorly?
- What would you do differently in estimation next time?

## Step 2: Capture Learnings

### What Worked
- Which frameworks served you well?
- Which decisions were right? Why?
- What should you do again?

### What Didn't Work
- Which assumptions were wrong?
- Which frameworks failed you?
- What trade-offs had unexpected consequences?

### Failures Documented
Classify failures by type:
- **Strategy failure** — Wrong opportunity or wrong market
- **Opportunity failure** — Right market, wrong problem
- **Prioritization failure** — Right problem, wrong solution prioritized
- **Execution failure** — Right solution, poor implementation
- **Measurement failure** — Wrong metrics or wrong targets

### What Was Surprising
- What did you not predict?
- What did users do that you didn't expect?
- What competitive response occurred?

## Step 3: Update PM Profile

**This is the core compounding mechanism.** Update `pm-profile.yaml` with:

### New Project Pattern
Add to `project_patterns`:
```yaml
- project: "[Feature Name]"
  date: "YYYY-MM-DD"
  domain: "[domain]"
  opportunity_type: "[signal type]"
  solution_type: "[differentiator | mmr | neutralizer]"
  outcome_metric: "[metric name]"
  predicted: "[prediction]"
  actual: "[actual]"
  delta: "[+/- %]"
  key_learning: "[one sentence]"
  activation:
    setup: "[actual rate]"
    aha: "[actual rate]"
    habit: "[actual rate]"
  engagement:
    casual_pct: "[actual %]"
    core_pct: "[actual %]"
    power_pct: "[actual %]"
  business_impact: "[summary]"
```

### Updated Thresholds
Recalculate averages across all project patterns:
```yaml
thresholds:
  avg_activation_setup: "[recalculated]"
  avg_activation_aha: "[recalculated]"
  avg_activation_habit: "[recalculated]"
  avg_estimation_accuracy: "[recalculated]"
  typical_time_to_habit: "[recalculated]"
```

### Decision Log Entry
Add to `decision_log`:
```yaml
- date: "YYYY-MM-DD"
  feature: "[name]"
  decision: "[what was decided]"
  rationale: "[why]"
  outcome: "[what actually happened]"
  would_decide_differently: "[yes/no and why]"
```

### Framework Adjustments
If a framework consistently fails or succeeds, note it:
```yaml
framework_notes:
  - "Activation funnel works well for B2B employee-facing products"
  - "Revenue predictions tend to be 20% optimistic — discount accordingly"
  - "User segmentation (casual/core/power) maps well to enterprise engagement"
```

## Step 4: Generate Compound Document

Write to `docs/compounds/YYYY-MM-DD-<feature>-compound.md`:

```markdown
---
date: YYYY-MM-DD
feature: "[feature name]"
outcome: "[success | partial | failure | pivot]"
key_learning: "[one sentence]"
profile_updated: true
---

# Compound: [Feature Name]

## Outcome Summary
[What happened in 2-3 sentences]

## Predictions vs Actuals
[Table of predicted vs actual metrics]

## Estimation Calibration
[Where predictions were off and why]

## What Worked
[Frameworks, decisions, approaches that succeeded]

## What Didn't Work
[Failures classified by type]

## What Was Surprising
[Unexpected outcomes]

## PM Profile Updates
- Added project pattern: [summary]
- Updated thresholds: [what changed]
- Added to decision log: [key decision]
- Framework note: [any framework adjustment]

## Implications for Future Work
[What the next PM cycle should do differently]
```

## Step 5: Profile Update Confirmation

Show the PM what changed in their profile:

```
Profile updated:

New project pattern added: [Feature Name]
  Outcome metric: [predicted] → [actual] ([delta])
  Activation: Setup [X]%, Aha [Y]%, Habit [Z]%

Thresholds recalculated:
  avg_activation_setup: [old] → [new]
  avg_estimation_accuracy: [old] → [new]

Decision logged: [summary]

Your PM operating system is now smarter. The next /pm:opportunity
will reference this learning, and /pm:measure will use updated
thresholds for predictions.
```

## Step 6: Team Knowledge Sharing

After capturing individual learnings, ask:

Use **AskUserQuestion tool**:

"Is any of this worth sharing with the PM team?"

**Options:**
1. **Share key learning** — Promote the top insight to `team-profile.yaml` via `/pm:share`
2. **Share threshold update** — Share calibrated metrics (e.g., "activation takes 3 weeks for enterprise")
3. **Share warning** — Share a mistake or anti-pattern so others avoid it
4. **Keep personal** — This stays in your pm-profile.yaml only

If sharing: Run `/pm:share` with the selected learning.

## Post-Compound Options

**Options:**
1. **View updated profile** — See full pm-profile.yaml
2. **Compare across projects** — See patterns across all compounded projects
3. **Share with team** — Run `/pm:share` to promote more learnings
4. **Start next cycle** — Run `/pm:opportunity` for the next initiative
5. **Done** — Learnings captured

## The Compounding Effect

- **Cycle 1:** You manually define activation thresholds. Predictions are guesses.
- **Cycle 5:** The system suggests thresholds based on 4 past projects. Predictions are within 20%.
- **Cycle 10:** The system knows your estimation bias, suggests corrections, flags when an opportunity looks like a past failure, and pre-fills metrics frameworks based on project type.

**Each product cycle makes the next one easier — not harder.**
