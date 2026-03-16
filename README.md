# Shepherd's Grid 个人博客使用手册

本项目是基于 **Jekyll + GitHub Pages** 搭建的个人博客，采用最简化的配置方式。

---

## 📁 目录结构

```
Leclerc423.github.io/
├── _article/              # 文章存放目录（Jekyll 隐藏目录）
│   ├── ai-tech/          # AI & 技术分类
│   ├── finance/          # 财经学习分类
│   ├── life-travel/      # 生活旅行分类
│   └── game-log/         # 游戏日志分类
├── _layouts/             # 布局模板
├── index.html            # 首页
├── _config.yml           # Jekyll 配置
└── README.md             # 本文档
```

---

## ✍️ 文章发布规范

### 1. 文件位置
文章必须放在 `_article/` 目录下的对应分类文件夹中：
- `ai-tech/` - AI & 技术
- `finance/` - 财经学习
- `life-travel/` - 生活旅行
- `game-log/` - 游戏日志

### 2. 文件命名
格式：`[分类缩写]-[文章英文标题]-[日期].md`
示例：`ai-tech-stable-diffusion-20260310.md`

### 3. Front Matter 格式

```yaml
---
layout: default
title: "文章标题"
date: 2026-03-16 12:00:00
pinned: false
category: ai-tech
tag: "AI & 技术"
tag_type: tech
---
```

**必填字段**：
- `layout`: 固定 `default`
- `title`: 文章标题（英文引号包裹）
- `date`: 发布时间（YYYY-MM-DD HH:MM:SS）
- `category`: 分类（ai-tech/finance/life-travel/game-log）
- `tag`: 标签文字
- `tag_type`: 标签样式（tech/life）

---

## 📤 发布步骤

### 本地 Git 操作

```bash
# 1. 同步远程代码
git pull origin main

# 2. 将文章放入对应分类文件夹
git add _article/ai-tech/你的文章.md

# 3. 提交并推送
git commit -m "新增文章：文章标题"
git push origin main

# 4. 等待部署（1-2分钟）
```

---

## 🎯 验证步骤

1. **访问博客首页**：https://leclerc423.github.io
2. **检查文章列表**：应该显示"最近发布"
3. **点击文章**：跳转到详情页，检查内容是否正常

---

## ⚙️ 配置说明

### _config.yml 核心配置

```yaml
collections:
  posts:
    output: true
    permalink: /:path.html  # 使用完整文件路径

defaults:
  - scope:
      path: ""
      type: "posts"
    values:
      layout: default
      pinned: false
      tag: "文章"
      tag_type: tech
```

### 关键点

1. **使用 posts 集合**：Jekyll 默认集合名
2. **`:path.html`**：保持完整文件路径
3. **`_article/`**：Jekyll 隐藏目录，必须用 `_` 开头

---

## ❓ 常见问题

### 文章不显示
- 检查 Front Matter 格式是否正确
- 确认文件放在 `_article/` 下
- 检查 category 字段值是否正确

### 页面 404
- 检查 permalink 配置
- 确认 `layout: default` 存在

---

## 🌐 访问地址
博客：https://leclerc423.github.io
