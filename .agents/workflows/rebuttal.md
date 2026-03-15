---
description: Standardized process for Rebuttal preparation and response
---

# 🔄 Rebuttal Workflow (Rebuttal Workflow)

When review comments are received, coordinate Reviewer + Writer + Coder to complete high-quality Rebuttal.

---

## Trigger Conditions
- Received top conference review results
- User request: `/rebuttal`

---

## Step 1: Review Comment Analysis (Reviewer-led)

1. Parse each reviewer's comments line by line
2. Classify comments:

| Type | Description | Handling Strategy |
|------|------|---------|
| 🔴 **Reasonable Criticism** | Indeed a weakness of the paper | Acknowledge + Show improvement |
| 🟡 **Misunderstanding** | Reviewer misunderstood | Politely clarify + Point to original text |
| 🟢 **Constructive Suggestion** | Helpful improvement suggestion | Thank + Adopt/Explain plan |
| ⚪ **Out of Scope** | Unreasonable requirement | Elegantly define scope |

3. Identify common issues across reviewers (same issue pointed by multiple reviewers = importance ×2)
4. Prioritize all issues

---

## Step 2: Rebuttal Strategy Formulation (Planner + Reviewer)

1. Determine core arguments of Rebuttal
2. Assign tasks:
   - Need supplementary experiments → **Coder**
   - Need paper modifications → **Writer**
   - Need additional citations → **Surveyor**
3. Develop time plan (typically Rebuttal window 5-7 days)
4. Determine overall framework for Rebuttal response

---

## Step 3: Supplementary Work (Parallel Execution)

### Coder Supplementary Experiments
- Run extra experiments requested by reviewers by priority
- Generate new result tables and visualizations
- Ensure results are reliable and reproducible

### Writer Prepare Revision
- Mark paragraphs in paper needing modification
- Write revised passages (for Rebuttal citation)
- Prepare Diff comparison (before vs. after)

### Surveyor Supplementary Citations
- Search for missing citations mentioned by reviewers
- Provide BibTeX for new citations

---

## Step 4: Rebuttal Writing (Writer-led)

### Response Format
```markdown
We sincerely thank all reviewers for their constructive feedback.
We address each concern below.

---

## Response to Reviewer 1 (Score: X)

**[W1] [Summary of reviewer's original comment]**

Thank you for this insightful comment. [Response content]

[If supplementary experimental data]
| Method | Metric | Result |
|--------|--------|--------|
| ...    | ...    | ...    |

**[W2] ...**
...

---

## Response to Reviewer 2 (Score: X)
...

---

## Summary of Changes
1. [Change 1] (Section X, Paragraph Y)
2. [Change 2] (Table Z)
3. [Change 3] (Appendix A)
```

### Writing Points
- Start with thanks, sincere attitude
- Answer directly, don't dodge questions
- Let data and facts speak
- Point out content already in paper that reviewers may have missed
- Keep length within limits
- Read multiple times to ensure tone is not defensive

---

## Step 5: Internal Audit (Reviewer audits Rebuttal)

1. **Reviewer** reviews Rebuttal draft
2. Check points:
   - [ ] Every issue has a response
   - [ ] Responses are well-supported, not empty
   - [ ] Tone appropriate (neither submissive nor aggressive)
   - [ ] Supplementary data/experiments are reliable
   - [ ] Length doesn't exceed limit
   - [ ] No contradictory content
3. Modification suggestions → **Writer** revises
4. Confirm final version

---

## Step 6: Submit Rebuttal

1. **Planner** final check and confirmation
2. Format confirmation (meets conference Rebuttal requirements)
3. Submit Rebuttal
4. If paper revision is allowed, submit Revised Paper simultaneously

---

## Rebuttal Golden Rules

1. **Thanks > Justification**: Thank sincerely first, then respond elegantly
2. **Data > Promises**: Let experimental results speak, not "we will change"
3. **Specific > General**: Point to specific paragraphs/tables in paper, don't speak in generalities
4. **All Issues Need Response**: Don't ignore even minor issues
5. **Consistent Voice**: All responses maintain logical consistency
6. **Control Length**: Concise and powerful, don't pad
