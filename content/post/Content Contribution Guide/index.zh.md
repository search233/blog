---
title: 博客编写指南
date: 2026-07-12
description: 向本博客贡献文章的方式
lastmod: 2026-07-12
author: "yangz"
slug: "contribution-guide"
draft: false
toc: true
math: false
comments: true
categories:
    - documentation
tags:
    - Hugo
    - blog
---





欢迎向我的博客投稿！为了保持博客内容的高质量与排版一致性，请在撰写和提交文章前，仔细阅读以下指南。

<!--more-->




## 准备工作

本博客基于 Hugo (Stack 主题) 搭建，所有文章均使用 Markdown 语法编写。

环境准备：建议使用 VS Code 或 Typora 等支持 Markdown 实时预览的编辑器。

图片处理：文章内若包含图片，请尽量压缩体积（建议单张图片不超过 500KB，推荐使用 WebP 或 JPG 格式）。



## 内容组织结构 (Page Bundles)
为了方便管理文章及其自带的图片资源，本博客统一采用 Hugo 的 Page Bundles 模式。请为你的新文章创建一个独立的文件夹。

目录命名规范：
在 content/post/ 目录下新建文件夹：

```
content/post/
└── my-awesome-post/             <-- 你的文章文件夹
    ├── index.zh.md                 <-- 文章主内容(中文)（名称必须是 index）
    ├── index.en.md                 <-- 文章主内容(英文)
    ├── cover.jpg                <-- 文章封面图（可选）
    └── step1-screenshot.png     <-- 文章内插图（可选）
```



## Frontmatter 属性配置
每篇新文章的头部（index.*.md 的最上方）必须包含 YAML 格式的元数据配置。请直接复制以下模板并修改：

```yaml
---
title: "你的文章标题"
description: "用一两句话简要概括文章内容，有助于首页卡片展示和 SEO"
date: 2026-07-12                                # 写作日期
author: "你的名字或网名"
slug: "my-awesome-post"                         # 自定义 URL 路径（建议与文件夹同名）
image: "cover.jpg"                              # 封面图文件名，没有可不填
draft: false                                    # 是否为草稿（提交时请设为 false）
toc: true                                       # 是否开启右侧目录
categories:
    - Technology                                # 大分类
tags:
    - Hugo                                      # 标签
    - Markdown
---
```

📌 更详细的字段说明，请参考： [Frontmatter 维护指南]({{< ref "post/frontmatter-guide/index.md" >}})。



## 排版与特色功能规范

为了保持全站排版的一致性与美观度，请创作者遵守以下编写规范：

1. **首页摘要截断**：请在文章开头的引言完毕后，另起一行加入 `<!--more-->` 标签。这能决定首页卡片展示哪些摘要内容。
2. **标题层级规范**：文章正文内最高只能使用 `## 二级标题`，严禁使用 `# 一级标题`（该级别已留给文章大标题），否则会导致右侧目录导航（TOC）错乱。
3. **本地图片引用**：在 Page Bundles 模式下，请将图片放在文章同级文件夹内，并在 Markdown 中直接书写文件名，例如 `![描述](image.png)`。
4. 站内文章跳转：若需引用本站其他文章，请使用 Hugo 动态解析语法避免死链：`{{</* ref "post/目标文件夹名/index.md" */>}}`
5. 多媒体嵌入：嵌入视频或精美引用请使用以下短代码：

* **B站视频：** `{{</* bilibili "BV号" */>}}`
* **YouTube：** `{{</* youtube "视频ID" */>}}`

* **专属引用块：**`  {{</* quote author="作者" source="出处" */>}}内容{{</* /quote */>}}`

更详细的信息请参考：[排版与特色功能规范]({{< ref "post/format-standerds/index.md" >}})



## 投稿与提交方式
目前接受以下方式的投稿（请根据你的实际情况勾选/修改）：

方式 A：通过 GitHub 提交（推荐）

1. Fork 本博客的 GitHub 仓库。
2. 在 content/post/ 下按照上述规范创建你的文章文件夹并撰写内容。
3. 本地测试无误后，提交并推送（Push）到你的 Fork 仓库。
4. 向主仓库提交一个 Pull Request (PR)，等待管理员审核。

方式 B：通过邮件投稿

如果你不熟悉 Git 操作，可以将写好的文章文件夹打包（包含 index.md 和图片），发送至邮箱：`pterocaryz@outlook.com`，邮件主题注明 【博客投稿】文章标题。



## 版权说明
投稿文章必须为原创内容。若为翻译或转贴，请务必在文章开头注明原作者及原文链接。

本站所有文章默认采用 CC BY-NC-SA 4.0（署名-非商业性使用-相同方式共享） 许可协议。投稿即代表你同意该协议。