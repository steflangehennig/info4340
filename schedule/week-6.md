---
layout: page
title: "Week 6: Text as Data with LLMs"
subtitle: "Use | Turning unstructured text into structured data - and revealing its hidden structure"
permalink: /schedule/week-6/
---

<div class="note" markdown="0">
  <strong>Module:</strong> <span class="badge badge-green">Use</span> &nbsp;|&nbsp;
  <strong>Deliverable:</strong> Text classification pipeline (due before Week 7 begins) &nbsp;|&nbsp;
  <a href="{{ site.baseurl }}/assignments/week-6-text/">See assignment →</a>
</div>

## Learning objectives

By the end of this week, you should be able to:

1. Hand-code a validation set and compute inter-annotator reliability (Cohen's κ)
2. Build and cross-validate an sklearn text classifier
3. Run an LLM classifier with structured JSON output at scale
4. Evaluate classifiers formally: precision, recall, F1 per class, confusion matrix
5. Compute LLM classification costs and project to production scale
6. Construct a topic co-occurrence network and test community structure against a null model
7. Compare what classification reveals vs. what network analysis reveals

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Session 1 · Class 11</div>
  <div class="session-content">
    <div class="session-title">Turning text into data</div>
    <p>The text-as-data pipeline with a text corpus: hand-code 25+ texts for validation, build an sklearn baseline with cross-validation, and run an LLM classifier with structured output. You will be tracking tokens and timing for the next class's cost analysis.</p>
    <div class="session-topics">
      <span class="topic-tag">Hand-coding + calibration</span>
      <span class="topic-tag">Python: sklearn with cross-validation</span>
      <span class="topic-tag">Python: LLM structured classifier</span>
    </div>
  </div>
</div>

<div class="session-block" markdown="0">
  <div class="session-label">Session 2 · Class 12</div>
  <div class="session-content">
    <div class="session-title">Evaluation, costs, and networks</div>
    <p>Compute inter-annotator reliability with a partner, run formal evaluation (precision/recall/F1 per class), analyze LLM costs projected to production scale, then build a topic co-occurrence network with community detection tested against a random null model.</p>
    <div class="session-topics">
      <span class="topic-tag">Inter-annotator kappa</span>
      <span class="topic-tag">Precision/recall/F1 per class</span>
      <span class="topic-tag">Cost analysis and projections</span>
      <span class="topic-tag">Network modularity vs. null model</span>
    </div>
  </div>
</div>

## Prepare before class

**Before Session 1:**

- Read Békés, [Data Analysis with AI, Week 5: Text as Data](https://gabors-data-analysis.com/ai-course/unit5/index.html) - text-to-data pipelines and evaluation
- Review the [Python for analysts guide]({{ site.baseurl }}/guides/python-analysts/) sections on sklearn and networkx

**Before Session 2:**

- Review your Session 1 classification results
- Coordinate with a partner: you'll both need to independently code the same 20 texts for the kappa exercise

## Key concepts

| Concept | What it means |
|---|---|
| **Inter-annotator reliability** | Cohen's κ between two human coders on the same texts; if κ < 0.6, the coding scheme needs revision |
| **Precision/recall/F1 per class** | Not just overall accuracy, performance broken down by category to identify systematic weaknesses |
| **Cost analysis** | Per-text LLM cost from actual token counts, projected to production scale, compared to human coding |
| **Modularity** | How well a network's communities separate tested against a random null model to check significance |

## Readings and resources

- Békés, Gábor. [Data Analysis with AI, Week 5: Text as Data](https://gabors-data-analysis.com/ai-course/unit5/index.html) - the classification and validation pipeline for Session 1: hand-rating first, structured-output prompting, agreement against a labeled sample
- [networkx community detection docs](https://networkx.org/documentation/stable/reference/algorithms/community.html) - modularity and the detection algorithms behind Session 2's network analysis

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">Text Classification Pipeline</div>
  <div class="assignment-preview-meta">4 components | 30 points | Due before Week 7's first class | Submit via Canvas</div>
  <p>Hand-coded validation with inter-annotator kappa, sklearn + LLM classifiers with formal per-class evaluation, cost analysis projected to production scale, topic co-occurrence network with modularity significance testing, and comparison memo.</p>
  <a href="{{ site.baseurl }}/assignments/week-6-text/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week we enter the **Evaluate** module with **Evaluating GenAI Outputs** - rubric design, systematic scoring, and the question of when to trust LLM-as-judge.
