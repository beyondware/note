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

### homebrew-bottles

```sh
export HOMEBREW_INSTALL_FROM_API=1
```

```sh
echo 'export HOMEBREW_API_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles/api"' >> ~/.bash_profile
```

```sh
export HOMEBREW_API_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles/api"
```

```sh
echo 'export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles"' >> ~/.bash_profile
```

```sh
export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles"
```

> https://help.mirrors.cernet.edu.cn/homebrew-bottles/

### brew

```sh
echo 'export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git"' >> ~/.bash_profile
```

```sh
export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git"
```

### homebrew-core


```sh
echo 'export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git"' >> ~/.bash_profile
```

```sh
export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git"
```

> https://mirrors.tuna.tsinghua.edu.cn/help/homebrew/

### pypi

```sh
export HOMEBREW_PIP_INDEX_URL="https://pypi.tuna.tsinghua.edu.cn/simple"
```

> https://help.mirrors.cernet.edu.cn/pypi/

## brew

1、安装

### 官方源

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

> https://github.com/Homebrew/install

### 中科大源

```sh
/bin/bash -c "$(curl -fsSL https://mirrors.ustc.edu.cn/misc/brew-install.sh)"
```

> https://mirrors.ustc.edu.cn/help/brew.git.html

> ==> Downloading and installing Homebrew... //可能会卡一段时间，耐心等待。。。

2、将 brew 程序的相关路径加入到环境变量中

```sh
test -d /home/linuxbrew/.linuxbrew && eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
```

```sh
test -r ~/.bash_profile && echo "eval \"\$($(brew --prefix)/bin/brew shellenv)\"" >> ~/.bash_profile
```

```sh
test -r ~/.profile && echo "eval \"\$($(brew --prefix)/bin/brew shellenv)\"" >> ~/.profile
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

## 新版

### 替换源

#### brew

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

#### homebrew-cask（只适合 macOS）

```sh
brew tap --custom-remote --force-auto-update homebrew/cask https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask.git
```

```sh
brew tap --custom-remote --force-auto-update homebrew/cask-versions https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask-versions.git
```

```sh
brew tap --custom-remote --force-auto-update homebrew/cask-fonts https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask-fonts.git
```

```sh
brew tap --custom-remote --force-auto-update homebrew/cask-drivers https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask-drivers.git
```

```sh
brew tap --custom-remote --force-auto-update homebrew/services https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-services.git
```

```sh
brew update
```

#### 输出信息

```sh
brew --version
```

```sh
Homebrew 4.0.16
Homebrew/homebrew-core (git revision 456d5eec8dc; last commit 2023-05-07)
Homebrew/homebrew-cask (git revision 2fac4c7af7; last commit 2023-05-07)
```

#### 报错信息

```sh
Please note that these warnings are just used to help the Homebrew maintainers
with debugging if you file an issue. If everything you use Homebrew for is
working fine: please don't worry or file an issue; just ignore this. Thanks!

Warning: You have an unnecessary local Cask tap.
This can cause problems installing up-to-date casks.
Please remove it by running:
  brew untap homebrew/cask

Warning: You have an unnecessary local Core tap!
This can cause problems installing up-to-date formulae.
Please remove it by running:
 brew untap homebrew/core
```

### 恢复源

#### brew

```sh
unset HOMEBREW_BREW_GIT_REMOTE
```

```sh
git -C "$(brew --repo)" remote set-url origin https://github.com/Homebrew/brew
```

#### homebrew-core

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

#### homebrew-cask（只适合 macOS）

```sh
brew tap --custom-remote --force-auto-update homebrew/cask https://github.com/Homebrew/homebrew-cask
```

```sh
brew tap --custom-remote --force-auto-update homebrew/cask-versions https://github.com/Homebrew/homebrew-cask-versions
```

```sh
brew tap --custom-remote --force-auto-update homebrew/cask-fonts https://github.com/Homebrew/homebrew-cask-fonts
```

```sh
brew tap --custom-remote --force-auto-update homebrew/cask-drivers https://github.com/Homebrew/homebrew-cask-drivers
```

```sh
brew tap --custom-remote --force-auto-update homebrew/services https://github.com/Homebrew/homebrew-services
```

```sh
brew update
```

## 当前源

```sh
git -C "$(brew --repo)" remote -v
```

> /home/linuxbrew/.linuxbrew/Homebrew

```sh
git -C "$(brew --repo homebrew/core)" remote -v
```

> /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-core

```sh
git -C "$(brew --repo homebrew/cask)" remote -v
```

> /home/linuxbrew/.linuxbrew/Homebrew/Library/Taps/homebrew/homebrew-cask

## 旧版

### 替换源

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

### 恢复源

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

5、查询软件库

> https://docs.brew.sh/Manpage

> https://formulae.brew.sh/

## 注意事项

1、只支持 macOS (--cask)

```sh
Error: Invalid `--cask` usage: Casks do not work on Linux
```

2、报错信息

```sh
Disable this behaviour by setting HOMEBREW_NO_INSTALL_CLEANUP.
Hide these hints with HOMEBREW_NO_ENV_HINTS (see `man brew`).
```

- 解决方法

```sh
export HOMEBREW_NO_INSTALL_CLEANUP=TRUE
```

3、如果安装过程有冲突，建议先删除**对应目录**再尝试重新安装。

```sh
sudo rm -rf /home/linuxbrew
```
