---
layout: page
title: "Guide: AI Use Log"
permalink: /guides/ai-use-log/
---

## What is an AI use log?

An AI use log is a record of how you used AI tools during an assignment. It documents what you asked, what the tool produced, and what you (the analyst) decided to do with that output.

Starting Week 3, every weekly deliverable in this course requires one.

## Why we use it

The AI use log serves three purposes:

1. **Accountability.** In professional settings, analysts are responsible for their work products, even when AI helped produce them. The log makes that chain of responsibility visible: here's what AI did, here's what I verified, here's what I changed.

2. **Learning.** Writing a log forces you to notice when you're relying on AI vs. exercising your own judgment. Over 10 weeks, your logs will show you how your relationship with AI tools evolves. This includes where you trust them more, where you trust them less, and where you've learned to verify.

3. **Reproducibility.** If someone else reads your work, the log tells them which parts came from you and which came from a tool. This is the professional equivalent of citing your sources, except the "source" is a probabilistic model that might produce different output tomorrow.

## What to include

For each meaningful AI interaction during the assignment, record:

| Element | What to write |
|---|---|
| **Tool** | Which AI tool you used (e.g., Claude.ai, ChatGPT, GitHub Copilot, Claude Code, Python API) |
| **Task** | What you were trying to accomplish (e.g., "generate a data dictionary," "debug a pandas error," "draft the limitations section") |
| **Prompt** | What you asked - include the full prompt for important interactions, or summarize for routine ones |
| **Output** | What the tool produced - summarize, quote key parts, or note "code that did X" |
| **Your decision** | What you did with the output: used as-is, modified, partially used, or rejected - and why |
| **Verification** | How you checked the output: ran the code, compared to documentation, checked against source data, etc. |

You don't need to log every single interaction. Focus on the interactions that shaped your work, e.g., the ones where AI generated something you built on, or where you caught an error, or where AI's suggestion changed your approach.

## Format

Use whatever format is clearest. Here are three options. Pick the one that works best for you.

### Option A: Table format

| # | Tool | Task | Prompt (summary) | What AI produced | My decision | Verification |
|---|---|---|---|---|---|---|
| 1 | Claude.ai | Draft data dictionary | "Generate a data dictionary for this CSV" + first 15 rows | Dictionary with 11 entries, descriptions for each column | Modified 4 descriptions, corrected the unit_price entry (AI missed the $48.99 anomaly) | Compared each entry to .info() and .value_counts() output |
| 2 | Copilot | Fix date parsing | Inline suggestion while writing pd.to_datetime() | Suggested format="mixed" parameter | Used as-is | Ran the code - dates parsed correctly |
| 3 | Claude.ai | Draft limitations section | "What are the limitations of this analysis?" + my report draft | 4 bullet points about data coverage, sample size, and missing context | Rewrote 3 of 4 - AI's points were generic; I added specifics about the logical missingness in delivery_days | Checked each limitation against my actual data and analysis |

### Option B: Narrative format

> **Data dictionary (Claude.ai).** I pasted the first 15 rows of the CSV and asked Claude to generate a data dictionary. The draft was roughly 70% accurate - it correctly identified column types and wrote reasonable descriptions for most variables. However, it described `unit_price` as "consistent across product categories" without noticing the $48.99 anomaly for customer C-812, and it described `delivery_days` missingness as random when it's actually logical (only missing for non-delivered orders). I corrected both entries and verified every description against `.info()` and `.value_counts()` output.
>
> **Date cleaning (Copilot).** While writing the date parsing code, Copilot suggested `pd.to_datetime(df["order_date"], format="mixed")`. I accepted the suggestion and it worked correctly for the mixed ISO/US date formats in the dataset.
>
> **Report draft (Claude.ai).** I asked Claude to draft a limitations section based on my report. Three of its four points were too generic ("sample size may be insufficient") so I rewrote them with specifics tied to the actual data issues I found.

### Option C: Annotated prompt log

For assignments with extensive AI interaction, you can include a prompt log with annotations:

```
PROMPT 1 (Claude.ai):
"Here are the first 15 rows of a business orders CSV. Generate a data
dictionary with variable name, type, description, and any issues you notice."
[pasted 15 rows]

AI OUTPUT: [data dictionary with 11 entries]

MY NOTES: Descriptions mostly good. Fixed: (1) unit_price - AI didn't catch
the $48.99 anomaly, (2) delivery_days - AI called missingness "random" but
it's logical, (3) customer_segment - AI didn't note the inconsistent casing.
Verified all entries against pandas output.
```

## What makes a good log vs. a bad one

**Good log:** Specific about what you prompted, honest about what AI got right and wrong, documents your verification steps, and shows your judgment.

**Bad log:** "I used ChatGPT to help with the assignment." This tells the reader nothing. It's like citing "the internet" as a source.

**Also a bad log:** Logging every trivial interaction ("I asked Copilot to autocomplete a print statement"). Focus on interactions that matter.

## Common questions

**Do I need to log every autocomplete suggestion from AI?**
No. Log interactions that shaped your work - generating code blocks, drafting sections, debugging errors, exploring data. Routine autocompletions (closing brackets, finishing variable names) don't need logging.

**What if I didn't use AI for part of the assignment?**
That's fine, just note it. "I wrote the interpretation section without AI assistance because I wanted to make sure the contextual framing reflected my understanding of the data." That's valuable information.

**What if AI was wrong and I rejected its output?**
Log it. These are often the most valuable entries. "I asked Claude to identify outliers in the revenue column. It flagged 3 values as outliers based on z-scores, but after checking the business context, all 3 were legitimate high-value enterprise orders. I kept them." This shows analytical judgment.

**Can I use AI to help write the log?**
Yes, but the log needs to be accurate. If AI helps you format or organize the log, that's fine. If AI invents interactions that didn't happen, that's academic dishonesty.

**How long should it be?**
As long as it needs to be. A simple assignment might have 3-5 entries. A complex data pipeline might have 10-15. Quality over quantity - a few detailed entries are better than many vague ones.
