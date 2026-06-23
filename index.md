---
layout: default
---

<div class="home-hero">
  <div class="home-hero-inner">
    <h1 class="home-title">INFO 4340: Analytics and AI</h1>
    <p class="home-desc">A graduate course on using, evaluating, and governing AI tools in applied professional settings.</p>
    <div class="home-meta">
      <span class="meta-pill">{{ site.term }}</span>
      <span class="meta-pill">{{ site.meeting }}</span>
    </div>
  </div>
</div>

<div class="home-grid">
  <div class="home-main">
    <div class="section-label">Course materials</div>
    <div class="card-grid">
      <a href="{{ site.baseurl }}/syllabus/" class="nav-card">
        <div class="nav-card-title">Syllabus</div>
        <div class="nav-card-desc">Course overview, policies, & learning outcomes</div>
      </a>
      <a href="{{ site.baseurl }}/schedule/" class="nav-card">
        <div class="nav-card-title">Schedule</div>
        <div class="nav-card-desc">Quarter-based schedule with topics & deliverables</div>
      </a>
      <a href="{{ site.baseurl }}/guides/" class="nav-card">
        <div class="nav-card-title">Guides</div>
        <div class="nav-card-desc">Setup, tools, & technical references</div>
      </a>
      <a href="{{ site.baseurl }}/assignments/" class="nav-card">
        <div class="nav-card-title">Assignments</div>
        <div class="nav-card-desc">Deliverables, rubrics, & submission info</div>
      </a>
    </div>

    <div class="section-label">About this course</div>
    <p style="font-size:14px; color:var(--muted); line-height:1.7;">
      INFO 4340 is organized around four competencies: <strong>understand</strong> what LLMs are and where they fail; <strong>use</strong> GenAI in applied workflows; <strong>evaluate</strong> AI outputs systematically; and <strong>govern</strong> AI in organizational settings. Students complete a final applied project integrating all four elements.
    </p>
  </div>

  <div class="home-sidebar">
    <div class="sidebar-card">
      <div class="sidebar-card-head">Contact</div>
      <div class="sidebar-card-body">
        <p><strong>Instructor</strong><br>{{ site.instructor }}</p>
        <p><strong>Email</strong><br><a href="mailto:{{ site.contact }}">{{ site.contact }}</a></p>
        <p><strong>Office hours</strong><br>{{ site.office_hours }}</p>
      </div>
    </div>
  </div>
</div>
