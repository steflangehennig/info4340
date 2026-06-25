---
layout: page
title: "Week 4: Debugging AI's Work"
subtitle: "Use | Output that looks right is not necessarily right"
permalink: /schedule/week-4/
---

<div class="note" markdown="0">
  <strong>Module:</strong> <span class="badge badge-green">Use</span> &nbsp;|&nbsp;
  <strong>Deliverable:</strong> Debugging and review log (due before Week 5 Monday) &nbsp;|&nbsp;
  <a href="{{ site.baseurl }}/assignments/week-4-debugging/">See assignment →</a>
</div>

## Learning objectives

By the end of this week, you should be able to:

1. Identify failure modes in AI-generated analytic code without being told what to look for
2. Quantify the exact numerical impact of each bug on key business metrics
3. Build an automated test suite (`run_validation()`) that catches data quality and logic errors
4. Apply three test habits: row-count checks, data-description checks, code/unit checks
5. Use lightweight versioning to track changes
6. Conduct a peer code review using both manual inspection and automated test suites

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Monday</div>
  <div class="session-content">
    <div class="session-title">Why AI code breaks - quantifying the damage</div>
    <p>Five failure modes of AI-generated code, the three test habits, then a bug hunt on a provided dataset: you'll find bugs in an AI-generated script and compute the exact dollar and percentage impact of each one. "Revenue is wrong" is not enough - you need to say by how much.</p>
    <div class="session-topics">
      <span class="topic-tag">Five failure modes</span>
      <span class="topic-tag">Three test habits</span>
      <span class="topic-tag">Bug hunt + impact analysis</span>
    </div>
  </div>
</div>

<div class="session-block" markdown="0">
  <div class="session-label">Wednesday</div>
  <div class="session-content">
    <div class="session-title">Test suites, versioning, and review discipline</div>
    <p>Build an automated test suite function that runs 10+ validation checks and produces a pass/fail report. Then peer-review a classmate's Week 3 notebook using both manual inspection and your test suite - comparing what each method catches.</p>
    <div class="session-topics">
      <span class="topic-tag">Automated test suite</span>
      <span class="topic-tag">Lightweight versioning</span>
      <span class="topic-tag">Peer review: manual + automated</span>
    </div>
  </div>
</div>

## Prepare before class

**Before Monday:**

- Make sure you have access to the Week 3 v2 dataset (`week3-orders-v2.csv`)
- Review your Week 3 notebook - you'll use it during Wednesday's peer review

**Before Wednesday:**

- Bring your Week 3 notebook ready to share with a partner
- Review the [Python for analysts guide]({{ site.baseurl }}/guides/python-analysts/) section on assertions

## Key concepts

| Concept | What it means |
|---|---|
| **Three test habits** | Row-count checks, data-description checks, code/unit checks - run every time you use AI code |
| **Quantitative impact** | Not "the bug made revenue wrong" but "the bug overstated revenue by $12,400 (8.3%)" |
| **Test suite** | A reusable `run_validation()` function with 8+ checks that produces a pass/fail report - infrastructure, not one-off assertions |
| **Peer review** | Manual checklist + automated test suite, comparing what each catches |

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">Debugging and Review Log</div>
  <div class="assignment-preview-meta">3 components | 30 points | Due before class, Week 5 Monday | Submit via Canvas</div>
  <p>Bug report with quantitative impact analysis, fixed script with an automated test suite, and peer review combining manual and automated checks.</p>
  <a href="{{ site.baseurl }}/assignments/week-4-debugging/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week: **AI as Analytic/Research Companion** - you'll use AI to help design an analysis, not just execute one. The shift: from "write me code" to "help me think through an approach."
