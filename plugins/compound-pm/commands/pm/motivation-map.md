---
name: pm:motivation-map
description: Map the full adoption equation for a feature — motivation, friction, nudge, and satisfaction
argument-hint: "[feature or product to analyze]"
---

# Motivation Map

## Purpose

Every product decision is governed by one equation:

```
Nudge × (Motivation − Friction)^Satisfaction = Adoption
```

This command maps each component for a specific feature, producing an actionable analysis of why users will or won't adopt. It surfaces the specific levers you can pull to increase adoption.

## Input

<motivation_input> #$ARGUMENTS </motivation_input>

**If empty:** Ask "What feature or product experience do you want to map the motivation equation for?"

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
```

Load segments:
```bash
cat docs/segments/*.md 2>/dev/null
```

## Step 1: Define the Target Action

What specific user action are you trying to drive?
- Not "use the feature" but "complete [specific action] for the first time"
- Not "engage more" but "return within 7 days and perform [action] again"

State it precisely: "I want [persona] to [specific action] within [timeframe]."

## Step 2: Map Motivation (What Pushes Toward Action)

### Functional Motivation
- What task does this help them perform?
- What problem does it solve?
- How much time/effort does it save?
- Score: [1-10]

### Social Motivation
- How does using this change how others perceive them?
- Does it give them something to share/show?
- Does it signal competence, status, or belonging?
- Score: [1-10]

### Emotional Motivation
- How does using this make them FEEL?
- Does it reduce anxiety? Create joy? Build confidence?
- Does it generate "happy hormones" (accomplishment, validation)?
- Score: [1-10]

### Personal Motivation
- Does this align with their identity or values?
- Does it make them feel smart, competent, or in control?
- Does it raise their self-esteem or security?
- Score: [1-10]

### Motivation Boosters
- **How important is the job?** (1-10)
- **How urgent is it?** (1-10)
- **What are the benefits of action?** [list]
- **What are the consequences of inaction?** [list]
- **How good is their current alternative?** (1-10, where 10 = perfect alternative, 1 = no alternative)

**Overall Motivation Score:** [weighted average, 1-10]

**Dominant motivation type:** [The strongest driver — this determines your messaging and design]

## Step 3: Map Friction (What Pushes Away from Action)

For each friction type, score 1-10 (10 = maximum friction):

### Comprehension Friction
- Do I understand what this is? [score]
- Do I understand what it does for me? [score]
- Do I understand what my next action is? [score]

### Decision Friction
- When do I need to make a decision? [score]
- How complex is the decision? [score]
- What is the cost of making the wrong decision? [score]
- How much thought do I need before acting? [score]

### Action Friction
- How difficult is it to initiate the action? [score]
- How difficult is it to complete the action? [score]
- How many steps are involved? [count]

### Habit Friction
- How inconsistent is this with my current behavior? [score]
- What do I have to give up? [list]
- What else is competing for my attention right now? [score]

### Emotional Friction
- What do I stand to lose? [list]
- How anxious does this make me? [score]
- Am I avoiding information this might surface? (Ostrich effect) [Y/N]

**Overall Friction Score:** [weighted average, 1-10]

**Highest friction point:** [The single biggest barrier — this is your #1 product problem to solve]

## Step 4: Map Nudges (What Triggers Action)

### Intrinsic Nudges (from within the user)
- Personal habits that align with this action
- Self-imposed rules or goals
- Internal motivation spikes (pain point just happened)
- Score: [1-10]

### Extrinsic Nudges (from the product/environment)
- Notifications or reminders
- Social proof (others are doing this)
- Urgency signals (limited time, scarcity)
- Default behavior (opt-out vs opt-in)
- Environmental triggers (time of day, context)
- Score: [1-10]

### Nudge-Motivation Alignment
**Critical check:** Does the nudge align with the dominant motivation type?

| Motivation Type | Effective Nudge | Ineffective Nudge |
|----------------|----------------|-------------------|
| Functional | "This will save you 2 hours" | "Everyone is using this" |
| Social | "Your team is already using this" | "This is 30% faster" |
| Emotional | "You deserve a break" | "Optimal resource allocation" |
| Personal | "Level up your skills" | "Limited time offer" |

**Overall Nudge Score:** [1-10]

## Step 5: Map Satisfaction (What Brings Them Back)

After the user completes the action:

- Did it fulfill the promised job? [Y/N, score 1-10]
- Did it live up to expectations? [Y/N, score 1-10]
- Did it generate positive emotion? [Y/N, what emotion?]
- Did it give social validation? [Y/N, how?]
- Did it feel reassuring or raise self-esteem? [Y/N]
- Did it make them feel smart? [Y/N]
- **Would they do it again?** [Y/N, why/why not?]

**Overall Satisfaction Score:** [1-10]

**Satisfaction gap:** [Where expectations exceed reality — this kills retention]

## Step 6: Calculate and Interpret

```
Nudge ([score]) × (Motivation ([score]) − Friction ([score]))^Satisfaction ([score]) = Adoption
```

### Interpretation Guide

| Scenario | Diagnosis | Action |
|----------|-----------|--------|
| High motivation, high friction | Users want this but can't do it | Reduce friction — simplify, remove steps |
| Low motivation, low friction | Easy but nobody cares | Increase motivation — better value prop, different segment |
| High motivation, low friction, low nudge | Want it, can do it, but don't start | Add triggers — notifications, defaults, social proof |
| Everything high but low satisfaction | They try once but don't return | Fix the experience — it's not delivering on the promise |
| Low motivation across all types | Wrong feature for this segment | Reconsider — who actually needs this? |

## Step 7: Generate Action Plan

Based on the map, produce 3-5 specific product actions:

1. **Highest-impact friction reduction:** [specific change]
2. **Nudge to add:** [specific trigger aligned with motivation type]
3. **Satisfaction improvement:** [specific change to post-action experience]
4. **Motivation amplifier:** [specific way to increase perceived value]

## Step 8: Generate Document

Write to `docs/motivation-maps/YYYY-MM-DD-<feature-name>.md`:

```markdown
---
date: YYYY-MM-DD
feature: "[feature name]"
target_action: "[specific action]"
motivation_score: [1-10]
friction_score: [1-10]
nudge_score: [1-10]
satisfaction_score: [1-10]
dominant_motivation: "[functional | social | emotional | personal]"
highest_friction: "[type]"
predicted_adoption: "[formula result]"
---

# Motivation Map: [Feature]

## Target Action
[Precise action statement]

## Motivation Analysis
[Scores and analysis for each type]

## Friction Analysis
[Scores and analysis for each type]

## Nudge Analysis
[Intrinsic, extrinsic, alignment check]

## Satisfaction Analysis
[Post-action assessment]

## Adoption Equation
[Calculation and interpretation]

## Action Plan
[3-5 specific product actions with priority]
```

## Post-Map Options

Use **AskUserQuestion tool**:

**Question:** "Motivation map complete. What's next?"

**Options:**
1. **Run `/pm:simulate`** — Simulate per-segment reactions
2. **Run `/pm:spec`** — Build the spec with motivation insights
3. **Run `/pm:ux-psychology`** — Apply behavioral design patterns to the flow
4. **Map another feature** — Compare motivation maps across features
