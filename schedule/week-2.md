---
layout: page
title: "Week 2: LLMs, Harnesses, and Setup"
subtitle: "Understand · What are LLMs, and how do analysts work with them?"
permalink: /schedule/week-2/
---

<div class="note" markdown="0">
  <strong>Module:</strong> <span class="badge badge-blue">Understand</span> &nbsp;·&nbsp;
  <strong>Deliverable:</strong> Tool setup and comparison note (due before Week 3 Monday) &nbsp;·&nbsp;
  <a href="{{ site.baseurl }}/assignments/week-2-comparison/">See assignment →</a>
</div>

## Learning objectives

By the end of this week, you should be able to:

1. Explain what tokens, context windows, and next-token prediction are
2. Distinguish closed/frontier models from open-weights models
3. Explain the harness concept: same model, different interface, different workflow
4. Set up VS Code, Claude Code, and/or GitHub Copilot
5. Compare AI tool surfaces on the same task and identify tradeoffs
6. Estimate token counts and API costs for analytic tasks

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Monday</div>
  <div class="session-content">
    <div class="session-title">What LLMs are and why it matters for your work</div>
    <p>We'll look inside LLMs — tokens, next-token prediction, context windows — and explore the model landscape (closed vs. open-weights). Then we'll unpack the harness concept: same model, very different experience depending on the interface. Includes a hands-on tokenization activity in Python.</p>
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
    <div class="session-title">Setting up and comparing your tools</div>
    <p>We'll set up your development environment (VS Code, Claude Code, Copilot) following the setup guide, then do a hands-on comparison: same data task, different AI surfaces. You'll explore, clean, and summarize a dataset using multiple tools and document what works best for what.</p>
    <div class="session-topics">
      <span class="topic-tag">Tool setup workshop</span>
      <span class="topic-tag">Hands-on: tool comparison task</span>
      <span class="topic-tag">Discussion: surface → task fit</span>
    </div>
  </div>
</div>

## Prepare before class

**Before Monday:**

- Read your Week 1 use case reflection feedback (posted on Canvas)
- Skim Békés, [Data Analysis with AI, Week 1](https://gabors-data-analysis.com/ai-course/unit1/index.html) — focus on the "LLMs and harnesses" framing

**Before Wednesday:**

- Start the [developer setup guide]({{ site.baseurl }}/guides/dev-setup/) — install VS Code and get Python working. We'll finish the AI tool setup in class, but having the basics ready saves time.
- If you have trouble with any step, note where you got stuck — we'll troubleshoot together.

## Key concepts

| Concept | What it means |
|---|---|
| **Tokens** | Subword pieces that LLMs process. Not words — "unhappiness" might become ["un", "happiness"]. Token count determines cost and what fits in a prompt. |
| **Next-token prediction** | The core mechanism: given all preceding tokens, predict the most probable next one. The model computes probabilities, not truth. |
| **Context window** | Everything the model can see at once: your prompt, pasted documents, conversation history, and its response. Typically 128K–200K tokens. |
| **Closed / frontier models** | Models like Claude, GPT-4o, Gemini — accessed via API, weights not available, strongest general capabilities. |
| **Open-weights models** | Models like Llama, Mistral, Qwen — weights downloadable, can run locally, more control but often smaller. |
| **Harness** | The interface wrapping the model. "The model is the engine; the harness is the car." Chat, API, IDE agent, and CLI are different harnesses for the same engine. |

## Readings and resources

- Békés, Gábor. [Data Analysis with AI, Week 1: LLMs, Models & Harnesses + Setup](https://gabors-data-analysis.com/ai-course/unit1/index.html) — the conceptual backbone for this week
- Microsoft. [Generative AI for Beginners, Lessons 2–4](https://github.com/microsoft/generative-ai-for-beginners) — tokens, prompting basics, and model selection
- Course setup guide: [Developer setup guide]({{ site.baseurl }}/guides/dev-setup/)

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">Tool Setup and Comparison Note</div>
  <div class="assignment-preview-meta">~1–2 pages · Due before class, Week 3 Monday · Submit via Canvas</div>
  <p>Confirm your dev environment works, compare AI tool surfaces on the same data task, and reflect on which surface fits which kind of analytic work.</p>
  <a href="{{ site.baseurl }}/assignments/week-2-comparison/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week we move into the **Use** module with **From Raw Data to Report** — you'll use AI to explore a messy dataset, document it, clean it, and produce a short directed report. The tools you set up this week are the foundation for everything from Week 3 onward.
