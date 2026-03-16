---
layout: default
title: Shepherd's Grid - 首页
---

<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Shepherd's Grid - {{ page.title }}</title>
  <link rel="stylesheet" href="/css/main.css">
</head>
<body>
  <div class="hud-top-line"></div>

  <!-- F1 赛道装饰 - 首页顶部 -->
  <svg class="track-bg track-bg-top" viewBox="0 0 1000 60" xmlns="http://www.w3.org/2000/svg">
    <defs>
      <linearGradient id="trackGradient" x1="0%" y1="0%" x2="100%" y2="0%">
        <stop offset="0%" style="stop-color:#e10600;stop-opacity:0.1" />
        <stop offset="50%" style="stop-color:#e10600;stop-opacity:0.3" />
        <stop offset="100%" style="stop-color:#e10600;stop-opacity:0.1" />
      </linearGradient>
    </defs>
    <path d="M50,30 C100,10 150,10 200,30 S300,50 350,30 S450,10 500,30 S600,50 650,30 S750,10 800,30 S900,50 950,30" stroke="url(#trackGradient)" stroke-width="4" fill="none" stroke-linecap="round"/>
  </svg>

  <div class="container">
    <!-- 简化标题 -->
    <div class="hero-simple">
      <h1 class="hero-title">🏁 Shepherd's Grid</h1>
      <p class="hero-subtitle">AI & 技术 · 财经学习 · 生活旅行 · 游戏日志</p>
    </div>

    <!-- 分类导航 -->
    <div class="categories-nav">
      <a href="#" class="nav-item active" data-category="all">
        <span class="nav-text">📚 全部文章</span>
      </a>
      <a href="/categories/ai-tech/" class="nav-item" data-category="ai-tech">
        <span class="nav-text">🤖 AI 技术</span>
      </a>
      <a href="/categories/finance/" class="nav-item" data-category="finance">
        <span class="nav-text">💰 财经赛道</span>
      </a>
      <a href="/categories/life-travel/" class="nav-item" data-category="life-travel">
        <span class="nav-text">✈️ 生活赛道</span>
      </a>
      <a href="/categories/game-log/" class="nav-item" data-category="game-log">
        <span class="nav-text">🎮 游戏赛道</span>
      </a>
    </div>

    <!-- 文章列表 -->
    <div class="posts-list">
      {% if site.posts.size > 0 %}
        {% for post in site.posts %}
          {% assign post_category = post.category %}
          {% unless post_category %}{% assign post_category = 'all' %}{% endunless %}

          <article class="post-item post-{{ post_category }}" data-category="{{ post_category }}">
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
        {% endfor %}

      {% else %}
      <div class="empty-grid">
        <p class="empty-text">暂无文章</p>
      </div>
      {% endif %}
    </div>
  </div>

  <script>
    document.addEventListener('DOMContentLoaded', function() {
      // 分类切换
      document.querySelectorAll('.nav-item').forEach(item => {
        item.addEventListener('click', function(e) {
          e.preventDefault();
          const category = this.dataset.category;

          // 更新导航状态
          document.querySelectorAll('.nav-item').forEach(nav => nav.classList.remove('active'));
          this.classList.add('active');

          // 切换内容区
          document.querySelectorAll('.posts-section').forEach(section => {
            if (category === 'all') {
              section.style.display = 'block';
            } else {
              section.style.display = 'none';
            }
          });
        });
      });

      // 点击卡片跳转
      document.querySelectorAll('.post-card').forEach(card => {
        card.addEventListener('click', function(e) {
          if (e.target.tagName !== 'A') {
            const link = this.querySelector('a');
            if (link) link.click();
          }
        });
      });
    });
  </script>
</body>
</html>
