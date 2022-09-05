## 安装依赖

> git node.js

## 仓库命名

- github

> https://github.com/beyondware/beyondware.github.io

对应主页

> https://beyondware.github.io

1. 仓库中必须创建一个 index.html 文件

2. 打开 Settings，Github Pages 点击 source 将 None 改成 Main(新版)/Master（旧版）

- gitee

> https://gitee.com/beyondware/beyondware

对应主页（主页不会自动更新，需要手动更新 :disappointed_relieved: ）

> https://beyondware.gitee.io

## 安装 hexo

```sh
npm install hexo-cli -g
```

- 显示：INFO Start blogging with Hexo!表示成功。

1、查询版本

```sh
hexo -v
```

2、初始化

```sh
hexo init
```

3、启动 hexo

```sh
hexo s 或者 hexo server
```

4、终止运行

> Ctrl+C

## 新建

1、文章

```sh
hexo n "文章标题" 或者 hexo new "文章标题"
```

文章路径`source\_posts`

```sh
---
title: 文章标题
seo_title: 搜索标题
author: 作者
date: 创作时间
updated: 更新时间
description: 文章概要
tags: 标签
categories: 分类
layout: page
toc: true //生成目录
pin: true //顶置
link: 跳转外链
headimg: 图片链接
---
```

- 标签

> tags: [标签]

或者

```sh
tags:
  - 标签
  - 标签
```

- 分类

> categories: [分类]

或者

```sh
categories:
  - [父分类,子分类]
  - [父分类]
```

2、归档

```sh
hexo new page archives
```

3、标签页

```sh
hexo new page tags
```

> type: "tags"

4、分类页

```sh
hexo new page categories
```

> type: "categories"

5、友情链接

```sh
hexo new page links
```

> type: "links"

6、关于

```sh
hexo new page about
```

> type: "about"

## 主题

以`https://github.com/volantis-x/hexo-theme-volantis`为例

### 新版

1、安装

```sh
npm i hexo-theme-volantis
```

2、修改`_config.yml`文件

> theme: volantis

```sh
type: git
repo: git@gitee.com:beyondware/beyondware.git
branch: master
```

3、添加并修改`_config.volantis.yml`文件

### 旧版

1、克隆

```sh
git clone https://github.com/volantis-x/hexo-theme-volantis/ themes/volantis
```

2、修改`_config.yml`文件

```sh
theme: volantis
```

3、更新

> cd themes/volantis

```sh
git pull
```

- 显示`Already up to date.`更新成功

## 部署

1、安装 hexo-deployer-git

```sh
npm install --save hexo-deployer-git
```

- 否则报错`ERROR Deployer not found: git`

2、部署前，整理

```sh
hexo clean
```

3、生成（非必要）

```sh
hexo g 或者 hexo generate
```

- 静态页面生成到 public 目录

4、部署(远程仓库)

```sh
hexo d 或者 hexo deploy
```

- 显示`INFO Deploy done: git`表示部署成功
