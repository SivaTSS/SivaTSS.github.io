---
permalink: /portfolio/
title: "Portfolio"
toc: 
toc_label: "Table of Contents"
toc_icon: "bookmark"
---

# Portfolio

<p class="intro">A selection of my recent projects. Click on any card to learn more.</p>

<div class="projects-grid">

  {% assign projects = site.data.projects | slice: 0, 8 %}
  {% for project in projects %}
  <a href="{{ project.link | default: '#' }}" class="project-card"{% if project.link %} target="_blank" rel="noopener"{% endif %}>
    <div class="card-image-wrapper">
      {% if project.image %}
      <img src="{{ project.image }}" alt="{{ project.title }} screenshot" class="card-image">
      {% else %}
      <div class="card-image placeholder"></div>
      {% endif %}
    </div>
    <div class="card-content">
      <h2 class="card-title">{{ project.title }}</h2>
      <p class="card-description">{{ project.description }}</p>
      {% if project.technologies %}
      <p class="card-tech"><strong>Tech:</strong> {{ project.technologies | join: ", " }}</p>
      {% endif %}
    </div>
  </a>
  {% endfor %}

</div>

<!-- Optional: add pagination if you have more than 8 -->
{% if site.data.projects.size > 8 %}
<nav class="portfolio-pagination">
  <a href="/portfolio/page2/" class="button">Next Projects →</a>
</nav>
{% endif %}

<style>
/* Intro text */
.intro {
  margin: 0 0 1rem;
  color: var(--color-text-secondary);
  font-size: 1.1rem;
  text-align: center;
}

/* Grid */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 1.5rem;
  margin-top: 1.5rem;
}

/* Card */
.project-card {
  background: var(--color-bg-secondary);
  border-radius: var(--border-radius);
  overflow: hidden;
  box-shadow: var(--shadow-small);
  text-decoration: none;
  color: inherit;
  display: flex;
  flex-direction: column;
  transition: transform .2s, box-shadow .2s;
}
.project-card:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-medium);
}

/* Image wrapper for consistent aspect ratio */
.card-image-wrapper {
  width: 100%;
  padding-top: 56.25%; /* 16:9 aspect */
  position: relative;
  background: var(--color-bg-tertiary);
}
.card-image {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  object-fit: cover;
  transition: transform .3s;
}
.project-card:hover .card-image {
  transform: scale(1.05);
}
/* Placeholder if no image */
.card-image.placeholder {
  position: absolute;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: var(--color-bg-tertiary);
}

/* Content */
.card-content {
  padding: 1rem 1.25rem;
  flex: 1;
  display: flex;
  flex-direction: column;
}
.card-title {
  margin: 0 0 .5rem;
  font-size: 1.25rem;
}
.card-description {
  flex: 1;
  margin: 0 0 .75rem;
  color: var(--color-text-secondary);
  line-height: 1.4;
}
.card-tech {
  margin: 0;
  font-size: .9rem;
  color: var(--color-text-secondary);
}

/* Pagination */
.portfolio-pagination {
  text-align: center;
  margin: 2rem 0;
}
.portfolio-pagination .button {
  display: inline-block;
  padding: .6rem 1.2rem;
  border-radius: var(--border-radius-small);
  background-color: var(--color-accent);
  color: #fff;
  text-decoration: none;
  transition: background .2s;
}
.portfolio-pagination .button:hover {
  background-color: var(--color-accent-hover);
}
</style>
