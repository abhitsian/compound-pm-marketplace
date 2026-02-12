# Compound PM Plugin

## Philosophy

Each product cycle should make subsequent cycles easier — not harder. This plugin codifies product management frameworks into a compounding loop where every opportunity evaluated, every spec written, and every launch measured feeds back into the system.

## Personalization Architecture

The plugin adapts to each PM through a **PM Profile** (`pm-profile.yaml`) that gets created on first use and enriched after every `/pm:compound` cycle.

**How it works:**
1. `/pm:onboard` creates the initial profile (from import or interactive Q&A)
2. Every command reads the profile to adapt outputs to the PM's frameworks, vocabulary, and past patterns
3. Every `/pm:compound` updates the profile with new learnings, metric thresholds, and decision outcomes
4. Over time, the plugin knows the PM's preferred frameworks, typical activation thresholds, stakeholder landscape, and past decisions

## Directory Structure

```
commands/pm/         # Core PM workflow commands
agents/
├── review/          # Spec review agents
└── research/        # Research and analysis agents
skills/              # Domain expertise
```

## Command Naming Convention

All commands use `pm:` prefix to avoid collisions:
- `/pm:onboard` — First-time profile setup
- `/pm:opportunity` — Evaluate opportunities
- `/pm:solution` — Design and evaluate solutions
- `/pm:spec` — Write detailed specs
- `/pm:review` — Multi-agent spec review
- `/pm:buyin` — Stakeholder alignment
- `/pm:measure` — Impact tracking framework
- `/pm:compound` — Capture learnings (most important step)
- `/pm:lfg` — Full autonomous PM workflow

## Core Loop

```
Opportunity → Solution → Spec → Review → Build → Measure → Compound → Repeat
```

## PM Profile Location

The PM profile lives at `pm-profile.yaml` in the project root. It contains:
- Preferred frameworks and vocabulary
- Past metric patterns and thresholds
- Decision log with outcomes
- Stakeholder landscape
