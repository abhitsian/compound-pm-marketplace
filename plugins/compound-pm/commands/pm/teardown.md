---
name: pm:teardown
description: Guided product teardown that trains simulation muscle — practice modeling how users think, feel, and act
argument-hint: "[product or feature to tear down]"
---

# Product Teardown

## Purpose

Train your simulation muscle by systematically analyzing how a product works on users psychologically. This isn't "list 5 things you like." It's a structured practice of modeling user cognition, emotion, and behavior at each step of a product experience.

Over time, your teardown log builds a library of patterns that sharpens your intuition for what works and why.

## Input

<teardown_input> #$ARGUMENTS </teardown_input>

**If empty:** Ask "What product or feature do you want to tear down? Name the product, or paste a URL/screenshot."

## Step 0: Load PM Profile

```bash
cat pm-profile.yaml 2>/dev/null
```

**If profile has `teardown_log`:** Reference past teardowns for comparison patterns.

## Step 1: Define the Simulation Target

Use **AskUserQuestion tool**:

**Question:** "Who are you simulating as you use this product?"

**Options:**
1. **New user, first visit** — No context, no trust, easily distracted
2. **Returning user with a specific job** — Has a task, moderate patience
3. **Power user evaluating depth** — Knows the category, high standards
4. **Churned user reconsidering** — Skeptical, needs re-convincing

Then define the persona:
- **Context:** What's happening in their life/work right now?
- **Motivation type:** Functional, social, emotional, or personal?
- **Urgency:** How badly do they need this solved right now?
- **Best alternative:** What are they currently doing instead?

## Step 2: Apply the Null Hypothesis

Before starting the teardown, set expectations:

**For consumer products:** "Assume the user is lazy, selfish, vain, confused, and easily distracted. The product must overcome ALL of these."

**For B2B products:** "Assume the customer doesn't really need this product, will not pay for it, and will not deploy or use it. The product must prove them wrong."

Write down the null hypothesis for this specific product and persona.

## Step 3: Walk the Flow — Narrate the Internal Monologue

For each screen/step in the product experience, analyze:

### Motivation Check
- What job is the user trying to do at this step?
- How important is this job right now?
- What are the benefits of continuing?
- What are the consequences of abandoning?

### Friction Analysis
- Do I understand what's happening on this screen?
- How many decisions am I being asked to make? (Hick's Law)
- How difficult is it to initiate the next action?
- How inconsistent is this with my expectations/habits?
- What do I stand to lose by proceeding?
- How much thought do I need to put in before acting?

### Nudge Identification
- What intrinsic nudge is at play? (personal motivation, habit, self-imposed rule)
- What extrinsic nudge is the product applying? (notification, social proof, urgency, default)
- Does the nudge align with the motivation type?

### Emotional State
- How is the user FEELING right now? (confident, confused, anxious, delighted, impatient)
- Is the product aware of this emotion?
- Does the next step address or ignore the emotion?

### Cognitive Bias Exploitation
- Which cognitive biases is this step leveraging? (social proof, scarcity, anchoring, default effect, endowment effect, loss aversion)
- Is it doing so ethically?

## Step 4: Identify Where the Product Beats the Null Hypothesis

List the specific moments where the product overcomes the null hypothesis:
- "Despite being lazy, the user continues because [specific design choice]"
- "Despite being confused, the user understands because [specific design choice]"
- "Despite not needing this, the customer considers paying because [specific value delivery]"

These are the product's **strengths** — the moments of genuine craft.

## Step 5: Identify Where the Null Hypothesis Wins

List the specific moments where the product fails to overcome the null hypothesis:
- "A lazy user would abandon here because [specific friction]"
- "A confused user would misunderstand this because [specific UI issue]"
- "A skeptical B2B buyer would say no here because [specific gap]"

These are the product's **weaknesses** — where users likely drop off.

## Step 6: Satisfaction Assessment

If the user completes the flow:
- Did it fulfill the promised job?
- Did it live up to expectations?
- Did it generate positive emotion? (accomplishment, social validation, reassurance)
- Did it make them feel smart?
- Would they tell someone about it?

Apply the formula: `Nudge × (Motivation − Friction)^Satisfaction = Adoption`

Rate each component 1-10 and calculate the overall adoption likelihood.

## Step 7: Pattern Recognition

**If past teardowns exist in profile:**
- "This onboarding pattern is similar to [past product]. That one scored [X] on friction. This one scores [Y]."
- "You consistently [miss/catch] friction in [category]. Watch for that here."

**Cross-reference with known patterns:**
- Cold start problem handling
- Progressive disclosure usage
- Social proof placement
- Decision fatigue management
- Doherty threshold compliance (>400ms = churn risk)

## Step 8: Self-Reflection (Metacognition)

Ask the user:
- "What surprised you in this teardown?"
- "Where did your initial reaction differ from the structured analysis?"
- "What bias might be affecting your evaluation?" (Do you like/dislike this brand? Are you anchored by a competitor?)

## Step 9: Generate Teardown Document

Write to `docs/teardowns/YYYY-MM-DD-<product-name>.md`:

```markdown
---
date: YYYY-MM-DD
product: "[product name]"
persona: "[persona description]"
persona_type: "[new_user | returning | power_user | churned]"
motivation_type: "[functional | social | emotional | personal]"
product_type: "[consumer | b2b]"
overall_score: "[1-10]"
motivation_score: "[1-10]"
friction_score: "[1-10]"
nudge_score: "[1-10]"
satisfaction_score: "[1-10]"
---

# Teardown: [Product Name]

## Persona
[Who you simulated, their context, motivation, urgency]

## Null Hypothesis
[The assumption the product must overcome]

## Flow Analysis
### Step 1: [Screen/Step Name]
- **User thinking:** [internal monologue]
- **Motivation:** [what's driving them forward]
- **Friction:** [what's holding them back]
- **Nudge:** [what's pushing them to act]
- **Emotion:** [how they feel]
- **Bias at play:** [which cognitive bias is relevant]

[Repeat for each step]

## Strengths (Null Hypothesis Beaten)
- [Specific moments of craft]

## Weaknesses (Null Hypothesis Wins)
- [Specific drop-off risks]

## Satisfaction Assessment
[Formula application and scores]

## Patterns Recognized
[Connections to past teardowns and known patterns]

## Self-Reflection
[What surprised you, what biases affected your analysis]

## Key Takeaway
[One sentence: what would you steal from this product for your own?]
```

## Step 10: Update PM Profile

Add to `teardown_log` in pm-profile.yaml:
```yaml
- date: "YYYY-MM-DD"
  product: "[name]"
  type: "[consumer | b2b]"
  overall_score: [1-10]
  key_learning: "[one sentence]"
  blind_spot_noticed: "[what you missed or misjudged]"
```

Over time, this log reveals your simulation patterns:
- "You consistently underrate friction in signup flows"
- "You overrate the effectiveness of social proof nudges"
- "Your satisfaction predictions are 20% higher than actual for B2B products"

## Post-Teardown Options

Use **AskUserQuestion tool**:

**Question:** "Teardown complete. What's next?"

**Options:**
1. **Apply learnings** — Use insights on your own product via `/pm:friction-log`
2. **Do another teardown** — Build the practice
3. **Compare teardowns** — See patterns across past teardowns
4. **Done** — Teardown logged
