---
name: pm:solution
description: Design and evaluate solution approaches for an identified opportunity
argument-hint: "[opportunity doc path or description]"
---

# Solution Design & Evaluation

## Purpose

Take a framed opportunity and systematically generate, evaluate, and select solution approaches. Uses the PM's creativity techniques, classification framework, and validation criteria.

## Input

<solution_input> #$ARGUMENTS </solution_input>

**If a file path is provided:** Read the opportunity document.
**If a description is provided:** Use it as context.
**If empty:** Check `docs/opportunities/` for the most recent opportunity doc.

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
```

Read the opportunity document to extract: customer problem, HMW statement, persona, business context.

## Step 1: Solution Ideation

Apply the PM's creativity techniques systematically. Default: 20 techniques in two rounds.

### Round 1: Incremental Solutions (lower risk)
Apply these lenses to the HMW statement:

| Technique | Prompt |
|-----------|--------|
| Remove friction | What friction can we eliminate? |
| Add friction | Where would adding friction improve outcomes? |
| Bundle | What separate things should be combined? |
| Unbundle | What combined things should be separated? |
| Make it smaller | What's the minimum version that delivers value? |
| Make it unnecessary | Can we eliminate the need entirely? |
| Make it the only thing | What if this was the entire product? |
| Reduce anxiety | What worries users? How do we address that? |
| Solve an unexpressed need | What do users need but haven't asked for? |
| Make it skeuomorphic | What real-world metaphor fits? |

### Round 2: Innovative Solutions (higher risk, higher potential)
Apply these lenses:

| Technique | Prompt |
|-----------|--------|
| Do the opposite | What if we reversed the assumption? |
| Reframe | What if the problem is actually different? |
| Combine unrelated things | What unexpected combination creates value? |
| Solve multiple problems | Can one solution address several pain points? |
| Surprise | What would delight users unexpectedly? |
| Make them feel smarter | How can the product make users look good? |
| Build distribution in | How can the product spread itself? |
| Add constraints | What constraints would force a better solution? |
| Remove constraints | What rules are we following unnecessarily? |
| Make it much bigger | What if we 10x the scope? |

Present the top 3-5 most promising solutions.

## Step 2: Define Metrics Per Solution

For each proposed solution, define:

| Metric Type | Definition |
|-------------|-----------|
| **Primary success metric** | The outcome metric this directly impacts |
| **Secondary metric** | Supporting indicator |
| **Tradeoff metric** | What might get worse |
| **Leading indicator** | Early signal of success/failure |

## Step 3: Evaluate Solutions

### Risk Assessment (per solution)
Score each on four dimensions:

- **Valuable** — Will the customer find it valuable?
- **Usable** — Will the customer be able to use it?
- **Feasible** — Can we build it with current capabilities?
- **Viable** — Will it impact the outcome metric as hoped?

### Risk vs Impact Matrix
Plot each solution:

```
         High Impact
              │
  Big Bets    │    No Brainers
              │
─────────────────────────────
              │
  Duds        │    Quick Wins
              │
         Low Impact
```

### Classification
Label each solution as:
- **Differentiator** — Unique competitive advantage
- **MMR (Minimum Market Requirement)** — Must-have to compete
- **Neutralizer** — Catches up to competitors

## Step 4: Validation Plan

For each shortlisted solution, define how to validate assumptions:

| Risk Type | Validation Method |
|-----------|-------------------|
| **Value risk** | Painted doors, user interviews, surveys |
| **Usability risk** | Prototype testing, user testing with mocks |
| **Feasibility risk** | Engineering spikes, technical POCs |
| **Viability risk** | Talk with sales/GTM, recruit pilot customers |

## Step 5: Reference Past Solutions

**If PM profile has `project_patterns`:**
- Find similar past solutions
- "When we faced [similar problem], we chose [approach] and it resulted in [outcome]."
- Flag any patterns: "We've used [approach] 3 times — it tends to [pattern]."

## Step 6: Generate Solution Document

Write to `docs/solutions/YYYY-MM-DD-<kebab-case-name>-solutions.md`:

```markdown
---
date: YYYY-MM-DD
opportunity: "[link to opportunity doc]"
solutions_evaluated: [count]
recommended: "[solution name]"
classification: "[differentiator | mmr | neutralizer]"
status: "evaluated"
---

# Solutions: [Opportunity Title]

## Opportunity Summary
[Brief recap of the customer problem and HMW]

## Solutions Evaluated

### Solution A: [Name] ← Recommended
[Description]

**Metrics:**
- Primary: [metric]
- Secondary: [metric]
- Tradeoff: [metric]
- Leading indicator: [metric]

**Risk Assessment:** V[score] U[score] F[score] Vi[score]
**Classification:** [Differentiator | MMR | Neutralizer]
**Risk vs Impact:** [No Brainer | Big Bet | Quick Win]

### Solution B: [Name]
[Same structure]

### Solution C: [Name]
[Same structure]

## Recommendation
[Which solution and why — referencing risk/impact, classification, and past patterns]

## Validation Plan
[How to validate before full build]

## Trade-offs Documented
[Key trade-off decisions and rationale]

## Next Steps
→ `/pm:spec` to detail the recommended solution
→ `/pm:buyin` to align stakeholders on the approach
```

## Post-Generation Options

Use **AskUserQuestion tool**:

**Options:**
1. **Run `/pm:spec`** — Detail the recommended solution
2. **Run `/pm:buyin`** — Create stakeholder alignment narratives
3. **Explore more solutions** — Apply additional creativity techniques
4. **Compare with past projects** — See how similar decisions played out
