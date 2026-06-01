---
layout: page
permalink: /repositories/
title: Repositories
description: Most of my research has code open-sourced at <a href='https://github.com/'>GitHub</a>.
nav: true
nav_order: 4
---

<style>
  .repository-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 1rem;
    margin-top: 1.25rem;
  }

  .repository-card {
    display: flex;
    flex-direction: column;
    gap: 0.75rem;
    min-height: 210px;
    padding: 1rem;
    border: 1px solid var(--global-divider-color);
    border-radius: 8px;
    background: var(--global-card-bg-color);
  }

  .repository-card-header {
    display: flex;
    align-items: flex-start;
    justify-content: space-between;
    gap: 0.75rem;
  }

  .repository-title {
    display: inline-flex;
    align-items: center;
    gap: 0.45rem;
    font-weight: 600;
    line-height: 1.25;
  }

  .repository-owner {
    margin: -0.35rem 0 0;
    color: var(--global-text-color-light);
    font-size: 0.9rem;
  }

  .repository-description {
    flex: 1;
    margin: 0;
  }

  .repository-meta,
  .repository-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 0.45rem;
  }

  .repository-pill {
    display: inline-flex;
    align-items: center;
    gap: 0.35rem;
    padding: 0.18rem 0.5rem;
    border: 1px solid var(--global-divider-color);
    border-radius: 999px;
    color: var(--global-text-color-light);
    font-size: 0.82rem;
    line-height: 1.35;
  }

  .repository-language {
    flex: 0 0 auto;
    color: var(--global-theme-color);
    font-size: 0.85rem;
    font-weight: 600;
  }
</style>

<div class="repository-grid">
  {% for repo in site.data.repositories.featured_repos %}
    <article class="repository-card">
      <div class="repository-card-header">
        <div>
          <a class="repository-title" href="{{ repo.url }}" target="_blank" rel="noopener noreferrer">
            <i class="fa-brands fa-github"></i>
            {{ repo.name }}
          </a>
          <p class="repository-owner">{{ repo.owner }}</p>
        </div>
        {% if repo.language %}
          <span class="repository-language">{{ repo.language }}</span>
        {% endif %}
      </div>

      <p class="repository-description">{{ repo.description }}</p>

      <div class="repository-meta">
        {% if repo.venue %}
          <span class="repository-pill"><i class="fa-regular fa-calendar"></i>{{ repo.venue }}</span>
        {% endif %}
      </div>

      {% if repo.tags %}
        <div class="repository-tags">
          {% for tag in repo.tags %}
            <span class="repository-pill">{{ tag }}</span>
          {% endfor %}
        </div>
      {% endif %}
    </article>
  {% endfor %}
</div>
