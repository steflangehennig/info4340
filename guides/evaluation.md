---
layout: page
title: "Guide: Evaluation Frameworks"
subtitle: "Rubrics, scoring scripts, and agreement metrics for evaluating AI outputs"
permalink: /guides/evaluation/
---

## What this guide covers

This guide collects the evaluation tools and frameworks introduced across Weeks 7-8 into a single reference. Use it when designing evaluations for your final project or any professional AI workflow.

## The five evaluation targets

Before evaluating, know what you're evaluating. These are different tasks with different methods.

| Target | Question | Method |
|---|---|---|
| **Model** | Is this model better than that one for my task? | Run both on the same inputs, compare with rubric or metrics |
| **Prompt** | Does this prompt version produce better output? | A/B test prompt variations on held-out inputs |
| **Output** | Is this specific output good enough to use? | Score against a rubric with justification |
| **Workflow** | Does the end-to-end pipeline produce reliable results? | Test cases (typical + edge + adversarial), monitoring |
| **Safeguard** | Are the guardrails working? | Red-teaming, subgroup analysis, policy compliance checks |

## Building a rubric

A rubric makes evaluation systematic, defensible, and repeatable. Every rubric has dimensions, scales, and anchors.

### Step 1: Choose dimensions

Select 4-6 from this menu based on your specific task:

| Dimension | What it assesses | Best for |
|---|---|---|
| **Accuracy** | Are factual claims correct and verifiable? | Summaries, reports, factual Q&A |
| **Completeness** | Does it address all parts of the task? | Summaries, classification, extraction |
| **Relevance** | Is it focused on the user's actual need? | Search, recommendation, Q&A |
| **Specificity** | Does it provide concrete, usable detail? | Reports, advice, code |
| **Transparency** | Does it state assumptions or uncertainty? | Analysis, recommendations |
| **Consistency** | Would similar inputs produce similar outputs? | Classification, batch processing |
| **Bias / fairness** | Could errors affect groups differently? | Classification, screening, scoring |
| **Privacy** | Does the workflow expose sensitive data? | Any workflow with PII or confidential data |
| **Actionability** | Can a decision-maker act on this output? | Reports, recommendations, briefs |
| **Review need** | What must be checked before use? | All outputs in professional settings |

### Step 2: Define the scale

Use a 0-4 scale:

| Score | Meaning |
|---|---|
| 0 | Unacceptable - unusable, wrong, or harmful |
| 1 | Poor - major issues requiring substantial revision |
| 2 | Adequate - usable with revision |
| 3 | Good - minor issues, usable with light editing |
| 4 | Excellent - no issues found, ready for use |

### Step 3: Write anchors for your specific task
#### What is an anchor?
An anchor is the concrete description of what a specific score level looks like for a given dimension. It ties the abstract number to something observable so that two different raters reading the same output would arrive at a similar score.

Without anchors, "accuracy = 3" is subjective - one rater's 3 is another's 2. With anchors, both raters share a reference point that describes what they'd actually see in the output at that level. A common mistake is writing anchors that just restate the dimension name with an adjective:

| Score | Weak anchor (don't do this!) |
|---|---|
| 0 | Very inaccurate |
| 2 | Somewhat accurate |
| 4 | Very accurate |

These don't help, as they describe how the rater feels about accuracy, not what they'd observe. You also don't need to anchor all five levels. Define what 0, 2, and 4 look like for your specific task, with scores of 1 and 3 fall naturally between them. A good anchor describes the output itself:

**Example for a customer feedback summary task:**

| Score | Strong anchor (do this!) |
|---|---|
| 0 | Contains fabricated statistics, invented citations, or misattributed claims |
| 2 | Most claims are correct but 1–2 minor factual errors are present |
| 4 | All factual claims verified against source data; no errors found |

A good thing to ask yourself: could two people who've never spoken to each other read these anchors and score the same output within 1 point of each other? If yes, the anchors are doing their job. If not, they need to be more specific.

### Rubric template

```
Task: [describe the task]
Audience: [who will use the output]
Risk level: [low / medium / high]

| Dimension | 0 (unacceptable) | 2 (adequate) | 4 (excellent) | Score | Justification |
|-----------|-------------------|--------------|----------------|-------|---------------|
| [dim 1]   | [anchor]          | [anchor]     | [anchor]       |       |               |
| [dim 2]   | [anchor]          | [anchor]     | [anchor]       |       |               |
| [dim 3]   | [anchor]          | [anchor]     | [anchor]       |       |               |
| [dim 4]   | [anchor]          | [anchor]     | [anchor]       |       |               |

Total: __ / [max]
Recommendation: acceptable / acceptable with revision / unacceptable
```

## Agreement metrics

### Cohen's kappa (κ)

Measures agreement between two raters, correcting for chance. Use when two people (or a person and an LLM) score the same outputs.

```python
from sklearn.metrics import cohen_kappa_score

kappa = cohen_kappa_score(rater_1_labels, rater_2_labels)
```

**Interpretation:**

| κ value | Meaning |
|---|---|
| < 0 | Less than chance agreement |
| 0.01-0.20 | Slight agreement |
| 0.21-0.40 | Fair agreement |
| 0.41-0.60 | Moderate agreement |
| 0.61-0.80 | Substantial agreement |
| 0.81-1.00 | Near-perfect agreement |

For most analytic tasks, aim for κ > 0.6 (substantial agreement) before trusting automated labels.

### Precision, recall, and F1

Use when evaluating classification accuracy against ground truth.

```python
from sklearn.metrics import classification_report

print(classification_report(true_labels, predicted_labels))
```

| Metric | What it measures | When it matters |
|---|---|---|
| **Precision** | Of items labeled X, how many actually are X? | When false positives are costly (e.g., flagging someone as high-risk) |
| **Recall** | Of all actual X items, how many did we catch? | When false negatives are costly (e.g., missing a safety issue) |
| **F1** | Harmonic mean of precision and recall | When you need a single balanced score |

**Subgroup analysis:** Always compute precision/recall by subgroup, not just overall. A classifier with 90% overall accuracy might have 60% accuracy for a specific category.

```python
from sklearn.metrics import precision_recall_fscore_support

p, r, f1, support = precision_recall_fscore_support(y_true, y_pred, labels=labels)
```

## Test case design

### The three test case types

Every evaluation should include at least one of each:

**Typical case** - a straightforward, representative input. This tests the happy path. If the system fails here, it's not ready.

**Edge case** - an unusual, ambiguous, or boundary input. Tests whether the system handles uncertainty gracefully rather than guessing confidently.

**Adversarial case** - an input designed to make the system fail. Tests robustness and whether the system knows what it doesn't know.

### Test case template

```
Name: [descriptive name]
Type: typical / edge / adversarial
Input: [the specific input to send]
Expected behavior: [what a good response looks like]
Failure mode: [what a bad response looks like]
Evaluation: [how you'll score it]
Pass criteria: [what counts as acceptable]
```

### Example test cases for a customer feedback classifier

| Name | Type | Input | Expected | Failure |
|---|---|---|---|---|
| Clear billing complaint | Typical | "Charged twice for March subscription" | billing, high confidence | Wrong category |
| Mixed complaint | Edge | "Setup took 3 weeks and then I got billed for the wrong plan" | onboarding + billing, with both noted | Only one label assigned |
| Off-topic input | Adversarial | "What's the weather in Denver?" | Low confidence or "unclassifiable" | Confident classification into a category |
| Ambiguous tone | Edge | "The product works, I guess" | product_quality, low confidence | High confidence positive or negative |

## Evaluation approaches compared

| Approach | Speed | Cost | Nuance | Best for |
|---|---|---|---|---|
| **Human evaluation** | Slow | High | High | High-stakes decisions, subjective quality, fairness |
| **Automated checks** | Fast | Free | Low | Format validation, assertion checks, keyword presence |
| **LLM-as-judge** | Fast | Low | Medium | Preliminary screening, consistency checks, scale |
| **Hybrid** | Medium | Medium | High | Production systems: automate easy cases, human-review hard ones |

### When to trust LLM-as-judge

Trust it for: format compliance, basic factual checks, consistency across outputs, preliminary scoring before human review.

Don't trust it alone for: high-stakes decisions, fairness assessments, domain-specific accuracy, anything where being wrong causes real harm (what might this look like?).

Always validate: run LLM-as-judge on your human-scored test set first and compute κ. If agreement is below 0.6, the LLM judge isn't reliable enough for your task.

## The eval pipeline pattern

*Adapted from Anthropic's Building with the Claude API course.*

Professional AI evaluation is organized as a pipeline, not a one-time scoring session:

1. **Cases** - a stored set of inputs with expected behavior (your test cases: typical, edge, adversarial)
2. **Run** - execute every case programmatically against the model or workflow
3. **Grade** - score each output using the cheapest reliable grader: code graders for anything rule-checkable (format, allowed values), model graders (LLM-as-judge) for quality dimensions, humans for a validation sample
4. **Aggregate** - pass rates, mean rubric scores, agreement metrics (κ), and a decision

The pipeline mindset changes two things. First, evaluation becomes repeatable. When you change a prompt or model, you re-run the same cases and compare. Second, it becomes affordable. Code graders are free, so you reserve expensive human judgment for what actually needs it. Your Week 7 kappa and MDD work answers the pipeline's most important question e.g., can the grader itself be trusted?

## Putting it all together

For your final project evaluation:

1. **Design the rubric** - 4-6 dimensions with task-specific anchors
2. **Write test cases** - at least 1 typical, 1 edge, 1 adversarial
3. **Score with the rubric** - human scores with justifications
4. **Compute agreement** - if you have a second rater or LLM-as-judge, compute κ
5. **Analyze subgroups** - check whether performance varies by input type, category, or group
6. **Make a recommendation** - acceptable, acceptable with revision, or unacceptable, with evidence
7. **Document everything** - rubric, scores, test cases, and agreement metrics in your AI use log
