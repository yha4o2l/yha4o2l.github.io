---
title: "博客已重建"
description: ""
keywords: ""

date: 2023-09-20T23:08:21+08:00
lastmod: 2023-09-20T23:08:21+08:00

categories:
  - 杂记
tags:
  - 

share: false
followme: false
nav: false
copyright: false
---

本博客站点已被重新建立。

<!--more-->
本博客依旧是使用[Hugo](https://gihugo.io)框架通过[Github Actions](https://github.com/features/actions)自动部署到[Github Pages](https://pages.github.com/)上，并使用[hugo-next](https://github.com/hugo-next/hugo-theme-next)主题。

本博客的内容大概会比之前更加丰富吧，除了之前的学习笔记以外，也计划写些书籍读后感、影视观后感、游戏玩后感等文章。

---
本博客开启了自动更新“文章最后修改时间”功能。

如果你也在使用Hugo部署博客，并且也懒得每次改文章都手动更新文章的修改时间，可以在hugo配置文件（如`config.yaml`）中添加如下配置：

```yaml
enableGitInfo: true  # 允许Hugo读取Git commit信息

frontmatter:  # 优先级从左到右
  lastmod = ['lastmod', ':git', 'modified', 'date', 'publishdate', 'pubdate', 'published']
```

如果你用的配置文件是toml（如`hugo.toml`）：

```toml
[frontmatter]
  lastmod = ['lastmod', ':git', 'modified', 'date', 'publishdate', 'pubdate', 'published']
```

此功能详见[Hugo文档](https://gohugo.io/getting-started/configuration/#configure-front-matter)
