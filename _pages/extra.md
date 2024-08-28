---
layout: page
title: extras
permalink: /extras/
description: 
nav: true
nav_order: 4
horizontal: false
display_categories: [study, teach, fun, personal]
enable_category_badges: true
---

<!-- pages/extras.md -->
<div class="extras">
  {% if page.display_categories and page.enable_category_badges %}
    <!-- Category Filter badges -->
    <div class="project-filter mb-4">
      <span class="badge badge-pill badge-filter active filter-badge" data-filter="all">All</span>
      {% for category in page.display_categories %}
        <span class="badge badge-pill badge-filter filter-badge" data-filter="{{ category }}">{{ category | capitalize }}</span>
      {% endfor %}
    </div>
  {% endif %}

  {% if page.display_categories %}
    <!-- Display categorized extras -->
    {% for category in page.display_categories %}
      {% assign categorized_extras = site.extras | where: "category", category %}
      {% assign sorted_extras = categorized_extras | sort: "importance" %}

      <div class="project-item" data-category="{{ category }}">
        {% if page.horizontal %}
          <div class="container">
            <div class="row">
            {% for extra in sorted_extras %}
              {% include extras_horizontal.liquid %}
            {% endfor %}
            </div>
          </div>
        {% else %}
          <div class="container">
            <div class="row">
            {% for extra in sorted_extras %}
              <div class="col-md-12 mb-4">
                {% include extras.liquid %}
              </div>
            {% endfor %}
            </div>
          </div>
        {% endif %}
      </div>

    {% endfor %}

  {% else %}

    <!-- Display extras without categories -->
    {% assign sorted_extras = site.extras | sort: "importance" %}

    {% if page.horizontal %}
      <div class="container">
        <div class="row">
        {% for extra in sorted_extras %}
          {% include extras_horizontal.liquid %}
        {% endfor %}
        </div>
      </div>
    {% else %}
      <div class="container">
        <div class="row">
        {% for extra in sorted_extras %}
          <div class="col-md-12 mb-4">
            {% include extras.liquid %}
          </div>
        {% endfor %}
        </div>
      </div>
    {% endif %}
  {% endif %}
</div>

<script>
  document.addEventListener("DOMContentLoaded", function () {
    const filterBadges = document.querySelectorAll(".filter-badge");
    const projectItems = document.querySelectorAll(".project-item");

    // Initialize badge styles and active states
    function initializeBadges() {
      filterBadges.forEach((badge) => {
        badge.style.backgroundColor = "var(--global-theme-color)";
        badge.style.color = "var(--global-card-bg-color)";
        badge.style.cursor = "pointer";  // Make badges clickable
      });
    }

    // Initialize badge styles
    initializeBadges();

    filterBadges.forEach((badge) => {
      badge.addEventListener("click", () => {
        // Remove 'active' class from all badges
        filterBadges.forEach((b) => {
          b.classList.remove("active");
          b.style.backgroundColor = "var(--global-theme-color)";
          b.style.color = "var(--global-card-bg-color)";  // Reset to default
        });

        // Add 'active' class to clicked badge
        badge.classList.add("active");

        const filter = badge.getAttribute("data-filter");

        // Change color of the clicked badge
        badge.style.backgroundColor = "var(--global-card-bg-color)";
        badge.style.color = "var(--global-theme-color)";  // Change text color to theme color

        // Filter project items
        projectItems.forEach((item) => {
          item.style.display = "none";
        });

        if (filter === "all") {
          projectItems.forEach((item) => {
            item.style.display = "block";
          });
        } else {
          projectItems.forEach((item) => {
            if (item.getAttribute("data-category") === filter) {
              item.style.display = "block";
            }
          });
        }
      });
    });
  });
</script>