---
layout: page
title: "Week 4: Debugging and Review Log"
subtitle: "3 components | Due before Week 5's first class | Submit via Canvas"
permalink: /assignments/week-4-debugging/
---

## Assignment

Find bugs in AI-generated code, quantify their impact, build an automated test suite, and review a classmate's work.

### Components 1-2: Bug report and fixed script

Submit as a single Jupyter notebook (`.ipynb`) with rendered `.html` that runs top to bottom without errors.

1. **Bug report** - as a markdown table at the top of the notebook, columns: bug description, which test habit caught it, the fix, and the exact numerical impact (dollar difference, percentage error, whether key metrics like top segment or growth rates change)
2. **Fixed script with automated test suite** - your corrected code, followed by a `run_validation(df_raw, df_clean, delivered)` function containing 8+ checks that produce a pass/fail DataFrame report. The suite must pass when run on your fixed data.

### Component 3: Peer review (manual + automated)

Submit as a short PDF (1 page is enough). Review a classmate's Week 3 notebook using both a manual checklist and the automated test suite you built in Component 2. Include the pass/fail output from running your test suite on their notebook, and report what each method caught that the other missed.

## Rubric

| Criterion | Excellent (5) | Adequate (3) | Needs revision (1) |
|---|---|---|---|
| Bug identification | 5+ bugs with clear descriptions | 3-4 bugs | Fewer than 3 |
| Quantitative impact | Dollar and % impact for each bug with comparison table | Some impact but incomplete | No quantitative impact |
| Test suite quality | 8+ checks, reusable function, passes on fixed data | Some checks but not structured | No test suite |
| Fix quality | All fixed, code runs with test suite passing | Most fixed | Incomplete |
| Peer review | Both manual and automated with specific findings | One method only | Missing |
| Consequence analysis | Impact contextualized for decisions | Some consequences | No discussion |

**Total: 30 points**
