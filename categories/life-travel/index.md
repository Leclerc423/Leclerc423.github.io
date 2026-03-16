---
layout: default
title: 生活赛道
category: life-travel
---

<div class="category-page">
  <div class="category-header">
    <h1>✈️ 生活赛道</h1>
  </div>

  <div class="posts-list">
    {% for post in site.categories.life-travel %}
      <article class="post-item" data-category="life-travel">
        <h2 class="post-title">
          {% if post.pinned %}
          <span class="pin-badge">🔥 置顶</span>
          {% endif %}
          <a href="{{ post.url }}">{{ post.title }}</a>
        </h2>

        <div class="post-meta">
          <time class="post-date">📅 {{ post.date | date: '%Y-%m-%d' }}</time>
        </div>

        {% if post.excerpt %}
        <p class="post-excerpt">{{ post.excerpt }}</p>
        {% endif %}

        <a href="{{ post.url }}" class="post-link">查看详情 →</a>
      </article>
    {% else %}
    <div class="empty-grid">
      <p class="empty-text">暂无文章</p>
    </div>
    {% endfor %}
  </div>

  <a href="/" class="back-link">⬅️ 返回首页</a>
</div>
