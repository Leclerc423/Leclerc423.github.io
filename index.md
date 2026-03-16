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
    <!-- Hero 区域 - 发车格风格 -->
    <div class="hero-grid">
      <!-- 发车格背景 -->
      <div class="grid-bg">
        <svg class="grid-lines" viewBox="0 0 400 200" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <pattern id="gridPattern" width="40" height="40" patternUnits="userSpaceOnUse">
              <line x1="20" y1="0" x2="20" y2="200" stroke="#e10600" stroke-width="1" opacity="0.3"/>
              <line x1="0" y1="100" x2="400" y2="100" stroke="#e10600" stroke-width="1" opacity="0.3"/>
            </pattern>
          </defs>
          <rect width="400" height="200" fill="url(#gridPattern)"/>
        </svg>
      </div>

      <div class="hero-content">
        <h1 class="hero-title">
          <span class="grid-number">1</span>
          Shepherd's Grid
        </h1>
        <p class="hero-subtitle">AI & 技术 · 财经学习 · 生活旅行 · 游戏日志</p>
      </div>
    </div>

    <!-- 赛道分隔线 -->
    <div class="track-divider">
      <svg viewBox="0 0 20 4" xmlns="http://www.w3.org/2000/svg">
        <path d="M0,2 L20,2" stroke="#e10600" stroke-width="2" stroke-linecap="round"/>
      </svg>
    </div>

    <!-- 分类导航 - 赛车发车格风格 -->
    <div class="categories-nav">
      {% for post in site.posts limit:5 %}
        {% assign post_category = post.category %}
        {% unless post_category %}{% assign post_category = 'all' %}{% endunless %}
      {% endfor %}

      <a href="#" class="nav-item active" data-category="all">
        <span class="nav-icon">🏁</span>
        <span class="nav-text">全部发车</span>
      </a>
      <a href="/categories/ai-tech/" class="nav-item" data-category="ai-tech">
        <span class="nav-icon">🤖</span>
        <span class="nav-text">AI 技术</span>
      </a>
      <a href="/categories/finance/" class="nav-item" data-category="finance">
        <span class="nav-icon">🏁</span>
        <span class="nav-text">财经赛道</span>
      </a>
      <a href="/categories/life-travel/" class="nav-item" data-category="life-travel">
        <span class="nav-icon">🏁</span>
        <span class="nav-text">生活赛道</span>
      </a>
      <a href="/categories/game-log/" class="nav-item" data-category="game-log">
        <span class="nav-icon">🏁</span>
        <span class="nav-text">游戏赛道</span>
      </a>
    </div>

    <!-- 文章内容区 -->
    <div class="content-wrapper">
      {% if site.posts.size > 0 %}
        <div class="posts-section" id="section-all">
          <div class="section-header">
            <h2>🏁 发车格 · 全部文章</h2>
            <div class="section-count">{{ site.posts.size }} 辆赛车</div>
          </div>

          <div class="posts-grid">
            {% for post in site.posts %}
              {% assign post_category = post.category %}
              {% unless post_category %}{% assign post_category = 'all' %}{% endunless %}

              <div class="post-card post-{{ post_category }}" data-category="{{ post_category }}">
                <div class="card-content">
                  <h3 class="post-title">
                    {% if post.pinned %}
                    <span class="pin-badge">🔥 置顶</span>
                    {% endif %}
                    <a href="{{ post.url }}">{{ post.title }}</a>
                  </h3>

                  <div class="post-meta">
                    <time class="post-date">
                      📅 {{ post.date | date: '%Y-%m-%d' }}
                    </time>
                    {% if post.tag %}
                    <span class="post-tag">{{ post.tag }}</span>
                    {% endif %}
                  </div>

                  {% if post.excerpt %}
                  <p class="post-excerpt">{{ post.excerpt }}</p>
                  {% endif %}

                  <a href="{{ post.url }}" class="card-link">查看详情 →</a>
                </div>
              </div>
            {% endfor %}
          </div>
        </div>

        {% else %}
        <div class="empty-grid">
          <svg class="empty-track" viewBox="0 0 120 60" xmlns="http://www.w3.org/2000/svg">
            <path d="M10,30 Q30,10 50,30 T90,30 T110,30" stroke="#e10600" stroke-width="2" fill="none" opacity="0.3"/>
            <circle cx="60" cy="30" r="8" fill="#e10600" opacity="0.4"/>
          </svg>
          <p class="empty-text">赛道待发车 · 暂无文章</p>
        </div>
        {% endif %}
    </div>
  </div>

  <!-- 赛道分隔线 -->
  <div class="track-divider-bottom">
    <svg viewBox="0 0 20 4" xmlns="http://www.w3.org/2000/svg">
      <path d="M0,2 L20,2" stroke="#e10600" stroke-width="2" stroke-linecap="round"/>
    </svg>
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
