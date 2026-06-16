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
2. Use AI to explore, describe, and document a dataset — then verify its output
3. Identify common data quality issues: mixed formats, inconsistent categories, missing values, duplicates, data entry errors
4. Build a verified data dictionary
5. Clean and aggregate data using pandas with AI assistance
6. Write a directed report with a specific question, evidence, interpretation, and limitations

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Monday</div>
  <div class="session-content">
    <div class="session-title">From messy data to understanding</div>
    <p>We enter the Use module with a core distinction: vibe reports vs. directed reports. Then you'll get a messy dataset and use AI + pandas to discover what's in it, what's wrong with it, and how to document it. The central lesson: AI accelerates discovery, but the analyst verifies.</p>
    <div class="session-topics">
      <span class="topic-tag">Vibe vs. directed reports</span>
      <span class="topic-tag">Data-to-report pipeline</span>
      <span class="topic-tag">Dataset discovery with AI</span>
      <span class="topic-tag">Data dictionary workshop</span>
    </div>
  </div>
</div>

<div class="session-block" markdown="0">
  <div class="session-label">Wednesday</div>
  <div class="session-content">
    <div class="session-title">Building the directed report</div>
    <p>We'll clean the dataset (standardize dates, fix categories, handle missing values, resolve anomalies), then learn what makes a report "directed" — question, evidence, interpretation, limitations, reproducibility. You'll start writing your report in class.</p>
    <div class="session-topics">
      <span class="topic-tag">Python: cleaning and aggregation</span>
      <span class="topic-tag">Anatomy of a directed report</span>
      <span class="topic-tag">Work session: write the report</span>
    </div>
  </div>
</div>

## Prepare before class

**Before Monday:**

- Skim Békés, [Data Analysis with AI, Week 2](https://gabors-data-analysis.com/ai-course/) — focus on the discover → document → clean → report pipeline
- Make sure your Python environment and AI tools are working (see the [setup guide]({{ site.baseurl }}/guides/dev-setup/) if needed)

**Before Wednesday:**

- Review your Monday data quality findings — you'll build on them
- Think about which analysis question you want to pursue for your report

## Key concepts

| Concept | What it means |
|---|---|
| **Vibe report** | An unfocused "analysis" with no clear question — what AI produces when you say "analyze this data" |
| **Directed report** | Analysis driven by a specific question, with verified evidence, interpretation in context, and stated limitations |
| **Data dictionary** | Documentation of every variable: name, type, description, issues, and cleaning decisions |
| **AI use log** | A record of what you prompted, what AI produced, and what you changed — the accountability trail |
| **Reproducibility** | Code and documentation that let someone else verify your work end-to-end |

## Readings and resources

- Békés, Gábor. [Data Analysis with AI, Week 2](https://gabors-data-analysis.com/ai-course/) — data discovery, documentation, cleaning, and reporting with AI
- Dataset for this week posted on Canvas

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">Directed Report with AI Use Log</div>
  <div class="assignment-preview-meta">4 components · 30 points · Due before class, Week 4 Monday · Submit via Canvas</div>
  <p>Submit a README + data dictionary, a reproducible Python notebook, a directed report (1–2 pages), and an AI use log documenting your workflow.</p>
  <a href="{{ site.baseurl }}/assignments/week-3-report/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week: **Debugging AI's Work** — you'll learn to inspect, test, and document AI-written code. The central lesson: output that looks right is not necessarily right.
