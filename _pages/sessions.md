---
layout: page
title: sessions
permalink: /sessions/
description: Sessions conducted by Pie and AI Kathmandu
nav: true
nav_order: 3
display_categories: [ambassador, work, fun]
horizontal: false
---

<!-- pages/sessions.md -->
<div class="sessions">
{% if site.enable_session_categories and page.display_categories %}
  <!-- Display categorized sessions -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_sessions = site.sessions | where: "category", category %}
  {% assign sorted_sessions = categorized_sessions | sort: "importance" %}
  <!-- Generate cards for each session -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for session in sorted_sessions %}
      {% include sessions_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for session in sorted_sessions %}
      {% include sessions.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display sessions without categories -->

{% assign sorted_sessions = site.sessions | sort: "importance" %}

  <!-- Generate cards for each session -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for session in sorted_sessions %}
      {% include sessions_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for session in sorted_sessions %}
      {% include sessions.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
