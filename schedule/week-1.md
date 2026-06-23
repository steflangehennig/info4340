---
layout: page
title: "Week 1: Generative AI for Analysts"
subtitle: "Understand | What does GenAI change about analytic work?"
permalink: /schedule/week-1/
---

<div class="note" markdown="0">
  <strong>Module:</strong> <span class="badge badge-blue">Understand</span> &nbsp;|&nbsp;
  <strong>Deliverable:</strong> Use case reflection (due before Week 2 Monday) &nbsp;|&nbsp;
  <a href="{{ site.baseurl }}/assignments/week-1-reflection/">See assignment →</a>
</div>

## Learning objectives

By the end of this week, you should be able to:

1. Explain what generative AI and LLMs are at a high level
2. Distinguish using AI as a tool from delegating judgment to AI
3. Identify analyst tasks where GenAI can be useful - and where it can go wrong
4. Score GenAI use cases on five risk dimensions quantitatively and compute a composite risk score
5. Compare risk scores across groups and identify sources of disagreement
6. Describe the course architecture: **understand, use, evaluate, govern**
7. Make API calls to an LLM in Python, including batch processing with structured JSON output
8. Parse AI-generated responses and compute summary statistics from the results

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Monday</div>
  <div class="session-content">
    <div class="session-title">What does GenAI change about analytic work?</div>
    <p>We'll start with introductions and a discussion of where you've already used AI tools. Then a short lecture on how GenAI is reshaping analyst workflows - and why fluency is not the same as accuracy. The core activity is a quantitative risk-scoring exercise: you'll rate use cases on five dimensions (1-5 each), compute composite scores, and compare your ratings with another group's.</p>
    <div class="session-topics">
      <span class="topic-tag">Opening discussion</span>
      <span class="topic-tag">Mini-lecture: GenAI for analysts</span>
      <span class="topic-tag">Quantitative risk scoring</span>
      <span class="topic-tag">Cross-group comparison</span>
    </div>
  </div>
</div>

<div class="session-block" markdown="0">
  <div class="session-label">Wednesday</div>
  <div class="session-content">
    <div class="session-title">First hands-on: seeing what GenAI does</div>
    <p>We'll introduce the course spine (understand, use, evaluate, govern), then get hands-on with Python. You'll make your first API calls, experiment with temperature, and then process a batch of 10 texts programmatically - parsing structured JSON output and analyzing the results as a dataset. We'll also do a prompt diagnosis exercise.</p>
    <div class="session-topics">
      <span class="topic-tag">Course architecture</span>
      <span class="topic-tag">Python: API calls and temperature</span>
      <span class="topic-tag">Python: batch processing with structured output</span>
      <span class="topic-tag">Prompt diagnosis activity</span>
    </div>
  </div>
</div>

## Prepare before class

**Before Monday:**
- No readings this week - come ready to discuss where you've already used AI tools (ChatGPT, Claude, Copilot, Gemini, or others)
- Think about one time AI was useful and one time it failed or surprised you

**Before Wednesday:**
- Check that you can access [Google Colab](https://colab.research.google.com) with your DU account
- The Python notebook link will be posted on Canvas

## Key concepts

| Concept | What it means |
|---|---|
| **Fluency ≠ accuracy** | GenAI output can sound confident, polished, and professional while being factually wrong, missing context, or fabricated |
| **Analyst responsibility** | AI can produce work products; analysts remain responsible for quality, verification, documentation, interpretation, and accountability |
| **Risk dimensions** | Stakes, data sensitivity, affected population, reversibility, and degree of automation - scored 1–5 each for a composite risk score |
| **Structured output** | Requesting JSON-formatted responses from LLMs so results can be parsed and analyzed as data |
| **Understand / Use / Evaluate / Govern** | The four-verb framework that organizes every topic, reading, and assignment in this course |

## Readings and resources

This week's readings are optional background - the main learning happens in class activities.

- Békés, Gábor. [Data Analysis with AI: Course overview](https://gabors-data-analysis.com/ai-course/) - skim the course philosophy to understand the applied backbone we'll build on
- Microsoft. [Generative AI for Beginners, Lesson 1](https://github.com/microsoft/generative-ai-for-beginners) - accessible introduction to GenAI concepts

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">GenAI Use Case Reflection</div>
  <div class="assignment-preview-meta">~1 page | Due before class, Week 2 Monday | Submit via Canvas</div>
  <p>Describe one realistic GenAI use case in a future analyst role. Explain what AI would do, what the human analyst would still be responsible for, what would need to be verified, and the risk level - including a quantitative score on the five risk dimensions.</p>
  <a href="{{ site.baseurl }}/assignments/week-1-reflection/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week we'll move into **LLMs, harnesses, and setup** - you'll learn the conceptual model behind how these systems work (tokens, context windows, model landscape), set up your development environment, and run a systematic model benchmarking exercise. See the [setup guide]({{ site.baseurl }}/guides/dev-setup/) to get a head start.
