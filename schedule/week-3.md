---
layout: page
title: "Week 3: From Raw Data to Report"
subtitle: "Use · How can GenAI support a reproducible data-to-report pipeline?"
permalink: /schedule/week-3/
---

<div class="note" markdown="0">
  <strong>Module:</strong> <span class="badge badge-green">Use</span> &nbsp;·&nbsp;
  <strong>Deliverable:</strong> Directed report with AI use log (due before Week 4 Monday) &nbsp;·&nbsp;
  <a href="{{ site.baseurl }}/assignments/week-3-report/">See assignment →</a>
</div>

## Learning objectives

By the end of this week, you should be able to:

1. Distinguish a vibe report from a directed report
2. Explore a 2,000-row dataset using AI + pandas, identifying data quality issues that require code — not just eyeballing
3. Build a verified data dictionary documenting variables, missingness patterns, and cleaning decisions
4. Clean data at scale with assertions after every step
5. Conduct a formal statistical test and report results with effect sizes and confidence intervals
6. Write a directed report with a methods section, results, interpretation, and limitations

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Monday</div>
  <div class="session-content">
    <div class="session-title">From messy data to understanding — at scale</div>
    <p>We enter the Use module with a core distinction: vibe reports vs. directed reports. You'll work with a 2,000-row business orders dataset — large enough that you can't eyeball every row. Use AI + pandas to discover data quality issues, compare what AI finds to what your code reveals, and build a verified data dictionary.</p>
    <div class="session-topics">
      <span class="topic-tag">Vibe vs. directed reports</span>
      <span class="topic-tag">Data-to-report pipeline</span>
      <span class="topic-tag">AI vs. code discovery at scale</span>
      <span class="topic-tag">Data dictionary workshop</span>
    </div>
  </div>
</div>

<div class="session-block" markdown="0">
  <div class="session-label">Wednesday</div>
  <div class="session-content">
    <div class="session-title">Cleaning, analysis, and statistical evidence</div>
    <p>You'll write your own cleaning pipeline (the notebook gives requirements, not step-by-step code), learn how to include formal statistical tests in a directed report (t-test, ANOVA, chi-square, confidence intervals), and start building the report with a proper methods section.</p>
    <div class="session-topics">
      <span class="topic-tag">Python: cleaning at scale</span>
      <span class="topic-tag">Statistical evidence in reports</span>
      <span class="topic-tag">Work session: analysis and drafting</span>
    </div>
  </div>
</div>

## Prepare before class

**Before Monday:**

- Skim Békés, [Data Analysis with AI, Week 2](https://gabors-data-analysis.com/ai-course/) — focus on the discover → document → clean → report pipeline
- Make sure your Python environment and AI tools are working (see the [setup guide]({{ site.baseurl }}/guides/dev-setup/) if needed)
- Review the [Python for analysts guide]({{ site.baseurl }}/guides/python-analysts/) for pandas reference

**Before Wednesday:**

- Review your Monday data quality findings
- Choose which analysis question you want to pursue
- Brush up on basic hypothesis testing if needed (t-test, ANOVA, chi-square)

## Key concepts

| Concept | What it means |
|---|---|
| **Vibe report** | An unfocused "analysis" with no clear question — what AI produces when you say "analyze this data" |
| **Directed report** | Analysis driven by a specific question, with a methods section, verified evidence, formal statistical tests, and stated limitations |
| **Data dictionary** | Documentation of every variable: name, type, description, missingness pattern, issues, and cleaning decisions |
| **Methods section** | How you cleaned the data, what you computed, what test you used and why, sample size, and exclusions |
| **Effect size** | How large the difference or relationship is — not just whether it's statistically significant |

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">Directed Report with AI Use Log</div>
  <div class="assignment-preview-meta">4 components · 30 points · Due before class, Week 4 Monday · Submit via Canvas</div>
  <p>README + data dictionary, reproducible notebook with assertions, a 3–4 page directed report with methods section and formal statistical test, and an AI use log.</p>
  <a href="{{ site.baseurl }}/assignments/week-3-report/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week: **Debugging AI's Work** — you'll learn to find bugs in AI-generated code, quantify their impact, and build an automated test suite. The central lesson: output that looks right is not necessarily right.
