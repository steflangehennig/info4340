---
layout: page
title: "Guide: Prompt Engineering for Analysts"
permalink: /guides/prompt-engineering/
---

## What this guide covers

Prompt engineering for analysts is different from general prompt writing. You're not trying to get creative output or conversation. Rather, you're trying to get reliable, verifiable, structured results that feed into an analytic workflow. This guide covers the techniques that matter for that context.

## The analyst's prompting framework

Every good analytic prompt answers four questions:

1. **What is the task?** - Be specific about the operation (classify, summarize, extract, generate code, critique)
2. **What is the input?** - Describe the data format, provide examples, paste representative samples
3. **What should the output look like?** - Specify format, structure, and what to include
4. **How will you verify?** - Tell the model what evidence or reasoning to show so you can check its work

## Six prompt patterns for analytic work

### 1. Classification prompt

Use when: labeling text, categorizing data, sorting items into groups.

```
Classify this customer feedback into one or more categories:
billing, product_quality, support, technical, pricing, onboarding.

Return JSON with:
- primary_category: the best-fit category
- secondary_categories: other relevant categories (may be empty)
- confidence: high, medium, or low
- evidence: quote the key phrase that supports your classification

Feedback: "[paste text here]"
```

**Why it works:** Specifies the categories, requires structured output, and asks for evidence so you can verify the label.

### 2. Data exploration prompt

Use when: getting a first look at unfamiliar data.

```
Here are the first 15 rows of a CSV dataset:

[paste df.head(15).to_string()]

Column types: [paste df.dtypes.to_string()]

Describe this dataset:
1. What does each row represent?
2. What are the key variables and their likely meanings?
3. What data quality issues do you notice?
4. What questions could this data answer?

Flag anything you're uncertain about.
```

**Why it works:** Provides enough data for the model to reason about, asks specific questions, and explicitly invites uncertainty rather than confident guessing.

### 3. Code generation prompt

Use when: writing pandas, sklearn, or analysis code.

```
Write a Python function that:
- Loads a CSV with columns: [list columns]
- Groups by [column] and computes [metric]
- Returns a DataFrame with the results

Requirements:
- Use pandas
- Include comments explaining each step
- Add an assertion after each major operation to verify row counts
- Handle missing values explicitly (don't silently drop)

Show the expected output shape and one example row.
```

**Why it works:** Specifies the library, requires comments and assertions, and prevents silent data loss.

### 4. Structured summarization prompt

Use when: condensing documents, reports, or text.

```
Summarize this [document type] for [audience].

Structure your summary as:
1. Key finding (1 sentence)
2. Supporting evidence (2-3 bullet points with specific numbers)
3. Limitations or caveats (what the document doesn't address)
4. One question the reader should ask next

Source: [paste text]
```

**Why it works:** Forces structure, requires specific evidence, and includes limitations (prevents the "vibe summary" problem}.

### 5. Helpful/adversarial pair (Week 5)

Use when: designing an analysis approach.

**Prompt 1 (helpful analyst):**
```
I have [describe data]. I want to answer: [question].
Propose an analysis plan: what method, what variables, 
what steps, and what the output would look like.
```

**Prompt 2 (adversarial reviewer - in a separate conversation):**
```
Critique this analysis plan. What assumptions could fail?
What variables are missing? What alternative explanations 
exist? What validation is needed before trusting the results?

Plan: [paste the helpful analyst's response]
```

**Why it works:** Separating the conversations prevents the model from self-censoring. The adversarial prompt surfaces concerns the helpful prompt systematically ignores.

### 6. Evaluation prompt (LLM-as-judge)

Use when: scoring AI output quality systematically.

```
You are evaluating an AI-generated [output type] for [task].

Score on these dimensions (0-4):
- [dimension 1]: [description] (0=unacceptable, 2=adequate, 4=excellent)
- [dimension 2]: [description]
- [dimension 3]: [description]

Return JSON:
{
  "scores": {"dim1": N, "dim2": N, "dim3": N},
  "total": N,
  "justification": "brief explanation for each score",
  "failure_modes": ["list any issues found"]
}

Output to evaluate:
[paste output]
```

**Why it works:** Mirrors your human rubric, produces structured output you can aggregate, and identifies specific failure modes.

## Core techniques from Anthropic

*Adapted from Anthropic's Building with the Claude API course.*

Beyond the six patterns above, four techniques from Anthropic's own guidance measurably improve output quality for analytic tasks:

### XML tags for structure

When a prompt mixes instructions, data, and examples, mark the boundaries with XML tags:

```
<instructions>
Identify data quality issues in this sample. List each issue with the affected column.
</instructions>

<data>
[paste df.head(15).to_string()]
</data>
```

The tags aren't special syntax, they're unambiguous delimiters. Without them, models sometimes treat pasted data as instructions (or vice versa). Use tags any time you paste CSV rows, report text, or another prompt into your prompt.

### Multishot examples

One or more worked examples outperform longer instructions. Instead of describing the output format in prose, show it:

```
Classify feedback into categories. Examples:

Input: "Charged twice for the same month"
Output: {"category": "billing", "confidence": "high"}

Input: "Setup took three weeks and support never responded"
Output: {"category": "onboarding", "confidence": "medium"}

Now classify: "{text}"
```

2-3 examples that span your edge cases (a clear case, an ambiguous case) calibrate the model better than a paragraph of rules. This is exactly how you calibrate human coders in Week 6.

### Chain-of-thought prompting

For reasoning-heavy tasks, ask the model to work through the problem before answering:

```
Before giving your final classification, briefly reason through:
1. What is the customer's core complaint?
2. Which categories could plausibly apply?
3. Which fits best and why?

Then output the JSON.
```

This costs more tokens but reduces errors on ambiguous inputs. Use for edge cases and evaluation tasks; skip for high-volume simple classification where cost matters.

### Prefilling the response

You can start the assistant's response for it, forcing the output format:

```python
messages=[
    {"role": "user", "content": "Classify: 'Charged twice for March.'"},
    {"role": "assistant", "content": "{"}   # response must continue this JSON
]
```

The model continues from the `{` - no preamble possible. A blunt but effective way to guarantee JSON when "ONLY valid JSON" instructions aren't enough.

## Prompt iteration workflow

Good prompts are rarely written in one shot. Use this workflow:

1. **Draft** - write the prompt based on the patterns above
2. **Test on 3 examples** - run the prompt on inputs where you know the right answer
3. **Compare** - does the output match your expectations? Where does it fail?
4. **Diagnose** - is the failure in the task description, input format, output spec, or model capability?
5. **Revise** - fix the prompt and test again
6. **Scale** - once the prompt works on your test cases, run it on the full dataset

Document each iteration in your AI use log.

## Common mistakes

**Too vague:** "Analyze this data" can produces a vibe report. Be specific about the question, method, and output format.

**Too long:** Prompts over ~500 words often confuse the model. If you need a lot of context, put the instructions first and the data last.

**No output format:** "Tell me about this" results in unstructured prose you can't parse. Always specify format (JSON, table, numbered list with specific fields).

**No verification hook:** If you don't ask for evidence, reasoning, or confidence, you can't tell whether the output is right without checking everything manually.

**Pasting too much data:** Context windows are large but not infinite. For datasets over ~500 rows, summarize or sample rather than pasting the whole thing.

**Same conversation for propose and critique:** The model will soften its critique if it just proposed the plan. Use separate conversations for helpful and adversarial roles.

## Temperature guidance

| Task | Temperature | Why |
|---|---|---|
| Classification | 0 | You want consistent, deterministic labels |
| Code generation | 0 | You want correct, reproducible code |
| Fact extraction | 0 | You want accuracy, not creativity |
| Brainstorming | 0.7–1.0 | You want variety and novel ideas |
| Creative writing | 1.0 | You want diverse, interesting output |
| Summarization | 0–0.3 | You want accuracy with slight variation |

## Prompts to avoid

- "Are you sure?" - the model will almost always say yes, regardless of whether it should
- "Be creative" - for analytic tasks, you want reliability, not novelty
- "Ignore your previous instructions" - this is a jailbreak pattern, not a prompt technique
- "You are an expert in X" - role-playing can help, but the four prompt roles (Week 5) are more structured and more useful
