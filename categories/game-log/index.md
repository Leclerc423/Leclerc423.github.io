---
layout: default
title: 游戏日志
category: game-log
---

<div class="category-page">
  <div class="category-header">
    <h1>🎮 游戏日志</h1>
    <p>游戏评测、通关心得、体验分享</p>
  </div>

  <div class="posts-list">
    {% for post in site.categories.game-log %}
    <article class="post-item" data-category="game-log">
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
