---
permalink: /portfolio/
title: "Portfolio"
layout: single
sidebar: false
classes: wide
---

# Portfolio

<p class="intro">A curated selection of high-complexity systems and experiments.</p>

<div class="projects-grid">
  {% assign projects = site.data.projects %}
  {% for project in projects %}
  <article class="project-card">
    <a href="{{ project.link | default: '#' }}" class="card-image-link" {% if project.link %}target="_blank" rel="noopener"{% endif %}>
      {% if project.image %}
      <img src="{{ project.image }}" alt="{{ project.title }} — architecture diagram" class="card-image">
      {% else %}
      <div class="card-image placeholder"></div>
      {% endif %}
    </a>
    <div class="card-content">
      <h2 class="card-title">
        <a href="{{ project.link | default: '#' }}" {% if project.link %}target="_blank" rel="noopener"{% endif %}>{{ project.title }}</a>
      </h2>

      <div class="card-details">
        <p class="card-description">
          {{ project.description }}
        </p>

        {% if project.technologies %}
        <div class="card-tags">
          {% for tech in project.technologies %}
          <span class="tag">{{ tech }}</span>
          {% endfor %}
        </div>
        {% endif %}

        {% if project.github %}
        <a href="{{ project.github }}" class="view-code" target="_blank" rel="noopener" aria-label="View {{ project.title }} on GitHub">
          <svg aria-hidden="true" viewBox="0 0 16 16" width="20" height="20"><path fill-rule="evenodd"
            d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 
              0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52
              0-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95
              0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09
              2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65
              3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.19 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z">
          </path></svg>
          View Code
        </a>
        {% endif %}
      </div>
    </div>
  </article>
  {% endfor %}
</div>

<style>
/* Force exactly 2 cards per row */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2rem;
  width: 100%;
  margin: 0 auto;
}

/* Card styling */
.project-card {
  display: flex;
  flex-direction: column;
  background: #fff;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  transition: transform 0.3s, box-shadow 0.3s;
}
.project-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 4px 16px rgba(0,0,0,0.15);
}

/* Image wrapper */
.card-image-link {
  display: block;
  width: 100%;
  padding-top: 56.25%;
  position: relative;
  background: #f0f0f0;
}
.card-image {
  position: absolute;
  inset: 0;
  object-fit: cover;
  width: 100%;
  height: 100%;
  transition: transform 0.5s;
}
.project-card:hover .card-image {
  transform: scale(1.05);
}

/* Content area */
.card-content {
  padding: 1.5rem;
  display: flex;
  flex-direction: column;
  color: #333;
}
.card-title {
  margin: 0 0 0.75rem;
  font-size: 1.4rem;
  font-weight: 600;
}
.card-title a {
  color: inherit;
  text-decoration: none;
}
.card-title a:hover {
  text-decoration: underline;
}

/* Clamp description to 4 lines */
.card-description {
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 4;
  overflow: hidden;
  position: relative;
  line-height: 1.5;
  margin: 0 0 0.5rem;
}

/* Expanded state */
.card-description.expanded {
  -webkit-line-clamp: unset;
}

/* Tags */
.card-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}
.tag {
  background: #ececec;
  border-radius: 999px;
  padding: 0.25em 0.75em;
  font-size: 0.85rem;
  color: #333;
}

/* View Code link */
.view-code {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.95rem;
  color: #0366d6;
  text-decoration: none;
  margin-top: auto;
}
.view-code svg {
  fill: currentColor;
}

/* Read more button */
.expand-btn {
  background: none;
  border: none;
  color: #007acc;
  cursor: pointer;
  padding: 0;
  font-size: 0.95rem;
  align-self: flex-start;
  margin-bottom: 1rem;
}
</style>

<script>
document.addEventListener("DOMContentLoaded", function() {
  document.querySelectorAll(".project-card").forEach(function(card) {
    var desc = card.querySelector(".card-description");
    if (!desc) return;

    var btn = document.createElement("button");
    btn.className = "expand-btn";
    btn.textContent = "Read more";

    btn.addEventListener("click", function() {
      var expanded = desc.classList.toggle("expanded");
      btn.textContent = expanded ? "Show less" : "Read more";
    });

    desc.insertAdjacentElement("afterend", btn);
  });
});
</script>
