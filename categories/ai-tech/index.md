---
layout: default
title: AI & 技术
category: ai-tech
---

<div class="category-page">
  <div class="category-header">
    <h1>🤖 AI & 技术</h1>
    <p>探索人工智能、技术部署与实践经验</p>
  </div>

  <div class="posts-list">
    {% for post in site.categories.ai-tech %}
    <article class="post-item" data-category="ai-tech">
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
    </article>
    {% else %}
    <div class="empty-state">
      <p>暂无文章 · 暂无内容</p>
    </div>
    {% endfor %}
  </div>
</div>
