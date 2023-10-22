---
title: "我使用 Docker 运行 MariaDB 的常用命令"
description: ""
keywords: "Docker,docker,MariaDB,mariadb,MySQL,mysql"

date: 2023-09-21T00:58:13+08:00
lastmod: 2023-09-21T00:58:13+08:00

categories:
  - 配置记录
tags:
  - Docker
  - MySQL

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
#url: "spider-intro.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
# 开启数学公式渲染，可选值： mathjax, katex
# Support Math Formulas render, options: mathjax, katex
#math: mathjax
# 开启各种图渲染，如流程图、时序图、类图等
# Enable chart render, such as: flow, sequence, classes etc
#mermaid: true
---

本文介绍我使用 Docker 启动 MariaDB 镜像的常用参数，这些参数亦适用于 MySQL 镜像，把命令中的`mariadb`换成`mysql`也可以正常运行没有问题。

MariaDB 数据库软件是 MySQL 数据库软件的一个社区版分支，MariaDB 数据库兼容 MySQL，但二者的驱动程序互不兼容。

<!--more-->

本人常用的 Docker 运行 MariaDB 命令配置如下：

  ```sh
  docker run -e="MYSQL_ROOT_PASSWORD=123456" -e="LANG=C.UTF-8" -v=mysql-data:/var/lib/mysql --restart=unless-stopped --name=mariadb -p 3306:3306 -d mariadb
  ```

  逐行分解版：

  ```sh
  docker run \
  -e="MYSQL_ROOT_PASSWORD=mypassword" \
  -e="LANG=C.UTF-8" \
  -v=mysql-data:/var/lib/mysql \
  --restart=unless-stopped \
  --name=mariadb \
  -p 3306:3306 \
  -d \
  mariadb
  ```

---

+ `-e`是`--env`的缩写，这一参数用于设置容器中程序的环境变量。
  + `MYSQL_ROOT_PASSWORD`变量是指定MySQL(或MariaDB)的 ROOT 用户初始密码。
  + `LANG`变量是避免使用`docker exec`命令进入容器时控制台显示的非英文字符串变成乱码。这一变量是否设置对于使用Navicat、Dbeaver、Datagrip等数据库客户端没有影响。
    + 注：如果不将`LANG=C.UTF-8`用英文引号括起来，由于变量中存在`=`号，Docker 会识别错误，报“invalid reference format”（无效的引用格式）错误，如下所示：

```sh
> docker run -e=MYSQL_ROOT_PASSWORD=123456 -e=LANG=C.UTF-8 -p 3306:3306 -d mariadb
docker: invalid reference format: repository name must be lowercase.
See 'docker run --help'.
```

解决此问题有两种方法：

1. 将`LANG=C.UTF-8`用英文单引号或双引号括起来，如`-e='LANG=C.UTF-8'`，注意不要使用中文单双引号；
2. 使用`--env=LANG=C.UTF-8`。

---

+ `-v`是`--volume`的缩写，这一参数用于向容器挂载目录或挂载文件，使用格式是`-v 容器外部目录:容器内部目录`。此处是我将数据卷`mysql-data`与容器中的`/var/lib/mysql`进行关联，以便于数据的持久化。

---

+ `--restart`这一参数用于配置容器的重启策略。
  可用的重启策略主要有以下几种：
  + `no`（不重启）
在容器退出时不重启容器。这是不添加 `--restart` 参数启动容器的默认行为。
  + `on-failure:[max-retrives]`（出现故障时重启，可选试图重启的次数）
只有在容器非正常退出时，才会重启容器。可选参数`[max-retrives]`为最大试图重启次数，超出次数则不再试图自动重启。
  + `always`（总是重启）
总是重启容器。Docker 守护进程重启，则容器也会执行重启，即使容器是用户手动停止的。
  + `unless-stopped`（总是重启，已停止的除外）
只要容器退出就重启容器，但是 Docker 守护进程启动前就已经停止运行的容器不算在内。

---

`--name`这一参数用于指定容器名称。如果在创建容器时不使用这个参数，Docker 会随机分配一个容器名。

---

`-p`是`--port`的缩写，这一参数用于向容器开放端口，使用格式是`-p 宿主机(容器外部)端口:容器内部端口`。

---

`-d`参数表示让容器在后台运行。如果不指定这一参数，如果在运行容器时不使用这个参数，Docker 会将容器运行记录输出到控制台。

---
`run`指令的最后是要运行的镜像名，指定要运行的镜像。镜像名后可以指定镜像版本号，如`mysql:5.8`就是指定运行MySQL5.8版本的镜像。如果不指定版本号就默认运行最新版本的镜像。
