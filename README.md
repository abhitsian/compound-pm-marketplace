# Compound PM Marketplace

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) plugin marketplace for product managers.

## Available Plugins

| Plugin | Description | Version |
|--------|-------------|---------|
| [compound-pm](plugins/compound-pm/) | Your second brain as a PM — 15 commands, 9 agents, 6 skills that compound with each product cycle | 1.0.0 |

## Installation

```bash
# Add the marketplace
claude plugin marketplace add https://github.com/abhitsian/compound-pm-marketplace

# Install the plugin
claude plugin install compound-pm
```

Restart Claude Code after installation.

## Quick Start

```
/pm:welcome     # Guided first-run experience
/pm:onboard     # Create your PM profile
/pm:context     # Load your work environment
```

Then run the core loop on something real:

```
/pm:opportunity  # Frame the problem
/pm:solution     # Design solutions
/pm:spec         # Write the spec
/pm:review       # 5 agents review in parallel
/pm:measure      # Define predictions
/pm:compound     # Capture learnings (never skip this)
```

## How It Works

Compound PM encodes your PM operating system into three knowledge layers:

- **pm-profile.yaml** — How you think. Your frameworks, vocabulary, and past patterns. Auto-enriched by `/pm:compound` after each cycle.
- **team-profile.yaml** — What the team knows collectively. Built via `/pm:share`.
- **work-context.yaml** — What you're working within. Company OKRs, team capacity, customer signals, competitive landscape.

Every command loads all three layers to produce personalized, context-aware output.

```
Observe → Opportunity → Solution → Spec → Review → Measure → Compound
   ↑                                                              │
   └──────────────── learnings feed back ──────────────────────────┘
```

**Cycle 1:** Generic frameworks. Predictions are guesses.
**Cycle 10:** System knows your estimation bias, flags similar past failures, pre-fills metrics by project type.
**Cycle 20:** Your second brain knows more about your PM operating system than you consciously remember.

## All Commands

### Setup
| Command | Purpose |
|---------|---------|
| `/pm:welcome` | Guided first-run experience |
| `/pm:onboard` | Create your PM profile from docs or interactive Q&A |
| `/pm:context` | Set up your operating environment |

### Research & Discovery
| Command | Purpose |
|---------|---------|
| `/pm:research` | Ingest signals from support, NPS, feature requests, sales, usage data |
| `/pm:interview` | Prepare guides, capture notes, synthesize patterns |

### Core Product Loop
| Command | Purpose |
|---------|---------|
| `/pm:opportunity` | Signal → problem → business context → prioritized opportunity |
| `/pm:solution` | 20 creativity techniques → risk/impact matrix → classification |
| `/pm:spec` | Vision narrative → journey map → metrics → launch criteria |
| `/pm:review` | 5 specialized agents review your spec in parallel |
| `/pm:measure` | Predictions framework with activation funnel and continue/pause/pivot criteria |
| `/pm:compound` | Compare predictions vs actuals, update profile, share with team |

### Decision-Making & Communication
| Command | Purpose |
|---------|---------|
| `/pm:decide` | Frame decisions — options, criteria, pre-mortem, reversibility |
| `/pm:buyin` | Stakeholder-specific narratives using 6 buy-in techniques |
| `/pm:product-review` | Weekly reviews for team, leadership, or all-hands |
| `/pm:share` | Promote a learning to the team knowledge base |

### Shortcut
| Command | Purpose |
|---------|---------|
| `/pm:lfg` | Full pipeline: opportunity → solution → spec → review → measure → buyin |

## Agents

### Review Agents (run in parallel during `/pm:review`)
| Agent | Focus |
|-------|-------|
| customer-advocate | Does this solve the real customer problem? |
| metrics-reviewer | Are metrics measurable? Are thresholds specific? |
| business-case-reviewer | Is revenue quantified with methodology? |
| scope-creep-detector | One problem well or three problems poorly? |
| past-pattern-checker | Have we seen this before? What did we learn? |

### Research Agents
| Agent | Focus |
|-------|-------|
| opportunity-researcher | Search past work for similar opportunities |
| pm-profile-analyzer | Extract frameworks from PM docs during onboarding |
| research-synthesizer | Find patterns across multiple interviews |
| competitive-landscape | Research competitive positioning and market context |

## Skills

| Skill | Expertise |
|-------|-----------|
| pm-operating-system | Loads PM profile and adapts every command |
| metrics-design | Metrics hierarchies, activation funnels, engagement dimensions |
| opportunity-evaluation | 5-question framework, business context, prioritization |
| solution-creativity | 20 systematic techniques for solution generation |
| vision-narrative | 3-part aspirational narratives |
| stakeholder-buyin | 6 techniques: framing, social proof, goal seek, inception, citation, narration |

## Documentation

- [Plugin README](plugins/compound-pm/README.md) — Full plugin documentation
- [Onboarding Guide](plugins/compound-pm/docs/onboarding-guide.md) — 5-day guided setup
- [Cheat Sheet](plugins/compound-pm/docs/cheatsheet.md) — Quick reference
- [Sample Profile](plugins/compound-pm/docs/sample-pm-profile.yaml) — Example PM profile

## License

MIT
