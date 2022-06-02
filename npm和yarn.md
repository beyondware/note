---
title: npm、yarn 使用方法
author: beyondware
tags:
  - [npm]
categories:
  - [node]
---

## node

> https://nodejs.org/en/

查询版本

```sh
node -v
```

```sh
npm -v
```

### nvm

> https://github.com/nvm-sh/nvm

Windows 版本

> https://github.com/coreybutler/nvm-windows

列出可安装 node 版本

```sh
nvm list available
```

安装指定版本（例如：16.13.0）

```sh
nvm install 版本号
```

列出已安装的版本

```sh
nvm list
```

使用指定的版本（例如：16.13.0）

```sh
nvm use 版本号
```

### cgr

> https://github.com/daysai/cgr

## npm 修改路径

获取 npm 配置信息

```sh
npm config list
```

> ~/.npmrc

查询当前路径

```sh
npm -g root
```

- 默认路径

> C:\Users\Administrator\AppData\Roaming\npm

- 修改路径

> D:\Program Files\nodejs

> 创建 2 个文件夹 node_global 和 node_cache

或者

- 全局模块

```sh
npm config set prefix “D:\Program Files\nodejs\node_global”
```

> 在 node_global 下创建 node_modules 文件夹

- cache 缓存

```sh
npm config set cache “D:\Program Files\nodejs\node_cache”
```

系统变量-新建

> 变量名：NODE_PATH

> 变量值：D:\Program Files\nodejs\node_global\node_modules

系统变量-Path 追加

> D:\Program Files\nodejs

> D:\Program Files\nodejs\node_global

用户变量

> C:\Users\beyondware\AppData\Roaming\npm

改成

> D:\Program Files\nodejs\node_global

### 安装 cnpm

```sh
npm install -g cnpm –registry=https://registry.npmmirror.com
```

查询版本

```sh
cnpm -v
```

## 修改源

查看当前 npm 源

```sh
npm config get registry
```

修改 npm 源

```sh
npm config set registry https://registry.npmmirror.com/
```

还原 npm 源

```sh
npm config set registry https://registry.npmjs.org/
```

查看配置列表

```sh
npm config list
```

### 常用命令

初始化

```sh
npm init -y //全部 yes
```

安装

```sh
npm install 或者 npm i
```

> npm install -dev //开发环境

> npm install -g //全局安装

安装指定版本

```sh
npm install 包名@版本号
```

> npm install 包名@latest //最后版本

删除

```sh
npm uninstall
```

> npm uninstall -g //全局删除

升级

```sh
npm update
```

清空缓存

```sh
npm cache clean –force
```

### nrm

> https://github.com/Pana/nrm

安装 nrm

```sh
npm install -g nrm
```

列出 nrm 源

```sh
nrm ls
```

使用 taobao

```sh
nrm use taobao
```

测试响应速度

```sh
nrm test taobao
```

添加镜像地址

```sh
nrm add URL ‘registry_URL’
```

删除镜像地址

```sh
nrm del ‘taobao’
```

## yarn 修改路径

> ~/.yarnrc

查看 yarn 版本

```sh
yarn -v
```

创建 yarn_global 文件夹（全局安装）

> yarn config set global-folder “D:\Program Files\Yarn\yarn_global”

> yarn config set prefix “D:\Program Files\Yarn\yarn_global”

创建 yarn_cache 文件夹（全局缓存）

```sh
yarn config set cache-folder “D:\Program Files\Yarn\yarn_cache”
```

查看所有配置

```sh
yarn config list
```

查看当前 bin 位置

```sh
yarn global bin
```

添加到系统环境变量

> D:\Program Files\Yarn\yarn_global\bin

查看当前全局安装位置

```sh
yarn global dir
```

### 修改源

查看当前 yarn 源

```sh
yarn config get registry
```

修改 yarn 源

```sh
yarn config set registry https://registry.npmmirror.com/
```

还原 yarn 源

```sh
yarn config set registry https://registry.yarnpkg.com/
```

### 常用命令

初始化

```sh
yarn init
```

安装所有包

```sh
yarn install
```

添加依赖项

```sh
yarn add
```

> yarn add –dev //开发环境

> yarn global add //全局安装

删除

```sh
yarn remove
```

> yarn global remove //全局删除

升级

```sh
yarn upgrade 或者 yarn up
```

列出已安装

```sh
yarn list
```

缓存列表

```sh
yarn cache list
```

清空缓存

```sh
yarn cache clean
```

### yrm

> https://github.com/i5ting/yrm

安装 yrm

```sh
npm install -g yrm
```

列出 yrm 源

```sh
yrm ls
```

使用 taobao

```sh
yrm use taobao
```

测试访问速度

```sh
yrm test taobao
```
