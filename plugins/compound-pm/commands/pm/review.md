---
name: pm:review
description: Multi-agent review of a product spec from different PM perspectives
argument-hint: "[spec doc path]"
---

# Multi-Agent Spec Review

## Purpose

Spawn specialized PM review agents in parallel to evaluate a product spec from multiple perspectives. Each agent focuses on a specific domain and returns prioritized findings.

## Input

<review_input> #$ARGUMENTS </review_input>

**If a file path:** Read the spec document.
**If empty:** Check `docs/specs/` for the most recent spec.

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
```

Read the spec document in full.

## Step 1: Spawn Review Agents (Parallel)

Launch ALL of these agents **in parallel**:

### Customer & Problem

- Task **customer-advocate**: Does this spec actually solve the stated customer problem? Is the HMW framed correctly? Would the target persona find this valuable? Are edge cases covered? Is the journey map complete?

### Metrics & Measurement

- Task **metrics-reviewer**: Is the metrics framework complete? Is the activation funnel properly defined with measurable thresholds? Are outcome metrics actually measurable? Do leading indicators predict the outcome? Are baselines established? Is the Continue/Pause/Pivot criteria specific enough?

### Business & Strategy

- Task **business-case-reviewer**: Is the revenue impact quantified with methodology? Is the pricing/packaging decision justified? Does the competitive analysis hold up? Is strategic fit clearly articulated? Is the defensibility argument solid?

### Scope & Complexity

- Task **scope-creep-detector**: Is this solving one problem well, or three problems poorly? Are there capabilities listed that don't serve the core HMW? Is the scope boundary clear? Are there "nice to haves" disguised as "must haves"? Is the MVP actually minimum?

### Institutional Knowledge

- Task **past-pattern-checker**: Have we seen this pattern before? Search `docs/opportunities/`, `docs/compounds/`, and `docs/specs/` for similar past work. What did we learn? Are we repeating a mistake? Are we ignoring a past success?

## Step 2: Consolidate Findings

Wait for all agents to complete, then merge findings into a single prioritized list.

### Output Format

```markdown
## Spec Review: [Spec Title]

### P1 — MUST FIX (blocks shipping)
- [ ] [Finding] (agent-name)
- [ ] [Finding] (agent-name)

### P2 — SHOULD FIX (ship but fix soon)
- [ ] [Finding] (agent-name)
- [ ] [Finding] (agent-name)

### P3 — NICE TO FIX (consider for iteration)
- [ ] [Finding] (agent-name)
- [ ] [Finding] (agent-name)

### Strengths Noted
- [What's working well] (agent-name)
- [What's working well] (agent-name)
```

### Priority Classification

| Priority | Criteria |
|----------|---------|
| **P1 — MUST FIX** | Customer problem is wrong, metrics are unmeasurable, revenue estimate has no methodology, scope is unclear, past failure being repeated |
| **P2 — SHOULD FIX** | Missing edge cases, incomplete activation funnel, weak competitive analysis, trade-offs not documented |
| **P3 — NICE TO FIX** | Better framing possible, additional metrics would help, positioning could be sharper |

## Step 3: Present Findings

Show the consolidated review to the user.

## Post-Review Options

Use **AskUserQuestion tool**:

**Question:** "Review complete. [X] P1s, [Y] P2s, [Z] P3s found. What's next?"

**Options:**
1. **Fix all P1s** — Address must-fix findings and update spec
2. **Triage findings** — Go through each finding one by one to accept/reject/modify
3. **Fix all P1s and P2s** — Address both critical and important findings
4. **View details** — Deep dive into specific findings
