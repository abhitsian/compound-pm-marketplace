---
name: pm:bias-check
description: Check a product decision against cognitive biases most likely to affect your judgment right now
argument-hint: "[decision or product direction to check]"
---

# Cognitive Bias Check

## Purpose

Your brain lies to you in predictable ways. This command applies cognitive bias analysis to a specific product decision you're about to make — not a generic list of biases, but a targeted check of which biases are most likely distorting YOUR judgment on THIS decision right now.

Over time, the plugin tracks which biases you're most susceptible to and flags them proactively.

## Input

<bias_input> #$ARGUMENTS </bias_input>

**If empty:** Ask "What decision or product direction are you evaluating? Describe what you're leaning toward and why."

## Step 0: Load PM Profile

```bash
cat pm-profile.yaml 2>/dev/null
```

**If profile has `bias_patterns`:** Pre-load the user's known susceptibilities.

## Step 1: Capture the Decision State

Ask the user (use **AskUserQuestion tool**):

**Question:** "Where are you in this decision?"

**Options:**
1. **Leaning toward a direction** — I have a preference but want to check it
2. **Stuck between options** — I can't decide and want to understand why
3. **Already decided, want a sanity check** — Gut says yes, brain wants validation
4. **Evaluating someone else's proposal** — Checking for blind spots in their thinking

Then capture:
- What's the decision?
- What are you leaning toward (if applicable)?
- What evidence supports your leaning?
- What evidence contradicts it?
- Who else has weighed in, and what did they say?
- What's the time pressure?

## Step 2: Screen for Active Biases

Evaluate the decision against the most impactful product biases. For each, assess if it's ACTIVE (likely distorting this decision) or INACTIVE (not relevant here).

### Information Biases

| Bias | Signal It's Active | Check Question |
|------|-------------------|----------------|
| **Confirmation bias** | You're only citing evidence that supports your view | "What evidence would make you change your mind? Have you looked for it?" |
| **Availability heuristic** | Your reasoning relies on recent or vivid examples | "Are you overweighting something because you experienced it recently?" |
| **Survivorship bias** | You're citing success stories without considering failures | "How many companies tried this and failed? Do you know?" |
| **Anchoring** | The first number/option you heard is dominating | "If the first data point had been different, would your conclusion change?" |
| **Information bias** | You want more data before deciding, but more data won't change the answer | "What specific data would actually change this decision?" |

### Social Biases

| Bias | Signal It's Active | Check Question |
|------|-------------------|----------------|
| **Mimetic desire** | You want this because competitors/peers want it | "Would you pursue this if no competitor was doing it?" |
| **Bandwagon effect** | Everyone seems to agree, so it must be right | "Who is the smartest person who would disagree, and why?" |
| **Authority bias** | A leader/expert said it, so you're not questioning it | "If a junior PM proposed this exact idea, would you evaluate it the same way?" |
| **HiPPO effect** | The Highest Paid Person's Opinion is driving the decision | "Remove the person who proposed this. Does the idea still stand?" |

### Decision Biases

| Bias | Signal It's Active | Check Question |
|------|-------------------|----------------|
| **Sunk cost fallacy** | You've already invested time/money, so you want to continue | "If you were starting fresh today with no prior investment, would you make this same choice?" |
| **Status quo bias** | You're choosing inaction because change is uncomfortable | "If the current state didn't exist, would you build it this way?" |
| **Loss aversion** | Fear of losing outweighs potential for gaining (2x effect) | "Are you overweighting what you might lose vs what you might gain?" |
| **Planning fallacy** | You're underestimating time, cost, and complexity | "What happened last time you estimated something similar?" |
| **Optimism bias** | You believe your project is special and the usual failure rates don't apply | "What's the base rate of success for projects like this?" |
| **Endowment effect** | You overvalue your own idea/product because it's yours | "If a competitor built this exact feature, would you think it was impressive?" |

### Framing Biases

| Bias | Signal It's Active | Check Question |
|------|-------------------|----------------|
| **Framing effect** | The way the problem was presented is driving your answer | "If this problem were described differently, would your answer change?" |
| **Baader-Meinhof** | You just learned about this problem and now see it everywhere | "Did you notice this problem before it was brought to your attention?" |
| **Scope insensitivity** | You're not distinguishing between "affects 100 users" and "affects 100,000 users" | "How many users are actually affected? Is that number proportional to your reaction?" |

## Step 3: Deep Dive on Active Biases

For each bias identified as ACTIVE:

1. **Name it explicitly** — "Confirmation bias is likely active because..."
2. **Show the evidence** — "You cited [X, Y, Z] supporting your view but haven't mentioned [counter-evidence]"
3. **Apply the check question** — Ask it directly
4. **Suggest a de-biasing action:**
   - Confirmation bias → "Actively seek 3 pieces of disconfirming evidence"
   - Mimetic desire → "Remove competitor context. Would you still do this?"
   - Sunk cost → "Imagine you're a new PM starting today. What would you do?"
   - Planning fallacy → "Use reference class forecasting: what happened with similar past projects?"
   - Anchoring → "Generate the number independently before looking at the anchor"

## Step 4: The Intellectual Flexibility Test

From Shreyas Doshi's framework:

1. "Have I been exactly right about everything?" (No.)
2. "Is there anyone in history who has been more right than me on this topic?" (Yes.)
3. "Is it remotely possible that information I don't have could make me more right?" (Yes.)
4. "Given the stakes and ambiguity, is it worth seeking that information?" (Evaluate.)
5. "Is there a non-zero chance of making a better decision with more input?" (Usually yes.)

**If all answers point to "seek more input":** Recommend specific input to seek.
**If stakes are low and decision is reversible:** "Your biases exist but the cost of being wrong is low. Decide fast."

## Step 5: Red Hat Thinking

Put on the Red Hat (emotional thinking from de Bono's framework):
- "How does this decision FEEL, separate from the analysis?"
- "What's your gut saying that your spreadsheet isn't?"
- "If you had to decide in 10 seconds with no data, what would you choose?"

Note where gut and analysis agree (high confidence) and where they diverge (investigate further).

## Step 6: Generate Bias Check Report

Write to `docs/bias-checks/YYYY-MM-DD-<decision-name>.md`:

```markdown
---
date: YYYY-MM-DD
decision: "[decision statement]"
biases_active: ["list", "of", "active", "biases"]
risk_level: "[high | medium | low]"
recommendation: "[proceed | investigate | reverse_direction]"
---

# Bias Check: [Decision]

## Decision State
[What you're deciding, what you're leaning toward, why]

## Active Biases Found

### [Bias 1 Name] — HIGH RISK
- **Evidence:** [Why this bias is active]
- **Impact:** [How it's distorting the decision]
- **De-biasing action:** [What to do about it]

### [Bias 2 Name] — MEDIUM RISK
[Same structure]

## Inactive Biases (Cleared)
[List of biases checked but not active — builds confidence]

## Intellectual Flexibility Assessment
[Results of the 5-question test]

## Gut vs Analysis
[Where they agree and diverge]

## Recommendation
[Proceed with awareness / Investigate specific things / Reconsider direction]
```

## Step 7: Update PM Profile

Add to `bias_patterns` in pm-profile.yaml:
```yaml
- date: "YYYY-MM-DD"
  decision: "[name]"
  biases_found: ["list"]
  most_impactful: "[bias name]"
  action_taken: "[what you did about it]"
  outcome: "pending"
```

Over time, patterns emerge:
- "Confirmation bias has been active in 7 of your last 10 decisions"
- "You're most susceptible to mimetic desire when evaluating competitive features"
- "Your planning fallacy averages 40% underestimate on timeline"

These patterns get surfaced proactively during `/pm:opportunity` and `/pm:decide`.

## Post-Check Options

Use **AskUserQuestion tool**:

**Question:** "Bias check complete. What's next?"

**Options:**
1. **Proceed with awareness** — Decision stands, biases acknowledged
2. **Investigate gaps** — Seek the disconfirming evidence identified
3. **Run `/pm:decide`** — Full decision framework with bias check integrated
4. **Done** — Bias check logged
