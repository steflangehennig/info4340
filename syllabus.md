---
layout: page
title: Syllabus
subtitle: INFO 4340 | Fall 2026
---

## Course description

INFO 4340 prepares graduate analysts to work alongside generative AI systems in applied business settings. Rather than treating AI as a black box or a magical solution, the course develops four practical competencies: understanding what LLMs are and where they fail, using GenAI in applied analytic workflows, evaluating AI outputs systematically, and governing AI in organizational contexts.

The course uses Python throughout as an analyst would. This includes cleaning data, classifying text, building evaluation pipelines, and creating reproducible work.

## Learning outcomes

By the end of the course, you will be able to:

1. Students will understand the architecture behind AI systems and LLMs, including how such systems are trained and assessed.
2. Students will be proficient in the implementation of AI systems through programming environments, including Python.
3. Students will implement analytical techniques through traditional methodologies and libraries and through AI solutions.
4. Students will assess the effectiveness of using AI tools as an alternative to traditional programming techniques and will demonstrate proficiency in determining the correctness and utility of AI models.
5. Students will assess the ethical considerations of implementing AI solutions in a business environment.


## Before the first class

Complete [Week 0]({{ site.baseurl }}/schedule/week-0/) before our first meeting. It takes about 90 minutes and covers account setup (Canvas, Google, GitHub), installing Python, VS Code, and Git, and running a setup check script whose output you submit to Canvas. It counts toward your participation grade.

Nothing in Week 0 costs money or assumes prior Python experience. If a step breaks, submit the setup check output anyway and post in the Week 0 discussion thread. Troubleshooting a broken install is a normal part of this work, and doing it before the term starts protects our class time.

## Required materials

- Békés, Gábor. [*Data Analysis with AI*](https://gabors-data-analysis.com/ai-course/) (free online)
- NIST AI Risk Management Framework (free, [nist.gov](https://www.nist.gov/itl/ai-risk-management-framework))
- LLMs Research Lab [LLMsVisual Cards](https://llmsresearch.github.io/llm-flashcards/)
- AI Incident Database ([incidentdatabase.ai](https://incidentdatabase.ai/))
- Additional readings will be posted to Canvas


## Assignments and grading

| Component | Weight |
|---|---|
| Weekly deliverables (Weeks 1-9) | 45% |
| Final project (workflow package + presentation) | 45% |
| Participation and peer review | 10% |

## Course policies

### AI use
This course is explicitly about using AI tools, therefore you are expected to use them. However, your submitted work must include an **AI use log** documenting what you prompted, what the tool produced, and what you changed or decided. See the [AI use log guide]({{ site.baseurl }}/guides/ai-use-log/) for formats and examples. Submitting AI output as your own analysis without this log is academic dishonesty.

### Python and coding
**This is not a Python programming class.** You will not be graded on code elegance, and no prior Python experience is required. You are expected to learn as you go, and using AI assistance to write code is expected rather than discouraged.

That said, you will use Python every week - cleaning data, calling APIs, computing evaluation metrics, and producing reproducible notebooks. What you are responsible for is understanding what the code does and verifying that it is right, not writing it from scratch. The [developer setup guide]({{ site.baseurl }}/guides/dev-setup/), the [Python for analysts guide]({{ site.baseurl }}/guides/python-analysts/), and my office hours are there if you need support. All final deliverables require a reproducible Python notebook.

### API access and cost
Starting in Week 1, you will make calls to a large language model API from Python. A class API key will be provided - you do not need to set up your own billing account or pay out of pocket for coursework. Use the class key for course assignments only. Because API calls cost real money per token, several assignments ask you to track and project those costs; treating cost as a design constraint is part of the course.

### Late work
Deliverables are due before class on the week listed (more information on Canvas).

