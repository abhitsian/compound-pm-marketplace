# Compound PM — Your Second Brain as a Product Manager

**v2.0.0** — Now compounds judgment, not just artifacts.

Each product cycle should make the next one easier — not harder.

Compound PM is a Claude Code plugin that encodes your PM operating system into reusable commands, agents, and skills. It learns how **you** work, remembers what **you've** tried, and gets smarter with every cycle.

v1.0 compounded **artifacts** — specs, decisions, learnings. v2.0 adds a second compounding layer: **judgment**. Simulation accuracy, bias awareness, segmentation instincts, strategic reasoning. The plugin goes from "PM workflow automation" to "PM skill development platform."

## What's in the box

| Category | Count | Description |
|----------|-------|-------------|
| Commands | 31 | Full PM workflow loop + research + rituals + skill development + strategy + growth |
| Agents | 13 | Specialized reviewers, researchers, synthesizers, coaches, analysts |
| Skills | 11 | Domain expertise for PM frameworks, simulation, behavioral design, strategy, growth |

## Installation

### Claude Code

```bash
# Add the marketplace
claude plugin marketplace add https://github.com/abhitsian/compound-pm-marketplace

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
                            │
                    ┌───────┴────────┐
                    │  v2.0: Judgment │
                    │  also compounds │
                    └────────────────┘
          Teardown → Simulate → Bias-Check → Compound
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
| `/pm:review` | Specialized agents review your spec in parallel (P1/P2/P3 findings) |
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

### Skill Development (v2.0)

| Command | Purpose |
|---------|---------|
| `/pm:teardown` | Guided product teardown that trains simulation muscle |
| `/pm:simulate` | Simulate user reactions before shipping |
| `/pm:bias-check` | Check decisions for cognitive biases |
| `/pm:friction-log` | Structured friction logging practice |
| `/pm:wayrtd` | "What Are You Really Trying To Do?" — peel back feature requests to find the real need |
| `/pm:motivation-map` | Map the adoption equation: Nudge x (Motivation - Friction)^Satisfaction = Adoption |
| `/pm:ux-psychology` | Apply behavioral design principles to flows |

### Strategy (v2.0)

| Command | Purpose |
|---------|---------|
| `/pm:segment` | Needs-based segmentation (not demographics) |
| `/pm:differentiate` | Competitive differentiation using 7 Powers |
| `/pm:strategy` | Full strategy document |

### Growth & Metrics (v2.0)

| Command | Purpose |
|---------|---------|
| `/pm:growth-model` | Growth loop design and analysis |
| `/pm:retention` | Retention analysis with cohort curves |
| `/pm:north-star` | North Star Metric with ecosystem analysis and guardrails |
| `/pm:goals` | Team goal setting from NSM |
| `/pm:tradeoff` | Structured tradeoff analysis |

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

**Individual layer** — How you think. Your frameworks, your vocabulary, your past patterns. Created by `/pm:onboard`, enriched by every `/pm:compound`. In v2.0, this layer also tracks your simulation accuracy, bias tendencies, and segmentation instincts.

**Team layer** — What the team knows collectively. When PM A learns "enterprise activation takes 3 weeks," PM B gets that insight automatically. Managed by `/pm:share`.

**Environment layer** — What you're working within. Company priorities, team capacity, customer health, competitive moves. Managed by `/pm:context`.

Every `/pm:` command loads all three layers to produce situationally aware, personalized output.

## How Personalization Compounds

**Cycle 1:** You define metrics manually. Predictions are guesses. Frameworks are generic. Teardowns miss half the design decisions.

**Cycle 5:** The system suggests activation thresholds from 4 past projects. It references past decisions. Predictions are within 20%. Your simulation accuracy is tracked — you predicted 60% of user reactions correctly.

**Cycle 10:** The system knows your estimation bias (you tend to overpredict adoption by 15%), flags when an opportunity looks like a past failure, pre-fills metrics frameworks by project type, and suggests which buy-in technique works best for your VP Engineering. Your bias-check surfaces your three most common cognitive biases. Teardown accuracy hits 75%.

**Cycle 20:** Your second brain knows more about your PM operating system than you consciously remember. Your simulation muscle is strong enough to predict user reactions before building. Your segmentation instincts are calibrated. Strategy documents write themselves from pattern-matched components.

## The Adoption Equation

v2.0 introduces the adoption equation as a core analytical framework:

```
Nudge x (Motivation - Friction)^Satisfaction = Adoption
```

`/pm:motivation-map` applies this equation to any feature or flow, mapping each variable to concrete product decisions. Over time, the plugin learns your product's typical motivation drivers, friction sources, and satisfaction multipliers.

## Product Sense Components

v2.0 is built on Shreyas Doshi's product sense framework:

```
Product Sense = Cognitive Empathy + Domain Knowledge + Creativity

Cognitive Empathy
├── Metacognition      — Awareness of your own thinking patterns
├── Intellectual Flexibility — Ability to hold multiple viewpoints
└── Simulation         — Predicting user reactions before building
```

The skill development commands (`/pm:teardown`, `/pm:simulate`, `/pm:bias-check`, `/pm:friction-log`, `/pm:wayrtd`) systematically train each component. The coaching agents (`simulation-coach`, `bias-detector`) provide feedback loops that accelerate improvement.

## Agents

### Review Agents (run in parallel during `/pm:review`)

| Agent | Focus |
|-------|-------|
| `customer-advocate` | Does this solve the real customer problem? Is the journey complete? |
| `metrics-reviewer` | Are metrics measurable? Is the activation funnel defined? Are thresholds specific? |
| `business-case-reviewer` | Is revenue quantified with methodology? Is pricing justified? |
| `scope-creep-detector` | Is this solving one problem well or three poorly? What can be cut? |
| `past-pattern-checker` | Have we seen this before? What did we learn last time? |
| `strategy-reviewer` | Reviews strategy docs for completeness and intellectual honesty (v2.0) |

### Research Agents

| Agent | Focus |
|-------|-------|
| `opportunity-researcher` | Search past work for similar opportunities and outcomes |
| `pm-profile-analyzer` | Extract PM frameworks from documents during onboarding |
| `research-synthesizer` | Find patterns across multiple interviews and signal reports |
| `competitive-landscape` | Research competitive positioning and market context |
| `growth-analyst` | Analyzes growth loops and retention assumptions (v2.0) |

### Coaching Agents (v2.0)

| Agent | Focus |
|-------|-------|
| `simulation-coach` | Reviews teardowns for blind spots and simulation accuracy |
| `bias-detector` | Proactively detects cognitive biases in product documents |

## Skills

| Skill | Expertise |
|-------|-----------|
| `pm-operating-system` | Personalization engine — loads PM profile and adapts every command |
| `metrics-design` | Complete metrics hierarchy, activation funnels, engagement dimensions |
| `opportunity-evaluation` | 5-question framework, business context, prioritization matrices |
| `solution-creativity` | 20 systematic creativity techniques for solution generation |
| `vision-narrative` | 3-part narrative: aspirational problem → opinionated solution → user resolution |
| `stakeholder-buyin` | 6 buy-in techniques: framing, social proof, goal seek, inception, citation, narration |
| `simulation` | Cognitive empathy engine — metacognition, intellectual flexibility, simulation (v2.0) |
| `behavioral-design` | Motivation theory, UX psychology, decision science (v2.0) |
| `strategy-craft` | Segmentation, differentiation, 7 Powers (v2.0) |
| `growth-systems` | Growth loops, retention, viral mechanics (v2.0) |
| `analytical-thinking` | NSM, ecosystem analysis, goals, tradeoffs (v2.0) |

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
│   ├── reviews/                 # /pm:product-review output
│   ├── teardowns/               # /pm:teardown output (v2.0)
│   ├── simulations/             # /pm:simulate output (v2.0)
│   ├── friction-logs/           # /pm:friction-log output (v2.0)
│   ├── bias-checks/             # /pm:bias-check output (v2.0)
│   ├── wayrtd/                  # /pm:wayrtd output (v2.0)
│   ├── motivation-maps/         # /pm:motivation-map output (v2.0)
│   ├── ux-psychology/           # /pm:ux-psychology output (v2.0)
│   ├── segments/                # /pm:segment output (v2.0)
│   ├── strategy/                # /pm:strategy output (v2.0)
│   ├── growth/                  # /pm:growth-model output (v2.0)
│   ├── retention/               # /pm:retention output (v2.0)
│   ├── metrics/                 # /pm:north-star output (v2.0)
│   ├── goals/                   # /pm:goals output (v2.0)
│   └── tradeoffs/               # /pm:tradeoff output (v2.0)
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
/pm:review             # Get it reviewed by specialized agents.
/pm:measure            # How will we know it worked?
/pm:compound           # What did we learn? (Don't skip this.)
```

### Step 4: Train your judgment (v2.0)
```
/pm:teardown           # Pick a product. Tear it down. Train simulation muscle.
/pm:simulate           # Before shipping, simulate user reactions.
/pm:bias-check         # Before deciding, check for cognitive biases.
/pm:friction-log       # Walk through a flow. Log every friction point.
/pm:wayrtd             # Customer asks for a feature? Find what they really need.
```

### Step 5: Think strategically (v2.0)
```
/pm:segment            # Who are your users, really? (Needs, not demographics.)
/pm:differentiate      # What makes you defensible? (7 Powers framework.)
/pm:strategy           # Full strategy document from segmentation to moats.
/pm:north-star         # Define the metric that matters most.
/pm:goals              # Cascade team goals from your North Star Metric.
/pm:growth-model       # Design and analyze growth loops.
/pm:retention          # Cohort analysis — who stays and why.
```

### Step 6: Never skip the compound step
This is where the gains accumulate. Without it, you've done traditional PM with AI help. With it, every cycle makes the next one faster, more accurate, and more informed. In v2.0, compounding applies to both your artifacts and your judgment — simulation accuracy, bias awareness, and strategic instincts all improve with every cycle.

## Philosophy

Most PM work gets harder over time because each product cycle starts from scratch. Different PMs reinvent the same frameworks. Past learnings live in people's heads and leave when they do.

Compound PM flips this:

- **Individual compound:** Your PM profile gets smarter with each cycle
- **Team compound:** Shared learnings propagate to every PM on the team
- **Environmental awareness:** Every command knows your current context
- **Research continuity:** Past customer conversations inform future opportunities
- **Decision memory:** Past decisions and their outcomes guide future choices
- **Judgment compound (v2.0):** Simulation accuracy, bias awareness, and segmentation instincts improve with deliberate practice
- **Strategic compound (v2.0):** Strategy documents build on past segmentation work, competitive analysis, and growth experiments

The result: your second brain as a PM. It remembers what you've tried, knows how you think, and gets better at helping you with every product cycle. In v2.0, it also trains how you see — sharpening the cognitive empathy, analytical rigor, and strategic intuition that separate good PMs from great ones.

## License

MIT
