---
layout: page
permalink: /papers/
title: Papers
nav: true
nav_order: 1
---
<!-- List comes from _data/scholar.yml, refreshed from Google Scholar by bin/update_scholar.py -->

<div class="scholar-papers about-text">
  <p class="scholar-source">
    Imported from <a href="https://scholar.google.com/citations?user={{ site.scholar_userid }}">Google Scholar</a>.
  </p>

  <ol class="scholar-list">
    {%- for paper in site.data.scholar.papers %}
    <li>
      <div class="scholar-title"><a href="{{ paper.url }}">{{ paper.title }}</a></div>
      <div class="scholar-authors">{{ paper.authors | replace: "CT Ye", "<strong>CT Ye</strong>" }}</div>
      {%- if paper.venue != "" %}
      <div class="scholar-venue"><em>{{ paper.venue }}</em></div>
      {%- endif %}
      {%- if paper.citations > 0 %}
      <div class="scholar-cites">Cited by {{ paper.citations }}</div>
      {%- endif %}
    </li>
    {%- endfor %}
  </ol>
</div>

<style>
.scholar-source { color: var(--global-text-color-light); font-size: 0.95rem; }
.scholar-list { list-style: decimal; padding-left: 1.5rem; margin-top: 1.5rem; }
.scholar-list li { margin-bottom: 1.25rem; padding-left: 0.25rem; }
.scholar-title { font-weight: 500; }
.scholar-cites { font-size: 0.9rem; color: var(--global-text-color-light); }
</style>
