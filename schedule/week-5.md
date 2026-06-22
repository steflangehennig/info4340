---
layout: page
title: "Week 5: AI as Analytic Companion"
subtitle: "Use · Using AI to reason about design — not just execute code"
permalink: /schedule/week-5/
---

<div class="note" markdown="0">
  <strong>Module:</strong> <span class="badge badge-green">Use</span> &nbsp;·&nbsp;
  <strong>Deliverable:</strong> Analytic design critique + implementation (due before Week 6 Monday) &nbsp;·&nbsp;
  <a href="{{ site.baseurl }}/assignments/week-5-design/">See assignment →</a>
</div>

## Learning objectives

By the end of this week, you should be able to:

1. Use AI to propose, critique, and refine an analytic design (four prompt roles)
2. Apply the helpful/adversarial pairing technique
3. Conduct outlier analysis and determine appropriate data transformations
4. Implement customer segmentation with formal model selection (elbow + silhouette + gap statistic) and holdout validation
5. *Or* implement a linear mixed model with AIC/BIC comparison, residual diagnostics, and confidence intervals
6. Report results with effect sizes and statistical evidence, not just point estimates

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Monday</div>
  <div class="session-content">
    <div class="session-title">AI as design critic</div>
    <p>The shift from "write me code" to "help me think." Four prompt roles (helpful analyst, adversarial reviewer, domain expert, methods reviewer), the helpful/adversarial pairing technique, and an activity where you propose and attack an analysis plan.</p>
    <div class="session-topics">
      <span class="topic-tag">Four prompt roles</span>
      <span class="topic-tag">Helpful/adversarial pairing</span>
      <span class="topic-tag">Propose and attack activity</span>
    </div>
  </div>
</div>

<div class="session-block" markdown="0">
  <div class="session-label">Wednesday</div>
  <div class="session-content">
    <div class="session-title">From design to rigorous implementation</div>
    <p>Implement your analysis with formal model selection: for clustering, that means three metrics (elbow, silhouette, gap statistic), outlier analysis, and holdout validation. For the LMM track, AIC/BIC comparison across 4+ specifications with residual diagnostics and confidence intervals. Then a group design critique.</p>
    <div class="session-topics">
      <span class="topic-tag">Python: segmentation or LMM</span>
      <span class="topic-tag">Formal model selection</span>
      <span class="topic-tag">Holdout validation</span>
      <span class="topic-tag">Group design critique</span>
    </div>
  </div>
</div>

## Prepare before class

**Before Monday:**

- Read Békés, [Data Analysis with AI, Week 4](https://gabors-data-analysis.com/ai-course/) — focus on the helpful/adversarial prompt pattern
- Think about a business question for the 185-customer dataset

**Before Wednesday:**

- Review your Monday reconciliation
- Skim the [sklearn KMeans docs](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html) or [statsmodels mixedlm docs](https://www.statsmodels.org/stable/mixed_linear.html) depending on your track

## Key concepts

| Concept | What it means |
|---|---|
| **Helpful/adversarial pairing** | Two separate AI interactions: one proposes, the other attacks. You reconcile. |
| **Gap statistic** | Compares clustering quality to random data — tests whether clusters are real or noise |
| **Holdout validation** | Fit on 70%, evaluate on 30% — tests whether clusters generalize |
| **AIC/BIC** | Information criteria for model comparison: lower is better, BIC penalizes complexity more |
| **ICC** | Intraclass correlation: proportion of variance that's between-group vs. within-group |

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">Analytic Design Critique + Implementation</div>
  <div class="assignment-preview-meta">3 components · 30 points · Due before class, Week 6 Monday · Submit via Canvas</div>
  <p>Design document with adversarial critique, Python implementation with formal model selection (3 metrics or AIC/BIC), holdout validation, and AI use log.</p>
  <a href="{{ site.baseurl }}/assignments/week-5-design/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week closes out the Use module with **Text as Data with LLMs** — classification, network analysis, and the question of when an LLM adds value over a simpler method.
