# Shepherd's Grid 个人博客使用手册

本项目是基于 **Jekyll + GitHub Pages** 搭建的个人博客，采用标准的 Jekyll 配置方式。

---

## 📁 目录结构

```
Leclerc423.github.io/
├── _posts/              # 文章存放目录（Jekyll 标准目录）
│   ├── ai-tech/         # AI & 技术分类
│   ├── finance/         # 财经学习分类
│   ├── life-travel/     # 生活旅行分类
│   └── game-log/        # 游戏日志分类
├── _layouts/            # 布局模板
├── index.html           # 首页
├── _config.yml          # Jekyll 配置
└── README.md            # 本文档
```

---

## ✍️ 文章发布规范

### 1. 文件位置
文章必须放在 `_posts/` 目录下的对应分类文件夹中：
- `ai-tech/` - AI & 技术
- `finance/` - 财经学习
- `life-travel/` - 生活旅行
- `game-log/` - 游戏日志

### 2. 文件命名格式
**标准格式**：`[分类]/[日期]-[标题].md`
示例：`ai-tech/20260313-AI-Flag-Work.md`

### 3. Front Matter 格式

```yaml
---
layout: default
title: "文章标题"
date: 2026-03-13 17:16:00
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

# 2. 创建分类文件夹
mkdir -p _posts/ai-tech

# 3. 将文章放入对应文件夹
git add _posts/ai-tech/你的文章.md

# 4. 提交并推送
git commit -m "新增文章：文章标题"
git push origin main

# 5. 等待部署（1-2分钟）
```

---

## 🎯 验证步骤

1. **访问博客首页**：https://leclerc423.github.io
2. **查看文章列表**：应该显示"最近发布"
3. **查看调试信息**：
   - 应该显示 `site.posts.size: 2` 或更多
   - 如果显示 `0`，说明 Jekyll 没有识别到文章
4. **点击文章**：跳转到详情页

---

## ⚙️ 配置说明

### _config.yml 核心配置

```yaml
collections:
  posts:
    output: true
    permalink: /:year/:month/:day/:title.html  # 标准日期格式

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

---

## 🔍 调试信息

如果看不到文章，首页会显示：
- `site.posts.size: 2` → 应该能看到文章
- `site.posts.size: 0` → Jekyll 没有识别到文章

---

## 🌐 访问地址
博客：https://leclerc423.github.io
