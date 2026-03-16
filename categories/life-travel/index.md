---
layout: default
title: 生活旅行
category: life-travel
---

<div class="category-page">
  <div class="category-header">
    <h1>✈️ 生活旅行</h1>
    <p>城市漫步、生活随笔、旅行记录与感悟</p>
  </div>

  <div class="posts-list">
    {% for post in site.categories.life-travel %}
    <article class="post-item" data-category="life-travel">
      <div class="post-header">
        <h3 class="post-title">
          {% if post.pinned %}
          <span class="pin-badge">📌 置顶</span>
          {% endif %}
          <a href="{{ post.url }}">{{ post.title }}</a>
        </h3>
        <div class="post-meta">
          <time class="post-date" datetime="{{ post.date | date: '%Y-%m-%d' }}">
            {{ post.date | date: '%Y-%m-%d' }}
          </time>
        </div>
      </div>
      {% if post.excerpt %}
      <div class="post-excerpt">{{ post.excerpt }}</div>
      {% endif %}
    </article>
    {% else %}
    <div class="empty-state">
      <p>暂无文章 · 暂无内容</p>
    </div>
    {% endfor %}
  </div>
</div>
