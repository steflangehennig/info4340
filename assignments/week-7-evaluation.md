---
layout: page
title: "Week 7: Prompt and Output Evaluation Memo"
subtitle: "8 components | Due before Week 8's first class | Submit via Canvas"
permalink: /assignments/week-7-evaluation/
---

## Assignment

Conduct a rigorous evaluation of AI-generated outputs with multi-rater agreement, prompt sensitivity testing, and formal criteria for meaningful differences.

### Components

Submit as one PDF memo, using the numbered items below as your section headings in order.

1. **Task description and prompt(s)** - what, why, full prompts, model, settings
2. **Three outputs** - different prompts, models, or settings
3. **Rubric** - 4-6 dimensions with 0–4 anchors specific to this task
4. **Score table with justifications** - each output on each dimension
5. **Multi-rater agreement** - human-human κ AND human-LLM κ, compared
6. **Prompt sensitivity** - LLM-as-judge run 3x at temp=0, variance reported
7. **Meaningful difference analysis** - MDD computed, applied to output comparisons
8. **Recommendation + AI use log** - acceptable / with revision / unacceptable, citing scores, κ, and MDD. See the [AI use log guide]({{ site.baseurl }}/guides/ai-use-log/) for the log itself - attach it as an appendix.

Any code you wrote to compute κ or MDD needs to be submitted as `.ipynb` and rendered as .html. 

## Rubric

| Criterion | Excellent (5) | Adequate (3) | Needs revision (1) |
|---|---|---|---|
| Rubric quality | Specific, calibrated anchors | Present but vague | Missing or generic |
| Scoring rigor | All scored with justifications | Scores but thin justifications | No justifications |
| Multi-rater agreement | Human-human AND human-LLM κ, compared | One κ pair only | No agreement analysis |
| Prompt sensitivity | 3 runs, variance reported, reliability assessed | Mentioned but not computed | Not tested |
| MDD analysis | Computed and applied to output comparisons | Mentioned but not applied | No MDD |
| Recommendation | Evidence-based citing scores, κ, and MDD | Present but weakly supported | Missing |

**Total: 30 points**
