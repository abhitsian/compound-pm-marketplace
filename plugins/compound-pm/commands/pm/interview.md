---
name: pm:interview
description: Prepare interview guides, capture structured notes, and extract patterns from customer conversations
argument-hint: "[research question, persona, or 'debrief' to capture notes from a completed interview]"
---

# Customer Interview

## Purpose

World-class PMs generate insights, they don't just process them. This command helps prepare for customer interviews, capture structured notes, and build a searchable research library that feeds into opportunity evaluation.

## Input

<interview_input> #$ARGUMENTS </interview_input>

## Mode Detection

Determine the mode from input:

| Input | Mode |
|-------|------|
| Research question or topic | **Prepare** — Generate interview guide |
| "debrief" or "capture" | **Debrief** — Capture notes from completed interview |
| File path to past interviews | **Analyze** — Extract patterns across interviews |
| Empty | Ask which mode |

---

## Mode 1: Prepare Interview Guide

### Step 1: Understand the Research Goal

Use **AskUserQuestion tool**:

- "What are you trying to learn?" (The research question, not the feature)
- "Who are you talking to?" (Persona, role, company type)
- "What do you already know or assume?" (Hypotheses to validate/invalidate)
- "How many interviews are planned?" (1 exploratory, 5 for patterns, 10+ for validation)

### Step 2: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
```

Check for past interviews on this topic:
```bash
ls docs/research/interviews/ 2>/dev/null
```

### Step 3: Generate Interview Guide

Structure based on research type:

#### Exploratory Interview (learning, open-ended)
```markdown
# Interview Guide: [Topic]
Date: YYYY-MM-DD
Research Question: [What we're trying to learn]

## Warm-up (2 min)
- Thank them for their time
- Explain the purpose (learning, not selling)
- Ask permission to take notes

## Context Setting (5 min)
- "Tell me about your role and what a typical day looks like."
- "How does [topic area] fit into your work?"

## Current Behavior (10 min)
- "Walk me through the last time you [did the thing we're researching]."
- "What was the hardest part?"
- "What happened next?"
- [Follow the story, don't redirect]

## Pain Points (10 min)
- "What's the most frustrating thing about [process]?"
- "If you could wave a magic wand, what would change?"
- "How do you work around [problem] today?"

## Validation (5 min)
- [Hypothesis-specific questions]
- "On a scale of 1-10, how painful is [specific problem]?"
- "Would you pay to solve this? How much?"

## Close (3 min)
- "Is there anything I should have asked but didn't?"
- "Would you be open to testing a prototype when we have one?"
- "Can you introduce me to anyone else who deals with this?"

## Notes for Interviewer
- Listen more than talk (80/20 rule)
- Follow stories, don't redirect to your script
- Write down exact quotes
- Note emotions and body language
- Don't pitch or validate your solution
```

#### Validation Interview (testing specific hypotheses)
```markdown
# Interview Guide: [Feature/Hypothesis]
Date: YYYY-MM-DD
Hypothesis: [What we believe to be true]

## Setup
- "We're testing an idea and want your honest feedback."

## Current State
- "How do you handle [problem] today?"
- "How often does this come up?"

## Hypothesis Testing
- Show concept/prototype
- "What's your first reaction?"
- "Would this fit into how you work today?"
- "What would stop you from using this?"
- "What's missing?"

## Prioritization
- "Compared to [other problems], where does this rank?"
- "Would this change how you use [product]?"
```

### Step 4: Save Guide

Write to `docs/research/guides/YYYY-MM-DD-<topic>-guide.md`

**Options:**
1. **Start interviewing** — Come back after for `/pm:interview debrief`
2. **Refine guide** — Adjust questions
3. **Review past interviews** — Check if similar research exists

---

## Mode 2: Debrief (Capture Interview Notes)

### Step 1: Capture Raw Notes

Ask the PM to share their notes, or walk through the interview:

- "Who did you talk to?" (Role, company, persona)
- "What was the top insight from this conversation?"
- "Any direct quotes worth capturing?"
- "What surprised you?"
- "Did it confirm or challenge your hypothesis?"
- "What should you ask next time?"

### Step 2: Structure the Notes

```markdown
---
date: YYYY-MM-DD
participant:
  role: "[Role]"
  company_type: "[Company type/size]"
  persona: "[Persona category]"
research_question: "[What we were learning]"
hypothesis_status: "[confirmed | challenged | new_insight]"
confidence_contribution: "[how much this moves our confidence]"
---

# Interview: [Participant Role] at [Company Type]

## Key Insights

### Insight 1: [Title]
**Quote:** "[Exact quote]"
**Implication:** [What this means for our product]
**Confidence:** [1 participant / 3 of 5 / widespread]

### Insight 2: [Title]
**Quote:** "[Exact quote]"
**Implication:** [What this means]
**Confidence:** [level]

## Current Behavior
[How they handle the problem today]

## Pain Points (ranked by participant)
1. [Most painful]
2. [Second]
3. [Third]

## Workarounds
[How they hack around the problem]

## Surprising Findings
[Things we didn't expect]

## Hypothesis Update
- **Before:** [What we believed]
- **After:** [How this interview changes our view]
- **Remaining questions:** [What we still need to learn]

## Follow-up Actions
- [ ] [Action item]
- [ ] [Action item]
```

### Step 3: Save and Cross-Reference

Write to `docs/research/interviews/YYYY-MM-DD-<participant-type>.md`

Check if enough interviews exist to run synthesis:
```bash
ls docs/research/interviews/ | wc -l
```

If 3+ interviews on the same topic exist:
"You have [X] interviews on this topic. Run `/pm:research-synthesis` to extract patterns across all interviews?"

---

## Mode 3: Analyze (Pattern Extraction)

### Step 1: Load All Interviews

Read all interview files matching the topic:
```bash
ls docs/research/interviews/*[topic]*.md
```

Or read all interviews in the directory if no topic specified.

### Step 2: Extract Patterns

Across all interviews, identify:

| Pattern Type | What to Look For |
|-------------|-----------------|
| **Frequency** | Same pain point mentioned in X of Y interviews |
| **Intensity** | Pain rated 8+ in multiple interviews |
| **Workarounds** | Same hack used by multiple participants |
| **Quotes** | Similar language used independently |
| **Segments** | Different personas experiencing the problem differently |
| **Surprises** | Unexpected findings that appeared in 2+ interviews |

### Step 3: Generate Research Synthesis

Write to `docs/research/synthesis/YYYY-MM-DD-<topic>-synthesis.md`:

```markdown
---
date: YYYY-MM-DD
topic: "[Research topic]"
interviews_analyzed: [count]
personas_represented: ["persona1", "persona2"]
confidence_level: "[high | medium | low]"
---

# Research Synthesis: [Topic]

## Summary
[2-3 sentence executive summary of findings]

## Top Findings (by frequency and intensity)

### Finding 1: [Title] (mentioned by X/Y participants)
**Evidence:**
- "[Quote 1]" — [Participant type]
- "[Quote 2]" — [Participant type]
**Implication:** [What to do with this]
**Confidence:** [High/Medium/Low based on sample]

### Finding 2: [Title] (mentioned by X/Y participants)
[Same structure]

## Persona Differences
[How different personas experience the problem differently]

## Workaround Patterns
[Common hacks people use — these are feature candidates]

## What We're Confident About
[Findings with strong evidence]

## What We're NOT Confident About
[Findings that need more research]

## Recommended Next Steps
- [ ] Run more interviews focused on [specific gap]
- [ ] Proceed to `/pm:opportunity` with [specific insight]
- [ ] Test [hypothesis] with painted door or prototype

## Raw Data
[Links to all individual interview files]
```

### Step 4: Feed into Opportunity Pipeline

**Options:**
1. **Run `/pm:opportunity`** — Convert top finding into an opportunity evaluation
2. **Run more interviews** — Generate a follow-up interview guide
3. **Share with team** — Export synthesis for team review
4. **Done** — Research captured
