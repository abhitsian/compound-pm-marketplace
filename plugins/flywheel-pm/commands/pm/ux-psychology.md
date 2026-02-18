---
name: pm:ux-psychology
description: Apply behavioral design principles and cognitive psychology to a specific product flow
argument-hint: "[product flow or screen to analyze]"
---

# UX Psychology Analysis

## Purpose

Apply behavioral psychology and UX design principles to a specific product flow. Not a generic checklist — a targeted analysis of how human cognition, emotion, and behavior interact with your design at each step.

## Input

<ux_input> #$ARGUMENTS </ux_input>

**If empty:** Ask "What product flow or screen do you want to analyze through a behavioral psychology lens? Describe the flow or paste a screenshot."

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
```

Load relevant teardowns and friction logs:
```bash
ls docs/teardowns/ docs/friction-logs/ 2>/dev/null
```

## Step 1: Map the Flow

List each step in the user flow:
1. [Entry point — how do they get here?]
2. [Step 2]
3. [Step 3]
4. ...
N. [Completion — what happens after?]

For each step, note: What is the user supposed to DO here?

## Step 2: Apply Decision Science

### Hick's Law (Choice Overload)
For each step:
- How many choices is the user presented with?
- **Threshold:** >4 choices at any step creates decision fatigue
- **Fix:** Reduce choices, use progressive disclosure, set smart defaults

### Decision Fatigue
- How many decisions has the user made by this point in the flow?
- Is this flow positioned early or late in the user's session?
- **Fix:** Move complex decisions earlier, reduce total decision count, batch related choices

### Default Effect
- What happens if the user takes no action? Is the default good for them?
- **Principle:** 75-90% of users accept defaults. Make defaults serve the user.
- Are you using opt-out (user starts with it) or opt-in (user must choose it)?

## Step 3: Apply Cognitive Psychology

### Cold Start Problem
- What does the user see on first use with zero data?
- **Principle:** Users need value within 60 seconds or they question their decision to try.
- **Fix:** Pre-populate with examples, use progressive onboarding, show what's possible

### Progressive Disclosure
- Are you showing everything at once or revealing complexity gradually?
- **Principle:** Show only what's needed for the next decision. Hide the rest.
- Where is complexity exposed too early?

### Reactive Onboarding
- Are you teaching before doing, or letting them do first and teaching after?
- **Principle:** People learn by doing, not by reading. Let them act, then explain what happened.
- Where are you blocking action with education?

### Doherty Threshold
- Does any step take >400ms to respond?
- **Principle:** Delays >400ms break the user's feeling of direct manipulation.
- **Fix:** Skeleton screens, optimistic updates, loading states with useful information

### Context Craving
- At each step, does the user have enough context to act confidently?
- **Principle:** Sometimes users crave context and clarity OVER efficiency.
- Where are you prioritizing speed over understanding?

## Step 4: Apply Behavioral Psychology

### Social Proof
- Where could showing what others do reduce friction?
- **Types:** Number of users, testimonials, peer activity, expert endorsement
- **Warning:** Social proof backfires when numbers are small or irrelevant

### Loss Aversion
- What does the user stand to lose at each step?
- **Principle:** Pain of losing is 2x the pleasure of gaining.
- Frame gains as "don't miss out" rather than "you could get." But use ethically.

### Endowment Effect
- Has the user invested anything (time, data, personalization) before being asked to commit?
- **Principle:** People overvalue what they already have/built.
- **Tactic:** Get them to personalize BEFORE asking for payment/commitment

### Commitment Escalation (Foot-in-the-Door)
- Are you asking for a big commitment too early?
- **Principle:** Small actions of compliance snowball into larger ones.
- Start with a tiny ask. Build from there.

### Sunk Cost Engagement
- Can you show users what they've already invested?
- **Principle:** People continue activities they've already invested in.
- Progress bars, streaks, "you've already completed X" messaging

### Curiosity Gap
- Are there moments where incomplete information drives the user forward?
- **Principle:** People crave to complete incomplete information.
- Tease value, then deliver. But don't be manipulative.

### Framing Effects
- How are options, prices, or outcomes framed?
- **Principle:** "90% success rate" vs "10% failure rate" feel different despite being identical.
- Review every piece of copy for framing opportunities

## Step 5: Apply Emotional Design

### Cognitive Dissonance
- Is anything in the flow contradicting the user's beliefs or self-image?
- **Principle:** When beliefs conflict with actions, people feel discomfort and may abandon.
- **Example:** A health-conscious person using a junk food delivery app
- **Fix:** Align messaging with user identity. Don't surface contradictions.

### Aha Moment
- Where does the user first understand the true value?
- **Principle:** The Aha moment is when retention starts. Everything before it is at-risk.
- Is the path to Aha as short as possible?
- What percentage of users currently reach it?

### User Delight
- Where could you add unexpected positive moments?
- **Principle:** Peak-end rule — people remember the peak and the end most.
- Invest delight at the peak moment and the final step

### Anxiety Reduction
- Where is the user anxious? (payment, data sharing, irreversible actions)
- **Techniques:** Money-back guarantee, "you can change this later," preview before commit, undo option

### Accomplishment Signaling
- Does the product tell users they've achieved something?
- **Principle:** Dopamine hit from accomplishment drives repeat behavior.
- Celebrate completions. Show progress. Mark milestones.

## Step 6: Identify the Top 3 Psychological Friction Points

Across all the analysis, identify the 3 moments where psychology is most working against you:

1. **[Step X] — [Principle violated]:** [What's happening and why it hurts]
2. **[Step Y] — [Principle violated]:** [What's happening and why it hurts]
3. **[Step Z] — [Principle violated]:** [What's happening and why it hurts]

For each, provide a specific, actionable fix.

## Step 7: Generate Document

Write to `docs/ux-psychology/YYYY-MM-DD-<flow-name>.md`:

```markdown
---
date: YYYY-MM-DD
flow: "[flow name]"
steps_analyzed: [count]
top_issues: ["issue1", "issue2", "issue3"]
principles_applied: [count]
---

# UX Psychology: [Flow Name]

## Flow Map
[Steps in the flow]

## Decision Science Analysis
[Hick's Law, decision fatigue, defaults]

## Cognitive Psychology Analysis
[Cold start, progressive disclosure, reactive onboarding, Doherty threshold]

## Behavioral Psychology Analysis
[Social proof, loss aversion, endowment, commitment escalation, curiosity gap, framing]

## Emotional Design Analysis
[Cognitive dissonance, Aha moment, delight, anxiety, accomplishment]

## Top 3 Fixes
[Specific changes ranked by impact]

## Score Card
| Principle | Status | Priority |
|-----------|--------|----------|
| [Principle] | [Good / Needs Work / Broken] | [P1/P2/P3] |
```

## Post-Analysis Options

Use **AskUserQuestion tool**:

**Question:** "UX psychology analysis complete. What's next?"

**Options:**
1. **Run `/pm:friction-log`** — Create a detailed friction log for this flow
2. **Run `/pm:motivation-map`** — Map the motivation equation for this flow
3. **Apply to spec** — Integrate findings into `/pm:spec`
4. **Done** — Analysis documented
