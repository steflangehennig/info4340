---
layout: page
title: "Week 7: Evaluating GenAI Outputs"
subtitle: "Evaluate | \"Looks right\" is not an evaluation strategy"
permalink: /schedule/week-7/
---

<div class="note" markdown="0">
  <strong>Module:</strong> <span class="badge badge-orange">Evaluate</span> &nbsp;|&nbsp;
  <strong>Deliverable:</strong> Prompt and output evaluation memo (due before Week 8 Monday) &nbsp;|&nbsp;
  <a href="{{ site.baseurl }}/assignments/week-7-evaluation/">See assignment →</a>
</div>

## Learning objectives

By the end of this week, you should be able to:

1. Distinguish five evaluation targets: model, prompt, output, workflow, safeguard
2. Create a task-specific rubric with scored dimensions and calibrated anchors
3. Score GenAI outputs independently and compute multi-rater agreement
4. Compute Cohen's κ across multiple rater pairs (human-human and human-LLM)
5. Test prompt sensitivity: does the LLM-as-judge produce consistent scores?
6. Compute minimum detectable difference (MDD) and determine whether score differences are meaningful
7. Design test cases with typical, edge, and adversarial inputs linked to rubric criteria

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Monday</div>
  <div class="session-content">
    <div class="session-title">What does "good" mean? Rubric design and calibrated scoring</div>
    <p>Five evaluation targets, a 10-dimension evaluation template, and rubric design for a specific task. Then a calibrated bake-off: 3+ students score the same three AI outputs independently, producing the data you'll analyze on Wednesday.</p>
    <div class="session-topics">
      <span class="topic-tag">Five evaluation targets</span>
      <span class="topic-tag">Rubric design</span>
      <span class="topic-tag">Calibrated multi-rater bake-off</span>
    </div>
  </div>
</div>

<div class="session-block" markdown="0">
  <div class="session-label">Wednesday</div>
  <div class="session-content">
    <div class="session-title">Measuring reliability and designing test cases</div>
    <p>Put numbers on Monday's disagreements: multi-rater Cohen's κ (human-human and human-LLM), prompt sensitivity testing (is the LLM judge consistent?), and minimum detectable difference — the threshold below which score differences are just rater noise. Then design test cases for your final project.</p>
    <div class="session-topics">
      <span class="topic-tag">Multi-rater kappa</span>
      <span class="topic-tag">Prompt sensitivity (3 runs)</span>
      <span class="topic-tag">Minimum detectable difference</span>
      <span class="topic-tag">Test case design</span>
    </div>
  </div>
</div>

## Prepare before class

**Before Monday:**

- Review the [evaluation frameworks guide]({{ site.baseurl }}/guides/evaluation/) - rubric building and kappa interpretation
- Think about what task from your final project you'd want to evaluate

**Before Wednesday:**

- Bring your Monday rubric and scores - you'll use them for the kappa and MDD exercises

## Key concepts

| Concept | What it means |
|---|---|
| **Multi-rater kappa** | Cohen's κ computed across multiple rater pairs (human-human and human-LLM) to test whether agreement is consistent |
| **Prompt sensitivity** | Running LLM-as-judge 3x on the same output at temp=0. If scores vary, the evaluation itself is unreliable. |
| **Minimum detectable difference (MDD)** | The smallest score difference that exceeds inter-rater noise. Differences below MDD are not meaningful. |
| **Calibrated bake-off** | 3+ raters score independently before comparing - produces data for quantitative agreement analysis |

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">Prompt and Output Evaluation Memo</div>
  <div class="assignment-preview-meta">8 components | 30 points | Due before class, Week 8 Monday | Submit via Canvas</div>
  <p>Rubric, scored outputs with justifications, multi-rater agreement (human-human and human-LLM κ), prompt sensitivity analysis, minimum detectable difference, and evidence-based recommendation.</p>
  <a href="{{ site.baseurl }}/assignments/week-7-evaluation/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week: **Failures, Incidents, and Risk** - real AI incidents, subgroup error analysis with formal disparity metrics, and the sociotechnical failure chain.
