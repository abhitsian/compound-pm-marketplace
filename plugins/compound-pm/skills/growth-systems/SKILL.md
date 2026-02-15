---
name: growth-systems
description: Growth loops, retention frameworks, viral mechanics, and acquisition models. Use when designing growth engines, diagnosing retention problems, or evaluating acquisition strategies.
---

# Growth Systems Skill

## Purpose

Growth is a system of interconnected loops, not a set of tactics. This skill provides frameworks for understanding, measuring, and improving the loops that drive product growth.

Based on Reforge growth frameworks and Web 2.0/mobile-era viral loop mechanics.

## Growth Loop Fundamentals

### What Is a Growth Loop?
A closed system where the output of one cycle becomes the input of the next.

```
Input → User Action → Output → [Output becomes next cycle's Input]
```

Unlike funnels (which have a start and end), loops are self-reinforcing. The best products have one dominant loop that drives the majority of growth.

### Types of Growth Loops

#### Acquisition Loops
| Loop | Mechanism | Example |
|------|-----------|---------|
| **Viral** | Users invite/share → new users join | Dropbox referral, WhatsApp sharing |
| **Content** | Users create → content discovered → new users create | YouTube, Instagram, TikTok |
| **Paid** | Revenue → ad spend → new users → revenue | Subscription apps, SaaS |
| **SEO/AEO** | Content indexed → discovered via search/AI → conversion | Wikipedia, Stack Overflow |
| **Sales** | Success → referrals/case studies → new customers | Enterprise SaaS |
| **Community** | Users help users → community grows → attracts new users | Reddit, Discord |

#### Engagement Loops
| Loop | Mechanism | Example |
|------|-----------|---------|
| **Habit** | Trigger → action → reward → investment | Duolingo streaks, social feeds |
| **Social** | User acts → others notified → they act → notification | Slack, Instagram likes |
| **Progress** | Advance → unlock → new reasons to return | Gaming, learning platforms |
| **Recommendation** | Consume → algorithm learns → better suggestions | Netflix, Spotify |

#### Monetization Loops
| Loop | Mechanism | Example |
|------|-----------|---------|
| **Expansion** | Success → needs grow → upgrade → more success | Slack seats, AWS usage |
| **Network pricing** | More users → more value → higher WTP → investment | Marketplace pricing |

## Viral Mechanics

### Viral Factor Calculation

```
Viral Factor = New users acquired via existing users / Original cohort size
```

**Practical measurement:**
1. Take a cohort of users from a specific time period
2. Track shared URLs with user IDs (e.g., `product.com/share?ref=[user_id]`)
3. Count new signups attributed to that cohort
4. Ratio = viral factor

| Viral Factor | Interpretation |
|-------------|---------------|
| >1.0 | Self-sustaining viral growth (very rare) |
| 0.5-1.0 | Meaningful viral amplification |
| 0.1-0.5 | Some organic sharing |
| <0.1 | Not meaningfully viral |

### Optimization Levers
1. **Increase shares/invites per user** — Make sharing contextual and valuable
2. **Increase conversion on shared links** — Optimize landing experience
3. **Reduce time to first share** — Get users to value (and share) faster
4. **Improve targeting** — Help users share with people likely to convert

### Viral Loop Anti-Patterns
- **Address book imports** → Short-term growth, long-term spam reputation
- **Forced sharing** → Users resent mandatory social actions
- **Incentive-only referrals** → Attracts low-quality users motivated by reward, not product
- **Growth without retention** → Viral spikes followed by mass churn

## Retention Framework

### The 10 Stickiness Signals

| # | Signal | Healthy Threshold |
|---|--------|-------------------|
| 1 | Cohort retention curves flatten | Yes — plateau exists |
| 2 | Actives / Registered users | >25% |
| 3 | Power user curve (smile shape) | Concentration at high end |
| 4 | Viral factor | >0.5 |
| 5 | DAU/MAU ratio | >50% consumer, >30% B2B |
| 6 | D1/D7/D30 retention | >60/30/15 |
| 7 | Revenue per user expansion | Positive trend |
| 8 | Organic acquisition at scale | >60% |
| 9 | Subscription annual retention | >65% |
| 10 | Older markets more engaged | Yes |

**6+ green:** Strong retention → invest in growth loops
**3-5 green:** Adequate → fix gaps before scaling
**<3 green:** Weak → growth investment is premature

### Retention Curve Shapes

```
Healthy:     Weak:        Critical:
100%─┐       100%─┐       100%─┐
     │\           │\           │\
     │ \___       │ \          │ \
     │     |      │  \         │  \
     └─────       │   \__      │   \
                  └──────      └────→0
```

### New User Retention (First 7 Days)

The most leveraged retention period:
- **D1 retention** predicts long-term retention more than any other metric
- **Time to Aha** should be <5 min (consumer) or <1 day (B2B)
- **Activation rate** is the conversion from "signed up" to "experienced value"
- The **magic number** = the behavior that predicts retention (find it, optimize toward it)

### Resurrection Framework

| Strategy | When to Use | Mechanism |
|----------|------------|-----------|
| Product improvement email | After shipping something relevant to churned users | "Here's what changed since you left" |
| Social trigger | When a churned user's connections are active | "Your colleague just..." |
| Pain recurrence | When the original problem resurfaces | "Still dealing with [problem]?" |
| Win-back offer | When price was a churn factor | Time-limited discount |
| Seasonal/contextual | When product usage is cyclical | "It's [season], time to [action]" |

## AI-Specific Growth Considerations

### AI Acquisition Data Pyramid
1. **Foundation:** Product data (usage, features, engagement)
2. **Middle:** AI interaction data (queries, outputs, feedback)
3. **Top:** Value-creation data (outcomes, results, ROI)

### AI Retention Challenges
- **Novelty effect:** Initial excitement fades → usage drops
- **Trust erosion:** One bad output can destroy confidence
- **Habit disruption:** AI changes workflows, creating friction
- **Value plateau:** After initial wow, incremental value unclear

### AI Retention Strategies
- Variable reward (different helpful output each time)
- Progressive capability revelation
- Personalization that improves with use
- Clear value quantification ("saved you X hours this week")
