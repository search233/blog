---

title: Frontmatter 维护指南
date: 2026-07-12
description: 在 HUGO 中编写博文需要的 Frontmatter 的清单
lastmod: 2026-07-12
author: "你的名字"
slug: "Frontmatter-Maintenancs"
draft: false
toc: true
math: false
comments: true
categories:
    - documentation
tags:
    - Hugo
    - Markdown
    - Frontmatter

---



## 基础元数据字段

此部分字段用于定义文章的核心属性，影响页面的基本展示、生成时间及 SEO 表现。

- **`title`** (String): **【必填】** 文章的标题。  
- **`description`** (String): **【推荐】** 文章的简短描述或摘要。该内容会渲染在首页文章卡片上，同时作为网页的 SEO Meta Description。  
- **`date`** (Date/String): **【必填】** 文章的创建日期，标准格式为 `YYYY-MM-DD`（如 `2026-01-26`），亦可追加具体时间戳（如 `2026-01-26T15:30:00+08:00`）。  
- **`lastmod`** (Date/String): 文章的最后修改日期。若不填写，Hugo 可配置为默认读取文件的最后修改时间。
- **`author`** (String/Array): 文章作者的名称。用于多作者博客或覆盖全局默认作者配置。  
- **`draft`** (Boolean): 草稿状态。若设为 `true`，则在生产环境中默认不编译和显示此文章。
- **`weight`** (Integer): 排序权重。数字越小，文章在列表中的排列位置越靠前，常用于文章置顶。

---

## 分类与组织字段

用于构建网站的内容索引，规范分类和标签有助于提升读者的检索体验。

- **`categories`** (Array of Strings): 文章的分类名称。Stack 主题会为分类生成独立的分类卡片。  
- **`tags`** (Array of Strings): 文章的标签列表。用于更细粒度的聚合管理。  
- **`slug`** (String): 自定义文章 URL 的末尾部分。如果不填写，系统默认使用 Markdown 文件的名称作为 URL 路径。  
- **`url`** (String): 完全自定义页面路径。一旦填写，将无视网站的默认 Permalinks 规则。

---

## 视觉与布局控制

此部分字段直接影响 Stack 主题的独特卡片流式布局和页面交互。

- **`image`** (String): **【推荐】** 文章的封面图/特色图片。  
  - *本地路径*：若采用 Page Bundles 模式（即文章在一个独立文件夹内），可直接填写同目录下的图片文件名（如 `cover.jpg`）。  
  - *网络路径*：也可以使用绝对 URL 链接。
- **`toc`** (Boolean): 是否启用文章右侧的目录导航导航栏（Table of Contents）。侧边栏较长或短视频页面可设为 `false` 关闭。  
- **`hidden`** (Boolean): 是否在列表中隐藏。设为 `true` 后，该文章不会出现在首页列表、分类页和归档页中，但依然可以通过直接输入 URL 进行访问。

---


## 增强功能特性开关

用于控制单个页面内高级插件或脚本的按需加载，从而优化网页加载速度。

- **`math`** (Boolean): 是否在当前页面启用 **KaTeX** 数学公式渲染引擎。当文章包含数学公式时必须设为 `true`。  
- **`comments`** (Boolean): 是否为此文章启用评论区。若全局开启了评论（如 Giscus、Waline、Disqus），可通过此字段对单篇文章进行关闭（设为 `false`）。
- **`license`** (String/Boolean): 覆盖全局配置，为当前文章指定独立的版权协议（如 `CC BY-NC-SA 4.0`）。

---


## 特殊页面高级字段

Stack 主题依赖特定的 Frontmatter 字段来生成诸如“搜索”、“归档”或“友链”等特殊功能页面。

- **`layout`** (String): 指定特殊的页面布局。Stack 主题内置了以下常用模板：

  - `search`：创建全局搜索页面。
  - `archives`：创建时间线归档页面。
  - `links`：创建友情链接展示页。

- **`menu`** (Object): 将当前页面固定导航到侧边栏或主菜单。

  YAML

  ```
  menu:
      main:
          name: "关于我"       # 菜单显示名称
          weight: -10         # 菜单排序权重，越小越靠前
          params:
              icon: user      # 对应的图标名称（支持 Tabler Icons）
  ```

- **`links`** (Array of Objects): **仅在 `layout: links` 页面生效**，用于维护友情链接的卡片数据。

  YAML

  ```
  links:
    - title: "GitHub"                  # 网站名称
      description: "开发者开源社区"       # 网站简介
      website: "https://github.com"     # 网站链接
      image: "https://github.com/favicon.ico" # 网站 Logo/头像
  ```
---
## 标准 Frontmatter 完整维护模板

在撰写新文章时，可直接复制以下 YAML 模板并按需填写：

```markdown
---
title: "这里填写文章标题"
description: "这里填写一到两句精炼的文章摘要，有助于 SEO 和首页卡片展示"
date: 2026-07-12T17:30:00+08:00
lastmod: 2026-07-12T17:30:00+08:00
author: "你的名字"
slug: "custom-post-url"
image: "cover.jpg"
draft: false
toc: true
math: false
comments: true
categories:
    - Technology
tags:
    - Hugo
    - Markdown
---

这里开始编写你的文章内容...
```