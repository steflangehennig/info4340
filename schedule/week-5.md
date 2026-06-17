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

1. Use AI to propose, critique, and refine an analytic design
2. Apply four prompt roles: helpful analyst, adversarial reviewer, domain expert, methods reviewer
3. Use the helpful/adversarial pairing technique to stress-test an analysis plan
4. Implement a customer segmentation with sklearn k-means
5. Evaluate clusters using both statistical metrics and business judgment
6. Conduct a structured group design critique

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Monday</div>
  <div class="session-content">
    <div class="session-title">AI as design critic</div>
    <p>The shift from "write me code" to "help me think." You'll learn four prompt roles for analytic design (helpful analyst, adversarial reviewer, domain expert, methods reviewer), practice the helpful/adversarial pairing technique, and use AI to propose and attack an analysis plan for a real business question.</p>
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
    <div class="session-title">From design to implementation</div>
    <p>We'll implement a customer segmentation with sklearn k-means — building RFM features, clustering, and evaluating whether the segments are statistically valid, interpretable, stable, and actionable. Then a group design critique where your classmates play the adversarial roles.</p>
    <div class="session-topics">
      <span class="topic-tag">Python: k-means segmentation</span>
      <span class="topic-tag">Evaluating clusters</span>
      <span class="topic-tag">Group design critique</span>
    </div>
  </div>
</div>

## Prepare before class

**Before Monday:**

- Read Békés, [Data Analysis with AI, Week 4](https://gabors-data-analysis.com/ai-course/) — focus on AI as research companion and the helpful/adversarial prompt pattern
- Think about a business or analytic question you'd like to explore (from your work, interests, or the course dataset)

**Before Wednesday:**

- Review your Monday reconciliation — you'll present it to a group
- Skim the [sklearn KMeans documentation](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html) if you haven't used it before

## Key concepts

| Concept | What it means |
|---|---|
| **Helpful/adversarial pairing** | Two separate AI interactions: one proposes an approach, the other attacks it. The analyst reconciles. |
| **Four prompt roles** | Helpful analyst (proposes), adversarial reviewer (critiques), domain expert (adds context), methods reviewer (asks about validation) |
| **RFM features** | Recency (days since last purchase), Frequency (number of purchases), Monetary (total spend) — standard customer segmentation features |
| **Cluster evaluation** | Not just silhouette scores — also interpretability, stability, fairness, and domain validity |

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">Analytic Design Critique + Python Implementation</div>
  <div class="assignment-preview-meta">3 components · 30 points · Due before class, Week 6 Monday · Submit via Canvas</div>
  <p>Design document with AI-proposed plan and adversarial critique, Python implementation with evaluation, and an AI use log documenting all four prompt roles.</p>
  <a href="{{ site.baseurl }}/assignments/week-5-design/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week closes out the Use module with **Text as Data with LLMs** — you'll build a text classification pipeline comparing a traditional sklearn approach with an LLM-based classifier. The question: when does an LLM add value over a simpler method?
