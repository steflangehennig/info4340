---
layout: page
title: "Week 2: Tool Setup and Benchmarking Report"
subtitle: "~2 pages + code | Due before class, Week 3 Monday | Submit via Canvas"
permalink: /assignments/week-2-comparison/
---

## Assignment

Set up your development environment and run a systematic benchmarking experiment. Model and tool selection should be based on measured performance, not impressions.

### Part 1: Setup confirmation

Confirm your tools are working: VS Code, Python, at least one AI coding tool, and API access. Include screenshots or descriptions. Note any unresolved issues.

### Part 2: Benchmarking experiment

Run the systematic benchmarking experiment (5+ prompts × 2+ configurations). Report:

| Metric | What to report |
|---|---|
| Response time | Mean and standard deviation (seconds per call) |
| Token usage | Mean input, output, and total tokens per configuration |
| Cost projection | Estimated cost per 1,000 calls based on actual usage |
| Quality score | Mean score on each rubric dimension and overall |

Include the raw results table, not just aggregates.

### Part 3: Quantitative recommendation

Write a 3–5 sentence recommendation citing specific numbers: quality scores, response times, cost differences, and which configuration you'd choose for different task types.

### Part 4: Reflection

Did quantitative results match your qualitative impressions? What would a rigorous production evaluation require beyond this 5-prompt experiment?

### Part 5: AI use log

## Rubric

| Criterion | Excellent (5) | Adequate (3) | Needs revision (1) |
|---|---|---|---|
| Setup confirmation | All tools working with evidence | Most working | Incomplete |
| Benchmarking execution | 5+ prompts × 2+ configs, complete metrics | Benchmark run but metrics missing | Incomplete |
| Quality scoring | All outputs scored with justifications | Scores present but thin | No quality scoring |
| Recommendation | Data-driven with specific numbers and task nuance | Present but vague | Purely qualitative |
| Reflection | Connects data to impressions, identifies limitations | Some reflection | No reflection |

**Total: 25 points**
