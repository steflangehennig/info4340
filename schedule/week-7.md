---
layout: page
title: "Week 7: Evaluating GenAI Outputs"
subtitle: "Evaluate · \"Looks right\" is not an evaluation strategy"
permalink: /schedule/week-7/
---

<div class="note" markdown="0">
  <strong>Module:</strong> <span class="badge badge-orange">Evaluate</span> &nbsp;·&nbsp;
  <strong>Deliverable:</strong> Prompt and output evaluation memo (due before Week 8 Monday) &nbsp;·&nbsp;
  <a href="{{ site.baseurl }}/assignments/week-7-evaluation/">See assignment →</a>
</div>

## Learning objectives

By the end of this week, you should be able to:

1. Distinguish five evaluation targets: model, prompt, output, workflow, safeguard
2. Create a task-specific rubric with scored dimensions and anchors
3. Score GenAI outputs against a rubric and compare scores with peers
4. Compute and interpret Cohen's κ for inter-rater reliability
5. Compare human evaluation, automated checks, LLM-as-judge, and hybrid approaches
6. Design test cases with typical, edge, and adversarial inputs

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Monday</div>
  <div class="session-content">
    <div class="session-title">What does "good" mean? Rubric design and scoring</div>
    <p>We enter the Evaluate module with a core question: how do you know whether AI output is good enough? You'll learn five evaluation targets, a 10-dimension evaluation template, design a task-specific rubric, and score three AI outputs in a bake-off — then compare scores with your classmates.</p>
    <div class="session-topics">
      <span class="topic-tag">Five evaluation targets</span>
      <span class="topic-tag">Evaluation dimensions</span>
      <span class="topic-tag">Rubric design</span>
      <span class="topic-tag">Prompt/output bake-off</span>
    </div>
  </div>
</div>

<div class="session-block" markdown="0">
  <div class="session-label">Wednesday</div>
  <div class="session-content">
    <div class="session-title">Measuring agreement and designing test cases</div>
    <p>We'll put numbers on scoring disagreement with Cohen's κ, compare LLM-as-judge vs. human evaluation, and design test cases for your final project — including typical, edge, and adversarial inputs.</p>
    <div class="session-topics">
      <span class="topic-tag">Cohen's κ</span>
      <span class="topic-tag">Python: agreement scores</span>
      <span class="topic-tag">LLM-as-judge</span>
      <span class="topic-tag">Test case design</span>
    </div>
  </div>
</div>

## Prepare before class

**Before Monday:**

- Read the Evidently AI guide on [LLM evaluation](https://www.evidentlyai.com/blog/llm-evaluation) — focus on the distinction between evaluation targets
- Think about what task from your final project domain you'd want to evaluate

**Before Wednesday:**

- Review your Monday rubric and scores — you'll use them for the kappa exercise
- Start thinking about your final project: what AI workflow will you evaluate?

## Key concepts

| Concept | What it means |
|---|---|
| **Evaluation target** | What you're assessing: the model, the prompt, a single output, the full workflow, or a safeguard |
| **Rubric** | A structured scoring tool with dimensions, scales, and anchors that makes evaluation systematic and defensible |
| **Cohen's κ** | A measure of agreement between two raters that corrects for chance agreement — ranges from -1 to 1 |
| **LLM-as-judge** | Using a second LLM to evaluate the first — fast and cheap, but needs human validation |
| **Test cases** | Specific inputs designed to probe system behavior: typical (common case), edge (ambiguous), adversarial (designed to fail) |

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">Prompt and Output Evaluation Memo</div>
  <div class="assignment-preview-meta">7 components · 30 points · Due before class, Week 8 Monday · Submit via Canvas</div>
  <p>Choose a task, generate three outputs, design a rubric, score with justifications, analyze failure modes, and make an evidence-based recommendation about workflow acceptability.</p>
  <a href="{{ site.baseurl }}/assignments/week-7-evaluation/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week: **Failures, Incidents, and Risk** — you'll study real AI failures, analyze subgroup error rates, and write an AI incident brief. The shift: from evaluating your own outputs to learning from others' failures.
