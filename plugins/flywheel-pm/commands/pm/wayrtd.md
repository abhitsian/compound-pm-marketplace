---
name: pm:wayrtd
description: "What Are You Really Trying To Do? — peel back feature requests to find the real underlying need"
argument-hint: "[feature request, user feedback, or stakeholder ask]"
---

# WAYRTD — What Are You Really Trying To Do?

## Purpose

The single most powerful PM question (from Shreyas Doshi). When someone asks for a feature, a PM's job is to peel back the request to the real underlying need. Often, the stated request and the actual need are different — and the best solution addresses the need, not the request.

This command turns WAYRTD into a structured practice. Every feature request passes through it before entering the opportunity pipeline.

## Input

<wayrtd_input> #$ARGUMENTS </wayrtd_input>

**If empty:** Ask "What's the feature request, user feedback, or stakeholder ask you want to dig into?"

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
```

Search for related past WAYRTD analyses:
```bash
grep -rl "[relevant keywords]" docs/wayrtd/ 2>/dev/null
```

## Step 1: Capture the Surface Request

Document exactly what was asked for:
- **Who asked:** [User/customer, stakeholder, team member, data signal]
- **What they said:** [Exact words or close paraphrase]
- **Context:** [When did they ask? What were they doing? What triggered it?]
- **How many times:** [Is this one person or a pattern?]

## Step 2: The Five Whys (Adapted for Product)

Peel back the request through 5 levels:

### Level 1: What did they ask for?
> "[The literal request]"

### Level 2: What problem are they trying to solve?
"If they had [the requested feature], what would they DO with it?"
> "[The underlying task/problem]"

### Level 3: Why is that problem painful?
"What happens today without this? What's the workaround? What's the cost?"
> "[The pain and its consequences]"

### Level 4: What's the real underlying need?
"If you could magically make the pain disappear without any specific solution, what would be different?"
> "[The fundamental need — usually emotional or functional at a deep level]"

### Level 5: Is this the MOST important need?
"Among all the things this person deals with, where does this rank? What would they trade this for?"
> "[Priority and relative importance]"

## Step 3: Stakeholder Motivation Check

If the request came from an internal stakeholder:

| Question | Answer |
|----------|--------|
| What's their incentive? | [What metric or goal drives them?] |
| What are they really optimizing for? | [Their real objective, which may differ from stated] |
| Would they be satisfied with a different solution that achieves the same goal? | [Y/N] |
| Are they the user, or representing the user? | [Direct / Proxy] |
| How much domain context do they have? | [Deep / Moderate / Surface] |

**Common traps:**
- **Sales request:** Often reflects ONE customer's need, not the market's
- **Executive request:** Often shaped by what they saw at a conference or from a competitor
- **Engineering request:** Often a solution in search of a problem (technical elegance)
- **Support request:** Often the loudest pain, not the most important

## Step 4: Request vs Need Gap Analysis

| Dimension | The Request | The Real Need |
|-----------|-------------|---------------|
| **What they said** | [literal ask] | [underlying need] |
| **Who it serves** | [stated audience] | [actual audience — maybe broader or different] |
| **Success looks like** | [requested feature ships] | [real outcome achieved] |
| **How to measure** | [feature usage] | [outcome metric] |
| **Simplest solution** | [build what was asked] | [could be simpler, different, or already exists] |

### Gap Score
- **No gap:** Request = need. Build what was asked.
- **Small gap:** Request is directionally right but solution could be better.
- **Large gap:** Request and need are significantly different. Don't build as-asked.

## Step 5: Alternative Solutions

If a gap exists between request and need, generate 3 alternative ways to address the NEED (not the request):

1. **Minimal:** What's the simplest thing that addresses the real need?
2. **Different:** What approach would the requester never think of but would satisfy them more?
3. **Systemic:** Is there a way to eliminate the need entirely rather than serving it?

For each: How would the original requester react? Would they be satisfied?

## Step 6: The Validation Question

Before proceeding, ask:

"If we built [the request exactly as asked] and it didn't solve [the real underlying need], would the requester be satisfied?"

- **If yes:** The request IS the need. Build it.
- **If no:** The need is what matters. Solution should address the need, not the request.

## Step 7: Generate Document

Write to `docs/wayrtd/YYYY-MM-DD-<request-name>.md`:

```markdown
---
date: YYYY-MM-DD
requester: "[who asked]"
requester_type: "[user | customer | stakeholder | data_signal]"
surface_request: "[what they asked for]"
real_need: "[what they actually need]"
gap: "[none | small | large]"
recommendation: "[build_as_asked | modify | reframe | reject]"
---

# WAYRTD: [Surface Request]

## The Request
[Who asked, what they said, context]

## Five Whys
[Level 1 through Level 5]

## Stakeholder Motivation
[If internal request: incentives, real optimization target]

## Gap Analysis
[Request vs Need comparison]

## Alternative Solutions
[3 alternatives if gap exists]

## Recommendation
[Build as-asked / Modify the approach / Reframe the problem / Reject the request]

## What to Say Back
> [Suggested response to the requester that acknowledges their pain while redirecting to the real need]
```

## Step 8: Update PM Profile

Track WAYRTD patterns:
```yaml
- date: "YYYY-MM-DD"
  request: "[surface request]"
  real_need: "[underlying need]"
  gap: "[none | small | large]"
  requester_type: "[type]"
  outcome: "pending"
```

Over time, patterns emerge:
- "Sales requests have a large gap 70% of the time — always dig deeper"
- "User requests from power users usually have no gap — they know what they need"
- "Executive requests tend to be solutions — always WAYRTD to find the need"

## Post-WAYRTD Options

Use **AskUserQuestion tool**:

**Question:** "WAYRTD analysis complete. What's next?"

**Options:**
1. **Run `/pm:opportunity`** — Evaluate the REAL need as an opportunity
2. **Respond to requester** — Use the suggested response
3. **Run `/pm:motivation-map`** — Map the motivation behind the real need
4. **Done** — Analysis documented
