---
layout: default
title: 财经学习
category: finance
---

<div class="category-page">
  <div class="category-header">
    <h1>💰 财经学习</h1>
    <p>股市分析、投资理财、经济策略与心得</p>
  </div>

  <div class="posts-list">
    {% for post in site.categories.finance %}
    <article class="post-item" data-category="finance">
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
