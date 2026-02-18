---
name: behavioral-design
description: Apply behavioral psychology, UX principles, and decision science to product design. Use when designing user flows, evaluating UX quality, or diagnosing adoption problems.
---

# Behavioral Design Skill

## Purpose

Provide the behavioral psychology and UX design toolkit for building products that work with human nature, not against it. Covers decision science, cognitive psychology, emotional design, and habit formation.

## Decision Science

### Hick's Law
More choices = longer decision time = more abandonment.
- **Threshold:** >4 choices creates measurable decision fatigue
- **Fix:** Reduce choices, smart defaults, progressive disclosure

### Decision Fatigue
Users have a finite daily budget of decisions. Each decision depletes it.
- Late-in-session decisions get less attention
- Users default to "do nothing" when fatigued
- **Fix:** Front-load important decisions, batch related choices

### Default Effect
75-90% of users accept defaults.
- Defaults should serve the USER, not just the business
- Opt-out > Opt-in for desirable behaviors
- The default IS the experience for most users

### Framing Effect
Identical information presented differently leads to different decisions.
- "90% success rate" vs "10% failure rate" feel different
- "Save $50" vs "Don't lose $50" trigger different responses
- Review every piece of copy for framing opportunities

## Cognitive Psychology

### Cold Start Problem
Zero-data states are where most users churn.
- Users need value within 60 seconds
- Pre-populate with examples or sample data
- Show what's possible before asking for input
- "Empty state = churn state"

### Progressive Disclosure
Show only what's needed for the next decision.
- Hide complexity behind progressive layers
- Let users discover depth, don't force it
- Match information density to user sophistication level

### Reactive Onboarding
Let users DO first, then teach.
- Do not block action with education
- After the user acts, explain what happened and why
- Learning by doing > learning by reading
- Tutorial overlays have <5% completion rates. Stop using them.

### Doherty Threshold
Responses >400ms break the feeling of direct manipulation.
- Users perceive delays >1s as a different interaction mode
- Skeleton screens > spinners > blank screens
- Optimistic updates for user-initiated actions
- If delay is unavoidable: show useful information during the wait

### Context Craving
Sometimes users want clarity MORE than efficiency.
- Not every flow should be minimized
- Key moments (payment, data deletion, account changes) benefit from extra context
- Match speed to stakes

## Behavioral Psychology

### Social Proof
People follow others, especially similar others.
- **Types:** User counts, testimonials, peer activity, expert endorsement
- **Most effective:** Showing what similar users did (not generic "1M users")
- **Backfires when:** Numbers are small, audience is irrelevant, feels manipulative

### Loss Aversion
Pain of losing is 2x the pleasure of gaining.
- Users overvalue what they already have (endowment effect)
- Frame feature adoption as "don't lose X" rather than "gain X"
- Show users what they'll miss if they don't act
- Use ethically — this is powerful and easily abused

### Commitment Escalation (Foot-in-the-Door)
Small compliance → larger compliance.
- Start with a tiny ask (one-click action)
- Gradually increase commitment
- Each completed action makes the next more likely
- Personalization before payment leverages endowment effect

### Curiosity Gap
Incomplete information creates a craving to fill it.
- Tease value before delivering it
- "See how your metrics compare" > "Analytics dashboard"
- Progress indicators create curiosity about completion
- Don't be manipulative — deliver on the tease

### Mimetic Desire
People want what they see others wanting.
- Showing demand signals increases desire
- "Trending" and "popular" labels drive behavior
- In B2B: case studies showing peer success
- Warning: drives imitation, not necessarily good decisions

### Reciprocity
People feel compelled to return favors.
- Give value before asking for commitment
- Free tools, templates, insights → builds obligation
- Unexpected generosity is most effective

## Emotional Design

### Cognitive Dissonance
When beliefs conflict with actions, users feel discomfort.
- **Do not** remind users of behaviors that conflict with their self-image
- **Do** align messaging with the identity they want
- Users cope by: lying to themselves, changing behavior, or adopting offsetting behavior
- Products that surface contradictions lose users (Netflix "hours watched" backlash)

### Aha Moment
The moment a user understands the true value.
- Everything before the Aha moment is at-risk retention
- Identify your Aha moment precisely
- Make the path to Aha as short as possible
- Measure what % of users reach it and optimize ruthlessly

### Peak-End Rule
People remember the PEAK experience and the ENDING.
- Invest in making the peak moment amazing
- End every flow on a positive note
- A mediocre middle is forgiven if peak and end are strong

### Accomplishment Signaling
The dopamine hit from completing things drives repeat behavior.
- Celebrate completions (progress bars, congratulations, milestones)
- Break large tasks into small wins
- Show cumulative progress ("You've saved 14 hours this month")
- Make effort visible — people value results more when they see the work

### Anxiety Reduction
Anxious users don't convert.
- Identify anxiety points (payment, data sharing, irreversible actions)
- Add safety signals: "You can change this later," "Money-back guarantee," "Preview before submit"
- Undo > "Are you sure?" confirmation dialogs

## Habit Formation

### The Hook Model
```
Trigger → Action → Variable Reward → Investment
   ↑                                      │
   └──────── investment creates ──────────┘
```

- **Trigger:** Internal (emotion, need) or external (notification, context)
- **Action:** Simplest behavior in anticipation of reward
- **Variable Reward:** Unpredictable positive outcomes (social, material, self-achievement)
- **Investment:** User puts something in (data, content, social capital) that improves next cycle

### Habit Metrics
- Time between uses (decreasing = habit forming)
- % of sessions initiated by internal vs external trigger
- Usage without prompting/notification
