---
layout: default
title: 游戏日志
category: game-log
---

<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>{{ page.title }}</title>
  <link rel="stylesheet" href="/css/main.css">
</head>
<body>
  <div class="track-top"></div>

  <div class="container">
    <div class="header">
      <h1>🎮 游戏日志</h1>
      <p>游戏评测、通关心得、游戏体验</p>
    </div>

    <nav class="nav-list">
      <a href="/" class="nav-item active">📚 返回首页</a>
      <a href="/categories/ai-tech/" class="nav-item">🤖 AI 技术</a>
      <a href="/categories/finance/" class="nav-item">💰 财经</a>
      <a href="/categories/life-travel/" class="nav-item">✈️ 生活</a>
    </nav>

    <div class="article-list">
      {% if site.categories.game-log.size > 0 %}
        {% for post in site.categories.game-log %}
          <article class="article-item" data-category="game-log">
            <h2 class="article-title">
              {% if post.pinned %}
              <span class="pin-badge">🔥 置顶</span>
              {% endif %}
              <a href="{{ post.url }}">{{ post.title }}</a>
            </h2>

            <div class="article-meta">
              <time class="article-date">📅 {{ post.date | date: '%Y-%m-%d' }}</time>
            </div>

            {% if post.excerpt %}
            <p class="article-excerpt">{{ post.excerpt }}</p>
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
</body>
</html>
