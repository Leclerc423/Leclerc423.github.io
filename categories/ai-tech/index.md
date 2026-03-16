---
layout: default
title: AI 技术
category: ai-tech
---

<div class="category-page">
  <div class="category-header">
    <h1>🤖 AI 技术</h1>
  </div>

  <div class="posts-list">
    {% for post in site.categories.ai-tech %}
      <article class="post-item" data-category="ai-tech">
        <h2 class="post-title">
          {% if post.pinned %}
          <span class="pin-badge">🔥 置顶</span>
          {% endif %}
          <a href="{{ post.url }}">{{ post.title }}</a>
        </h2>

        <div class="post-meta">
          <time class="post-date">📅 {{ post.date | date: '%Y-%m-%d' }}</time>
          {% if post.tag %}
          <span class="post-tag">{{ post.tag }}</span>
          {% endif %}
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
