---
name: pm:research
description: Ingest and synthesize customer signals from multiple sources — support tickets, NPS, feature requests, sales notes, usage data
argument-hint: "[signal source: 'support', 'nps', 'requests', 'sales', 'usage', or paste raw data]"
---

# Customer Research — Signal Ingestion & Synthesis

## Purpose

Customer insights come from many sources — not just interviews. This command helps ingest, structure, and synthesize signals from support tickets, NPS comments, feature requests, sales call notes, and usage data into actionable patterns.

## Input

<research_input> #$ARGUMENTS </research_input>

## Step 0: Load Context

```bash
cat pm-profile.yaml 2>/dev/null
cat work-context.yaml 2>/dev/null
ls docs/research/ 2>/dev/null
```

## Step 1: Identify Signal Source

Use **AskUserQuestion tool**:

"What customer signals are you working with?"

**Options:**
1. **Support tickets** — Complaints, bugs, friction reports
2. **NPS/CSAT comments** — Satisfaction verbatims
3. **Feature requests** — What customers are asking for
4. **Sales call notes** — What prospects and customers say in sales conversations
5. **Usage data patterns** — Behavioral signals from analytics
6. **Paste raw data** — Dump text and let me structure it

## Step 2: Ingest Data

### For Support Tickets
Ask the PM to paste or describe the data. Structure each signal:

```yaml
- source: support
  date: "YYYY-MM-DD"
  customer_type: "[segment]"
  severity: "[critical | high | medium | low]"
  category: "[category]"
  verbatim: "[exact text or summary]"
  frequency: "[one-off | recurring | trending]"
```

### For NPS/CSAT Comments
```yaml
- source: nps
  date: "YYYY-MM-DD"
  score: [0-10]
  segment: "[customer segment]"
  verbatim: "[exact comment]"
  sentiment: "[positive | neutral | negative]"
  theme: "[extracted theme]"
```

### For Feature Requests
```yaml
- source: feature_request
  date: "YYYY-MM-DD"
  customer: "[customer or segment]"
  request: "[what they want]"
  underlying_need: "[why they want it — the real problem]"
  frequency: "[how many asked]"
  revenue_at_stake: "[if known]"
```

### For Sales Notes
```yaml
- source: sales
  date: "YYYY-MM-DD"
  deal_stage: "[prospect | trial | negotiation | renewal]"
  deal_size: "[if known]"
  verbatim: "[what was said]"
  objection_or_request: "[key takeaway]"
  competitor_mentioned: "[if any]"
```

### For Usage Data
```yaml
- source: usage
  date_range: "YYYY-MM-DD to YYYY-MM-DD"
  pattern_type: "[heavy_usage | struggle | workaround | abandonment]"
  description: "[what the data shows]"
  affected_users: "[count or segment]"
  potential_insight: "[what this might mean]"
```

## Step 3: Cluster into Themes

After ingesting signals, cluster them:

1. **Group by underlying need** (not surface request)
   - "Add CSV export" + "Need data in spreadsheet" + "Can't share reports" → **Theme: Data portability**

2. **Score each theme:**

| Theme | Frequency | Intensity | Revenue Signal | Trend |
|-------|-----------|-----------|---------------|-------|
| [Theme 1] | [X mentions] | [avg severity] | [$X at stake] | [growing/stable/declining] |
| [Theme 2] | [X mentions] | [avg severity] | [$X at stake] | [growing/stable/declining] |

3. **Classify signal type:**
   - **Limitation in product value** — Product doesn't do what they need
   - **Barrier to accessing value** — Product does it but they can't get to it
   - **Workaround pattern** — They've invented their own solution
   - **Abandonment pattern** — They gave up trying

## Step 4: Connect to Existing Knowledge

Search for related past research:
```bash
ls docs/research/synthesis/ docs/research/interviews/ docs/opportunities/ 2>/dev/null
```

- Does this theme connect to a past research finding?
- Does it relate to an existing opportunity?
- Does it confirm or challenge an assumption?

## Step 5: Generate Research Document

Write to `docs/research/signals/YYYY-MM-DD-<source>-<topic>.md`:

```markdown
---
date: YYYY-MM-DD
source: "[support | nps | feature_requests | sales | usage | mixed]"
signals_analyzed: [count]
themes_identified: [count]
top_theme: "[most frequent/intense theme]"
---

# Signal Analysis: [Source] — [Topic/Period]

## Summary
[2-3 sentences: what we looked at, what we found]

## Themes (ranked by frequency x intensity)

### Theme 1: [Name] — [X signals, severity Y]
**Evidence:**
- "[Verbatim 1]" — [source, customer type]
- "[Verbatim 2]" — [source, customer type]
**Signal type:** [limitation | barrier | workaround | abandonment]
**Revenue signal:** [$X at stake across Y accounts]
**Trend:** [growing | stable | declining]
**Connection to existing work:** [related opportunity or "new signal"]

### Theme 2: [Name]
[Same structure]

## Patterns Across Themes
[Meta-patterns: are multiple themes related? Do they affect the same persona?]

## What This Means
[Interpretation — what should we do with this information?]

## Confidence Level
- **High confidence:** [themes with 5+ signals from multiple sources]
- **Medium confidence:** [themes with 2-4 signals]
- **Low confidence:** [themes with 1 signal or single source]

## Recommended Next Steps
- [ ] Investigate [theme] further with `/pm:interview`
- [ ] Convert [theme] to opportunity with `/pm:opportunity`
- [ ] Share with [team] for additional context
```

## Step 6: Post-Analysis Options

**Options:**
1. **Run `/pm:interview`** — Prepare interviews to dig deeper into a theme
2. **Run `/pm:opportunity`** — Convert top theme to opportunity evaluation
3. **Add more signals** — Ingest from another source
4. **Compare to past research** — See how themes have evolved
5. **Share with team** — Export for team review
