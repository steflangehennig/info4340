---
layout: page
title: "Week 4: Debugging AI's Work"
subtitle: "Use · Output that looks right is not necessarily right"
permalink: /schedule/week-4/
---

<div class="note" markdown="0">
  <strong>Module:</strong> <span class="badge badge-green">Use</span> &nbsp;·&nbsp;
  <strong>Deliverable:</strong> Debugging and review log (due before Week 5 Monday) &nbsp;·&nbsp;
  <a href="{{ site.baseurl }}/assignments/week-4-debugging/">See assignment →</a>
</div>

## Learning objectives

By the end of this week, you should be able to:

1. Identify the five failure modes of AI-generated analytic code
2. Apply three test habits: row-count checks, data-description checks, code/unit checks
3. Find and fix bugs in realistic AI-generated code
4. Write assertions that prevent bugs from recurring
5. Use lightweight versioning to track changes
6. Conduct a structured peer code review

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Monday</div>
  <div class="session-content">
    <div class="session-title">Why AI code breaks — and how to catch it</div>
    <p>Five failure modes of AI-generated code (bad joins, silent missingness, wrong unit of observation, plausible-but-wrong plots, code that changes the question), the three test habits every analyst should run, and a bug hunt: you'll receive an AI-generated script that runs without errors and find what's wrong with it.</p>
    <div class="session-topics">
      <span class="topic-tag">Five failure modes</span>
      <span class="topic-tag">Three test habits</span>
      <span class="topic-tag">Bug hunt activity</span>
    </div>
  </div>
</div>

<div class="session-block" markdown="0">
  <div class="session-label">Wednesday</div>
  <div class="session-content">
    <div class="session-title">Testing, versioning, and review discipline</div>
    <p>We'll write assertions and verification checks, learn lightweight versioning (git commits, change logs, before/after screenshots), and do a peer code review of each other's Week 3 notebooks.</p>
    <div class="session-topics">
      <span class="topic-tag">Writing assertions</span>
      <span class="topic-tag">Lightweight versioning</span>
      <span class="topic-tag">Peer code review</span>
    </div>
  </div>
</div>

## Prepare before class

**Before Monday:**

- Make sure you have access to the Week 3 dataset (`week3-orders-messy.csv`)
- Review your Week 3 notebook — we'll use it during the peer review on Wednesday

**Before Wednesday:**

- Bring your Week 3 notebook (digital) ready to share with a partner
- If you haven't used git before, skim a [basic git tutorial](https://docs.github.com/en/get-started/start-your-journey/hello-world) — we'll cover just the essentials

## Key concepts

| Concept | What it means |
|---|---|
| **Three test habits** | Row-count checks (did rows appear or disappear?), data-description checks (do distributions match expectations?), code/unit checks (does each step do what you think?) |
| **Assertions** | One-line tests embedded in your code: if the condition is false, the code stops immediately. Cheap to write, expensive not to. |
| **Versioning** | Tracking what changed, when, and why — git commits, change logs, or before/after comparisons |
| **Peer code review** | Structured review of someone else's work using a checklist — catches errors the author can't see |

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">Debugging and Review Log</div>
  <div class="assignment-preview-meta">3 components · 30 points · Due before class, Week 5 Monday · Submit via Canvas</div>
  <p>Bug report documenting each error found, a fixed script with assertions, and peer review feedback on a classmate's Week 3 notebook.</p>
  <a href="{{ site.baseurl }}/assignments/week-4-debugging/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week: **AI as Analytic/Research Companion** — you'll use AI to help design an analysis, not just execute one. The shift: from "write me code" to "help me think through an approach."
