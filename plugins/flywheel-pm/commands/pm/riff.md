---
name: pm:riff
description: Riff on product news, launches, or announcements from multiple strategic angles — builds product sense and strategic thinking muscle
argument-hint: "[URL, news headline, product announcement, or topic to riff on]"
---

# Product Riff

## Purpose

Explore a piece of product news, a launch, or an announcement from multiple strategic angles. This is your PM gym — quick, structured reps that build product sense, strategic intuition, and pattern recognition over time.

Unlike `/pm:teardown` (which walks a product experience step-by-step) or `/pm:simulate` (which predicts user reactions), a riff is a rapid multi-angle exploration of a product *move*. What happened, why, and what it means.

## Input

<riff_input> #$ARGUMENTS </riff_input>

**If a URL:** Fetch and read the article/announcement.
**If a headline or description:** Use as context.
**If empty:** Ask "What product news, launch, or announcement do you want to riff on?"

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
```

**If profile has `riff_log`:** Reference past riffs for pattern connections.

If the input is a URL, fetch and summarize the announcement. Extract: company, product, what changed, stated rationale.

## Step 1: Set the Scene

Provide a crisp, neutral summary of the announcement in 3-4 sentences. State the facts — no analysis yet.

Then ask the PM for their gut reaction BEFORE any structured analysis.

Use **AskUserQuestion tool**:

**Question:** "Before we dig in — what's your gut reaction to this?"

**Options:**
1. **Smart move** — I think this is strategically strong
2. **Risky bet** — Interesting but could backfire
3. **Defensive play** — They had to do this, not because they wanted to
4. **Overhyped** — The reaction is bigger than the actual impact

This forces the PM to commit to a position before analysis (metacognition training — they'll compare their gut against structured reasoning later).

## Step 2: Pick Your Angles

Use **AskUserQuestion tool** (multiSelect):

**Question:** "Which angles do you want to explore? Pick 3-4."

**Options:**
1. **The Strategic "Why"** — Why this, why now, what's the play behind the play
2. **User Impact** — Who wins, who loses, what behavior changes
3. **Competitive Ripple** — What this forces competitors and adjacent players to do
4. **Business Model Lens** — How this makes or saves money, growth loop implications

*Note: After the selected angles are explored, the riff always ends with "Second-Order Effects", "Contrarian Take", "Steal This", and "Pattern Match" — these four are mandatory.*

## Step 3: Explore Each Angle

For EACH selected angle, follow this pattern:

### A. The PM Goes First

Use **AskUserQuestion tool** with an angle-specific question that forces the PM to think before getting analysis.

**For Strategic "Why":**
**Question:** "Why do you think they did this NOW? What changed?"
Options: timing-specific hypotheses based on the announcement (e.g., competitive pressure, tech inflection, internal milestone, market window)

**For User Impact:**
**Question:** "Who benefits most from this, and who gets disrupted?"
Options: specific user segments relevant to the announcement

**For Competitive Ripple:**
**Question:** "If you were the CEO of their biggest competitor, what would you do Monday morning?"
Options: specific strategic responses (match it, ignore it, counter-position, acquire)

**For Business Model Lens:**
**Question:** "How does this change their money math?"
Options: revenue model hypotheses (new revenue, retention play, expansion, CAC reduction)

### B. Expand the Angle

After the PM answers, go deeper using the frameworks from the `product-riff` skill:

- Apply the relevant frameworks (7 Powers, motivation theory, growth loops, etc.)
- Challenge the PM's take where appropriate — "You said X, but consider Y..."
- Surface non-obvious implications they might have missed
- Connect to patterns from past riffs if the profile has a riff log

Keep each angle expansion to 4-6 bullet points. Punchy, not exhaustive.

## Step 4: Mandatory Closing Angles

These four always happen, regardless of what was selected in Step 2.

### Second-Order Effects

Walk the chain:
- **1st order:** [The announcement] → [direct effect]
- **2nd order:** Because of that → [ecosystem change]
- **3rd order:** Because of that → [what breaks, what emerges]

Highlight the non-obvious 3rd order effect. This is where product sense lives.

### Contrarian Take

Present the strongest bear case:
- "Here's why this might fail or matter less than people think..."
- "The hidden cost they're paying is..."
- "Everyone is ignoring..."

### Steal This

Use **AskUserQuestion tool**:

**Question:** "What's the one transferable insight you'd apply to your own product?"

**Options:** 3-4 specific, concrete principles extracted from the riff (not features, but underlying principles). Make these actionable and relevant to the PM's context if pm-profile.yaml is available.

After the PM picks, expand on how to apply it — the constraint check (what's different about your context) and the anti-lesson (what to explicitly NOT copy).

### Pattern Match

Connect this announcement to known strategic patterns:
- **Historical parallel:** "This rhymes with [past move by company X]. That played out as [outcome]."
- **Pattern archetype:** Identify which play this is (platform play, bundling, counter-positioning, land-and-expand, etc.)
- **What's different:** The key variable that makes this NOT a straight repeat

## Step 5: Synthesis

Pull it all together in a tight summary:

```markdown
## Riff: [Announcement/Topic]

**The move:** [1-sentence summary]
**The strategic play:** [1-sentence "why"]
**Your gut said:** [their Step 1 answer]
**The analysis says:** [does it agree or disagree with gut?]
**Key insight:** [the single most non-obvious takeaway]
**Steal this:** [the transferable principle for your own product]
**Bear case:** [the strongest reason this might not work]
**Pattern:** [the strategic archetype]
**Open question:** [the thing nobody knows yet]
```

## Step 6: Self-Reflection

Use **AskUserQuestion tool**:

**Question:** "Looking back — did your gut reaction hold up after the structured analysis?"

**Options:**
1. **Yes, and I went deeper** — My instinct was right, the analysis added nuance
2. **Partially — I missed an angle** — One of the angles changed my view
3. **No — I flipped** — The structured analysis changed my position
4. **Still uncertain** — The more I think about it, the less sure I am

**This is the muscle-building moment.** Track whether the PM's gut aligns with analysis over time. PMs who consistently flip are still calibrating. PMs who always agree might not be thinking critically enough.

## Step 7: Generate Riff Document

Write to `docs/riffs/YYYY-MM-DD-<topic-kebab>.md`:

```markdown
---
date: YYYY-MM-DD
topic: "[announcement/topic]"
company: "[company name]"
gut_reaction: "[smart_move | risky_bet | defensive_play | overhyped]"
gut_held_up: "[yes_deeper | partially | flipped | uncertain]"
angles_explored: ["strategic_why", "user_impact", "competitive_ripple", "business_model"]
pattern_archetype: "[platform_play | bundling | unbundling | counter_positioning | ...]"
steal_this: "[one-sentence transferable insight]"
---

# Riff: [Topic]

## The Announcement
[Neutral 3-4 sentence summary]

## Gut Reaction
[PM's initial take and reasoning]

## Angle: [Name]
[Analysis from Step 3]

[Repeat for each angle]

## Second-Order Effects
[1st → 2nd → 3rd order chain]

## Contrarian Take
[Bear case]

## Steal This
[Transferable insight + how to apply + what NOT to copy]

## Pattern Match
[Historical parallel + archetype + what's different]

## Synthesis
[The tight summary from Step 5]

## Self-Reflection
[Gut vs analysis comparison]
```

## Step 8: Update PM Profile

Add to `riff_log` in pm-profile.yaml:
```yaml
- date: "YYYY-MM-DD"
  topic: "[announcement]"
  company: "[company]"
  gut_reaction: "[type]"
  gut_held_up: "[yes_deeper | partially | flipped | uncertain]"
  pattern: "[archetype]"
  steal_this: "[insight]"
```

Over time, this log reveals:
- "You default to 'smart move' — try looking for bear cases first"
- "Your gut flips 40% of the time on platform plays — you might be over-indexing on first impressions there"
- "You consistently miss business model implications — spend more time on that angle"
- "You've identified 3 counter-positioning plays this month — is there a pattern in what catches your eye?"

## Step 9: Post-Riff Options

Use **AskUserQuestion tool**:

**Question:** "Riff complete. What's next?"

**Options:**
1. **Go deeper — full teardown** — Run `/pm:teardown` on this product
2. **Apply to my product** — Use the "steal this" insight via `/pm:opportunity` or `/pm:strategy`
3. **Riff on something else** — Keep the streak going
4. **Done** — Riff logged
