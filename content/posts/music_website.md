---
title: "音乐网站项目"
description: "music_website"
keywords: "music_website"

date: 2023-10-22T21:58:51+08:00
lastmod:

categories:
  - 项目
tags:
  -

draft: true
# 原文作者
# Post's origin author name
#author:
# 原文链接
# Post's origin link URL
#link:
# 图片链接，用在open graph和twitter卡片上
# Image source link that will use in open graph and twitter card
#imgs:
# 在首页展开内容
# Expand content on the home page
#expand: true
# 外部链接地址，访问时直接跳转
# It's means that will redirecting to external links
#extlink:
# 在当前页面关闭评论功能
# Disabled comment plugins in this post
#comment:
#  enable: false
# 关闭文章目录功能
# Disable table of content
#toc: false
# 绝对访问路径
# Absolute link for visit
#url: "music_website.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
# 开启数学公式渲染，可选值： mathjax, katex
# Support Math Formulas render, options: mathjax, katex
#math: mathjax
# 开启各种图渲染，如流程图、时序图、类图等
# Enable chart render, such as: flow, sequence, classes etc
mermaid: true
---

我正在制作一个音乐网站的 SpringBoot 项目。

DeadLine 暂且定在2023年10月31日23:59，进度持续更新中。

<div class="timer"></div>
<script>
  let countDownDate = new Date("Oct 31, 2022 00:00:00").getTime();
  let timer = setInterval(function() {
  let now = new Date().getTime();
  let distance = countDownDate - now;
  let days = Math.floor(distance / (1000 * 60 * 60 * 24));
  let hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
  let minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
  let seconds = Math.floor((distance % (1000 * 60)) / 1000);
  console.log(days + " 天 " + hours + " 小时 " + minutes + " 分钟 " + seconds + " 秒 ");
  if (distance < 0) {
    clearInterval(timer);
    console.log('倒计时结束！');
  }
}, 1000);
</script>

<!--more-->

## 开发环境

- 操作系统：Windows 11
- JDK版本：17
- 数据库：
  - Postgres（部署在Docker上）
  - Redis（部署在Docker上）
- NodeJS版本：18
- IDE：
  - IntelliJ IDEA
  - Visual Studio Code

## 技术栈

- 后端框架：
  - [Spring Boot](https://spring.io/projects/spring-boot)
  - Spring Security（计划）
- 数据库：
  - [PostgresQL](www.postgresql.org)
  - 数据库操作层框架：[Spring Data JPA](https://spring.io/projects/spring-data-jpa)
- 前端框架：
  - [Vue3](https://cn.vuejs.org)
  - [Element-Plus](https://element-plus.org/zh-CN)
  - axios（计划）
- 其他：
  - Maven

## 额外内容

- 网站爬虫：
  - [yangjianxin1/QQMusicSpider](https://github.com/yangjianxin1/QQMusicSpider)
  - [Jack-Cherish/python-spider](https://github.com/Jack-Cherish/python-spider)
- 参考的同类开源项目：
  - [Yin-Hongwei/music-website](https://github.com/Yin-Hongwei/music-website)
- 做到一半~~走神~~思考实现的项目
  - [Learning Music](https://learningmusic.ableton.com/zh-Hans/index.html)

<!-- ## 遇到的问题与解决

- Postgres -->
