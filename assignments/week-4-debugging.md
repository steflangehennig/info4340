---
layout: page
title: "Week 4: Debugging and Review Log"
subtitle: "3 components | Due before class, Week 5 Monday | Submit via Canvas"
permalink: /assignments/week-4-debugging/
---

## Assignment

Find bugs in AI-generated code, quantify their impact, build an automated test suite, and review a classmate's work.

### Component 1: Bug report with quantitative impact

For each bug: what's wrong, which test habit caught it, the fix, and the exact numerical impact (dollar difference, percentage error, whether key metrics like top segment or growth rates change). Present as a comparison table.

### Component 2: Fixed script with automated test suite

Corrected code with a `run_validation(df_raw, df_clean, delivered)` function containing 8+ checks that produce a pass/fail DataFrame report. The suite must pass on your fixed data.

### Component 3: Peer review (manual + automated)

Review a classmate's Week 3 notebook using both the manual checklist and your automated test suite. Report what each method caught and what would fix the issues.

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
