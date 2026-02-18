---
name: pm:buyin
description: Generate stakeholder-specific alignment narratives using proven buy-in techniques
argument-hint: "[spec doc path or feature description]"
---

# Stakeholder Buy-In

## Purpose

Take a product spec and generate targeted narratives for different stakeholder types. Each narrative uses the buy-in technique most effective for that audience. Adapts to the PM's stakeholder landscape from their profile.

## Input

<buyin_input> #$ARGUMENTS </buyin_input>

**If a file path:** Read the spec document.
**If empty:** Check `docs/specs/` for the most recent spec.

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
```

Extract the PM's:
- Stakeholder landscape
- Preferred buy-in techniques
- Past successful approaches

## Step 1: Identify Target Stakeholders

Use **AskUserQuestion tool**:

**Question:** "Who do you need buy-in from for this initiative?"

**Options (multiSelect: true):**
1. **Engineering leadership** — CTO, VP Eng, Eng Directors
2. **Design & Research** — Design leads, UX researchers
3. **Go-to-Market** — Sales, Marketing, Channel Partners
4. **Executive leadership** — CEO, CPO, GM, VP Product

**If PM profile has `stakeholders`:** Pre-populate with known stakeholder types.

## Step 2: Generate Narratives

For each selected stakeholder type, generate a narrative using the most effective technique.

### For Visionary Stakeholders (executives, CPO)
**Technique: Narration + Vision**

Structure:
1. **The world today** — Paint the current reality with specific pain
2. **The world tomorrow** — What changes with this initiative
3. **Why now** — Urgency and timing
4. **What we need** — Clear ask

Style: Story-driven, aspirational, tied to company mission.

### For Executor Stakeholders (engineering, ops)
**Technique: Citation + Concreteness**

Structure:
1. **The problem** — Specific, data-backed
2. **The approach** — Technical feasibility and approach
3. **The scope** — What's in and out
4. **The timeline** — Phased delivery
5. **The metrics** — How we know it worked

Style: Concrete, evidence-based, technically grounded.

### For Process-Driven Stakeholders (program management, compliance)
**Technique: Alignment + Social Proof**

Structure:
1. **Business alignment** — How this maps to OKRs/priorities
2. **Cross-team alignment** — Who else supports this
3. **Risk mitigation** — What could go wrong and how we handle it
4. **Success criteria** — Specific, measurable outcomes
5. **Governance** — Review cadence and decision points

Style: Structured, cross-referenced, risk-aware.

### For GTM Stakeholders (sales, marketing, partners)
**Technique: Goal Seek + Customer Voice**

Structure:
1. **Customer pain** — Direct quotes and specific scenarios
2. **Competitive context** — How competitors are positioned
3. **Revenue opportunity** — Quantified impact
4. **Positioning** — How we talk about this
5. **Sales enablement** — What they need to sell it

Style: Customer-centric, revenue-focused, actionable.

## Step 3: Apply Advanced Techniques

### Inception
For each narrative, frame the initiative so stakeholders feel ownership:
- "During our cross-team session, the idea of [X] came up..."
- "Building on [stakeholder]'s point about [Y]..."
- Reference past conversations or shared goals

### Framing
Steer the audience to the desired conclusion:
- Lead with shared goals
- Present data that supports the direction
- Frame alternatives as less aligned with stated priorities

### Social Proof
Leverage shared opinions:
- "3 of our top 5 customers have asked for this"
- "Industry trend toward [X] — [competitor A] and [competitor B] have already moved"
- Reference internal supporters

## Step 4: Generate Documents

Write narratives to `docs/narratives/YYYY-MM-DD-<feature>-<stakeholder>.md`.

Example output:
```
docs/narratives/
├── 2026-02-12-task-center-executive.md
├── 2026-02-12-task-center-engineering.md
├── 2026-02-12-task-center-gtm.md
└── 2026-02-12-task-center-program.md
```

## Post-Generation Options

**Options:**
1. **Review and refine** — Adjust narratives for specific people
2. **Create presentation** — Convert to slide-friendly format
3. **Schedule conversations** — Draft async messages or meeting agendas
4. **Done** — Narratives are ready
