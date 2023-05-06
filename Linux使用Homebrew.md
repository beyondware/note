## 安装依赖（非 root 账号）

### Fedora

```sh
sudo dnf groupinstall "Development Tools"
```

```sh
sudo dnf install procps-ng curl file git
```

### Debian

```sh
sudo apt install build-essential procps curl file git
```

## 设置环境变量

### brew

```sh
echo 'export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/brew.git"' >> ~/.bash_profile
```

```sh
export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/brew.git"
```

### homebrew-core

```sh
echo 'export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/homebrew-core.git"' >> ~/.bash_profile
```

```sh
export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/homebrew-core.git"
```

### homebrew-bottles

```sh
echo 'export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.aliyun.com/homebrew/homebrew-bottles"' >> ~/.bash_profile
```

```sh
export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.aliyun.com/homebrew/homebrew-bottles"
```

- Brew 4.0 版本后默认使用元数据 JSON API 获取仓库信息，因此在大部分情况下不再需要配置（包括：homebrew-core、homebrew-cask）

```sh
export HOMEBREW_INSTALL_FROM_API=1
```

```sh
echo 'export HOMEBREW_API_DOMAIN="https://mirrors.cernet.edu.cn/homebrew-bottles/api"' >> ~/.bash_profile
```

```sh
export HOMEBREW_API_DOMAIN="https://mirrors.cernet.edu.cn/homebrew-bottles/api"
```

- PyPI

```sh
export HOMEBREW_PIP_INDEX_URL="https://mirrors.cernet.edu.cn/pypi/web/simple"
```

> https://docs.brew.sh/Installation

> https://developer.aliyun.com/mirror/homebrew

> https://help.mirrors.cernet.edu.cn/homebrew-bottles/

## brew

1、安装

### 官方源

```sh
/bin/bash -c "$(curl -fsSL https://ghproxy.com/https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

> https://github.com/Homebrew/install

### 中科大源

```sh
/bin/bash -c "$(curl -fsSL https://mirrors.ustc.edu.cn/misc/brew-install.sh)"
```

> https://mirrors.ustc.edu.cn/help/brew.git.html

> ==> Downloading and installing Homebrew... //可能会卡一段时间，耐心等待。。。

2、将 Homebrew 添加到 PATH 中

```sh
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> ~/.bash_profile
```

- 或者

```sh
test -d /home/linuxbrew/.linuxbrew && eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
```

```sh
test -r ~/.bash_profile && echo "eval \"\$($(brew --prefix)/bin/brew shellenv)\"" >> ~/.bash_profile
```

```sh
echo "eval \"\$($(brew --prefix)/bin/brew shellenv)\"" >> ~/.profile
```

> https://docs.brew.sh/Homebrew-on-Linux

3、验证结果

```sh
brew doctor
```

> Your system is ready to brew. //你的系统已经准备就绪

```sh
brew --version
```

- 输出结果

```sh
Homebrew 4.0.16
```

## homebrew-cask（4.0非必要，只适合 macOS）

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

- 输出结果

```sh
Homebrew 4.0.16
Homebrew/homebrew-cask (git revision 7f4566d8b8e; last commit 2023-05-05)
```

5、报错信息

```sh
error: cannot open .git/FETCH_HEAD: Permission denied
Error: Fetching /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask failed!
```

- 解决方法

```sh
sudo chown -R $(whoami) /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask
```
------

```sh
fatal: detected dubious ownership in repository at '/home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask'
To add an exception for this directory, call:

	git config --global --add safe.directory /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask
Homebrew/homebrew-cask (no Git repository)

```

- 解决方法

```sh
git config --global --add safe.directory /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask
```

## 查看安装路径

```sh
"$(brew --repo)"
```

> /home/linuxbrew/.linuxbrew/Homebrew

```sh
"$(brew --repo homebrew/core)"
```

> /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-core

```sh
"$(brew --repo homebrew/cask)"
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

### 旧版本

#### brew

```sh
git -C "$(brew --repo)" remote set-url origin https://github.com/Homebrew/brew.git
```

#### homebrew-core

```sh
git -C "$(brew --repo homebrew/core)" remote set-url origin https://github.com/Homebrew/homebrew-core.git
```

#### homebrew-cask

```sh
git -C "$(brew --repo homebrew/cask)" remote set-url origin https://github.com/Homebrew/homebrew-cask.git
```

#### 更新

```sh
brew update
```

### 新版本

#### brew

```sh
unset HOMEBREW_BREW_GIT_REMOTE
```

```sh
git -C "$(brew --repo)" remote set-url origin https://github.com/Homebrew/brew
```

#### homebrew-core

```sh
unset HOMEBREW_API_DOMAIN
```

```sh
unset HOMEBREW_CORE_GIT_REMOTE
```

```sh
brew tap --custom-remote homebrew/core https://github.com/Homebrew/homebrew-core
```

```sh
brew tap --custom-remote homebrew/command-not-found https://github.com/Homebrew/homebrew-command-not-found
```

```sh
brew update
```

## 替换源

### 旧版本

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

### 新版本

#### brew

```sh
export HOMEBREW_API_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles/api"
```

```sh
export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git"
```

```sh
brew update
```

#### homebrew-core

```sh
export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git"
```

```sh
brew tap --custom-remote --force-auto-update homebrew/core https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git
```

```sh
brew tap --custom-remote --force-auto-update homebrew/command-not-found https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-command-not-found.git
```

```sh
brew update
```

## brew --help

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

1、安装 gcc（brew 安装无需 sudo）

```sh
brew install gcc
```

2、安装 brew-cask-completion（macOS）

```sh
brew install brew-cask-completion
```

3、安装 cask 软件（macOS）

```sh
brew install --cask 软件名
```

4、清除旧版本软件包

```sh
brew cleanup
```

## 参考

> https://docs.brew.sh/Manpage

> https://formulae.brew.sh/

## 注意事项

1、只支持 macOS (--cask)

```sh
Error: Invalid `--cask` usage: Casks do not work on Linux
```

2、推荐使用**阿里源**，不建议使用**清华大学源**，好像有问题。

3、报错信息

```sh
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
```

- 解决方法

```sh
export HOMEBREW_NO_INSTALL_CLEANUP=TRUE
```

4、如果安装过程有冲突，建议先删除**对应目录**再尝试重新安装。

```sh
sudo rm -rf /home/linuxbrew
```
