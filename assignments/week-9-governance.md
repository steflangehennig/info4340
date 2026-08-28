---
layout: page
title: "Week 9: GenAI Governance Memo"
subtitle: "~2–3 pages | Due before Week 10's first class | Submit via Canvas"
permalink: /assignments/week-9-governance/
---

## Assignment

Write a governance memo for your final project's AI workflow with quantitative risk scoring and measurable thresholds.

### Components

Submit as one PDF, using the numbered items below as your section headings, in order.

1. **Workflow description** - what AI does, inputs, outputs
2. **Quantitative risk matrix** - likelihood (1-5) × impact (1-5) for each governance domain, with justifications
3. **Governance rules with thresholds** - top 3 risk domains, each with measurable triggers referencing course metrics (confidence thresholds, F1 minimums, disparity ratios, cost caps). Start by prompting an AI tool to draft rules for one risk domain, then rewrite them: AI-drafted policy language tends to default to principles ("review as needed") instead of measurable triggers. Log the before/after in your AI use log.
4. **Data rules** - what data enters AI, classification, restrictions
5. **Human review and disclosure** - who reviews, when, with at least one quantitative trigger
6. **Prohibited uses and escalation** - what's not allowed, what happens when a threshold is breached
7. **Connection to final project** - reference specific metrics from your Weeks 6–8 work

Any code you wrote to compute κ or MDD needs to be submitted as `.ipynb` and rendered as `.html`. **Also include** your AI use log covering the harm-estimate check in Component 3 - see the [AI use log guide]({{ site.baseurl }}/guides/ai-use-log/).

## Rubric

| Criterion | Excellent (5) | Adequate (3) | Needs revision (1) |
|---|---|---|---|
| Workflow clarity | Specific, operational | Present but vague | Missing |
| Risk matrix | All domains scored with likelihood × impact | Risk assigned without matrix | No assessment |
| Quantitative thresholds | 3+ rules with specific, measurable triggers, with AI's draft critiqued and rewritten in the use log | Some rules but thresholds vague, or AI draft not critiqued | Principles only |
| Data and review rules | Specific with quantitative triggers | Present but generic | No specifics |
| Escalation | Clear owner, breach > action > timeline | Some accountability | No structure |
| Course connection | References Weeks 6–8 metrics directly | Loosely connected | Disconnected |

**Total: 30 points**
