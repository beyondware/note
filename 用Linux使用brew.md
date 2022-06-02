---
title: 用Linux使用brew
author: beyondware
tags:
  - [brew]
categories:
  - [Linux]
---

## 安装依赖

```sh
sudo dnf groupinstall "Development Tools"
```

> 不要使用 root 账号安装

- 修改源（临时，不推荐）

```sh
export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/brew.git"
```

```sh
export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/homebrew-core.git"
```

```sh
export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.aliyun.com/homebrew/homebrew-bottles"
```

- 修改源（永久，推荐）

- brew

```sh
echo 'export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/brew.git"' >> ~/.bash_profile
```

```sh
export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/brew.git"
```

- homebrew-core

```sh
echo 'export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/homebrew-core.git"' >> ~/.bash_profile
```

```sh
export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/homebrew-core.git"
```

- homebrew-bottles

```sh
echo 'export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.aliyun.com/homebrew/homebrew-bottles"' >> ~/.bash_profile
```

```sh
export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.aliyun.com/homebrew/homebrew-bottles"
```

## brew

1、安装

```sh
/bin/bash -c "$(curl -fsSL https://ghproxy.com/https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

> ==> Tapping homebrew/core 可能会卡一段时间，耐心等待。。。

2、将 Homebrew 添加到 PATH 中

```sh
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> ~/.bash_profile
```

```sh
eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
```

3、验证结果

```sh
brew doctor
```

> Your system is ready to brew. //你的系统已经准备就绪

```sh
brew --version
```

- 显示结果

```sh
Homebrew 3.4.10
Homebrew/homebrew-core (git revision bbd7ae8672a; last commit 2022-05-08)
```

## homebrew-cask

> 只适合 macOS，Linux 不需要安装

1、创建目录

```sh
sudo mkdir -p /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask
```

2、提高权限(必须提权，否则安装会出问题)

```sh
sudo chown -R $(whoami) /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask
```

3、克隆 homebrew-cask

```sh
sudo git clone https://mirrors.aliyun.com/homebrew/homebrew-cask.git /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask
```

> 可能会卡一会，请耐心等待。。。

4、验证结果

```sh
brew --version
```

- 显示结果

```sh
Homebrew 3.4.10
Homebrew/homebrew-core (git revision bbd7ae8672a; last commit 2022-05-08)
Homebrew/homebrew-cask (git revision 015649e0307; last commit 2022-05-08)
```

## 查看安装路径

```sh
"$(brew --repo)"
```

> /home/linuxbrew/.linuxbrew/Homebrew

```sh
"$(brew --repo)/Library/Taps/homebrew/homebrew-core"
```

> /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-core

```sh
"$(brew --repo)/Library/Taps/homebrew/homebrew-cask"
```

> /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask

## 提高权限

```sh
sudo chown -R $(whoami) /home/linuxbrew/.linuxbrew/Homebrew
```

```sh
sudo chown -R $(whoami) /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-core
```

```sh
sudo chown -R $(whoami) /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask
```

## 查看源

```sh
git -C "$(brew --repo)" remote -v
```

```sh
git -C "$(brew --repo homebrew/core)" remote -v
```

```sh
git -C "$(brew --repo homebrew/cask)" remote -v
```

## 官方源

```sh
git -C "$(brew --repo)" remote set-url origin https://github.com/Homebrew/brew.git
```

```sh
git -C "$(brew --repo homebrew/core)" remote set-url origin https://github.com/Homebrew/homebrew-core.git
```

```sh
git -C "$(brew --repo homebrew/cask)" remote set-url origin https://github.com/Homebrew/homebrew-cask.git
```

```sh
brew update
```

## 替换源

```sh
git -C "$(brew --repo)" remote set-url origin https://mirrors.aliyun.com/homebrew/brew.git
```

```sh
git -C "$(brew --repo homebrew/core)" remote set-url origin https://mirrors.aliyun.com/homebrew/homebrew-core.git
```

```sh
git -C "$(brew --repo homebrew/cask)" remote set-url origin https://mirrors.aliyun.com/homebrew/homebrew-cask.git
```

```sh
brew update
```

## brew 命令

```sh
Example usage:
  brew search TEXT|/REGEX/
  brew info [FORMULA|CASK...]
  brew install FORMULA|CASK...
  brew update
  brew upgrade [FORMULA|CASK...]
  brew uninstall FORMULA|CASK...
  brew list [FORMULA|CASK...]

Troubleshooting:
  brew config
  brew doctor
  brew install --verbose --debug FORMULA|CASK

Contributing:
  brew create URL [--no-fetch]
  brew edit [FORMULA|CASK...]

Further help:
  brew commands
  brew help [COMMAND]
  man brew
  https://docs.brew.sh
```

## brew 常用命令

1、安装 gcc（安装不需要 sudo）

```sh
brew install gcc
```

2、安装 brew-cask-completion（补全 cask）

```sh
brew install brew-cask-completion
```

3、安装 cask 软件（只支持 macOS）

```sh
brew install --cask 软件名
```

## 参考文档

> https://github.com/Homebrew/install

> https://docs.brew.sh/Homebrew-on-Linux

> https://docs.brew.sh/Manpage

> https://formulae.brew.sh/formula/

> https://formulae.brew.sh/cask/

> https://developer.aliyun.com/mirror/homebrew

## 注意事项

1、只支持 macOS (--cask)，好像 Linux 不能使用。

```sh
Error: Installing casks is supported only on macOS
```

2、brew 使用脚本安装，而脚本内很多地址指向 GitHub，国内安装大概率会失败，安装前需要替换源。

3、推荐使用**阿里源**，不建议使用**清华大学源**，好像有问题。

4、没有提权的问题

```sh
fatal: unsafe repository ('/home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask' is owned by someone else)
```

- 解决方法

```sh
git config --global --add safe.directory /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask
```

5、需要提权操作

```sh
error: cannot open .git/FETCH_HEAD: Permission denied
Error: Fetching /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask failed!
```

- 解决方法

```sh
sudo chown -R $(whoami) /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask
```

6、如果安装过程有冲突，建议先删除对应目录再尝试重新安装
