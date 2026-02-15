# Compound PM Plugin

## Philosophy

Each product cycle should make subsequent cycles easier — not harder. This plugin codifies product management frameworks into a compounding loop where every opportunity evaluated, every spec written, and every launch measured feeds back into the system.

**v2.0 addition:** Beyond workflow automation, the plugin now develops core PM skills — simulation, strategy, behavioral design, growth thinking, and analytical reasoning. Artifacts compound AND judgment compounds.

## Personalization Architecture

The plugin adapts to each PM through a **PM Profile** (`pm-profile.yaml`) that gets created on first use and enriched after every `/pm:compound` cycle.

**How it works:**
1. `/pm:onboard` creates the initial profile (from import or interactive Q&A)
2. Every command reads the profile to adapt outputs to the PM's frameworks, vocabulary, and past patterns
3. Every `/pm:compound` updates the profile with new learnings, metric thresholds, and decision outcomes
4. Skill-development commands (`/pm:teardown`, `/pm:simulate`, `/pm:bias-check`) track judgment accuracy over time
5. Over time, the plugin knows the PM's preferred frameworks, typical activation thresholds, stakeholder landscape, cognitive blind spots, and simulation accuracy

## Directory Structure

```
commands/pm/         # Core PM workflow commands (31 total)
agents/
├── review/          # Spec and strategy review agents
├── research/        # Research and analysis agents
└── coaching/        # Skill development coaching agents
skills/              # Domain expertise (11 total)
docs/                # Onboarding guide, cheatsheet, sample profile
```

## Command Categories

### Setup & Configuration
- `/pm:welcome` — First-time guided experience
- `/pm:onboard` — Create PM profile
- `/pm:context` — Load work environment

### Skill Development (NEW in v2.0)
- `/pm:teardown` — Product teardown practice (simulation muscle)
- `/pm:simulate` — Predict user reactions to changes
- `/pm:bias-check` — Cognitive bias detection
- `/pm:friction-log` — Structured friction logging
- `/pm:wayrtd` — "What Are You Really Trying To Do?"
- `/pm:motivation-map` — Adoption equation analysis
- `/pm:ux-psychology` — Behavioral design analysis

### Strategy
- `/pm:segment` — Needs-based segmentation
- `/pm:differentiate` — Competitive differentiation (7 Powers)
- `/pm:strategy` — Full strategy document

### Research & Discovery
- `/pm:research` — Signal ingestion
- `/pm:interview` — Customer interview workflow

### Core Product Loop
- `/pm:opportunity` — Opportunity evaluation
- `/pm:solution` — Solution design
- `/pm:spec` — Spec writing
- `/pm:review` — Multi-agent review
- `/pm:measure` — Measurement framework
- `/pm:compound` — Learning capture

### Growth & Metrics
- `/pm:growth-model` — Growth loop design
- `/pm:retention` — Retention analysis
- `/pm:north-star` — North Star Metric design
- `/pm:goals` — Team goal setting
- `/pm:tradeoff` — Structured tradeoff analysis

### Decision-Making & Communication
- `/pm:decide` — Decision framework
- `/pm:buyin` — Stakeholder narratives
- `/pm:product-review` — Weekly reviews
- `/pm:share` — Team knowledge sharing

### Shortcuts
- `/pm:lfg` — Full pipeline

## Two Compounding Layers

1. **Artifact compounding** (v1.0) — Specs, decisions, and learnings get better over cycles
2. **Judgment compounding** (v2.0) — Simulation accuracy, bias awareness, segmentation instincts, and motivation analysis get sharper over cycles

## PM Profile Location

The PM profile lives at `pm-profile.yaml` in the project root. It contains:
- Preferred frameworks and vocabulary
- Past metric patterns and thresholds
- Decision log with outcomes
- Stakeholder landscape
- Teardown log with blind spot patterns (v2.0)
- Simulation log with accuracy tracking (v2.0)
- Bias patterns with susceptibility scores (v2.0)
- Friction log patterns (v2.0)
- Active segments (v2.0)

## Output Directories

```
docs/
├── research/          # Interviews, signals, synthesis
├── opportunities/     # Evaluated opportunities
├── solutions/         # Solution analyses
├── specs/             # Product specifications
├── measurements/      # Predictions + actuals
├── decisions/         # Decision logs
├── compounds/         # Captured learnings
├── narratives/        # Stakeholder narratives
├── reviews/           # Product reviews
├── teardowns/         # Product teardowns (v2.0)
├── simulations/       # User simulations (v2.0)
├── friction-logs/     # Friction logs (v2.0)
├── bias-checks/       # Bias check reports (v2.0)
├── wayrtd/            # WAYRTD analyses (v2.0)
├── motivation-maps/   # Motivation maps (v2.0)
├── ux-psychology/     # UX psychology analyses (v2.0)
├── segments/          # User segmentation (v2.0)
├── strategy/          # Strategy docs + differentiation (v2.0)
├── growth/            # Growth models (v2.0)
├── retention/         # Retention analyses (v2.0)
├── metrics/           # NSM and metrics hierarchy (v2.0)
├── goals/             # Team goals (v2.0)
└── tradeoffs/         # Tradeoff analyses (v2.0)
```
