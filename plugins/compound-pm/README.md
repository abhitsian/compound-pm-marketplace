# Compound PM — Your Second Brain as a Product Manager

Each product cycle should make the next one easier — not harder.

Compound PM is a Claude Code plugin that encodes your PM operating system into reusable commands, agents, and skills. It learns how **you** work, remembers what **you've** tried, and gets smarter with every cycle.

## What's in the box

| Category | Count | Description |
|----------|-------|-------------|
| Commands | 15 | Full PM workflow loop + research + rituals |
| Agents | 9 | Specialized reviewers, researchers, synthesizers |
| Skills | 6 | Domain expertise for PM frameworks |

## Installation

### Claude Code

```bash
# Add the marketplace
claude plugin marketplace add https://github.com/vaibhav/compound-pm-marketplace

# Install the plugin
claude plugin install compound-pm
```

### First Run

Restart Claude Code after installation, then:

```
/pm:onboard
```

This creates your personalized PM profile by importing your existing docs or through interactive Q&A.

## The Full Loop

```
Observe → Opportunity → Solution → Spec → Review → Measure → Compound
   ↑                                                              │
   └──────────────── learnings feed back ──────────────────────────┘
```

### Research & Discovery

| Command | Purpose |
|---------|---------|
| `/pm:research` | Ingest signals from support tickets, NPS, feature requests, sales notes, usage data |
| `/pm:interview` | Prepare interview guides, capture structured notes, synthesize patterns across interviews |

### Core Product Loop

| Command | Purpose |
|---------|---------|
| `/pm:opportunity` | Raw signal → framed problem → business context → prioritized opportunity |
| `/pm:solution` | 20 creativity techniques → risk/impact matrix → solution classification |
| `/pm:spec` | Vision narrative → journey map → metrics framework → launch criteria |
| `/pm:review` | 5 specialized agents review your spec in parallel (P1/P2/P3 findings) |
| `/pm:measure` | Full measurement framework with explicit, falsifiable predictions |
| `/pm:compound` | Compare predictions vs actuals, update your PM profile, share with team |

### Decision-Making & Communication

| Command | Purpose |
|---------|---------|
| `/pm:decide` | Frame decisions explicitly — options, criteria, pre-mortem, reversibility |
| `/pm:buyin` | Stakeholder-specific narratives using 6 buy-in techniques |
| `/pm:product-review` | Weekly/biweekly product reviews for any audience (team, leadership, all-hands) |
| `/pm:context` | Set up your operating environment — OKRs, team capacity, customer signals, competitive landscape |
| `/pm:share` | Promote a personal learning to the team's shared knowledge base |

### Full Pipeline

| Command | Purpose |
|---------|---------|
| `/pm:lfg` | Full autonomous pipeline: opportunity → solution → spec → review → measure → buyin |
| `/pm:onboard` | First-time profile setup (import your PM docs or interactive Q&A) |

## Three Knowledge Layers

```
┌─────────────────────────────────────────┐
│  pm-profile.yaml     (Individual)       │
│  Your frameworks, vocabulary, patterns, │
│  thresholds, decision log               │
├─────────────────────────────────────────┤
│  team-profile.yaml   (Team)            │
│  Shared learnings, team playbook,       │
│  calibrated thresholds, warnings        │
├─────────────────────────────────────────┤
│  work-context.yaml   (Environment)      │
│  Company OKRs, team capacity, customer  │
│  signals, competitive landscape         │
└─────────────────────────────────────────┘
```

**Individual layer** — How you think. Your frameworks, your vocabulary, your past patterns. Created by `/pm:onboard`, enriched by every `/pm:compound`.

**Team layer** — What the team knows collectively. When PM A learns "enterprise activation takes 3 weeks," PM B gets that insight automatically. Managed by `/pm:share`.

**Environment layer** — What you're working within. Company priorities, team capacity, customer health, competitive moves. Managed by `/pm:context`.

Every `/pm:` command loads all three layers to produce situationally aware, personalized output.

## How Personalization Compounds

**Cycle 1:** You define metrics manually. Predictions are guesses. Frameworks are generic.

**Cycle 5:** The system suggests activation thresholds from 4 past projects. It references past decisions. Predictions are within 20%.

**Cycle 10:** The system knows your estimation bias (you tend to overpredict adoption by 15%), flags when an opportunity looks like a past failure, pre-fills metrics frameworks by project type, and suggests which buy-in technique works best for your VP Engineering.

**Cycle 20:** Your second brain knows more about your PM operating system than you consciously remember.

## Agents

### Review Agents (run in parallel during `/pm:review`)

| Agent | Focus |
|-------|-------|
| `customer-advocate` | Does this solve the real customer problem? Is the journey complete? |
| `metrics-reviewer` | Are metrics measurable? Is the activation funnel defined? Are thresholds specific? |
| `business-case-reviewer` | Is revenue quantified with methodology? Is pricing justified? |
| `scope-creep-detector` | Is this solving one problem well or three poorly? What can be cut? |
| `past-pattern-checker` | Have we seen this before? What did we learn last time? |

### Research Agents

| Agent | Focus |
|-------|-------|
| `opportunity-researcher` | Search past work for similar opportunities and outcomes |
| `pm-profile-analyzer` | Extract PM frameworks from documents during onboarding |
| `research-synthesizer` | Find patterns across multiple interviews and signal reports |
| `competitive-landscape` | Research competitive positioning and market context |

## Skills

| Skill | Expertise |
|-------|-----------|
| `pm-operating-system` | Personalization engine — loads PM profile and adapts every command |
| `metrics-design` | Complete metrics hierarchy, activation funnels, engagement dimensions |
| `opportunity-evaluation` | 5-question framework, business context, prioritization matrices |
| `solution-creativity` | 20 systematic creativity techniques for solution generation |
| `vision-narrative` | 3-part narrative: aspirational problem → opinionated solution → user resolution |
| `stakeholder-buyin` | 6 buy-in techniques: framing, social proof, goal seek, inception, citation, narration |

## Project Structure

```
your-project/
├── pm-profile.yaml              # Your PM operating system (individual, auto-enriched)
├── team-profile.yaml            # Team shared knowledge (collective, via /pm:share)
├── work-context.yaml            # Operating environment (OKRs, team, customers, competition)
├── docs/
│   ├── research/
│   │   ├── interviews/          # /pm:interview debrief output
│   │   ├── signals/             # /pm:research signal analysis
│   │   ├── synthesis/           # Cross-interview pattern synthesis
│   │   └── guides/              # Interview guides
│   ├── opportunities/           # /pm:opportunity output
│   ├── solutions/               # /pm:solution output
│   ├── specs/                   # /pm:spec output
│   ├── measurements/            # /pm:measure predictions + actuals
│   ├── decisions/               # /pm:decide output
│   ├── compounds/               # /pm:compound learnings
│   ├── narratives/              # /pm:buyin stakeholder narratives
│   └── reviews/                 # /pm:product-review output
```

## Getting Started

### Step 1: Set up your profile
```
/pm:onboard
```
Import your existing PM docs or answer questions about how you work.

### Step 2: Set your context
```
/pm:context
```
Tell the plugin about your company priorities, team, customers, and competition.

### Step 3: Start the loop
```
/pm:research          # Got support tickets? NPS data? Sales notes?
/pm:interview          # Talking to customers? Prepare and capture.
/pm:opportunity        # Found something worth pursuing?
/pm:solution           # What should we build?
/pm:spec               # Detail it for execution.
/pm:review             # Get it reviewed by 5 specialized agents.
/pm:measure            # How will we know it worked?
/pm:compound           # What did we learn? (Don't skip this.)
```

### Step 4: Never skip the compound step
This is where the gains accumulate. Without it, you've done traditional PM with AI help. With it, every cycle makes the next one faster, more accurate, and more informed.

## Philosophy

Most PM work gets harder over time because each product cycle starts from scratch. Different PMs reinvent the same frameworks. Past learnings live in people's heads and leave when they do.

Compound PM flips this:

- **Individual compound:** Your PM profile gets smarter with each cycle
- **Team compound:** Shared learnings propagate to every PM on the team
- **Environmental awareness:** Every command knows your current context
- **Research continuity:** Past customer conversations inform future opportunities
- **Decision memory:** Past decisions and their outcomes guide future choices

The result: your second brain as a PM. It remembers what you've tried, knows how you think, and gets better at helping you with every product cycle.

## License

MIT
