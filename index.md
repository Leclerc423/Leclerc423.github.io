---
layout: default
title: Shepherd's Grid - 首页
---

<div class="track-top"></div>

<div class="container">
  <div class="header">
    <h1>🏁 Shepherd's Grid</h1>
    <p>AI & 技术 · 财经学习 · 生活旅行 · 游戏日志</p>
  </div>

  <nav class="nav-list">
    <a href="#" class="nav-item active" data-category="all">📚 全部文章</a>
    <a href="/categories/ai-tech/" class="nav-item" data-category="ai-tech">🤖 AI 技术</a>
    <a href="/categories/finance/" class="nav-item" data-category="finance">💰 财经</a>
    <a href="/categories/life-travel/" class="nav-item" data-category="life-travel">✈️ 生活</a>
    <a href="/categories/game-log/" class="nav-item" data-category="game-log">🎮 游戏</a>
  </nav>

  <div class="article-list">
    {% if site.posts.size > 0 %}
      {% for post in site.posts %}
        <article class="article-item" data-category="{{ post.category }}">
          <h2 class="article-title">
            {% if post.pinned %}
            <span class="pin-badge">🔥 置顶</span>
            {% endif %}
            <a href="{{ post.url }}">{{ post.title }}</a>
          </h2>

          <div class="article-meta">
            <time class="article-date">📅 {{ post.date | date: '%Y-%m-%d' }}</time>
            {% if post.tag %}
            <span class="article-tag">{{ post.tag }}</span>
            {% endif %}
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

        // 切换文章列表
        document.querySelectorAll('.article-item').forEach(article => {
          if (category === 'all') {
            article.style.display = 'block';
          } else if (article.dataset.category === category) {
            article.style.display = 'block';
          } else {
            article.style.display = 'none';
          }
        });
      });
    });
  });
</script>
