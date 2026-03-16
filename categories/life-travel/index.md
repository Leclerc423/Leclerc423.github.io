---
layout: default
title: 生活赛道
category: life-travel
---

<div class="category-page">
  <div class="category-header">
    <h1>✈️ 生活赛道</h1>
    <p>城市漫步、旅行记录、生活随笔与感悟</p>
  </div>

  <div class="track-divider">
    <svg viewBox="0 0 20 4" xmlns="http://www.w3.org/2000/svg">
      <path d="M0,2 L20,2" stroke="#e10600" stroke-width="2" stroke-linecap="round"/>
    </svg>
  </div>

  <div class="posts-list">
    {% for post in site.categories.life-travel %}
      <article class="post-item" data-category="life-travel">
        <div class="post-content">
          <h2 class="post-title">
            {% if post.pinned %}
            <span class="pin-badge">🔥 置顶</span>
            {% endif %}
            <a href="{{ post.url }}">{{ post.title }}</a>
          </h2>

          <div class="post-meta">
            <time class="post-date">📅 {{ post.date | date: '%Y-%m-%d' }}</time>
          </div>

          {% if post.excerpt %}
          <p class="post-excerpt">{{ post.excerpt }}</p>
          {% endif %}

          <a href="{{ post.url }}" class="post-link">查看详情 →</a>
        </div>
      </article>
    {% else %}
    <div class="empty-grid">
      <svg class="empty-track" viewBox="0 0 120 60" xmlns="http://www.w3.org/2000/svg">
        <path d="M10,30 Q30,10 50,30 T90,30 T110,30" stroke="#e10600" stroke-width="2" fill="none" opacity="0.3"/>
        <circle cx="60" cy="30" r="8" fill="#e10600" opacity="0.4"/>
      </svg>
      <p class="empty-text">赛道空荡 · 暂无文章</p>
    </div>
    {% endfor %}
  </div>

  <div class="track-divider">
    <svg viewBox="0 0 20 4" xmlns="http://www.w3.org/2000/svg">
      <path d="M0,2 L20,2" stroke="#e10600" stroke-width="2" stroke-linecap="round"/>
    </svg>
  </div>

  <a href="/" class="back-link">⬅️ 返回发车格</a>
</div>
