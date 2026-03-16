# Shepherd's Grid 个人博客使用手册
本项目是基于 **Jekyll + GitHub Pages** 搭建的个人博客，定位为「AI & 技术、财经学习、生活旅行、游戏日志」的内容分享平台，采用F1赛道风格设计，支持文章自动排序、置顶、分类筛选、自动部署等功能。

---

## 一、项目目录结构

Leclerc423.github.io/
├── .github/workflows/ # GitHub Actions 自动部署配置
├── _article/ # 文章存放目录（按分类分子文件夹）
│   ├── ai-tech/ # AI & 技术分类文章
│   ├── finance/ # 财经学习分类文章
│   ├── life-travel/ # 生活旅行分类文章
│   └── game-log/ # 游戏日志分类文章
├── _layouts/ # 页面布局模板（文章详情页通用布局）
├── css/ # 全局样式文件
├── index.html # 博客首页（核心入口）
├── _config.yml # Jekyll 全局配置文件
├── Gemfile # Jekyll 依赖配置
└── README.md # 本使用手册


---

## 二、文章发布规范
### 1. 文件命名规范
- 文件名格式：`[分类缩写]-[文章英文标题]-[发布日期].md`
- 示例：`ai-tech-stable-diffusion-deploy-20260310.md`
- 要求：
  - 后缀必须为 `.md`（Markdown文件）
  - 文件名仅使用英文、数字、横杠`-`，避免中文、空格、特殊符号

### 2. 文章内容格式
每篇文章**必须以固定格式的 Front Matter 开头**（Jekyll 用于识别文章属性的核心配置），下方为文章正文，完整示例如下：

```
--- 
# 文章核心属性（必填项，不可删除）
layout: default       # 固定值，关联文章详情页布局模板，不可修改
title: "Intel Mac 本地运行 Stable Diffusion 完整部署手册"  # 文章标题（必填）
date: 2026-03-10 22:00:00  # 发布时间（必填，用于文章排序，格式固定）
pinned: false          # 是否置顶（true=置顶，false=不置顶，非必填，默认false）
category: ai-tech     # 文章分类（必填，必须和导航栏分类对应，可选值见下方说明）
tag: "AI & 技术"     # 文章标签（必填，首页展示的标签文字）
tag_type: tech        # 标签样式（必填，对应CSS样式类，固定用tech即可）
---

# 这里是文章正文
正文完全支持 Markdown 语法，包括标题、列表、代码块、图片、链接等。

## 二级标题示例
- 无序列表1
- 无序列表2

### 三级标题示例

``` bash
# 代码块示例
git pull origin main
git push origin main
```
```

#### 分类可选值（必须和导航栏一一对应）
| 导航栏栏目 | category 字段值 | 对应存放文件夹 |
|------------|----------------|----------------|
| AI & 技术  | ai-tech        | _article/ai-tech/ |
| 财经学习   | finance        | _article/finance/ |
| 生活旅行   | life-travel    | _article/life-travel/ |
| 游戏日志   | game-log       | _article/game-log/ |

---

## 三、文章上传操作方式
### 本地 Git 终端操作
适合本地编写文章、熟悉 Git 操作的场景，步骤如下：
#### 1. **同步远程仓库最新代码**（避免推送冲突，每次推送前必须执行）
```bash
git pull origin main
```

#### 2.将编写好的文章文件，放入对应分类的文件夹
示例：AI & 技术的文章放入 _article/ai-tech/ 目录
- 例如：`git add _article/ai-tech/你的文章文件名.md`

#### 3.提交并推送文章到远程仓库
```bash
# 1. 将新文章加入 Git 追踪
git add _article/ai-tech/你的文章文件名.md

# 2. 提交修改（备注清晰说明新增/修改内容）
git commit -m "新增文章：Intel Mac 部署 Stable Diffusion 手册"

# 3. 推送至 GitHub 远程仓库
git push origin main
```

#### 4.等待自动部署
推送完成后，GitHub Actions 会自动触发 Jekyll 构建与部署，等待 1-2 分钟，构建状态变为绿色✅即完成，可访问博客查看文章。

---

## 四、新增 / 调整导航栏栏目操作
如需新增导航栏目、修改栏目名称、调整栏目顺序，按以下步骤操作：

### 1. 修改首页导航栏代码
打开根目录的 index.html，找到 nav 对应的代码块，示例如下：
```html
<div class="nav">
  <a href="#" class="active" data-category="all">全部文章</a>
  <a href="#" data-category="ai-tech">AI & 技术</a>
  <a href="#" data-category="finance">财经学习</a>
  <a href="#" data-category="life-travel">生活旅行</a>
  <a href="#" data-category="game-log">游戏日志</a>
</div>
```
``` markdown
新增栏目：在末尾新增一行，格式为 <a href="#" data-category="分类缩写">栏目名称</a>
示例：新增「读书笔记」栏目：<a href="#" data-category="book-note">读书笔记</a>
修改栏目名称：直接修改标签内的文字即可，示例：把「生活旅行」改为「生活随笔」
调整栏目顺序：直接调整 <a> 标签的上下顺序即可
```

### 2. 新增对应分类文件夹
在 _article/ 目录下，新建和 data-category 同名的文件夹，示例：新增 _article/book-note/ 文件夹，用于存放该分类的文章。

### 3. 更新配置和文档
更新 _config.yml 中的 defaults 配置，为新增的分类添加默认属性

后续该分类的文章，category 字段必须填写新增的分类缩写，存放至对应文件夹

### 4. 提交修改并部署
修改完成后，提交代码到仓库，自动触发部署后，新的导航栏目即可生效。

---

## 五、标签样式调整操作
### 1. 新增标签样式
打开 css/main.css 文件，找到标签样式对应的代码块，新增样式类即可，示例：
```css
/* 新增生活类标签样式 */
.tag-life {
  background: #007aff;
  color: white;
  padding: 2px 8px;
  border-radius: 4px;
  font-size: 12px;
}
```

### 2. 使用新标签样式
文章的 Front Matter 中，tag_type 字段填写新增的样式类名即可，示例：tag_type: life

---

## 六、常见问题排查
### 1. 文章上传后首页不显示
排查 1：确认文章的 category 字段值和导航栏的 data-category 完全一致
排查 2：确认文章 Front Matter 格式正确，开头和结尾的 --- 没有遗漏
排查 3：确认 GitHub Actions 构建成功（无红色❌报错）
排查 4：确认文章文件放入了对应分类的文件夹（_article/），且后缀为 .md
排查 5：确认文件路径正确，没有被放在错误的目录
### 2. 推送代码时提示 rejected 冲突
解决方案：先执行 git pull origin main 同步远程代码，合并完成后再执行 git push origin main 推送
### 3. 页面不更新，仍显示旧内容
解决方案：使用浏览器无痕模式访问博客，或按 Ctrl+Shift+R（Windows）/ Cmd+Shift+R（Mac）强制刷新浏览器缓存
### 4. Actions 构建失败
排查 1：确认文章 Front Matter 无语法错误（引号、冒号格式正确）
排查 2：确认 _config.yml、Gemfile 无修改错误，恢复默认配置即可
排查 3：打开 Actions 对应的失败任务，查看日志定位具体报错
### 5. 首页显示 Liquid 模板代码
解决方案：确认 index.html 开头的 Front Matter 格式正确，必须为完整的一对 ---，示例：

```html
---
layout: none
---
<!DOCTYPE html>
```

---

## 七、访问地址
博客线上地址：https://leclerc423.github.io
