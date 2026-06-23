---
layout: page
title: "Week 8: Failures, Incidents, and Risk"
subtitle: "Evaluate · AI failures are usually sociotechnical — not just technical"
permalink: /schedule/week-8/
---

<div class="note" markdown="0">
  <strong>Module:</strong> <span class="badge badge-orange">Evaluate</span> &nbsp;·&nbsp;
  <strong>Deliverable:</strong> AI incident brief (due before Week 9 Monday) &nbsp;·&nbsp;
  <a href="{{ site.baseurl }}/assignments/week-8-incident/">See assignment →</a>
</div>

## Learning objectives

1. Identify eight common AI failure modes and the sociotechnical failure chain
2. Analyze a real AI incident using a structured diagnosis worksheet
3. Compute subgroup error rates and formal disparity metrics (disparate impact ratio, equalized odds, chi-square)
4. Estimate quantitative harm at production scale (errors/month × cost per error)
5. Map failure modes to safeguards with quantitative trigger thresholds

## Sessions

<div class="session-block" markdown="0">
  <div class="session-label">Monday</div>
  <div class="session-content">
    <div class="session-title">When AI goes wrong</div>
    <p>Eight failure modes, the AI Incident Database, and an incident diagnosis workshop. Groups analyze real incidents and estimate harm quantitatively: how many affected, for how long, at what cost.</p>
    <div class="session-topics">
      <span class="topic-tag">Eight failure modes</span>
      <span class="topic-tag">AI Incident Database</span>
      <span class="topic-tag">Incident diagnosis + harm estimation</span>
    </div>
  </div>
</div>

<div class="session-block" markdown="0">
  <div class="session-label">Wednesday</div>
  <div class="session-content">
    <div class="session-title">Subgroup analysis, disparity metrics, and safeguards</div>
    <p>Using your Week 6 classification results: compute accuracy by subgroup, disparate impact ratios, equalized odds, and chi-square tests. Then project error rates to production scale with dollar-cost harm estimation. Safeguard mapping with quantitative trigger thresholds.</p>
    <div class="session-topics">
      <span class="topic-tag">Formal disparity metrics</span>
      <span class="topic-tag">Python: subgroup analysis</span>
      <span class="topic-tag">Quantitative harm estimation</span>
      <span class="topic-tag">Safeguard thresholds</span>
    </div>
  </div>
</div>

## Key concepts

| Concept | What it means |
|---|---|
| **Disparate impact ratio** | Error rate for one group divided by the reference group's rate. If > 1.25x (inverse 4/5 rule), flags potential bias. |
| **Equalized odds** | Whether the classifier has the same recall for each subgroup — equal accuracy across groups |
| **Quantitative harm estimation** | Project error rates to production volume: X errors/month × $Y cost = $Z monthly impact |
| **Safeguard threshold** | A quantitative trigger for intervention: "human review when confidence < 0.7" or "alert when subgroup error rate > 15%" |

## Deliverable

<div class="assignment-preview" markdown="0">
  <div class="assignment-preview-title">AI Incident Brief</div>
  <div class="assignment-preview-meta">~2–3 pages · 30 points · Due before class, Week 9 Monday · Submit via Canvas</div>
  <p>Analyze a real AI incident with failure chain, quantitative harm estimation, disparity analysis, and a recommended safeguard with a quantitative trigger threshold.</p>
  <a href="{{ site.baseurl }}/assignments/week-8-incident/" class="assignment-link">Full prompt and rubric →</a>
</div>

## Looking ahead

Next week: **Governing GenAI in Organizations** — translating evaluation and failure analysis into practical governance rules with quantitative risk scoring.
