---
layout: default
title: 生活旅行
permalink: /categories/life-travel/
---

<div class="track-top"></div>

<div class="container">
  <div class="header">
    <h1>✈️ 生活旅行</h1>
    <p>生活记录与旅行见闻</p>
  </div>

  <nav class="nav-list">
    <a href="/" class="nav-item active">📚 返回首页</a>
    <a href="/categories/ai-tech/" class="nav-item">🤖 AI 技术</a>
    <a href="/categories/finance/" class="nav-item">💰 财经</a>
    <a href="/categories/game-log/" class="nav-item">🎮 游戏</a>
  </nav>

  <div class="article-list">
    {% if site.categories['life-travel'].size > 0 %}
      {% for post in site.categories['life-travel'] %}
        <article class="article-item" data-category="life-travel">
          <h2 class="article-title">
            {% if post.pinned %}
            <span class="pin-badge">🔥 置顶</span>
            {% endif %}
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          </h2>

          <div class="article-meta">
            <time class="article-date">📅 {{ post.date | date: '%Y-%m-%d' }}</time>
            {% if post.tag %}
            <span class="article-tag">{{ post.tag }}</span>
            {% endif %}
          </div>

          {% if post.excerpt %}
          <p class="article-excerpt">{{ post.excerpt | strip_html | truncatewords: 20 }}</p>
          {% endif %}
        </article>
      {% endfor %}
    {% else %}
    <div class="empty-state">
      <p>暂无文章</p>
    </div>
    {% endif %}
  </div>
</div>
