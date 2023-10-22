---
title: "博客已重建"
description: ""
keywords: ""

date: 2023-09-20T23:08:21+08:00

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

<!-- ---

在 Github Pages 上部署 Hugo 博客的方法：

1. 安装版本控制软件[git](https://git-scm.com/)。
2. [注册 Github 账号](https://github.com/signup)。
3. 在操作系统中安装[Hugo](https://gihugo.io)。
4. 新建一个Hugo站点（此操作会新建一个文件夹，下称“站点文件夹”），并在新建的站点文件夹中初始化git仓库。
   - Hugo新建一个名为“blog”的站点：`Hugo new site blog`
   - 进入“blog”文件夹：`cd blog`
   - 初始化 git 仓库：`git init`
5. 在站点文件夹中新建`.github`目录，在此目录下新建一个`workflows`文件夹，并在`workflows`文件夹中新建一个 yaml 文件（如`page.yaml`）。
   - 如果站点文件夹名为“blog”，`page.yaml`的详细路径是`.../blog/.github/workflows/page.yaml`
6. 在`page.yaml`中设置工作流（workflow），详见[GitHub Actions 的工作流语法文档](https://docs.github.com/zh/actions/using-workflows/workflow-syntax-for-github-actions)。

> 以下是我的配置文件，基于[peaceiris/actions-gh-pages](https://github.com/peaceiris/actions-gh-pages)的推荐配置修改，值得注意的地方已用注释标出，可供参考：
>
> ```yaml
> name: GitHub Pages Deployment # 此工作流的名字
>
> on:
>   push: # 设定当推送（push）操作时执行此工作流
>     branches:
>       - main # 当 main 分支（branch）被推送时执行此工作流。如果这与你的分支名不同，请修改此处的分支名为你的分支。
>
> permissions:
>   contents: write # 设置此工作流具有仓库内容改写权限，不然部署时会报403错误。
>
> jobs:
>   deploy: 
>     runs-on: ubuntu-latest
>     concurrency:
>       group: ${{ github.workflow }}-${{ github.ref }}
>
>     steps:
>       - uses: actions/checkout@v3 # https://github.com/actions/checkout
>         with:
>           submodules: true # Fetch Hugo themes (true OR recursive)
>           fetch-depth: 0 # Fetch all history for .GitInfo and .Lastmod
>
>       - name: Setup Hugo
>         uses: peaceiris/actions-hugo@v2 # https://github.com/peaceiris/actions-hugo
>         with:
>           hugo-version: "latest"
>           extended: true
>
>       - name: Build
>         run: hugo --minify
>
>       - name: Deploy
>         uses: peaceiris/actions-gh-pages@v3 # https://github.com/peaceiris/actions-gh-pages
>         if: github.ref == 'refs/heads/main'
>         with:
>           github_token: ${{ secrets.GITHUB_TOKEN }}
>           publish_dir: ./public # 将本仓库根目录下的 /public/ 文件夹进行提交。Hugo会将生成的网页内容放在 /public/ 文件夹下。
>           publish_branch: gh-pages # 提交到本仓库的 gh-pages 分支
> ```

7. 引入主题
   - 可在[Hugo Themes](https://themes.gohugo.io/)网站寻找自己心仪的主题。
   - 安装主题的方法参见各主题的文档。
8. 编写博客文章
   - `hugo new post/demo.md`
     - 新建的“demo.md”的详细路径是`.../blog/content/post/demo.md`
9. Hugo，启动
   - `hugo server`
     - 启动的Hugo服务器使用1313端口，访问[localhost:1313](localhost:1313)即可预览效果
10. 在 Github[建立一个新的仓库](https://github.com/new)（Repository）
11. 在仓库页面中找到Settings（设置）标签，再找到Pages（网页）标签，进行Github Pages设置
12. 将站点文件夹推送到github仓库中
13. 等待部署完毕
14.  -->

---

本博客开启了自动更新“文章最后修改时间”功能。

如果你也在使用 Hugo 部署博客，并且也懒得每次改文章都手动更新文章的修改时间，可以在 hugo 配置文件（如`config.yaml`）中添加如下配置：

```yaml
enableGitInfo: true # 允许Hugo读取Git commit信息

frontmatter: # 优先级从左到右
  lastmod = ['lastmod', ':git', 'modified', 'date', 'publishdate', 'pubdate', 'published']
```

如果你用的配置文件是 toml（如`hugo.toml`）：

```toml
[frontmatter]
  lastmod = ['lastmod', ':git', 'modified', 'date', 'publishdate', 'pubdate', 'published']
```

此功能详见[Hugo 文档](https://gohugo.io/getting-started/configuration/#configure-front-matter)
