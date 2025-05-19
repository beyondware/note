### git 流程

1、新建远程仓库

> 添加-提交（选中已添加的内容）-推送

2、已有的远程仓库

- 修改克隆下来的文件（无需添加）

> 克隆-修改-提交（选中修改后的内容）-推送

- 添加新文件到克隆仓库（只添加新文件）

> 添加-提交（选中已添加的内容）-推送

### 常用命令

#### 显示带中文的目录、文件

```sh
git config --global core.quotepath false
```

#### 带颜色输出

```sh
sudo git config --system color.ui auto
```

1、初始化（目录）

```sh
git init
```

2、查看状态

```sh
git status
```

3、添加（缓存区）

- 添加所有文件到缓存区

```sh
git add
```

4、提交（本地仓库）

```sh
git commit -m ‘提交说明’
```

5、查看日志

```sh
git log
```

### 版本回退

1、查询

```sh
git reflog
```

2、回退

```sh
git reset –hard 版本唯一索引值
```

### 标签（版本号）

1、查看

```sh
git tag
```

2、创建

```sh
git tag 版本号
```

3、指定

```sh
git tag -a 版本号 -m "提交说明"
```

4、删除

```sh
git tag -d 版本号
```

5、发布

```sh
git push origin 版本号
```

### 分支管理

1、创建分支

```sh
git branch 分支名
```

2、切换分支

```sh
git checkout 分支名
```

- 主分支

```sh
git checkout master
```

3、查看分支列表

```sh
git branch
```

4、合并分支（先切换到主分支、再合并）

- 切换到主分支

```sh
git checkout master
```

- 再合并

```sh
git merge 分支名
```

5、删除分支

```sh
git branch -d 分支名
```

### 关联账号

1、查询

```sh
git config user.name
```

```sh
git config user.email
```

2、设置 git 账户

```sh
git config –global user.name “用户名”
```

```sh
git config –global user.email “邮箱”
```

3、查询 git 配置

```sh
git config –list
```

4、查询是否生成 ssh 密钥

```sh
cd ~/.ssh
```

5、生成 ssh 密钥（三次确认）

```sh
ssh-keygen -t rsa -C “邮箱”
```

6、查看 ssh 公钥

```sh
cat ~/.ssh/id_rsa.pub
```

7、将 ssh 公钥粘贴到 gitee

> 添加成功，系统会发邮件提醒

8、ssh 公钥验证(三次确认)

```sh
ssh -T git@gitee.com
```

或者

```sh
ssh -T git@github.com
```

> 显示 successfully 表示成功

### 推送到远程仓库

1、添加（远程仓库）

```sh
git remote add origin 远程仓库地址
```

2、推送（远程仓库）

```sh
git push -u origin master(主分支)
```

### 克隆到本地

1、克隆

```sh
git clone 远程仓库地址
```

2、拉取

```sh
git pull 远程仓库名 分支名
```

- 例如：主分支

```sh
git pull origin master
```

### TortoiseGit

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

### github 不删除仅清空仓库

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

### 使用 https:// 来替换 git://

```sh
git config --global url."https://".insteadOf git://
```

cat ~/.gitconfig 会多出一行参数

```sh
[url "https://"]   
    insteadOf = git://
```

