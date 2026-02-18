---
name: pm:context
description: Set up and update your work context — company priorities, team capacity, customer signals, competitive landscape
argument-hint: "[optional: 'update' to refresh existing context]"
---

# Work Context — Your Operating Environment

## Purpose

Your PM profile is your operating system — how you think. Your work context is your operating environment — what you're working within. Every `/pm:` command loads both to produce situationally aware outputs.

Without work context, the plugin gives you generic frameworks. With it, every command knows your OKRs, your team's capacity, your top accounts, and your competitive landscape.

## Input

<context_input> #$ARGUMENTS </context_input>

## Step 0: Check Existing Context

```bash
cat work-context.yaml 2>/dev/null
```

**If exists and input is "update":** Go to Step 2 (selective update).
**If exists and no input:** Show current context summary and ask what to update.
**If doesn't exist:** Go to Step 1 (full setup).

## Step 1: Full Context Setup

Walk through each section using **AskUserQuestion tool**, one section at a time.

### 1.1 Company Context

Ask:
- "What are your company's top 3 priorities this quarter/half?"
- "What's the primary business objective?" (Growth / Retention / Monetization / Market expansion / Platform)
- "What's the revenue target or key company-level metric?"
- "Any recent strategic shifts or announcements the team should be aware of?"

### 1.2 Team Context

Ask:
- "What's your team composition?" (# of engineers, designers, researchers)
- "What's currently in-flight?" (active projects, committed deliverables)
- "What's your team's biggest constraint right now?" (Capacity / Tech debt / Dependencies / Hiring / Skills gap)
- "Any upcoming capacity changes?" (holidays, on-call rotations, hiring pipeline)

### 1.3 Customer Context

Ask:
- "Who are your top 5 accounts? Any at risk?"
- "What are the top 3 customer complaints or requests you keep hearing?"
- "Any upcoming renewals or expansion conversations?"
- "What's your current NPS/CSAT trend?" (Improving / Flat / Declining / Unknown)

### 1.4 Competitive Context

Ask:
- "Who are your top 2-3 competitors for this product?"
- "Any recent competitor launches or moves?"
- "Where are you winning? Where are you losing?"
- "Any competitive threats you're tracking?"

### 1.5 Dependencies

Ask:
- "What other teams does your work depend on?"
- "Any cross-team initiatives or shared timelines?"
- "Any external dependencies?" (Vendors, partners, regulatory)
- "What's blocked or at risk right now?"

### 1.6 Active Bets

Ask:
- "What are the top 3 things you're betting on this quarter?"
- "For each: what's the status?" (Planning / In progress / Launched / Measuring)
- "What's the one thing that if it works, changes everything?"

## Step 2: Selective Update

If updating existing context, show current state and ask:

"Which section needs updating?"

**Options (multiSelect: true):**
1. **Company priorities** — OKRs changed, new strategic direction
2. **Team context** — Capacity changed, new projects started
3. **Customer signals** — New feedback, account changes
4. **Competitive landscape** — Competitor moved, win/loss update
5. **Dependencies** — New blockers, timeline changes
6. **Active bets** — Status changed, new bet added

Only update selected sections. Keep everything else.

## Step 3: Generate Context File

Write to `work-context.yaml`:

```yaml
# Work Context — Your operating environment
# Updated: YYYY-MM-DD
# Load alongside pm-profile.yaml for situational awareness

last_updated: "YYYY-MM-DD"

company:
  priorities:
    - "[Priority 1]"
    - "[Priority 2]"
    - "[Priority 3]"
  primary_objective: "[growth | retention | monetization | expansion | platform]"
  revenue_target: "[target]"
  strategic_notes: "[recent shifts or announcements]"

team:
  composition:
    engineers: [count]
    designers: [count]
    researchers: [count]
    other: "[roles and counts]"
  in_flight:
    - name: "[Project 1]"
      status: "[planning | building | launched | measuring]"
      target_date: "YYYY-MM-DD"
    - name: "[Project 2]"
      status: "[status]"
      target_date: "YYYY-MM-DD"
  constraint: "[capacity | tech_debt | dependencies | hiring | skills]"
  capacity_notes: "[upcoming changes]"

customers:
  top_accounts:
    - name: "[Account 1]"
      health: "[healthy | at_risk | churning]"
      renewal_date: "YYYY-MM-DD"
      notes: "[context]"
  top_complaints:
    - "[Complaint/request 1]"
    - "[Complaint/request 2]"
    - "[Complaint/request 3]"
  satisfaction_trend: "[improving | flat | declining | unknown]"

competitive:
  competitors:
    - name: "[Competitor 1]"
      threat_level: "[high | medium | low]"
      recent_moves: "[what they did]"
      our_advantage: "[where we win]"
      their_advantage: "[where they win]"
  win_loss_trend: "[improving | flat | declining | unknown]"

dependencies:
  teams:
    - name: "[Team name]"
      dependency_type: "[blocks_us | we_block_them | shared_timeline]"
      status: "[on_track | at_risk | blocked]"
      notes: "[context]"
  external:
    - "[Vendor/partner/regulatory dependency]"

active_bets:
  - name: "[Bet 1]"
    status: "[planning | in_progress | launched | measuring]"
    confidence: "[high | medium | low]"
    biggest_risk: "[what could go wrong]"
  - name: "[Bet 2]"
    status: "[status]"
    confidence: "[level]"
    biggest_risk: "[risk]"
  moonshot: "[the one thing that changes everything]"
```

## How Context Gets Used

Every `/pm:` command loads `work-context.yaml` and adapts:

| Command | Uses Context For |
|---------|-----------------|
| `/pm:opportunity` | Aligns opportunity to company priorities, checks against team capacity |
| `/pm:solution` | Factors in team constraints, competitive landscape |
| `/pm:spec` | References in-flight work to avoid conflicts, considers dependencies |
| `/pm:review` | Checks spec against company priorities, flags resource conflicts |
| `/pm:buyin` | Tailors narratives to current company priorities and stakeholder goals |
| `/pm:measure` | Sets targets relative to company revenue targets |
| `/pm:compound` | Captures context changes alongside learnings |

## Context Freshness

At the start of each session, if `work-context.yaml` is older than 2 weeks:

```
Your work context was last updated [X days ago]. Company priorities and
team capacity may have changed. Run /pm:context update to refresh.
```

## Post-Setup Options

**Options:**
1. **Run `/pm:opportunity`** — Evaluate an opportunity with full context
2. **Update a section** — Refresh specific context
3. **Share with team** — Export context for team alignment
4. **Done** — Context is set
