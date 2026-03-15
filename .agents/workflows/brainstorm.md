---
description: Fast Idea brainstorming session workflow
---

# 💡 Idea Brainstorm Workflow (Brainstorm Session)

A collaborative process for quickly generating and evaluating research Ideas.

---

## Trigger Conditions
- User wants new research Idea
- User request: `/brainstorm`
- Planner determines need for new research direction

---

## Step 1: Context Preparation (5 minutes)

**Planner** collects background information:
1. User's research direction constraints
2. Target conference and DDL
3. Available computing resources
4. Existing experimental infrastructure (reusable code/data)
5. Papers or inspirations user recently follows

**Scout** quickly provides:
1. Relevant popular papers from the past week
2. Current research trend keywords

---

## Step 2: Free Divergence (Ideator-led)

**Ideator** generates Ideas from multiple dimensions:

### Dimension 1: Problem-driven
- What are the obvious Limitations of existing methods?
- What problems have been neglected?
- What assumptions can be challenged?

### Dimension 2: Method Transfer
- What interesting methods from other fields can be borrowed?
- What effects can different technical combinations produce?

### Dimension 3: Data/Scenario-driven
- Are there new datasets or evaluation scenarios worth attention?
- What are the deficiencies of existing Benchmarks?

### Dimension 4: Theory-driven
- Are there unexplained experimental phenomena?
- Is there a gap between theory and practice?

**Goal**: Generate 5-10 rough Ideas, don't judge too early

---

## Step 3: Novelty Verification (Surveyor-assisted)

**Surveyor** quickly checks each Idea:
- Are there similar published works?
- What's the difference from the most similar work?
- Novelty rating: 🟢 Novel / 🟡 Different / 🔴 Too Similar

---

## Step 4: ACE Evaluation (Ideator + Planner)

Score Ideas that passed novelty verification:

| Idea | A (Attractiveness) | C (Contribution) | E (Executability) | Total | Recommend |
|------|-----------|-----------|-------------|------|------|
| Idea 1 | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ | 11 | 🟡 |
| Idea 2 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | 13 | 🟢 |
| ... | ... | ... | ... | ... | ... |

---

## Step 5: In-depth Discussion of Top 2 (Interactive with User)

Select top 2 Ideas by score for in-depth discussion:
1. Elaborate method idea in detail
2. Analyze possible experimental results
3. Discuss potential risks and Plan B
4. Align with user preferences
5. Finalize 1 Idea to push forward

---

## 🎯 Step 5.5: Critic Review (Critic's Decision)

**Critic** performs SHARP taste assessment on selected Idea:
1. Execute "One-sentence Insight Test" — Is core insight sharp enough?
2. Execute "Bar Test" — Can you make a colleague say "interesting" in 30 seconds?
3. Simulate the most demanding reviewer's stress test
4. Check for anti-pattern hits (wrapper innovation, stacking, etc.)
5. Give SHARP score and Taste verdict

**If passed** (SHARP ≥ 18) → Proceed to Step 6
**If not passed** → Return to Step 5 for iterative polishing with Ideator, or return to Step 2 for new divergence

---

## Step 6: Idea Card Finalization

**Ideator** outputs complete Research Idea Card (passed Critic review):
- Title
- One-sentence summary
- Motivation
- Key Idea
- Expected experiments
- Contribution Statement (3-4 items)
- Risks and Plan B
- 🎯 SHARP review score

Deliver to **Planner** to enter Paper Pipeline Phase 3.

---

## Notes
- Brainstorming phase encourages bold hypotheses, don't deny too early
- Novelty verification should be quick but not too strict (can follow up with in-depth research)
- **Critic review is a hard gate**: Ideas not passing SHARP ≥ 18 cannot enter the formal process
- Final selection needs to balance innovation and feasibility
- User's intuition and interests are important references
- Critic's harshness is to ensure the team doesn't waste time on Ideas that "can publish but aren't good enough"
