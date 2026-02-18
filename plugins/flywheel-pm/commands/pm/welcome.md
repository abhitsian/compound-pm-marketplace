---
name: pm:welcome
description: Guided first-run experience for new PMs — takes you from install to your first compounded cycle
argument-hint: ""
---

# Welcome to Flywheel PM

## Introduction

Welcome. This guide will take you from zero to your first full product cycle with Flywheel PM. By the end, you'll have:

1. A personalized PM profile that knows how you think
2. Your work context loaded so every command is situationally aware
3. One real product cycle completed — with learnings captured
4. A second brain that gets smarter every time you use it

**Time to first value: 15 minutes. Time to full setup: 1 hour. Time to compound: your first product cycle.**

## How This Works

Use **AskUserQuestion tool**:

**Question:** "Where are you in your journey?"

**Options:**
1. **Brand new** — Just installed, show me everything from the start
2. **Profile done** — I've run /pm:onboard, what's next?
3. **Context done** — Profile and context are set, ready to work
4. **First cycle done** — I've been through the loop once, how do I compound?

---

## Path 1: Brand New (Start Here)

### Phase 1: Know Yourself (10 min)

The plugin adapts to **your** PM operating system. Before it can help you think, it needs to understand how you think.

"Let's start by creating your PM profile. I'll help you encode your frameworks, vocabulary, and way of working."

**Run:** `/pm:onboard`

**What happens:**
- You'll choose between importing existing PM docs (fastest) or interactive Q&A
- The system extracts your preferred frameworks, metrics approaches, and decision patterns
- A `pm-profile.yaml` file is created — this is your PM operating system in machine-readable form

**Quick check after onboard:**

Show the PM their profile summary:
```
Your PM Profile:
━━━━━━━━━━━━━━━
Domain: [extracted]
Frameworks: [extracted]
Metrics approach: [extracted]
Problem framing: [extracted]

This looks right? If not, we can adjust.
```

Use **AskUserQuestion tool**:

**Question:** "Does this capture how you work?"

**Options:**
1. **Yes, let's continue** — Move to Phase 2
2. **Adjust something** — Let me fix specific parts
3. **Start over** — Redo the profile from scratch

### Phase 2: Know Your World (10 min)

Your profile is how you think. Your context is what you're working within. Without it, every output is generic. With it, everything is grounded in your reality.

"Now let's load your operating environment — your company's priorities, your team, your customers, and your competition."

**Run:** `/pm:context`

**What happens:**
- You'll answer questions about company OKRs, team composition, top customers, and competitors
- A `work-context.yaml` file is created — your operating environment
- Every future command will reference this context

**Quick check after context:**

```
Your Work Context:
━━━━━━━━━━━━━━━━━
Company priority: [extracted]
Team: [size] ([constraint])
Top customer concern: [extracted]
Main competitor: [extracted]
Active bets: [count]

Ready to start working.
```

### Phase 3: See Value Immediately (5 min)

Before diving into a full product cycle, let's show you what the plugin can do with something you're already working on.

Use **AskUserQuestion tool**:

**Question:** "What's a real thing you're thinking about right now at work? Pick the closest match."

**Options:**
1. **An opportunity I'm evaluating** — "Should we build X?"
2. **A decision I need to make** — "Should we do A or B?"
3. **A product review coming up** — "I need to present this week"
4. **Customer feedback I'm processing** — "I have signals to make sense of"

**Based on selection:**

#### If opportunity:
"Great. Tell me about it in one sentence."

[Take their input]

"Let me show you what `/pm:opportunity` does with this — using your frameworks, your context, and your vocabulary."

Run a lightweight version of `/pm:opportunity` with their input. Show them the structured output — the 5-question framework, the business context, the HMW statement — all adapted to their profile.

"This took 2 minutes. Without the plugin, this thinking takes a whiteboard and an hour. And next time, it'll reference this opportunity as a past pattern."

#### If decision:
"Tell me the decision in one sentence."

Run a lightweight `/pm:decide` — show options, criteria, reversibility classification.

"This forces explicit thinking before committing. It'll also be logged, so when you face a similar decision later, you'll have this as reference."

#### If product review:
"Who's the audience?"

Run `/pm:product-review` pulling from their work context.

"This generated a review from your context file. As you use more commands, the reviews get richer — pulling from specs, measurements, and compounds."

#### If customer feedback:
"Paste or describe the feedback."

Run a lightweight `/pm:research` to structure and theme the signals.

"This structured your raw signals into themes with frequency and intensity. Ready to feed into `/pm:opportunity` when you want to act on them."

### Phase 4: Your First Full Cycle (30-60 min)

"Now you've seen the plugin in action. Let's run through a complete cycle on something real. This is where the compounding starts."

Use **AskUserQuestion tool**:

**Question:** "Ready to run a full product cycle? Pick what to work on."

**Options:**
1. **The opportunity from Phase 3** — Continue what we started
2. **Something else** — I have a different initiative in mind
3. **Walk me through the commands first** — Show me the full loop before I commit
4. **Later** — I'll come back when I have something specific

#### If they want the walkthrough:

```
The Full Loop:
━━━━━━━━━━━━━

1. OBSERVE     /pm:research or /pm:interview
               ↓ signals, patterns, customer voice
2. EVALUATE    /pm:opportunity
               ↓ framed problem, business context, HMW
3. DESIGN      /pm:solution
               ↓ creativity techniques, risk/impact, classification
4. DETAIL      /pm:spec
               ↓ vision narrative, journey map, metrics, launch criteria
5. VALIDATE    /pm:review
               ↓ 5 agents review in parallel (P1/P2/P3)
6. ALIGN       /pm:buyin
               ↓ stakeholder-specific narratives
7. MEASURE     /pm:measure
               ↓ predictions, thresholds, continue/pause/pivot criteria
8. LEARN       /pm:compound  ← THIS IS WHERE THE MAGIC HAPPENS
               ↓ predictions vs actuals, profile update, team sharing

Plus anytime:
  /pm:decide          → Frame a decision explicitly
  /pm:product-review  → Generate a product review for any audience
  /pm:context update  → Refresh your operating environment
  /pm:share           → Share a learning with your PM team
```

#### Running the cycle:

Guide them through each step sequentially:

1. "/pm:opportunity [their idea]" — Generate the opportunity evaluation
   - Pause: "Does this framing feel right?"

2. "/pm:solution" — Generate solution candidates
   - Pause: "Which solution direction resonates?"

3. "/pm:spec" — Detail the chosen solution
   - Pause: "Is this detailed enough for your stakeholders?"

4. "/pm:review" — Run multi-agent review
   - Pause: "Any P1 findings to address?"

5. "/pm:measure" — Create measurement framework
   - Pause: "Are these predictions realistic?"

6. "/pm:compound" — Capture what you learned from THIS PROCESS
   - Even the first cycle has learnings: "Was the framework useful? What would you change?"

### Phase 5: What Just Happened

After the first cycle:

```
First Cycle Complete
━━━━━━━━━━━━━━━━━━━

What you now have:
  ✓ pm-profile.yaml — Your PM OS (will get smarter)
  ✓ work-context.yaml — Your operating environment
  ✓ docs/opportunities/[file] — Your first evaluated opportunity
  ✓ docs/solutions/[file] — Your solution analysis
  ✓ docs/specs/[file] — Your detailed spec
  ✓ docs/measurements/[file] — Your predictions (to compare later)
  ✓ docs/compounds/[file] — Your first learning

What happens next time:
  → /pm:opportunity will reference this past opportunity
  → /pm:measure will suggest thresholds from this project
  → /pm:review will check for patterns from this cycle
  → /pm:decide will reference decisions you made here

Your second brain just got its first memory.
```

Use **AskUserQuestion tool**:

**Question:** "What would you like to do next?"

**Options:**
1. **Run another cycle** — Start a new opportunity
2. **Set up team sharing** — Initialize team-profile.yaml for your PM team
3. **Explore individual commands** — Try specific commands on their own
4. **Read the full guide** — Deep dive into all 15 commands

---

## Path 2: Profile Done, What's Next?

"You have your PM profile. Two things will make it much more useful:"

1. **Set your context** → Run `/pm:context`
2. **Run your first cycle** → Pick an opportunity and go through the loop

"The profile tells the system HOW you think. The context tells it WHAT you're working on. Together, every output is personalized AND situationally grounded."

Jump to Phase 2 above.

---

## Path 3: Context Done, Ready to Work

"You're fully set up. Your profile and context are loaded. Every command will use both."

Jump to Phase 3 (See Value Immediately) or Phase 4 (First Full Cycle) above.

---

## Path 4: First Cycle Done, How to Compound

"You've been through the loop once. Here's how to make each cycle better than the last."

### The Compound Habits

**After every product cycle:**
```
/pm:compound
```
Compare predictions to actuals. Update your profile. Share with team. This is the step that separates "PM with AI help" from "Flywheel PM."

**Weekly ritual:**
```
/pm:product-review
```
Generate a review pulling from everything you've worked on. Do this every week.

**Before every big decision:**
```
/pm:decide
```
Frame it explicitly. Log it. Your future self will thank you.

**When context changes:**
```
/pm:context update
```
OKRs shifted? Team changed? New competitor? Update your context.

**When you learn something valuable:**
```
/pm:share
```
Promote it to the team layer so every PM benefits.

### The Compounding Timeline

```
Month 1:  Profile + context set. First cycle done.
          Plugin knows your frameworks but has no history.

Month 3:  3-5 cycles completed. Plugin knows your typical
          activation thresholds, your estimation patterns,
          and your past decisions.

Month 6:  10+ cycles. Plugin pre-fills metrics frameworks,
          flags opportunities that look like past failures,
          and suggests buy-in techniques that worked before.

Month 12: Your second brain knows your PM operating system
          better than you consciously remember. Team knowledge
          compounds across all PMs.
```

### Common Questions

**"Do I have to use every command?"**
No. Start with `/pm:opportunity` and `/pm:compound`. Add others as they become natural.

**"What if I skip the compound step?"**
The plugin still works, but it doesn't get smarter. You're doing traditional PM with AI help. The compound step is where the gains accumulate.

**"How does team sharing work?"**
When you run `/pm:compound`, you're asked "share with team?" If yes, the learning goes into `team-profile.yaml`. Other PMs get it automatically in their sessions.

**"What if my frameworks change?"**
Run `/pm:onboard` again, or edit `pm-profile.yaml` directly. The system adapts.

**"Can I use this for interviews and research only?"**
Absolutely. `/pm:interview` and `/pm:research` work standalone. They feed into the rest of the loop when you're ready.
