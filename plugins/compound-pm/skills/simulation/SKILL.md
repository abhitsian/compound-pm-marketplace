---
name: simulation
description: Cognitive empathy engine — simulation, metacognition, and intellectual flexibility for product decisions. Use when modeling user behavior, checking assumptions, or developing product intuition.
---

# Simulation Skill

## Purpose

Provide the cognitive empathy toolkit that underlies great product judgment. Simulation is the capacity to mentally model how others think, feel, and act — the core skill that separates good PMs from great ones.

Based on Shreyas Doshi's Product Sense framework.

## Three Components of Cognitive Empathy

### 1. Metacognition — Understanding Your Own Thinking

The ability to watch your own thought process and catch biases in real-time.

**Practices:**
- "What is causing this thought?" — Trace your reasoning backward
- "Why does this feeling exist?" — Separate emotion from analysis
- "Name your mind" — When your brain says "users will love this," ask which part of your brain is speaking (optimism? pattern matching? wishful thinking?)
- "Reward yourself for finding the cognitive bias behind past decisions" — Celebrate catching yourself, not being right

**Product application:**
- Before evaluating any feature: "What's my gut reaction, and what biases might drive it?"
- After any product decision: "Was I right for the right reasons, or right by luck?"
- During teardowns: "Am I evaluating this product, or projecting my preferences?"

### 2. Intellectual Flexibility — Updating Beliefs

The ability to change your mind when evidence warrants it.

**The 5-Question Test (use when stuck on a position):**
1. Have I been exactly right about everything? (No.)
2. Is there anyone in history more right than me on this? (Yes.)
3. Is it remotely possible that info I don't have could improve my view? (Yes.)
4. Given the stakes and ambiguity, is seeking that info worthwhile? (Evaluate.)
5. Is there a non-zero chance of a better decision with more input? (Usually yes.)

**Product application:**
- When you're certain about a product direction: Run the 5-question test
- When data contradicts your hypothesis: Celebrate the data, don't explain it away
- When a junior team member disagrees: Their fresh perspective might see what your experience blinds you to

### 3. Simulation — Modeling Others

The capacity to mentally envision how others think, feel, and act based on their unique context.

**Techniques:**
- **Out of body experience:** Physically imagine being the user. Where are they? What device? What mood? What just happened before this?
- **"Wake up in the morning" test:** Does this person wake up thinking about this problem? If not, your feature has an awareness problem before it has an adoption problem.
- **Nth order effects:** Go beyond first-order. If users do X, then Y happens, which causes Z. What does Z look like?

**Null Hypotheses:**
- **Consumer:** Users are lazy, selfish, vain, confused, and easily distracted
- **B2B:** Customer doesn't need your product, won't pay, won't deploy, won't use it

Products must overcome these defaults. Anything that doesn't is a weakness.

## Motivation Theory Framework

Every user action is governed by:

```
Nudge × (Motivation − Friction)^Satisfaction = Adoption
```

### Motivation Types
| Type | Question | Example |
|------|----------|---------|
| **Functional** | What tasks do I want to perform? | "I need to track expenses" |
| **Social** | How do I want to be perceived? | "I want my team to see me as organized" |
| **Emotional** | How do I want to feel? | "I want to feel in control of my finances" |
| **Personal** | What does this say about me? | "I'm the kind of person who plans ahead" |

### Friction Types
| Type | Questions to Ask |
|------|-----------------|
| **Comprehension** | Do I understand this? Is the next action clear? |
| **Decision** | How many choices? How complex? What's the cost of being wrong? |
| **Action** | How hard to start? How hard to finish? |
| **Habit** | How inconsistent with my current behavior? |
| **Emotional** | What do I stand to lose? How anxious does this make me? |

### Nudge Types
| Type | Source | Example |
|------|--------|---------|
| **Intrinsic** | Within the user | Personal motivation, habits, self-imposed rules |
| **Extrinsic** | From the product/environment | Notifications, social proof, defaults, urgency |

**Critical alignment:** Nudges must match the dominant motivation type. A functional nudge ("save 2 hours") won't move a socially-motivated user ("your team is using this").

### Satisfaction Checks
- Did it fulfill the promised job?
- Did it live up to expectations?
- Did it generate happy hormones?
- Did it give social validation?
- Did it make them feel smart?

## Cognitive Bias Reference (Product-Relevant)

### Biases That Affect Users
| Bias | Product Impact | Design Response |
|------|---------------|----------------|
| Status quo | Users resist change | Make defaults good; minimize required changes |
| Loss aversion | Fear of losing > joy of gaining | Frame as "don't miss out" vs "you could get" |
| Social proof | People follow others | Show what others are doing |
| Anchoring | First number sticks | Set anchors intentionally |
| Endowment | People overvalue what they own | Get users to invest (personalize) early |
| Ambiguity aversion | Prefer known risk over unknown | Provide clear information, reduce uncertainty |

### Biases That Affect PMs
| Bias | PM Impact | Mitigation |
|------|-----------|-----------|
| Confirmation | Seeking supporting evidence | Actively seek disconfirmation |
| Mimetic desire | Copying competitors | "Would I do this if no one else was?" |
| Sunk cost | Continuing failing projects | "If starting fresh, would I choose this?" |
| Planning fallacy | Underestimating effort | Use reference class forecasting |
| Survivorship | Learning only from successes | Study failures equally |

## How to Use This Skill

This skill is loaded as context by:
- `/pm:teardown` — for simulation and bias analysis
- `/pm:simulate` — for per-segment user modeling
- `/pm:bias-check` — for PM decision bias detection
- `/pm:friction-log` — for friction categorization
- `/pm:motivation-map` — for adoption equation analysis

It can also be invoked directly when any command needs to model user behavior or check cognitive biases.
