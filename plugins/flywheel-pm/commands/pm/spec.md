---
name: pm:spec
description: Transform a solution into a detailed, actionable product specification — from solution docs or via structured interview
argument-hint: "[solution doc path, feature description, or 'interview']"
---

# Product Specification

## Purpose

Take a recommended solution and produce a detailed spec that engineering, design, and stakeholders can execute against. Adapts to the PM's preferred spec structure, metrics framework, and vocabulary.

Supports two modes:
1. **Pipeline Mode** — Generate spec from an existing solution/opportunity doc (default)
2. **Interview Mode** — Create spec from scratch by interviewing the PM using AskUserQuestion

## Input

<spec_input> #$ARGUMENTS </spec_input>

## Step 0: Load Context & Select Mode

```bash
cat pm-profile.yaml 2>/dev/null
```

**Determine mode from input:**
- If input contains "interview" or no solution/opportunity doc exists → **Interview Mode** (go to Step 0a)
- If input is a file path or description → **Pipeline Mode** (go to Step 1)
- If empty → Ask the user

**If mode is ambiguous**, use **AskUserQuestion tool**:

**Question:** "How would you like to create this spec?"

**Options:**
1. **From solution doc** — I have a solution or opportunity doc to work from
2. **Interview me** — Start from scratch — ask me questions and build the spec from my answers
3. **Review existing spec** — Analyze a spec I already have against the quality checklist

If the user selects **"Interview me"** → go to Step 0a.
If the user selects **"Review existing spec"** → go to Step 0b.
Otherwise → go to Step 1 (Pipeline Mode).

## Step 0a: Interview Mode (AskUserQuestion-Based)

Read the spec template reference file for the full question framework:
```
Read skills/spec-review/references/spec-template.md
```

### Initial Context

Use **AskUserQuestion tool** to gather basic context:

**Question:** "What are we speccing? Give me the high-level picture."

**Options:**
1. **New feature** — Adding something that doesn't exist yet
2. **Enhancement** — Improving existing functionality
3. **Redesign** — Rethinking how something works

Then ask: feature name, target users, and high-level goal.

### Structured Interview

Walk through the 9 question categories from the spec-review skill, using AskUserQuestion for each group. Ask 2-3 questions per call, making options concrete and specific to the PM's project.

**Interview order:**
1. **Problem & Context** (questions 1-4) — User pain, persona, goals, business justification
2. **Scope & Prioritization** (questions 5-7) — MVP vs future, dependencies, constraints
3. **User Flows & Experience** (questions 8-12) — Happy path, entry points, UI, feedback, responsive
4. **Business Logic & Validation** (questions 13-16) — Input rules, business rules, data, limits
5. **Edge Cases & Error Handling** (questions 17-20) — Errors, communication, concurrency, boundaries
6. **Permissions & Security** (questions 21-24) — Access, roles, privacy, security risks
7. **Cross-Cutting Concerns** (questions 25-28) — Accessibility, loading, offline, patterns
8. **Success Metrics** (questions 29-31) — KPIs, analytics, launch criteria
9. **Assumptions & Risks** (questions 32-34) — Assumptions, open questions, failure modes

**Interview rules:**
- Ask non-obvious questions that surface hidden complexity
- Probe for edge cases: "What happens if..."
- Clarify scope boundaries: "What are we NOT doing?"
- Validate assumptions: "Are we assuming..."
- Explore error scenarios: "What can go wrong?"
- Define success: "How do we measure this worked?"
- Consider all user types: "Who can/cannot do this?"
- Follow up on vague answers — don't accept "it should work well"

After gathering all answers, proceed to Step 1 using interview answers as context (skip solution doc reading). Generate the full spec using the template structure from Part 2 of the reference file.

## Step 0b: Checklist Review Mode

Ask the user for the spec file path, then read:
1. The spec file to review
2. The review checklist from the spec-review skill

Analyze against the completeness checklist, quality checklist, and red flags list. Generate a review report:

```markdown
## Spec Review: [Feature Name]

**Overall Assessment:** [Complete / Needs Work / Incomplete]

### Strengths
- [What's well-documented]

### Critical (Must-fix before implementation)
- [ ] [Finding with specific recommendation]

### Important (Should-fix for quality)
- [ ] [Finding with specific recommendation]

### Nice-to-have (Would improve but not blocking)
- [ ] [Finding with specific recommendation]

### Questions for PM
- [Clarifying questions to resolve gaps]
```

Then use **AskUserQuestion tool**:

**Question:** "Review complete. [X] critical, [Y] important, [Z] nice-to-have findings. What's next?"

**Options:**
1. **Fix all critical issues** — Address must-fix findings and update spec
2. **Triage findings** — Go through each finding one by one to accept/reject/modify
3. **Fix all critical + important** — Address both tiers
4. **Run full `/pm:review`** — Multi-agent deep review with 5 specialized agents

**Done.** Do not proceed to Steps 1-7 for review mode.

## Step 1: Vision Narrative

Read solution doc to extract: recommended solution, metrics, risk assessment, validation plan.

## Step 1: Vision Narrative

Write a vision narrative following the PM's preferred structure. Default: 3-part structure.

### Part 1: The Aspirational Problem
Describe the problem in visceral, emotional terms. Lead with the user's pain.
- Use specific numbers and scenarios
- Make the reader feel the problem

### Part 2: The Opinionated Solution
Describe the solution in detail. Be specific and opinionated.
- Walk through the user journey step by step
- Show how each pain point is resolved
- Include key interactions and moments

### Part 3: The User-Centric Resolution
Close with what the user's world looks like after.
- Concrete outcome (time saved, friction removed)
- Emotional resolution (confidence, ease, delight)

## Step 2: Customer Journey Map

Map the end-to-end user journey with friction points:

```markdown
| Step | User Action | Current Experience | New Experience | Friction Removed |
|------|------------|-------------------|----------------|-----------------|
| 1    | [action]   | [pain]            | [improvement]  | [friction type] |
```

Rank friction points by:
- **Intensity** — How painful is this?
- **Frequency** — How often does this happen?
- **Impact** — What's the business impact of solving this?

## Step 3: Solution Details

### Core Capabilities
For each capability in the solution:
- **What it does** — Functional description
- **Why it matters** — User value
- **How it works** — Key interactions
- **Differentiator / MMR / Neutralizer** — Classification

### Trade-offs
Document every trade-off decision:
- **What we chose** vs **What we didn't choose**
- **Short-term** vs **Long-term** implications
- **Rationale** — Why this trade-off is acceptable

### Scope Boundaries
- **In scope** — What we're building
- **Out of scope** — What we're explicitly NOT building and why
- **Future scope** — What comes next if this succeeds

## Step 4: Metrics Framework

Use the PM's preferred metrics hierarchy. Default:

### Outcome Metric
The business outcome this drives. Define:
- Metric name and formula
- Current baseline
- Target
- Measurement methodology

### Activation Funnel
Use the PM's preferred funnel. Default: Setup → Aha → Habit.

| Stage | Definition | Target | Measurement |
|-------|-----------|--------|-------------|
| **Setup** | [What constitutes setup complete] | [%] | [How measured] |
| **Aha** | [First value moment] | [%] | [How measured] |
| **Habit** | [Repeated value — define frequency] | [%] | [How measured] |

**If PM profile has `thresholds`:** Pre-fill targets based on past project averages.

### Engagement Metrics
Use the PM's preferred dimensions. Default: Breadth / Depth / Intensity.

| Dimension | Metric | Definition |
|-----------|--------|-----------|
| **Breadth** | Features used | Average features used per [period] |
| **Depth** | Frequency | Average [actions] per [period] |
| **Intensity** | Time spent | Average time per session |

### User Segmentation
Use the PM's preferred segmentation. Default: Casual / Core / Power.

| Segment | Definition | Target Distribution |
|---------|-----------|-------------------|
| **Casual** | [frequency definition] | [%] |
| **Core** | [frequency definition] | [%] |
| **Power** | [frequency definition] | [%] |

### Business Metrics
- Revenue impact (quantified)
- Retention impact
- Expansion/upsell potential
- Platform value

## Step 5: Pricing & Packaging

Based on the PM's past patterns:
- **Who benefits?** All customers or a segment?
- **Which SKU?** Base, Pro, Add-on, New SKU?
- **Rationale** — Why this packaging decision?
- **WTP analysis** — What are alternatives? What would customers pay?

**If PM profile has past packaging decisions:** Reference them.

## Step 6: Launch Criteria

### Continue / Pause / Pivot Framework
Define criteria for each decision:

| Decision | Criteria |
|----------|---------|
| **Continue investing** | [specific metric thresholds met] |
| **Pause investment** | [metric thresholds not met after X period] |
| **Pivot** | [fundamental assumption invalidated] |

### Positioning
- **Positioning strategy** — Differentiator-based, value-based, or category-based
- **Key message** — One sentence that captures the value
- **Buyer awareness** — What do buyers need to understand?

## Step 7: Generate Spec Document

Write to `docs/specs/YYYY-MM-DD-<kebab-case-name>-spec.md`:

```markdown
---
date: YYYY-MM-DD
opportunity: "[link to opportunity doc]"
solution: "[link to solution doc]"
status: "draft"
outcome_metric: "[primary outcome metric]"
target: "[metric target]"
sku: "[base | pro | add-on | new]"
---

# Spec: [Feature Title]

## Vision Narrative
[3-part narrative]

## Customer Journey
[Journey map with friction points]

## Solution Details
### Capabilities
### Trade-offs
### Scope

## Metrics
### Outcome Metric
### Activation Funnel
### Engagement
### User Segments
### Business Metrics

## Pricing & Packaging
[SKU decision with rationale]

## Launch Criteria
### Continue / Pause / Pivot
### Positioning

## Open Questions
[Unresolved items]

## Next Steps
→ `/pm:review` to get multi-agent spec review
→ `/pm:buyin` to create stakeholder narratives
→ Hand off to engineering for `/workflows:plan`
```

## Post-Generation Options

**Options:**
1. **Run `/pm:review`** — Multi-agent spec review
2. **Run `/pm:buyin`** — Create stakeholder alignment narratives
3. **Refine spec** — Adjust sections
4. **Hand off to engineering** — Generate a `/workflows:plan` compatible plan
