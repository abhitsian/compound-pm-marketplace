# Flywheel PM — Onboarding Guide

## The 5-Day Journey

This guide takes you from install to a fully compounding PM practice in 5 days. Each day builds on the last. By Day 5, you have a second brain that knows how you think, what you're working on, and what you've learned.

---

## Day 1: Install & Identity (15 min)

### What you'll do
Set up the plugin and create your PM profile.

### Steps

**1. Install (2 min)**
```bash
claude plugin marketplace add https://github.com/abhitsian/flywheel-pm-marketplace
claude plugin install flywheel-pm
```
Restart Claude Code.

**2. Run the welcome guide (3 min)**
```
/pm:welcome
```
This walks you through the full setup interactively.

**3. Create your profile (10 min)**
```
/pm:onboard
```

Choose your path:
- **Have PM docs?** (operating system deck, past specs, frameworks doc) → Import mode. Point to the files and the system extracts your frameworks.
- **No docs?** → Interactive Q&A. Answer 8-10 questions about how you evaluate opportunities, classify solutions, structure metrics, and get buy-in.
- **Want to start light?** → Minimal mode. Basic profile that builds over time.

### What you'll have
- `pm-profile.yaml` — Your PM operating system encoded

### Checkpoint
Open `pm-profile.yaml` and read it. Does it sound like you? If not, edit it or run `/pm:onboard` again.

---

## Day 2: Context & Quick Win (20 min)

### What you'll do
Load your work context and see the plugin do something useful on a real problem.

### Steps

**1. Set your context (10 min)**
```
/pm:context
```
Answer questions about:
- Your company's top priorities
- Your team's composition and constraints
- Your customers' biggest complaints
- Your competitive landscape
- What you're actively betting on

**2. Get a quick win (10 min)**

Pick ONE thing you're actually working on right now:

| If you have... | Run... |
|---------------|--------|
| An idea you're evaluating | `/pm:opportunity [describe it in one sentence]` |
| A decision you're stuck on | `/pm:decide [the decision]` |
| Customer feedback to process | `/pm:research` then paste the feedback |
| A product review due | `/pm:product-review` |

See the output. Notice how it uses YOUR frameworks from your profile and YOUR context.

### What you'll have
- `work-context.yaml` — Your operating environment
- One real output adapted to your world

### Checkpoint
Did the output use your terminology? Did it reference your company priorities? If it feels generic, your profile or context might need more detail.

---

## Day 3: First Full Cycle (45-60 min)

### What you'll do
Run through the complete product loop on something real.

### Steps

Pick an initiative you're actively working on. Not a toy example — something that matters. Then run the loop:

**1. Frame the opportunity (10 min)**
```
/pm:opportunity [your initiative]
```
The system will frame the customer problem, map business context, classify the opportunity, and check for past patterns (none yet — this is your first cycle).

Review the output. Adjust the HMW if it doesn't feel right.

**2. Design solutions (10 min)**
```
/pm:solution
```
The system applies creativity techniques, evaluates solutions on Valuable/Usable/Feasible/Viable, and classifies each as Differentiator/MMR/Neutralizer.

Pick the direction that resonates.

**3. Write the spec (15 min)**
```
/pm:spec
```
Vision narrative, customer journey map, metrics framework, pricing/packaging, launch criteria.

This is the artifact your stakeholders and engineers will use.

**4. Review the spec (5 min)**
```
/pm:review
```
5 agents review in parallel: customer-advocate, metrics-reviewer, business-case-reviewer, scope-creep-detector, past-pattern-checker.

Address any P1 findings.

**5. Define measurement (10 min)**
```
/pm:measure
```
Make explicit predictions. 30-day, 90-day, 6-month targets. Activation thresholds. Continue/Pause/Pivot criteria.

**These predictions are what you'll compare against in `/pm:compound` later.**

### What you'll have
- `docs/opportunities/` — Your first evaluated opportunity
- `docs/solutions/` — Your solution analysis
- `docs/specs/` — Your detailed spec
- `docs/measurements/` — Your predictions

### Checkpoint
You now have a complete product cycle documented. Everything from problem framing to measurement plan, in under an hour. How long does this usually take?

---

## Day 4: Communicate & Decide (30 min)

### What you'll do
Use the plugin for the PM work that happens between cycles — stakeholder alignment, decisions, and product reviews.

### Steps

**1. Generate stakeholder narratives (15 min)**
```
/pm:buyin
```
Pick the stakeholders you need to align. The system generates narratives using different techniques for each audience type:
- **Executives** → Vision + narration
- **Engineering** → Citation + concreteness
- **Sales** → Customer voice + goal seek

**2. Frame a pending decision (10 min)**
```
/pm:decide [a decision you're facing]
```
Even if it's small. Practice the habit of explicit decision framing: options, criteria, pre-mortem, reversibility.

**3. Generate a product review (5 min)**
```
/pm:product-review
```
For your next team meeting or leadership update. Notice how it pulls from your context and active work.

### What you'll have
- `docs/narratives/` — Stakeholder-ready narratives
- `docs/decisions/` — Your first logged decision
- `docs/reviews/` — A product review ready to share

### Checkpoint
You've now used the plugin for both the creative work (cycles) and the operational work (communication, decisions, reviews). These are the two halves of PM.

---

## Day 5: Compound & Share (20 min)

### What you'll do
Close the loop. Capture what you learned from this week. Start the compounding.

### Steps

**1. Compound your first cycle (15 min)**
```
/pm:compound [your initiative from Day 3]
```
Even though you haven't launched yet, you have learnings:
- Did the framework help you think differently?
- Was the metrics approach complete?
- Did the review catch something you missed?
- What would you do differently next cycle?

The system will:
- Capture your learnings
- Add a project pattern to your profile
- Update your thresholds (even from one data point)
- Ask if you want to share with the team

**2. Share something with the team (5 min)**
```
/pm:share
```
If you have other PMs using this plugin, share one insight. Even if you're the only PM, initialize `team-profile.yaml` — you'll build it over time.

### What you'll have
- `docs/compounds/` — Your first captured learning
- Updated `pm-profile.yaml` with a project pattern
- `team-profile.yaml` initialized

### Checkpoint
Read your updated `pm-profile.yaml`. It now has one project pattern. After 5 more cycles, it'll have 5. After 20, it'll predict your activation thresholds, flag similar past failures, and pre-fill your metrics frameworks.

**Your second brain just got its first real memory.**

---

## After Day 5: Building the Habit

### Weekly Rituals

| When | What | Command |
|------|------|---------|
| **Monday** | Review context, plan the week | `/pm:context update` → `/pm:product-review` |
| **Before each customer call** | Prepare interview guide | `/pm:interview [topic]` |
| **After each customer call** | Capture notes | `/pm:interview debrief` |
| **When evaluating ideas** | Run through the loop | `/pm:opportunity` → `/pm:solution` |
| **Before big decisions** | Frame explicitly | `/pm:decide` |
| **Friday** | Generate weekly update | `/pm:product-review` |
| **After each cycle** | **Never skip this** | `/pm:compound` |

### Progressive Mastery

**Level 1: Single commands (Week 1-2)**
Use individual commands as needed. `/pm:opportunity` when you're evaluating something. `/pm:product-review` for meetings. Get comfortable with the tools.

**Level 2: Connected cycles (Week 3-4)**
Run the full loop: opportunity → solution → spec → review → measure. See how each command builds on the last. Start compounding after each cycle.

**Level 3: Research-driven (Month 2)**
Start the loop earlier with `/pm:research` and `/pm:interview`. Build a research library that feeds into opportunities. Your decisions become evidence-based.

**Level 4: Team compound (Month 3+)**
Share learnings across the PM team. Use `/pm:share` after every compound. Build a team playbook that makes every PM faster.

**Level 5: Second brain (Month 6+)**
The system knows your estimation patterns, your past decisions, your successful frameworks, and your competitive landscape. You think, it remembers. You decide, it learns.

---

## The Commands at a Glance

```
RESEARCH          CORE LOOP              COMMUNICATE
━━━━━━━           ━━━━━━━━━              ━━━━━━━━━━━
/pm:research      /pm:opportunity        /pm:buyin
/pm:interview     /pm:solution           /pm:product-review
                  /pm:spec               /pm:decide
                  /pm:review
                  /pm:measure            SYSTEM
                  /pm:compound           ━━━━━━
                                         /pm:onboard
                                         /pm:context
SHORTCUTS                                /pm:share
━━━━━━━━━                                /pm:welcome
/pm:lfg (full pipeline)
```

---

## FAQ

**"I don't have time for all 15 commands."**
You don't need all 15. Start with 3: `/pm:opportunity`, `/pm:decide`, `/pm:compound`. Add others when they solve a real problem.

**"My company uses different frameworks."**
That's exactly the point. `/pm:onboard` captures YOUR frameworks. The plugin adapts to you, not the other way around.

**"I'm the only PM at my company."**
The individual profile and compound loop work perfectly for solo PMs. Skip the team layer or use it as your personal knowledge base.

**"I already have a PM tool (Notion, Linear, etc)."**
Flywheel PM doesn't replace your project management tool. It's your thinking tool. Use it to think through problems, then move the output into your existing tools.

**"What if I disagree with the output?"**
Good. That means you have taste. Edit the output, and the compound step captures what you changed. Over time, the system learns what you adjust and adapts.

**"How is this different from just asking Claude to help with PM work?"**
Three differences: (1) It knows your frameworks because you encoded them, (2) it remembers past cycles because the compound step captures them, (3) it knows your context because you loaded it. Generic AI chat has none of these.
