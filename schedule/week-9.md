---
layout: page
title: "Week 9: Governing GenAI in Organizations"
subtitle: "Govern | From principles to operating rules - with numbers"
permalink: /schedule/week-9/
---

<div class="note" markdown="0">
  <strong>Module:</strong> <span class="badge badge-orange">Govern</span> &nbsp;|&nbsp;
  <strong>Deliverable:</strong> GenAI governance memo (due before Week 10 begins) &nbsp;|&nbsp;
  <a href="{{ site.baseurl }}/assignments/week-9-governance/">See assignment →</a>
</div>

## Learning objectives

By the end of this week, you should be able to:

1. Explain why GenAI requires organizational governance, not just ethical principles
2. Apply the NIST AI Risk Management Framework (Govern, Map, Measure, Manage)
3. Compute a quantitative risk score using a likelihood × impact matrix
4. Draft governance rules with measurable thresholds tied to evaluation metrics from Weeks 7–8
5. Write an acceptable-use policy with quantitative triggers for review, escalation, and monitoring
6. Connect governance requirements to the specific tools you've built in this course

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Session 1 · Class 17</div>
  <div class="session-content">
    <div class="session-title">From principles to operating rules - with numbers</div>
    <p>The governance gap between "use AI responsibly" and specific operating rules. NIST AI RMF mapped to the quantitative tools you've built (rubrics, kappa, disparity metrics, cost analysis). Then a governance checklist workshop with a quantitative risk scoring matrix: likelihood × impact for each domain.</p>
    <div class="session-topics">
      <span class="topic-tag">Principles vs. operating rules</span>
      <span class="topic-tag">NIST AI RMF + course tools</span>
      <span class="topic-tag">Quantitative risk matrix</span>
      <span class="topic-tag">Governance rules with thresholds</span>
    </div>
  </div>
</div>

<div class="session-block" markdown="0">
  <div class="session-label">Session 2 · Class 18</div>
  <div class="session-content">
    <div class="session-title">Drafting policy and preparing to present</div>
    <p>Draft an acceptable-use policy where every section includes at least one measurable threshold. Before finalizing a threshold, back-test it against your own Week 6-8 results (Python: does the rule actually fire at a plausible rate on your data?). Peer-critique another group's policy for measurability and realism. Then dedicated final project work time.</p>
    <div class="session-topics">
      <span class="topic-tag">Acceptable-use policy with thresholds</span>
      <span class="topic-tag">Python: threshold back-testing</span>
      <span class="topic-tag">Policy critique for measurability</span>
      <span class="topic-tag">Final project work session</span>
    </div>
  </div>
</div>

## Prepare before class

**Before Session 1:**

- Review your Week 8 incident brief - the safeguard thresholds you wrote connect directly to this week
- Skim the [NIST AI RMF overview](https://www.nist.gov/itl/ai-risk-management-framework)

**Before Session 2:**

- Review your Session 1 risk matrix and governance rules
- Have your final project workflow defined well enough to write governance rules for it
- Bring your Week 6 and Week 8 results (classification confidence, subgroup error rates) - you'll back-test your thresholds against them in `class18-python-threshold-backtest.ipynb`

## Key concepts

| Concept | What it means |
|---|---|
| **Quantitative risk matrix** | Likelihood (1–5) × Impact (1–5) for each governance domain, producing a risk score (1–25) |
| **Governance threshold** | A measurable trigger for action: "human review when confidence < 0.7" - not "review when needed" |
| **Threshold back-testing** | Checking a proposed threshold against your own Week 6-8 results before finalizing it - what fraction of real cases would it actually flag? |
| **NIST AI RMF** | Four functions (Govern, Map, Measure, Manage) mapped to the quantitative tools students have built |
| **Acceptable-use policy** | Operating document: approved, restricted, and prohibited uses with specific triggers and escalation |

## Readings and resources

- [NIST AI Risk Management Framework](https://www.nist.gov/itl/ai-risk-management-framework) - overview and links to the full AI RMF 1.0 document; the four functions (Govern, Map, Measure, Manage) are detailed in the [AI RMF 1.0 PDF](https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.100-1.pdf) and [Playbook](https://airc.nist.gov/airmf-resources/playbook/) if you want more than the overview

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">GenAI Governance Memo</div>
  <div class="assignment-preview-meta">~2–3 pages | 30 points | Due before Week 10's first class | Submit via Canvas</div>
  <p>Quantitative risk matrix, governance rules with measurable thresholds referencing course metrics, data and review rules, escalation process, and connection to your final project.</p>
  <a href="{{ site.baseurl }}/assignments/week-9-governance/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week: **Final Project Presentations** - demonstrate all four competencies (understand, use, evaluate, govern) in a 10-minute presentation.
