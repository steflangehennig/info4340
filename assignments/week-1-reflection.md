---
layout: page
title: "Week 1: Use Case Reflection"
subtitle: "~1 page + scoring table | Due before class, Week 2 Monday | Submit via Canvas"
permalink: /assignments/week-1-reflection/
---

## Assignment

Describe one realistic GenAI use case in a future analyst role. This should be a task you might actually encounter in your career, not a toy example.

Your reflection should address all five of the following:

1. **The task.** What analytic work would GenAI support? Be specific about the domain, the data or inputs, and what the work product would be.
2. **AI's role.** What specifically would the AI do? (e.g., generate code, classify text, draft a summary, suggest an approach). Don't just say "help with analysis" - describe the actual interaction.
3. **Human responsibility.** What would the analyst still be responsible for? Think about judgment calls, verification, interpretation, and decisions that shouldn't be delegated.
4. **Verification.** What would need to be checked before using the AI output in a professional setting? What could go wrong, and how would you catch it?
5. **Quantitative risk score.** Score your use case on all five risk dimensions using the same 1-5 scale from the in-class risk-ranking activity, compute the composite, and classify it.

| Dimension | Score (1-5) | Justification |
|---|---|---|
| Stakes | | |
| Data sensitivity | | |
| Affected population | | |
| Reversibility | | |
| Automation degree | | |
| **Composite score** | **__/25** | |

**Classification:** Low (5-10) · Medium (11-17) · High (18-25)

Every dimension needs a one-sentence justification - a number with no reasoning behind it is not a score. Then, in prose, address which dimension drove your composite highest, and whether a small change to your workflow design (adding a review step, restricting the data, narrowing who is affected) would move the use case into a lower band.

## Format

- Approximately 1 page of prose (400-600 words), plus the scoring table
- Prose, not bullet points. Write this as a short professional memo - the table is the one exception.
- No AI use log required for this assignment, but you may use AI to help. If you do, note what you used and what you changed.

## Purpose

This assignment is low-stakes and formative. It's designed to get you thinking in the course's framework (understand, use, evaluate, govern), to surface your interests so we can connect course material to your work, and to establish from Week 1 that risk claims in this course carry numbers and stated reasoning, not just adjectives. The scoring scheme here is the same one you'll scale up in Week 9, where governance rules get attached to measurable thresholds.

## Rubric

| Criterion | Excellent (5) | Adequate (3) | Needs revision (1) |
|---|---|---|---|
| Task specificity | Clear, realistic analytic task with defined inputs and outputs | Identifiable task but vague on inputs, outputs, or domain | Generic or implausible task |
| AI role clarity | Describes a specific AI interaction (prompt type, expected output, tool surface) | Mentions AI involvement but vague about what it would actually do | Says "AI helps" without operational detail |
| Human responsibility | Identifies specific judgment, verification, and accountability the analyst owns | Acknowledges human involvement but doesn't specify what | Treats AI output as final or doesn't address human role |
| Verification plan | Names concrete checks (source verification, data validation, expert review, test cases) | Mentions the need to verify but vague about how | No verification discussion |
| Quantitative risk score | All five dimensions scored with per-dimension justification, composite computed and correctly classified | Table completed but justifications thin, or composite miscomputed or unclassified | Missing scores, missing table, or a risk level asserted without scoring |
| Writing quality | Clear, professional, well-organized prose | Readable but uneven | Hard to follow or incomplete |

**Total: 30 points**

## Examples of strong use cases

These illustrate the *kind* of use case that works well, not templates to copy.

> "Using an LLM to classify 200 public comments on a proposed city zoning change into support, opposition, and conditional support, then validating against 20 hand-coded examples."

> "Asking Claude to generate a first draft of a data dictionary for a messy HR dataset, then reviewing every field definition against the source documentation."

> "Using GenAI to draft a customer churn analysis report from a completed notebook, then checking every statistic against the actual output and rewriting the interpretation."

Notice that each is specific about the task, the AI's role, what the human checks, and where things could go wrong.
