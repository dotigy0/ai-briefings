---
layout: default
title: Dongwan's AI Briefings
---

<h1>☀️ Morning Briefings</h1>
<ul>
  {% for post in site.categories.briefing %}
    <li>
      {{ post.date | date: "%Y-%m-%d" }} —
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

<h1>🧠 Research</h1>
<ul>
  {% for post in site.categories.research %}
    <li>
      {{ post.date | date: "%Y-%m-%d" }} —
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>

<h1>📅 Weekly Briefings</h1>
<ul>
  {% for post in site.categories.weekly %}
    <li>
      {{ post.date | date: "%Y-%m-%d" }} —
      <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
