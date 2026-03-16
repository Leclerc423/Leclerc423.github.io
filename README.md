# Shepherd's Grid 个人博客使用手册

本项目是基于 **Jekyll + GitHub Pages** 搭建的个人博客，采用标准的 Jekyll 配置方式。

---

## 📁 目录结构

```
Leclerc423.github.io/
├── _posts/              # 文章存放目录（Jekyll 标准目录）
│   ├── ai-tech-20260313-AI-Flag-Work.md
│   ├── ai-tech-20260316-test-article.md
│   ├── finance-20260301-market-analysis.md
│   ├── game-log-20260310-gaming-review.md
│   └── life-travel-20260305-city-walk.md
├── _layouts/            # 布局模板
├── index.html           # 首页
├── _config.yml          # Jekyll 配置
└── README.md            # 本文档
```

**重要**：所有文章必须直接放在 `_posts/` 根目录，不允许创建子目录！

---

## ✍️ 文章发布规范

### 1. 文件位置
文章必须直接放在 `_posts/` **根目录**下：
- ❌ 错误：`_posts/ai-tech/文章.md`
- ✅ 正确：`_posts/ai-tech-20260313-文章标题.md`

### 2. 文件命名格式
**标准格式**：`[分类]-[日期]-[标题].md`
示例：`ai-tech-20260313-AI-Flag-Work.md`

**分类前缀**：
- `ai-tech` - AI & 技术
- `finance` - 财经学习
- `life-travel` - 生活旅行
- `game-log` - 游戏日志

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

# 2. 创建新文章（直接放在 _posts 根目录）
cat > _posts/finance-20260316-投资分析.md << 'EOF'
---
layout: default
title: 投资分析：当前市场趋势
date: 2026-03-16 10:00:00
pinned: false
category: finance
tag: 财经学习
tag_type: tech
---

# 投资分析：当前市场趋势

这里是文章正文内容...
EOF

# 3. 提交并推送
git add _posts/finance-20260316-投资分析.md
git commit -m "新增文章：投资分析"
git push origin main

# 4. 等待部署（1-2分钟）
```

---

## 🎯 验证步骤

1. **访问博客首页**：https://leclerc423.github.io
2. **查看文章列表**：应该显示"最近发布"标题
3. **查看调试信息**：
   - 应该显示 `site.posts.size: 5` 或更多
4. **点击文章**：跳转到详情页，检查内容是否正常

---

## ⚙️ 配置说明

### _config.yml 核心配置

```yaml
collections:
  posts:
    output: true
    permalink: /:year/:month/:day/:title.html

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

## ❌ 常见错误

### 1. 创建子目录
```bash
# ❌ 错误
mkdir _posts/ai-tech
mv 文章.md _posts/ai-tech/

# ✅ 正确
mv 文章.md _posts/
```

---

## 🌐 访问地址
博客：https://leclerc423.github.io
