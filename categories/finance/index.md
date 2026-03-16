---
layout: default
title: 财经
permalink: /categories/finance/
---

<div class="track-top"></div>

<div class="container">
  <div class="header">
    <h1>💰 财经</h1>
    <p>财经学习与市场分析</p>
  </div>

  <nav class="nav-list">
    <a href="/" class="nav-item active">📚 返回首页</a>
    <a href="/categories/ai-tech/" class="nav-item">🤖 AI 技术</a>
    <a href="/categories/life-travel/" class="nav-item">✈️ 生活</a>
    <a href="/categories/game-log/" class="nav-item">🎮 游戏</a>
  </nav>

  <div class="article-list">
    {% if site.categories['finance'].size > 0 %}
      {% for post in site.categories['finance'] %}
        <article class="article-item" data-category="finance">
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
