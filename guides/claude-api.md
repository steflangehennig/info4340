---
layout: page
title: "Guide: Claude API for Analysts"
subtitle: "Best Practices for using Claude's API"
permalink: /guides/claude-api/
---


This guide consolidates everything you need to know about working with the Claude API in this course. You've been making API calls since Week 1 - this guide explains what's actually happening in those calls. It also gives you a workflow for reliable, cost-aware analytic work.

*Portions of this guide are adapted from Anthropic's [Building with the Claude API](https://anthropic.skilljar.com/claude-with-the-anthropic-api) course.*

## Parts of an API call

Every call to the Claude API has the same basic structure:

```python
import anthropic

client = anthropic.Anthropic(api_key=api_key)

response = client.messages.create(
    model="claude-sonnet-4-6",       # which model
    max_tokens=1000,                  # response length cap
    temperature=0,                    # randomness (0 = deterministic)
    system="You are a data analyst.", # system prompt (optional)
    messages=[                        # the conversation
        {"role": "user", "content": "Classify this feedback: ..."}
    ]
)

text = response.content[0].text       # the response text
```

### model

This is which Claude model handles the request. In this course we use `claude-sonnet-4-6` most of the time. It's a strong balance of capability, speed, and cost. Smaller models (Haiku) are faster and cheaper; larger models are more capable, but slower and more expensive. Model choice is an empirical question (see Week 2's benchmarking discussion).

### max_tokens

The maximum length of the response, in tokens. This is a cap, not a target - the model stops when it's done or when it hits the cap, whichever comes first. If your responses are getting cut off mid-sentence, raise it. If you only need a short JSON object, keep it low (100–200) to put bounds around your costs.

### temperature

Controls randomness in the response. At `temperature=0`, the model picks the most probable token every time - same prompt, (nearly) same response. At `temperature=1`, it samples more freely.

| Task | Temperature |
|---|---|
| Classification, extraction, code generation | 0 |
| Summarization | 0–0.3 |
| Brainstorming, creative work | 0.7–1.0 |

For analytic work, **default to 0**. You want reproducibility.

## System prompts vs. user messages

This is the most important distinction you haven't been formally taught yet - even though you've been using it since Week 6.

The **system prompt** sets the model's role, constraints, and standing instructions for the whole conversation. The **user message** contains the specific request or data.

```python
response = client.messages.create(
    model="claude-sonnet-4-6",
    max_tokens=200,
    temperature=0,
    system="""You are classifying customer feedback for a product team.
Categories: billing, product_quality, support, technical, pricing, onboarding.
Always return valid JSON with keys: primary_category, confidence, evidence.
Never include text outside the JSON object.""",
    messages=[
        {"role": "user", "content": "Classify: 'Charged twice for March.'"}
    ]
)
```

**Why split them?** Three reasons:

1. **Consistency.** The system prompt applies to every message in the conversation. When you're classifying 143 texts in a loop, put the task definition and output format in the system prompt and only the text in the user message - the instructions can't drift.
2. **Reliability.** Models weight system prompts heavily for behavioral instructions like output format.
3. **Cost.** With the same system prompt across a batch, your per-item user messages stay short.

Rule of thumb: **role, rules, and format go in the system prompt; data goes in the user message.**

## Multi-turn conversations

The API is stateless - it has no memory between calls. A "conversation" is just the full message history you send each time:

```python
messages = [
    {"role": "user", "content": "What data quality issues are common in order data?"},
    {"role": "assistant", "content": "Common issues include mixed date formats, ..."},
    {"role": "user", "content": "How would I detect the first one in pandas?"}
]

response = client.messages.create(
    model="claude-sonnet-4-6",
    max_tokens=500,
    messages=messages   # the whole history, every time
)
```

Each call sends the entire history. Two implications for analysts:

- **Cost grows with conversation length.** Every prior turn is re-sent (and re-billed) as input tokens.
- **You control the context.** You can edit history, drop irrelevant turns, or start fresh. This is why the helpful/adversarial pairing (Week 5) uses *separate* conversations - the adversarial reviewer shouldn't see that the plan came from the same model.

## Structured output (JSON) patterns

You've used this pattern since Week 1. Here's the reliable version:

```python
SYSTEM = """Return ONLY valid JSON, no other text, no markdown fences:
{"primary_category": "...", "confidence": "high|medium|low", "evidence": "..."}"""

def classify(text):
    response = client.messages.create(
        model="claude-sonnet-4-6",
        max_tokens=150,
        temperature=0,
        system=SYSTEM,
        messages=[{"role": "user", "content": f"Classify:\n\n{text}"}]
    )
    raw = response.content[0].text.strip()

    # Defensive parsing: strip markdown fences if present
    if raw.startswith("```"):
        raw = raw.strip("`").removeprefix("json").strip()

    try:
        return json.loads(raw)
    except json.JSONDecodeError:
        return {"primary_category": "parse_error", "confidence": "low", "evidence": raw[:100]}
```

The essentials:

- **Specify the exact JSON schema** in the system prompt, including allowed values
- **Say "ONLY valid JSON, no other text"** - otherwise you'll get preamble
- **Always wrap `json.loads()` in try/except** - parse failures happen and shouldn't crash a 143-item batch
- **Record parse errors as data** - a parse error rate is itself a quality metric (Week 7)

## XML tags for complex prompts

When a prompt contains multiple parts - instructions, data, examples - Anthropic recommends XML tags to mark the boundaries:

```python
prompt = f"""<instructions>
Summarize the key finding in one sentence, then list two caveats.
</instructions>

<data>
{df.describe().to_string()}
</data>

<example>
Finding: Revenue grew 12% quarter-over-quarter, driven by Enterprise.
Caveats: excludes returns; Q4 partially estimated.
</example>"""
```

The tags aren't magic syntax - they're just unambiguous delimiters the model recognizes well. Use them whenever the model might confuse your instructions with your data (which happens more than you'd expect when pasting CSV rows or report text).

## Error handling and retries

API calls fail: rate limits, timeouts, transient errors. In a batch job, one failure shouldn't kill the run. The pattern:

```python
import time

def call_with_retry(prompt, max_retries=3):
    for attempt in range(max_retries):
        try:
            response = client.messages.create(
                model="claude-sonnet-4-6",
                max_tokens=200,
                temperature=0,
                messages=[{"role": "user", "content": prompt}]
            )
            return response
        except anthropic.RateLimitError:
            wait = 2 ** attempt          # exponential backoff: 1s, 2s, 4s
            time.sleep(wait)
        except anthropic.APIError as e:
            if attempt == max_retries - 1:
                raise
            time.sleep(1)
    raise RuntimeError("Max retries exceeded")
```

For course-sized batches (30–150 items), a simple try/except that logs failures and continues is usually enough. For production scale, exponential backoff is standard.

## Batch processing pattern

The canonical loop you've used since Week 1, with everything above assembled:

```python
results = []
for i, (_, row) in enumerate(df.iterrows()):
    try:
        parsed = classify(row["text"])          # includes retry + defensive parsing
        parsed["feedback_id"] = row["feedback_id"]
        parsed["error"] = None
    except Exception as e:
        parsed = {"feedback_id": row["feedback_id"], "error": str(e)}
    results.append(parsed)

    if (i + 1) % 25 == 0:
        print(f"Processed {i+1}/{len(df)}")

results_df = pd.DataFrame(results)
print(f"Done. Errors: {results_df['error'].notna().sum()}")
```

Habits that matter at scale:

- **Save intermediate results** (`results_df.to_csv("checkpoint.csv")`) every 50 items - a crash at item 140 of 143 shouldn't cost you the whole run
- **Log progress** so you know the loop is alive
- **Track errors as rows, not crashes** - analyze them afterward

## Tracking tokens and cost

Every response reports its token usage - use it:

```python
response.usage.input_tokens     # tokens you sent
response.usage.output_tokens    # tokens the model generated
```

Cost calculation (Sonnet pricing as used in this course):

```python
INPUT_RATE = 3.00 / 1_000_000    # $ per input token
OUTPUT_RATE = 15.00 / 1_000_000  # $ per output token

cost = (response.usage.input_tokens * INPUT_RATE +
        response.usage.output_tokens * OUTPUT_RATE)
```

You did this formally in Week 6's cost analysis. The habit to build: **track actuals, then project.** "This 143-text batch cost $0.11, so 100,000 texts ≈ $77" is an analyst's answer; "the API is cheap" is not.

Cost-control levers, in order of impact:

1. **Shorter prompts** - the system prompt is re-sent with every batch item
2. **Lower max_tokens** - caps worst-case output cost
3. **Smaller model** - if a cheaper model passes your eval suite (Week 7), use it
4. **Fewer calls** - batch related questions into one request where quality allows

## API keys and security

- **Never hardcode keys** in notebooks or scripts
- **Never commit keys to git** - add `.env` to your `.gitignore` (see the [Git guide]({{ site.baseurl }}/guides/git-github/))
- In Colab: use Secrets (`userdata.get("ANTHROPIC_API_KEY")`)
- Locally: use environment variables (`os.environ.get("ANTHROPIC_API_KEY")`)

If a key leaks, rotate it (delete and create a new one in the console). Course keys have low limits, but the habit matters - in professional settings a leaked key is a security incident.

## Quick reference

| I want to... | Do this |
|---|---|
| Consistent behavior across a batch | Put role/rules/format in `system`, data in the user message |
| Deterministic output | `temperature=0` |
| Reliable JSON | Exact schema in system prompt + "ONLY valid JSON" + try/except parse |
| Separate instructions from data | XML tags: `<instructions>`, `<data>` |
| Survive rate limits | Retry with exponential backoff |
| Not lose a long batch run | Checkpoint every 50 items |
| Know what this costs | `response.usage` × published rates, then project |
| Keep keys safe | Colab Secrets or env vars; never in git |

## Where this shows up in the course

- **Week 1:** batch loop, JSON parsing, temperature
- **Week 2:** benchmarking with `response.usage` for time/token/cost measurement
- **Week 5:** separate conversations for helpful/adversarial roles (context control)
- **Week 6:** system prompts for classification, cost analysis at scale
- **Week 7:** LLM-as-judge with structured scoring output
- **Final project:** all of the above in one reproducible pipeline
