---
name: pm:decide
description: Frame a decision explicitly with options, criteria, trade-offs, reversibility, and stakeholders before committing
argument-hint: "[decision to make]"
---

# Decision Framework

## Purpose

World-class PMs make decisions explicitly, not implicitly. This command forces structured thinking before committing: options, criteria, trade-offs, reversibility, and who needs to weigh in. Decisions are logged in your PM profile for future reference.

## Input

<decision_input> #$ARGUMENTS </decision_input>

**If empty:** Ask "What decision are you facing?"

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
```

Search for past similar decisions:
```bash
grep -r "[relevant keywords]" docs/compounds/ pm-profile.yaml 2>/dev/null
```

## Step 1: Classify the Decision

Use **AskUserQuestion tool**:

"What type of decision is this?"

**Options:**
1. **One-way door** — Hard to reverse (pricing change, architecture, killing a feature, org change)
2. **Two-way door** — Easy to reverse (feature flag, experiment, UI change, pilot)
3. **Not sure** — Help me figure it out

### Decision Rigor Matrix

| Type | Rigor Level | Approach |
|------|------------|---------|
| One-way door | High | Full analysis, stakeholder input, pre-mortem |
| Two-way door | Low | Quick analysis, decide fast, learn from outcome |

## Step 2: Frame the Decision

### The Decision Statement
"We need to decide: [specific, concrete statement]"

Not: "What should we do about notifications?"
But: "Should we build email notifications (3 weeks), in-app only (1 week), or both (5 weeks) for the Q2 release?"

### Options (minimum 3)

For each option:

```markdown
### Option A: [Name]
**Description:** [What this means concretely]
**Effort:** [Time/resources required]
**Upside:** [Best case outcome]
**Downside:** [Worst case outcome]
**Reversibility:** [Easy / Hard / Impossible]
```

Always include:
- **Option N: Do nothing** — What happens if we don't decide or act?

### Evaluation Criteria

What matters most for THIS decision:

| Criteria | Weight | Option A | Option B | Option C |
|----------|--------|----------|----------|----------|
| [Criteria 1] | [H/M/L] | [score] | [score] | [score] |
| [Criteria 2] | [H/M/L] | [score] | [score] | [score] |
| [Criteria 3] | [H/M/L] | [score] | [score] | [score] |

## Step 3: Pre-Mortem (for one-way doors)

"Imagine we chose [option] and it failed completely 6 months from now. What went wrong?"

For each option, generate 3-5 failure scenarios:
- What assumption was wrong?
- What external factor changed?
- What execution risk materialized?
- What stakeholder reaction occurred?

## Step 4: Stakeholder Input

"Who needs to weigh in before this decision?"

| Stakeholder | Why They Matter | Their Likely Position | When to Involve |
|------------|----------------|----------------------|----------------|
| [Person/Role] | [Why] | [Support/Oppose/Neutral] | [Before/During/After] |

## Step 5: Past Pattern Check

Search PM profile for similar past decisions:

**If similar decision found:**
"You faced a similar decision with [past project]: [decision]. The outcome was [outcome]. Key learning: [learning]. Does that apply here?"

**If no similar decision:** "This appears to be a new type of decision for you."

## Step 6: Recommendation

Based on the analysis:

```markdown
## Recommendation: [Option X]

**Why this option:**
- [Reason 1 tied to highest-weight criteria]
- [Reason 2]
- [Reason 3]

**Key risk to monitor:**
- [The biggest thing that could go wrong]
- **Mitigation:** [How to catch it early]

**Decision reversibility:** [Easy/Hard/Impossible]
**Confidence:** [High/Medium/Low]
```

## Step 7: Document and Log

Write to `docs/decisions/YYYY-MM-DD-<decision-name>.md`:

```markdown
---
date: YYYY-MM-DD
decision: "[statement]"
type: "[one_way_door | two_way_door]"
chosen: "[Option name]"
status: "[decided | pending_input | revisit_on_date]"
revisit_date: "YYYY-MM-DD"
---

# Decision: [Title]

## Context
[Why this decision needed to be made now]

## Options Evaluated
[Summary of each option with scores]

## Pre-Mortem
[Failure scenarios for chosen option]

## Decision
[What was decided and why]

## What Would Change This Decision
[Conditions under which we'd revisit]

## Stakeholder Sign-off
- [ ] [Stakeholder 1]
- [ ] [Stakeholder 2]
```

Also add to PM profile `decision_log`:
```yaml
- date: "YYYY-MM-DD"
  decision: "[statement]"
  type: "[one_way_door | two_way_door]"
  chosen: "[option]"
  rationale: "[why]"
  outcome: "pending"
  revisit_date: "YYYY-MM-DD"
```

## Post-Decision Options

**Options:**
1. **Share decision** — Generate stakeholder-specific communication
2. **Set reminder** — Flag for outcome review on [date]
3. **Run `/pm:spec`** — If decision leads to a spec
4. **Done** — Decision documented
