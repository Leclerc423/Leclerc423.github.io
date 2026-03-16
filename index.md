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
  <div class="container">
    <div class="hero">
      <h1>Shepherd's Grid</h1>
      <div class="sub">AI & 技术 · 财经学习 · 生活旅行 · 游戏日志</div>
    </div>

    <div class="categories-nav">
      <a href="#" class="nav-item active" data-category="all">
        <span class="nav-icon">📚</span>
        <span class="nav-text">全部文章</span>
      </a>
      <a href="/categories/ai-tech/" class="nav-item" data-category="ai-tech">
        <span class="nav-icon">🤖</span>
        <span class="nav-text">AI & 技术</span>
      </a>
      <a href="/categories/finance/" class="nav-item" data-category="finance">
        <span class="nav-icon">💰</span>
        <span class="nav-text">财经学习</span>
      </a>
      <a href="/categories/life-travel/" class="nav-item" data-category="life-travel">
        <span class="nav-icon">✈️</span>
        <span class="nav-text">生活旅行</span>
      </a>
      <a href="/categories/game-log/" class="nav-item" data-category="game-log">
        <span class="nav-icon">🎮</span>
        <span class="nav-text">游戏日志</span>
      </a>
    </div>

    <div class="content-wrapper">
      <!-- 全部文章 -->
      <div class="category-section" id="category-all">
        <div class="section-header">
          <h2>全部文章</h2>
          <div class="section-meta">
            <span class="total-count">{{ site.posts.size }} 篇文章</span>
          </div>
        </div>

        {% if site.posts.size > 0 %}
        <div class="posts-grid">
          {% for post in site.posts %}
            <div class="post-card post-{{ post.category }}" data-category="{{ post.category }}">
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
                  {% if post.tag %}
                  <span class="post-tag">{{ post.tag }}</span>
                  {% endif %}
                </div>
              </div>
              {% if post.excerpt %}
              <div class="post-excerpt">{{ post.excerpt }}</div>
              {% endif %}
            </div>
          {% endfor %}
        </div>
        {% else %}
        <div class="empty-state">
          <p>暂无文章 · 等待首发</p>
        </div>
        {% endif %}
      </div>

      <!-- 无文章提示 -->
      {% if site.posts.size == 0 %}
      <div class="empty-state">
        <p>暂无文章 · 等待首发</p>
      </div>
      {% endif %}
    </div>
  </div>

  <script>
    // 分类切换
    document.querySelectorAll('.nav-item').forEach(item => {
      item.addEventListener('click', (e) => {
        e.preventDefault();
        const category = e.currentTarget.dataset.category;

        // 更新导航状态
        document.querySelectorAll('.nav-item').forEach(nav => nav.classList.remove('active'));
        e.currentTarget.classList.add('active');

        // 切换内容
        document.querySelectorAll('.category-section').forEach(section => {
          if (category === 'all') {
            section.style.display = 'block';
          } else {
            section.style.display = 'none';
          }
        });
      });
    });

    // 点击卡片本身也能跳转
    document.querySelectorAll('.post-card').forEach(item => {
      item.addEventListener('click', (e) => {
        // 阻止冒泡，避免触发导航
        if (e.target.tagName !== 'A') {
          const link = item.querySelector('a');
          if (link) {
            link.click();
          }
        }
      });
    });
  </script>
</body>
</html>
