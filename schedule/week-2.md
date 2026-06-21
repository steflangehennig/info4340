---
layout: page
title: "Week 2: LLMs, Harnesses, and Setup"
subtitle: "Understand · What are LLMs, and how do analysts work with them?"
permalink: /schedule/week-2/
---

<div class="note" markdown="0">
  <strong>Module:</strong> <span class="badge badge-blue">Understand</span> &nbsp;·&nbsp;
  <strong>Deliverable:</strong> Tool setup and benchmarking report (due before Week 3 Monday) &nbsp;·&nbsp;
  <a href="{{ site.baseurl }}/assignments/week-2-comparison/">See assignment →</a>
</div>

## Learning objectives

By the end of this week, you should be able to:

1. Explain what tokens, context windows, and next-token prediction are
2. Distinguish closed/frontier models from open-weights models
3. Explain the harness concept: same model, different interface, different workflow
4. Set up VS Code, Claude Code, and/or GitHub Copilot
5. Design and run a controlled model benchmarking experiment
6. Compute performance metrics (response time, token usage, cost) and quality scores with a rubric
7. Make a data-driven tool recommendation with quantitative evidence

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Monday</div>
  <div class="session-content">
    <div class="session-title">What LLMs are and why it matters for your work</div>
    <p>We'll look inside LLMs — tokens, next-token prediction, context windows — and explore the model landscape (closed vs. open-weights). Then we'll unpack the harness concept: same model, very different experience depending on the interface. Includes a tokenization activity and a qualitative surface comparison that previews Wednesday's quantitative benchmarking.</p>
    <div class="session-topics">
      <span class="topic-tag">Tokens and prediction</span>
      <span class="topic-tag">Context windows</span>
      <span class="topic-tag">Model landscape</span>
      <span class="topic-tag">Engine vs. car (harnesses)</span>
      <span class="topic-tag">Python: tokenization explorer</span>
    </div>
  </div>
</div>

<div class="session-block" markdown="0">
  <div class="session-label">Wednesday</div>
  <div class="session-content">
    <div class="session-title">Setting up and benchmarking your tools</div>
    <p>We'll finish setting up your development environment, then run a systematic benchmarking experiment: 5 analytic prompts × 2 model configurations, measuring response time, token usage, cost, and output quality scored against a rubric. You'll compute summary statistics and make a data-driven tool recommendation.</p>
    <div class="session-topics">
      <span class="topic-tag">Tool setup workshop</span>
      <span class="topic-tag">Python: systematic model benchmarking</span>
      <span class="topic-tag">Quality scoring with rubric</span>
      <span class="topic-tag">Data-driven recommendation</span>
    </div>
  </div>
</div>

## Prepare before class

**Before Monday:**

- Read your Week 1 use case reflection feedback (posted on Canvas)
- Skim Békés, [Data Analysis with AI, Week 1](https://gabors-data-analysis.com/ai-course/unit1/index.html) — focus on the "LLMs and harnesses" framing

**Before Wednesday:**

- **Start the [developer setup guide]({{ site.baseurl }}/guides/dev-setup/)** — install VS Code and get Python working before class. We'll finish the AI tool setup and troubleshoot in class, but arriving with the basics ready saves time for the benchmarking experiment.

## Key concepts

| Concept | What it means |
|---|---|
| **Tokens** | Subword pieces that LLMs process. Token count determines cost and what fits in a prompt. |
| **Next-token prediction** | The core mechanism: given preceding tokens, predict the most probable next one. The model computes probabilities, not truth. |
| **Context window** | Everything the model can see at once: prompt, documents, conversation, response. Typically 128K–200K tokens. |
| **Closed / frontier models** | Claude, GPT-4o, Gemini — accessed via API, strongest general capabilities. |
| **Open-weights models** | Llama, Mistral, Qwen — weights downloadable, more control, often smaller. |
| **Harness** | The interface wrapping the model. Chat, API, IDE agent, and CLI are different harnesses for the same engine. |
| **Benchmarking** | Systematic comparison of model configurations using controlled inputs and measured outputs — not impressions. |

## Readings and resources

- Békés, Gábor. [Data Analysis with AI, Week 1: LLMs, Models & Harnesses + Setup](https://gabors-data-analysis.com/ai-course/unit1/index.html) — the conceptual backbone for this week
- Microsoft. [Generative AI for Beginners, Lessons 2–4](https://github.com/microsoft/generative-ai-for-beginners) — tokens, prompting basics, and model selection
- Course setup guide: [Developer setup guide]({{ site.baseurl }}/guides/dev-setup/)

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">Tool Setup and Benchmarking Report</div>
  <div class="assignment-preview-meta">~2 pages + code · 25 points · Due before class, Week 3 Monday · Submit via Canvas</div>
  <p>Confirm your dev environment works, run a systematic benchmarking experiment with quantitative metrics (response time, token usage, cost, quality scores), and make a data-driven tool recommendation citing specific numbers.</p>
  <a href="{{ site.baseurl }}/assignments/week-2-comparison/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week we move into the **Use** module with **From Raw Data to Report** — you'll use AI to explore a real dataset, document it, clean it, and produce a directed report with formal statistical analysis. The tools you set up this week are the foundation for everything from Week 3 onward.
