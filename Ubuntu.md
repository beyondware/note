---
title: Ubuntu
author: beyondware
tags:
  - [Ubuntu]
categories:
  - [Linux]
---

## SSH 登录

1、查看是否开启 SSH

```sh
ps -e | grep ssh
```

> 显示 00:00:00 sshd 表示开启了 SSH

2、安装 SSH

```sh
sudo apt install openssh-client
```

```sh
sudo apt install openssh-server
```

或者

```sh
sudo apt install ssh
```

3、查看 SSH 状态

```sh
systemctl status sshd
```

4、启动 SSH

```sh
sudo /etc/init.d/ssh start
```

> 显示 Starting ssh (via systemctl): ssh.service.表示开启 SSH

5、重启 SSH

```sh
sudo service ssh restart //重启
```

```sh
sudo service ssh stop //关闭
```

6、开机启动 SSH，修改 SSH 配置文件（ROOT 登录）

```sh
sudo vi /etc/ssh/sshd_config
```

> PermitRootLogin without-password 修改为 PermitRootLogin yes

## 安装依赖

```sh
sudo apt install git wget
```

查看当前 shell

```sh
echo $SHELL
```

查询已安装 shell

```sh
cat /etc/shells
```

## 安装 zsh

1、安装 zsh

```sh
sudo apt install zsh
```

2、设置 zsh 为默认 shell(重启生效)

```sh
sudo chsh -s /usr/bin/zsh
```

3、退出终端

```sh
exit
```

## 安装 oh-my-zsh

```sh
sh -c "$(wget https://ghproxy.com/https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```

### powerlevel10k

1、安装 powerlevel10k 主题

```sh
git clone --depth=1 https://ghproxy.com/https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

2、编辑

```sh
vim ~/.zshrc
```

3、修改 ZSH_THEME

> ZSH_THEME="powerlevel10k/powerlevel10k"

4、配置 powerlevel10k

```sh
p10k configure
```

5、执行生效

```sh
source ~/.zshrc
```

### zsh-autosuggestions（自动补全）

切换到

> cd ~/.oh-my-zsh/custom/plugins/

1、安装 zsh-autosuggestions

```sh
git clone https://ghproxy.com/https://github.com/zsh-users/zsh-autosuggestions.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

2、编辑

```sh
vim ~/.zshrc
```

> plugins 添加 zsh-autosuggestions

3、执行生效

```sh
source ~/.zshrc
```

如果高亮不明显，修改为 10

> ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE=’fg=10’

### zsh-syntax-highlighting（显示高亮）

切换到

> cd ~/.oh-my-zsh/custom/plugins/

1、安装 zsh-syntax-highlighting

```sh
git clone https://ghproxy.com/https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

2、编辑

```sh
vim ~/.zshrc
```

> plugins 添加 zsh-syntax-highlighting

3、执行生效

```sh
source ~/.zshrc
```

### 显示结果

```sh
plugins=(
git
sudo
zsh-autosuggestions
zsh-syntax-highlighting
)
```

### incr（自动补全、可选）

1、新建

> mkdir ~/.oh-my-zsh/plugins/incr

2、安装

```sh
wget http://mimosa-pudica.net/src/incr-0.2.zsh
```

3、移动到

```sh
mv incr-0.2.zsh ~/.oh-my-zsh/plugins/incr
```

4、写入到 zsh

```sh
echo 'source ~/.oh-my-zsh/plugins/incr/incr\*.zsh' >> ~/.zshrc
```

5、执行生效

```sh
source ~/.zshrc
```

## 终端设置

> 终端-点击“三杠”-配置文件首选项

- 文本和背景颜色：Solarized
- 调色板：Solarized

## 常用命令

1、安装

```sh
sudo apt install
```

2、卸载

```sh
sudo apt remove
```

- 自动卸载

```sh
sudo apt autoremove
```

3、列出与该包关联文件

```sh
dpkg -L | grep 包
```

4、系统更新

```sh
sudo apt update
```

## 修改镜像源

```sh
vi /etc/apt/sources.list
```

官方源

> http://archive.ubuntu.com/ubuntu/

阿里云

> https://developer.aliyun.com/mirror/ubuntu

清华大学

> https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/
