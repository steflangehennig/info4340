---
layout: page
title: "Week 4: Debugging and Review Log"
subtitle: "3 components · Due before class, Week 5 Monday · Submit via Canvas"
permalink: /assignments/week-4-debugging/
---

## Assignment

Document bugs found in AI-generated code, fix them with verification checks, and review a classmate's work.

### Component 1: Bug report

For each bug you found in the AI-generated analysis script, document:

1. **What's wrong** — describe the bug in plain language
2. **What check caught it** — which test habit (row-count, data-description, or code/unit check) revealed the issue?
3. **The fix** — what code change corrects the bug?
4. **The consequence** — what would happen if this error reached a stakeholder?

The script has 6 planted bugs. Document as many as you found.

### Component 2: Fixed script with verification checks

Submit a corrected version of the analysis script that fixes all identified bugs, includes assertions after each major step, includes comments explaining why each assertion is there, and runs end-to-end without assertion failures.

### Component 3: Peer review feedback

Submit your structured review of a classmate's Week 3 notebook, covering: does the code run, are row counts checked, are categories standardized, are missing values handled explicitly, does the report answer the stated question, can you verify a number from the report against the code, and is there an AI use log.

For each issue found, note what's wrong and what would fix it. Also note one thing the code does well.

## Format

- Bug report: table or narrative, 1–2 pages
- Fixed script: `.py` file or notebook that runs cleanly
- Peer review: 0.5–1 page using the checklist
- Include an AI use log

## Rubric

| Criterion | Excellent (5) | Adequate (3) | Needs revision (1) |
|---|---|---|---|
| Bug identification | 5+ bugs found with clear descriptions | 3–4 bugs found | Fewer than 3 or vague descriptions |
| Check attribution | Each bug linked to a specific test habit | Some test habits mentioned | No connection between checks and bugs |
| Fix quality | All bugs fixed, code runs cleanly | Most fixed but minor issues | Fixes incomplete or code doesn't run |
| Assertions | Meaningful assertions after each step with comments | Some assertions but incomplete | No assertions or trivial only |
| Consequence analysis | Specific, realistic downstream effects | Some consequences but generic | No consequence discussion |
| Peer review | Thorough checklist-based review with constructive feedback | Present but incomplete | Missing or perfunctory |

**Total: 30 points**
