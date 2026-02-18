# Flywheel PM Marketplace

A [Claude Code](https://docs.anthropic.com/en/docs/claude-code) plugin marketplace for product managers.

## Available Plugins

| Plugin | Description | Version |
|--------|-------------|---------|
| [flywheel-pm](plugins/flywheel-pm/) | Small pushes, unstoppable momentum — 32 commands, 13 agents, 13 skills. Your PM operating system that gets sharper with every product cycle | 2.2.0 |

## What's New in v2.0

v1.0 introduced **artifact compounding** — specs, decisions, and learnings get better with every cycle. v2.0 adds a second layer: **judgment compounding** — simulation accuracy, bias awareness, and segmentation instincts get sharper the more you use them.

Two layers of compounding:

1. **Artifact compounding (v1.0):** Your specs, decisions, and learnings improve because the system remembers what worked and what didn't.
2. **Judgment compounding (v2.0):** Your simulation accuracy, bias awareness, and segmentation instincts sharpen because the system trains your product intuition.

v2.0 adds 15 new commands, 5 new skills, and 4 new agents across skill development, strategy, and growth.

## Installation

```bash
# Add the marketplace
claude plugin marketplace add https://github.com/abhitsian/flywheel-pm-marketplace

# Install the plugin
claude plugin install flywheel-pm
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

Build judgment with the v2.0 skill-development commands:

```
/pm:teardown     # Tear down a product to train simulation muscle
/pm:simulate     # Simulate user reactions before shipping
/pm:bias-check   # Check your decisions for cognitive biases
```

## How It Works

Flywheel PM encodes your PM operating system into three knowledge layers:

- **pm-profile.yaml** — How you think. Your frameworks, vocabulary, and past patterns. Auto-enriched by `/pm:compound` after each cycle.
- **team-profile.yaml** — What the team knows collectively. Built via `/pm:share`.
- **work-context.yaml** — What you're working within. Company OKRs, team capacity, customer signals, competitive landscape.

Every command loads all three layers to produce personalized, context-aware output.

```
Observe → Opportunity → Solution → Spec → Review → Measure → Compound
   ^                                                              |
   └──────────────── learnings feed back ──────────────────────────┘

Teardown → Simulate → Bias-Check → Compound
   ^                                    |
   └──────── judgment sharpens ─────────┘
```

**Cycle 1:** Generic frameworks. Predictions are guesses.
**Cycle 10:** System knows your estimation bias, flags similar past failures, pre-fills metrics by project type.
**Cycle 20:** Your second brain knows more about your PM operating system than you consciously remember.

## All Commands (31)

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
| `/pm:opportunity` | Signal -> problem -> business context -> prioritized opportunity |
| `/pm:solution` | 20 creativity techniques -> risk/impact matrix -> classification |
| `/pm:spec` | Vision narrative -> journey map -> metrics -> launch criteria |
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

### Skill Development (v2.0)
| Command | Purpose |
|---------|---------|
| `/pm:teardown` | Guided product teardown that trains simulation muscle |
| `/pm:simulate` | Simulate user reactions before shipping |
| `/pm:bias-check` | Check decisions for cognitive biases |
| `/pm:friction-log` | Structured friction logging |
| `/pm:wayrtd` | "What Are You Really Trying To Do?" — peel back feature requests to find the real need |
| `/pm:motivation-map` | Map the adoption equation (motivation, ability, triggers) |
| `/pm:ux-psychology` | Apply behavioral design principles to user flows |

### Strategy (v2.0)
| Command | Purpose |
|---------|---------|
| `/pm:segment` | Needs-based user segmentation |
| `/pm:differentiate` | Competitive differentiation using the 7 Powers framework |
| `/pm:strategy` | Full strategy document |

### Growth & Metrics (v2.0)
| Command | Purpose |
|---------|---------|
| `/pm:growth-model` | Growth loop design |
| `/pm:retention` | Retention analysis |
| `/pm:north-star` | North Star Metric design |
| `/pm:goals` | Team goal setting derived from NSM |
| `/pm:tradeoff` | Structured tradeoff analysis |

### Shortcut
| Command | Purpose |
|---------|---------|
| `/pm:lfg` | Full pipeline: opportunity -> solution -> spec -> review -> measure -> buyin |

## Agents (13)

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

### Judgment Agents (v2.0)
| Agent | Focus |
|-------|-------|
| simulation-coach | Reviews teardowns for blind spots and simulation gaps |
| bias-detector | Detects cognitive biases in documents and decisions |
| strategy-reviewer | Reviews strategy docs for coherence and completeness |
| growth-analyst | Analyzes growth models for loop integrity and retention risks |

## Skills (11)

### Core Skills
| Skill | Expertise |
|-------|-----------|
| pm-operating-system | Loads PM profile and adapts every command |
| metrics-design | Metrics hierarchies, activation funnels, engagement dimensions |
| opportunity-evaluation | 5-question framework, business context, prioritization |
| solution-creativity | 20 systematic techniques for solution generation |
| vision-narrative | 3-part aspirational narratives |
| stakeholder-buyin | 6 techniques: framing, social proof, goal seek, inception, citation, narration |

### v2.0 Skills
| Skill | Expertise |
|-------|-----------|
| simulation | Cognitive empathy engine — predict user reactions with increasing accuracy |
| behavioral-design | Motivation theory and UX psychology for product flows |
| strategy-craft | Needs-based segmentation and competitive differentiation |
| growth-systems | Growth loop design, retention analysis, and flywheel mechanics |
| analytical-thinking | North Star Metrics, goal decomposition, and structured tradeoffs |

## Documentation

- [Plugin README](plugins/flywheel-pm/README.md) — Full plugin documentation
- [Onboarding Guide](plugins/flywheel-pm/docs/onboarding-guide.md) — 5-day guided setup
- [Cheat Sheet](plugins/flywheel-pm/docs/cheatsheet.md) — Quick reference
- [Sample Profile](plugins/flywheel-pm/docs/sample-pm-profile.yaml) — Example PM profile

## License

MIT
