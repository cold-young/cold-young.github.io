---
layout: page
title: extras
permalink: /extras/
description: extras
nav: true
nav_order: 4
horizontal: false
---

<!-- pages/extras.md -->
<div class="extras">
{% if site.enable_extra_categories and page.display_categories %}
  <!-- Display categorized extras -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_extras = site.extras | where: "category", category %}
  {% assign sorted_extras = categorized_extras | sort: "importance" %}
  <!-- Generate cards for each extra -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-2">
    {% for extra in sorted_extras %}
      {% include extras_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-2">
    {% for extra in sorted_extras %}
      {% include extras.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display extras without categories -->

{% assign sorted_extras = site.extras | sort: "**importance**" %}

  <!-- Generate cards for each extra -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-2">
    {% for extra in sorted_extras %}
      {% include extras_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="container">
    {% for extra in sorted_extras %}
      {% include extras.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
