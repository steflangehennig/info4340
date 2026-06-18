---
layout: page
title: "Week 6: Text Classification Pipeline"
subtitle: "4 components · Due before class, Week 7 Monday · Submit via Canvas"
permalink: /assignments/week-6-text/
---

## Assignment

Build a complete text-as-data pipeline: hand-code ground truth, compare classification approaches, construct a topic co-occurrence network, and analyze what each lens reveals.

### Component 1: Hand-coded validation set (15–20 texts)

Define your categories clearly, hand-code at least 15 texts with primary and secondary labels, and note any ambiguous cases.

### Component 2: Classification pipeline

sklearn baseline (TF-IDF + classifier) and LLM classifier with structured output. Include agreement metrics and analysis of disagreements.

### Component 3: Network analysis

Topic co-occurrence network from multi-label classifications: degree and betweenness centrality, community detection, visualization, and interpretation.

### Component 4: Comparison memo (1–2 pages) + AI use log

What did classification show? What did the network add? Where did they agree or diverge? What would you recommend to the product team?

## Rubric

| Criterion | Excellent (5) | Adequate (3) | Needs revision (1) |
|---|---|---|---|
| Ground truth | 15+ texts with clear categories, ambiguities documented | Present but categories vague | Fewer than 15 or no definitions |
| Classification comparison | Both approaches with agreement metrics and disagreement analysis | Both run but comparison thin | Only one approach |
| Network construction | Correct graph with centrality and communities | Graph built but analysis limited | No network |
| Network interpretation | Specific insights about co-occurrence patterns | Some interpretation but generic | No interpretation |
| Comparison memo | Clear argument for what each lens reveals | Describes both but doesn't compare | Missing |
| AI use log | Detailed: prompts, structured output, evaluation | Present but vague | Missing |

**Total: 30 points**
