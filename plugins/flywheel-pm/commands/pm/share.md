---
name: pm:share
description: Share a learning, pattern, or framework with your PM team's shared knowledge base
argument-hint: "[compound doc path, or 'from-profile' to share a profile pattern]"
---

# Team Knowledge Sharing

## Purpose

Individual PM knowledge compounds within one person's profile. Team knowledge compounds across the entire PM org. This command takes a personal learning and promotes it to the team layer so every PM benefits.

## Input

<share_input> #$ARGUMENTS </share_input>

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat team-profile.yaml 2>/dev/null
```

**If `team-profile.yaml` doesn't exist:** Create it (Step 1a).

## Step 1a: Initialize Team Profile (first time only)

```yaml
# Team PM Profile — Shared knowledge across the PM team
# Updated by: /pm:share and /pm:compound (when PM chooses "share with team")
# Read by: every /pm: command alongside individual pm-profile.yaml

created: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"

# Shared vocabulary — what WE call things
vocabulary:
  # Populated as PMs share their terms and the team converges

# Shared frameworks — what the team has agreed on
frameworks:
  # Populated as team standardizes approaches

# Team playbook — patterns that work for US
playbook: []
  # Each entry:
  # - pattern: "[name]"
  #   learned_by: "[PM name]"
  #   date: "YYYY-MM-DD"
  #   context: "[when this applies]"
  #   insight: "[what to do]"
  #   evidence: "[link to compound doc]"

# Shared thresholds — calibrated across the team's projects
thresholds: {}

# Competitive intelligence — shared across team
competitive: {}

# Team decision patterns — what the team has learned about deciding
decision_patterns: []
```

## Step 2: Choose What to Share

Use **AskUserQuestion tool**:

"What do you want to share with the team?"

**Options:**
1. **A learning from `/pm:compound`** — Promote a specific project learning
2. **A metric threshold** — Share a calibrated number (e.g., "activation takes 3 weeks for enterprise")
3. **A framework that worked** — Share a framework or technique that produced good results
4. **A decision pattern** — Share what you learned about a type of decision
5. **Competitive intelligence** — Share something about competitors
6. **A warning** — Share a mistake or anti-pattern to avoid

## Step 3: Structure for Sharing

### For a Learning
```yaml
- pattern: "[Name of the pattern]"
  learned_by: "[PM name from pm-profile.yaml]"
  date: "YYYY-MM-DD"
  context: "[When does this apply? What type of project/persona/market?]"
  insight: "[What should other PMs do/know?]"
  evidence: "[Link to compound doc or data]"
  tags: ["[domain]", "[framework]", "[persona]"]
```

### For a Threshold
```yaml
thresholds:
  [threshold_name]:
    value: "[number]"
    context: "[when this applies]"
    source: "[which project/data]"
    contributed_by: "[PM name]"
    date: "YYYY-MM-DD"
    sample_size: "[how many projects this is based on]"
```

### For a Warning
```yaml
- pattern: "WARNING: [Name]"
  learned_by: "[PM name]"
  date: "YYYY-MM-DD"
  context: "[When you might encounter this]"
  insight: "[What went wrong and how to avoid it]"
  evidence: "[Link to compound doc]"
  severity: "[high | medium]"
```

## Step 4: Update Team Profile

Add the structured entry to `team-profile.yaml`.

Show:
```
Shared with team:

[Pattern name]
Context: [when this applies]
Insight: [what to do]

This will now appear when any PM on the team runs /pm: commands
in relevant contexts.
```

## Step 5: How Team Knowledge Gets Used

Every `/pm:` command checks `team-profile.yaml`:

| Command | Checks Team Profile For |
|---------|------------------------|
| `/pm:opportunity` | Similar past learnings from other PMs, shared thresholds |
| `/pm:solution` | Frameworks that worked for the team, warnings about approaches |
| `/pm:measure` | Shared thresholds for predictions |
| `/pm:review` | Team patterns to validate against |
| `/pm:decide` | Decision patterns the team has learned |
| `/pm:compound` | Offers "share with team" option at the end |

## Integration with /pm:compound

When `/pm:compound` runs, after capturing individual learnings, it asks:

"Is this learning worth sharing with the team?"

**Options:**
1. **Share it** — Promote to team-profile.yaml (runs `/pm:share`)
2. **Keep it personal** — Stays in pm-profile.yaml only
3. **Not sure** — Save a note to review later

## Team Knowledge Compounding

```
PM A learns: "Manufacturing activation takes 3 weeks, not 1"
  → Shared to team-profile.yaml

PM B is planning a healthcare feature a month later
  → /pm:measure loads team threshold
  → "Based on team data from similar enterprise segments,
     activation typically takes 3 weeks. Adjust timeline accordingly."

PM B's actual result: 2.5 weeks for healthcare
  → Shared back to team-profile.yaml
  → Threshold updated: "Enterprise activation: 2-3 weeks (2 data points)"
```

Over time, the team's shared knowledge grows more accurate and more useful than any individual PM's profile.
