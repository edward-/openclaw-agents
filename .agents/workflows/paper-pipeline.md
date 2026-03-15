---
description: Complete pipeline from zero to paper submission, coordinating all Agents to complete a top conference paper
---

# 📋 Complete Paper Production Pipeline (Paper Pipeline)

This workflow defines the complete process from research direction to paper submission, including **Critic review nodes** and **Main Agent audit gates**.

---

## Phase 0: Project Initialization (Planner-led)

1. **Clear goals**: Confirm target conference, DDL, research scope
2. **Activate Scout**: Start monitoring latest papers in related directions
3. **Evaluate team**: Check if core 8 Agents meet needs, identify if custom Agents need to be added
4. **Create project board**: Initialize progress tracking document

**Output**: Project plan document, timeline, team configuration

---

## Phase 1: Literature Survey (Surveyor-led, 1-2 weeks)

1. **Surveyor** conducts systematic literature survey:
   - Collect important papers from related directions in the last 2-3 years
   - Organize method classification and SOTA comparison tables
   - Identify Research Gaps
2. **Scout** supplements latest preprints and trend information
3. **Planner** integrates survey results, confirms research direction

**Output**: Literature survey report, Research Gap list, recommended reading list

---

## Phase 2: Idea Generation and Screening (Ideator-led, 1 week)

1. **Ideator** generates 3-5 candidate Ideas based on survey results
2. Perform ACE scoring for each Idea (Attractiveness, Contribution, Executability)
3. **Surveyor** verifies novelty of candidate Ideas (if similar work exists)
4. Discuss with user, select Top 1-2 Ideas
5. **Ideator** refines Contribution Statement

**Output**: Idea evaluation report, candidate Research Idea Card, draft Contribution Statement

---

## 🎯 Phase 2.5: Idea Review (Critic's Decision, 3-5 days)

> ⚡ **This is the most critical taste gate. Cannot proceed to Phase 3 without passing this gate.**

1. **Critic** receives Idea Card + ACE evaluation, performs SHARP review
2. Execute "One-sentence Insight Test" and "Bar Test"
3. Simulate most demanding reviewer's Top 3 stress tests
4. Perform "Three Soul Questions for Papers"
5. Check for classic anti-pattern hits (wrapper innovation, stacking, SOTA chasing, etc.)
6. Give Taste verdict:
   - 🏆 **Exquisite** (23-25) → Push forward with full force
   - 🟢 **Refined** (18-22) → Pass, worth investing
   - 🟡 **Raw** (13-17) → Needs polishing, return to **Ideator** for iteration
   - 🔴 **Bland** (<13) → Start over, return to **Phase 2** for regeneration

**Pass criteria**: SHARP ≥ 18 (Refined and above)

**If not passed**:
- Critic gives specific taste improvement directions
- Ideator iterates and polishes Idea accordingly
- Maximum 3 rounds of iteration, if still not passed, escalate to Main Agent for arbitration

**Output**: SHARP review report, finalized Idea Card

---

## Phase 3: Method Design (Ideator + Coder collaboration, 1-2 weeks)

1. **Ideator** transforms Idea into detailed method design
2. **Coder** evaluates technical feasibility
3. Iterate and discuss method details:
   - Determine core algorithm
   - Design architecture diagram
   - Define loss function and training strategy
4. 🎯 **Critic** evaluates method elegance (Parsimony ≥ 4)
5. **Planner** confirms method plan

**Output**: Method design document, architecture diagram, experiment plan

---

## Phase 4: Code Implementation (Coder-led, 2-4 weeks)

1. **Coder** sets up project skeleton
2. Implement core algorithm modules
3. Implement data loading and preprocessing
4. Implement training and evaluation pipeline
5. Perform Sanity Check (small-scale quick validation)
6. **Planner** performs code review

**Output**: Runnable code repository, Sanity Check results

---

## Phase 5: Experiment Execution (Coder-led, 2-3 weeks)

1. **Coder** runs main experiments (Baseline comparison)
2. Run ablation experiments
3. Run analysis experiments (Case Study, Visualization, etc.)
4. Collect all experimental results
5. **Planner** checks experiment coverage

**Output**: Experiment result report, data tables, figures

---

## Phase 6: Paper Writing (Writer-led, 2-3 weeks)

1. **Writer** writes paper outline
2. Write each section in order:
   - Abstract (modify last)
   - Introduction (Ideator provides Motivation material)
   - Related Work (Surveyor provides draft)
   - Method (Coder provides technical details)
   - Experiments (Coder provides result data)
   - Conclusion
3. Create figures (architecture diagram, result visualization)
4. Organize references
5. 🎯 **Critic** evaluates narrative quality and memory points (at least 1 clear memory point)

**Output**: Paper draft (LaTeX)

---

## Phase 7: Internal Review and Revision (Reviewer + Critic + Writer iteration, 1-2 weeks)

1. **Reviewer** performs first round comprehensive review (technical dimension)
2. 🎯 **Critic** performs final quality review (taste dimension)
3. **Writer** revises paper based on Reviewer + Critic feedback
4. **Coder** supplements experiments (if required by Reviewer/Critic)
5. **Reviewer** performs second round review
6. Repeat until Reviewer gives Accept + **Critic confirms "worth submitting"**

**Output**: Revised paper, review report, final quality review report

---

## Phase 8: Submission Preparation (Planner coordinated, 2-3 days)

1. **Reviewer** performs final Camera-Ready check
2. Confirm format compliance (page count, fonts, anonymity)
3. Prepare Supplementary Material
4. Complete Submission Checklist
5. 🔐 **Main Agent final audit**: Phase Gate Audit
6. **Planner** confirms everything is ready
7. Submit! 🎉

**Output**: Final paper package (Main Paper + Appendix + Supplement)

---

## Time Budget Reference (3 months as example)

```
Week 1-2:   Phase 1 (Literature Survey)
Week 2-3:   Phase 2 (Idea Generation)
Week 3:     Phase 2.5 (🎯 Critic Review) ← Key Node
Week 3-4:   Phase 3 (Method Design)
Week 4-7:   Phase 4 (Code Implementation)
Week 7-9:   Phase 5 (Experiment Execution)
Week 9-11:  Phase 6 (Paper Writing)
Week 11-12: Phase 7 (Review Revision + Final Quality Review)
Week 12-13: Phase 8 (Submission Preparation + MainAgent Audit)
```

> ⚠️ Actual progress should be adjusted based on DDL countdown. If Phase 2.5 review fails and needs iteration, subsequent phases will be compressed accordingly.
