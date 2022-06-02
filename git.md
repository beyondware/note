---
title: git 使用方法
author: beyondware
tags:
  - [git]
description: 不要随意修改文件名称，否则会出现问题。
---

## git 流程

- 新建的远程仓库

> 添加-提交（选中已添加的内容）-推送

- 已有的远程仓库

1、修改克隆下来的文件（无需添加）

> 克隆-修改-提交（选中修改后的内容）-推送

2、添加新文件到克隆仓库（只添加新文件）

> 添加-提交（选中已添加的内容）-推送

## 常用命令

1、初始化（目录）

> git init

2、查看状态

> git status

3、添加（缓存区）

> git add //添加所有文件到缓存区

4、提交（本地仓库）

> git commit -m ‘提交说明’

5、查看日志

> git log

## 版本回退

1、查询

> git reflog

2、回退

> git reset –hard 版本唯一索引值

## 标签（版本号）

1、查看

> git tag

2、创建

> git tag 版本号

3、指定

> git tag -a 版本号 -m "提交说明"

4、删除

> git tag -d 版本号

5、发布

> git push origin 版本号

## 分支管理

1、创建分支

> git branch 分支名

2、切换分支

> git checkout 分支名

> git checkout master(主分支)

3、查看分支列表

> git branch

4、合并分支（先切换到主分支、再合并）

> git checkout master(主分支)

> git merge 分支名

5、删除分支

> git branch -d 分支名

## 关联账号

1、查询

> git config user.name

> git config user.email

2、设置 git 账户

> git config –global user.name “用户名”

> git config –global user.email “邮箱”

3、查询 git 配置

> git config –list

4、查询是否生成 ssh 密钥

> cd ~/.ssh

5、生成 ssh 密钥（三次确认）

> ssh-keygen -t rsa -C “邮箱”

6、查看 ssh 公钥

> cat ~/.ssh/id_rsa.pub

7、将 ssh 公钥粘贴到 gitee

- 添加成功，系统会发邮件提醒

8、ssh 公钥验证(三次确认)

> ssh -T git@gitee.com

或者

> ssh -T git@github.com

- 显示 successfully 表示成功

## 推送到远程仓库

1、添加（远程仓库）

> git remote add origin 远程仓库地址

2、推送（远程仓库）

> git push -u origin master(主分支)

## 克隆到本地

克隆

> git clone 远程仓库地址

拉取

> git pull 远程仓库名 分支名

> git pull origin master(主分支)

## TortoiseGit

1、创建一个文件夹

2、在文件夹上，鼠标右击“Git 在这里创建版本库”，在文件夹中生成一个.git 文件

3、创建的文件，在文件上鼠标右击-TortoiseGit-添加（A）…

4、再在文件上鼠标右击-Git 提交(C)->”master”…，并输入提交信息

- 生成秘钥

开始-->TortoiseGit-->PuTTYgen，点击 Generator
注意：生成时鼠标要不停划过进度条，不然进度条会一直不动！
保存秘钥：Save private key

- 代码回滚

TortoiseGit-->显示日志-->还原此版本做出的更改

## github 不删除仅清空仓库

1、远程仓库克隆

```sh
git clone
```

2、删除全部，仅保留.git

- 添加

```sh
git add *
```

- 提交

```sh
git commit -m 'Clean up the warehouse'
```

- 推送

```sh
git push origin master
```
