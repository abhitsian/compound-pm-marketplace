---
name: pm:friction-log
description: Create a structured friction log for any product flow — categorize, score, and pattern-match friction
argument-hint: "[product flow to log friction for]"
---

# Friction Log

## Purpose

A friction log is the PM equivalent of a surgeon's morbidity & mortality conference. Walk through a product flow as a specific persona, logging every moment of confusion, frustration, or wasted effort. Over time, your friction log library becomes a reference for what good and bad UX looks like — and the plugin pattern-matches across logs.

Inspired by Stripe's friction logging practice.

## Input

<friction_input> #$ARGUMENTS </friction_input>

**If empty:** Ask "What product flow do you want to friction-log? This can be your own product or a competitor's."

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
```

Load past friction logs for pattern matching:
```bash
ls docs/friction-logs/ 2>/dev/null
```

## Step 1: Set Up the Log

### Define the Persona
Use **AskUserQuestion tool**:

**Question:** "Who are you experiencing this flow as?"

**Options:**
1. **Brand new user** — No prior context, first time seeing the product
2. **Returning user with a task** — Knows the product, has a specific goal
3. **Admin/Setup user** — Configuring for others, patience level varies
4. **Evaluator** — Comparing to alternatives, looking for reasons to say yes or no

Define:
- **Name:** [Descriptive — "Busy engineering manager evaluating tools"]
- **Context:** [What's happening in their life right now]
- **Goal:** [Specific thing they're trying to accomplish]
- **Time budget:** [How long are they willing to spend]
- **Patience level:** [High / Medium / Low]

### Define the Flow
- **Start point:** [Where does the flow begin? URL, screen, entry point]
- **End point:** [What does success look like?]
- **Scope:** [Just this flow, or end-to-end experience?]

## Step 2: Walk the Flow — Log Everything

For each step, capture:

```markdown
### Step [N]: [Screen/Action Name]

**What I expected:** [What the persona would expect to see/happen]
**What actually happened:** [What they saw/experienced]
**How it made me feel:** [Emotion — confident, confused, annoyed, delighted, anxious, impatient]

**Friction type:** [Comprehension | Decision | Action | Habit | Emotional | None]
**Severity:** [Blocker | Major | Minor | Nit | Delight]

**Notes:** [Specific observation about copy, layout, interaction, timing]
```

### Friction Type Definitions

| Type | Description | Example |
|------|-----------|---------|
| **Comprehension** | Don't understand what this is or what to do | Jargon, unclear labels, missing context |
| **Decision** | Understand but can't decide what to do | Too many options, unclear consequences, no defaults |
| **Action** | Know what to do but it's hard to execute | Too many clicks, complex form, slow loading |
| **Habit** | Conflicts with existing behavior or expectations | Unfamiliar patterns, different from competitors |
| **Emotional** | Creates anxiety, doubt, or negative feelings | Irreversible actions, data sharing, commitment |

### Severity Definitions

| Severity | Impact | Example |
|----------|--------|---------|
| **Blocker** | User stops and cannot proceed | Error with no recovery, dead end, broken flow |
| **Major** | User can proceed but with significant effort or frustration | Confusing multi-step process, buried critical action |
| **Minor** | User notices but continues without much effort | Slightly unclear label, extra click |
| **Nit** | User might not consciously notice but it degrades the experience | Alignment issue, inconsistent capitalization |
| **Delight** | Positive surprise — something BETTER than expected | Helpful default, smart suggestion, pleasant animation |

## Step 3: Friction Score Summary

After walking the full flow:

| Metric | Count |
|--------|-------|
| Total steps | [N] |
| Blockers | [N] |
| Major friction points | [N] |
| Minor friction points | [N] |
| Nits | [N] |
| Delights | [N] |
| **Friction score** | [Blockers×4 + Major×3 + Minor×2 + Nit×1 − Delight×2] |

### Friction by Type

| Type | Count | Worst Moment |
|------|-------|-------------|
| Comprehension | [N] | [Step X] |
| Decision | [N] | [Step X] |
| Action | [N] | [Step X] |
| Habit | [N] | [Step X] |
| Emotional | [N] | [Step X] |

## Step 4: Pattern Matching

**If past friction logs exist:**
- Compare this flow's friction score to past logs
- "This flow has a friction score of [X]. Your average is [Y]. This is [above/below] average."
- "The comprehension friction pattern here is similar to [past product] — that flow had [X]% drop-off at the same point."
- Identify recurring friction patterns: "You've logged comprehension friction in onboarding flows [N] times. This is a category-level problem."

**Cross-flow patterns:**
- Are the same friction types showing up across multiple flows?
- Is there a systemic issue? (e.g., all your flows have decision friction at step 3)

## Step 5: Prioritized Fix List

Rank all friction points by: `Severity × Frequency × Ease of Fix`

| Priority | Step | Friction | Severity | Fix |
|----------|------|----------|----------|-----|
| P1 | [Step] | [Description] | Blocker/Major | [Specific fix] |
| P2 | [Step] | [Description] | Major/Minor | [Specific fix] |
| P3 | [Step] | [Description] | Minor/Nit | [Specific fix] |

## Step 6: Generate Document

Write to `docs/friction-logs/YYYY-MM-DD-<product-flow>.md`:

```markdown
---
date: YYYY-MM-DD
product: "[product name]"
flow: "[flow name]"
persona: "[persona description]"
friction_score: [number]
blockers: [count]
major: [count]
minor: [count]
delights: [count]
is_own_product: [true | false]
---

# Friction Log: [Product] — [Flow]

## Persona
[Who, context, goal, time budget, patience]

## Flow: [Start] → [End]

[Step-by-step log with friction annotations]

## Summary
[Friction score, counts by type and severity]

## Patterns
[Cross-log patterns, comparisons to past logs]

## Priority Fixes
[Ranked fix list]

## Key Takeaway
[One sentence: what's the single biggest insight from this log?]
```

## Step 7: Update PM Profile

Add to `friction_log_summary` in pm-profile.yaml:
```yaml
- date: "YYYY-MM-DD"
  product: "[name]"
  flow: "[flow]"
  friction_score: [number]
  dominant_friction_type: "[type]"
  key_learning: "[one sentence]"
```

## Post-Log Options

Use **AskUserQuestion tool**:

**Question:** "Friction log complete. What's next?"

**Options:**
1. **Run `/pm:ux-psychology`** — Deep behavioral analysis of the highest-friction steps
2. **Log another flow** — Build your friction log library
3. **Compare logs** — See patterns across all past friction logs
4. **Done** — Log saved
