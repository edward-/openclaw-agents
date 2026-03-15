---
description: Standard workflow for daily academic intelligence push
---

# 📰 Daily Academic Digest Workflow (Daily Digest)

Scout-led daily information push workflow.

---

## Trigger Conditions
- Daily timed trigger (recommended: 9:00 AM each day)
- User manual request: `/daily-digest`

---

## Execution Steps

### Step 1: Information Collection

Scout collects latest papers from:
1. New arXiv papers (cs.CL, cs.AI, cs.LG, cs.MA)
2. Semantic Scholar follow list updates
3. Latest developments from important research groups
4. Hot discussions on academic social media

### Step 2: Initial Filtering

Scout performs initial filtering on collected papers:
- Score by keyword matching
- Score by author/institution importance
- Score by relevance to user's research direction
- Keep Top 10-15 for detailed filtering

### Step 3: Detailed Filtering and Summary

Scout performs in-depth reading of papers that passed initial filtering:
- Read Abstract and Introduction
- Extract one-sentence summary
- Evaluate relevance score (1-5 ⭐)
- Mark connection to user's current project
- Select 3-5 papers for output

### Step 4: Generate Daily Report

Output using standard daily report template, including:
- Today's highlights (if any major progress)
- Today's selected papers (3-5 papers)
- DDL reminders (if upcoming conference DDLs)
- Inspiration notes (clues to push to Ideator)

### Step 5: Alert Check

Check if the following require urgent notification:
- 🔴 Collision alert: Papers highly similar to ongoing research
- 🟡 Technical breakthrough: Major progress in the field
- 🟡 DDL countdown: Target conference DDL reminder at 7/3/1 days

### Step 6: Distribution
- Push daily report to user
- Push alerts (if any) to Planner
- Push inspiration clues to Ideator
- Push new important paper information to Surveyor

---

## Weekly Report (Weekly Digest)

Generated additionally every Sunday:
1. Weekly paper statistics summary
2. Trend analysis (heating up/cooling down directions)
3. Competitive dynamics updates
4. Impact assessment on current research projects
5. Next week's attention items

---

## Custom Configuration

Users can customize pushes via:
```yaml
# daily_digest_config.yaml
push_time: "09:00"          # Push time
max_papers: 5               # Maximum daily papers to push
min_relevance: 3            # Minimum relevance threshold (1-5)
include_preprints: true     # Include arXiv preprints
language: "zh"              # Summary language (zh/en)
weekly_report: true         # Generate weekly report
alert_threshold: 0.8        # Collision alert similarity threshold
```
