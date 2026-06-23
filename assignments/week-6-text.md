---
layout: page
title: "Week 6: Text Classification Pipeline"
subtitle: "4 components · Due before class, Week 7 Monday · Submit via Canvas"
permalink: /assignments/week-6-text/
---

## Assignment

Build a complete text-as-data pipeline with formal evaluation, cost analysis, and network analysis.

### Component 1: Hand-coded validation (25+ texts) + inter-annotator kappa

Define categories, hand-code 25+ texts, compute Cohen's κ with a partner on 20 shared texts. If κ < 0.6, revise and document.

### Component 2: Classification pipeline with formal evaluation

sklearn baseline with cross-validation, LLM classifier on full corpus, precision/recall/F1 per class, confusion matrix, weakest-class analysis, and cost analysis (per-text cost projected to 10K/100K, compared to human coding).

### Component 3: Network analysis

Co-occurrence network, weighted centrality, community detection, modularity significance tested against 100-permutation null model, visualization.

### Component 4: Comparison memo (2–3 pages) + AI use log

What classification revealed, what the network added, cost-effectiveness analysis, actionable recommendation.

## Rubric

| Criterion | Excellent (5) | Adequate (3) | Needs revision (1) |
|---|---|---|---|
| Ground truth + kappa | 25+ coded, κ with partner, scheme documented | Some coding, κ missing | < 25 or no kappa |
| Classifier evaluation | P/R/F1 per class, confusion matrix, weakest class | Overall metrics only | No formal evaluation |
| Cost analysis | Per-text cost, projections, human comparison | Some cost | None |
| Network quality | Weighted centrality, communities, modularity vs. null | Basic network | No network |
| Comparison memo | Specific insights, actionable recommendation | Describes but doesn't compare | Missing |
| AI use log | Detailed | Incomplete | Missing |

**Total: 30 points**
