---
layout: page
title: "Week 6: Text as Data with LLMs"
subtitle: "Use · Turning unstructured text into structured data — and revealing its hidden structure"
permalink: /schedule/week-6/
---

<div class="note" markdown="0">
  <strong>Module:</strong> <span class="badge badge-green">Use</span> &nbsp;·&nbsp;
  <strong>Deliverable:</strong> Text classification pipeline (due before Week 7 Monday) &nbsp;·&nbsp;
  <a href="{{ site.baseurl }}/assignments/week-6-text/">See assignment →</a>
</div>

## Learning objectives

By the end of this week, you should be able to:

1. Explain the text-as-data pipeline: human coding → keywords → classical ML → LLM
2. Hand-code a validation set and define classification categories
3. Build and compare an sklearn baseline and an LLM text classifier
4. Design structured LLM output with category, confidence, and evidence
5. Construct a topic co-occurrence network from multi-label classifications
6. Apply centrality metrics and community detection to text data
7. Compare what classification reveals vs. what network analysis reveals

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Monday</div>
  <div class="session-content">
    <div class="session-title">Turning text into data</div>
    <p>The text-as-data pipeline: hand-coding ground truth, building an sklearn baseline, and running an LLM classifier with structured output. You'll compare all three approaches on the same customer feedback corpus and see where they agree and disagree.</p>
    <div class="session-topics">
      <span class="topic-tag">Text-as-data pipeline</span>
      <span class="topic-tag">Hand-coding ground truth</span>
      <span class="topic-tag">Python: sklearn baseline</span>
      <span class="topic-tag">Python: LLM classifier</span>
    </div>
  </div>
</div>

<div class="session-block" markdown="0">
  <div class="session-label">Wednesday</div>
  <div class="session-content">
    <div class="session-title">Structure in text: networks and scale</div>
    <p>We'll scale the classification pipeline to the full corpus, then apply a second analytical lens: network analysis. You'll build a topic co-occurrence network from multi-label classifications, compute centrality metrics, detect communities, and compare what the network reveals that classification alone doesn't.</p>
    <div class="session-topics">
      <span class="topic-tag">Scaling the pipeline</span>
      <span class="topic-tag">Topic co-occurrence networks</span>
      <span class="topic-tag">Centrality and community detection</span>
      <span class="topic-tag">Classification vs. networks</span>
    </div>
  </div>
</div>

## Prepare before class

**Before Monday:**

- Read Békés, [Data Analysis with AI, Week 5](https://gabors-data-analysis.com/ai-course/) — focus on text-to-data pipelines and evaluation
- Skim Ziems et al., "Can Large Language Models Transform Computational Social Science?" — for context on LLMs as zero-shot annotators

**Before Wednesday:**

- Review your Monday classification results — you'll build on them
- If unfamiliar with networkx, skim the [basic tutorial](https://networkx.org/documentation/stable/tutorial.html)

## Key concepts

| Concept | What it means |
|---|---|
| **Ground truth** | Hand-coded labels you create before automating — the benchmark for every classifier |
| **Structured output** | LLM responses in JSON with category, confidence, and evidence — parseable and auditable |
| **Multi-label classification** | Assigning primary + secondary categories to each text — enables network analysis |
| **Topic co-occurrence network** | Nodes = categories, edges = categories that appear together in the same text, weighted by frequency |
| **Community detection** | Algorithmic grouping of network nodes — may reveal structure your categories missed |

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">Text Classification Pipeline</div>
  <div class="assignment-preview-meta">4 components · 30 points · Due before class, Week 7 Monday · Submit via Canvas</div>
  <p>Hand-coded validation set, sklearn + LLM classification comparison, topic co-occurrence network analysis, and a comparison memo on what each lens reveals.</p>
  <a href="{{ site.baseurl }}/assignments/week-6-text/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week we enter the **Evaluate** module with **Evaluating GenAI Outputs** — you'll learn systematic methods for scoring AI output quality, including inter-rater reliability, precision/recall, and rubric design.
