## Debian 启用 Contrib 和 Non-Free

```sh
sudo apt-add-repository contrib non-free-firmware
```

```sh
sudo apt-add-repository contrib non-free
```

或者

1、修改源列表

```sh
sudo vim /etc/apt/sources.list
```

2、追加

```sh
deb http://deb.debian.org/debian/ bookworm(版本代码) main contrib non-free-firmware
deb http://deb.debian.org/debian/ bookworm(版本代码) main contrib non-free
```

3、更新

```sh
sudo apt update
```

4、验证添加 Contrib 和 Non-Free

```sh
grep -E "(contrib|non-free)" /etc/apt/sources.list
```

## 清理

```sh
sudo apt autoclean
```

```sh
sudo apt autoremove
```

## 系统

1、更新升级

```sh
sudo apt update && sudo apt upgrade
```

2、系统升级

```sh
sudo apt update && sudo apt dist-upgrade
```

3、系统升级（推荐）

```sh
sudo apt update && sudo apt full-upgrade
```

4、一键纯净更新

```sh
sudo apt update -y && apt full-upgrade -y && apt autoremove -y && apt autoclean -y
```

5、删除不必要的 rc 包（配置文件）

```sh
sudo dpkg --purge $(dpkg -l | awk '/^rc/{print $2}')
```

## 内核

1、查看当前的内核

```sh
uname -r
```

2、查看所有已安装的内核

```sh
dpkg --list | grep linux-image
```

3、自动删除未使用的旧版内核

```sh
sudo apt autoremove --purge
```

4、删除特定的内核

```sh
sudo apt-get purge linux-image-x.x.x-x-generic
```

5、更新 GRUB 引导加载程序

```sh
sudo update-grub
```

## 安装

```sh
sudo apt install 包名
```

### 本地安装

```sh
sudo apt install 包.deb
```

或者

```sh
dpkg -i 包.deb
```

- 报错的话，需要修复依赖项

```sh
sudo apt --fix-broken install 或者 sudo apt install -f
```

## 删除

### 删除并*保留*相关的配置文件

```sh
sudo apt remove 包名
```

或者

```sh
dpkg -r 包名
```

### 删除并*清除*相关的配置文件

```sh
sudo apt purge 包名
```

### 自动删除和任何依赖（指定某软件）

```sh
sudo apt autoremove 包名 --purge
```

### 自动删除和任何依赖

```sh
sudo apt autoremove --purge
```

## 升级

```sh
sudo apt upgrade 包名
```

### 升级（自动处理依赖关系）

```sh
sudo apt full-upgrade 包名
```

### 列出可升级的软件

```sh
apt list --upgradable
```

### 仅升级指定的软件包

```sh
sudo apt install --only-upgrade 包名
```

### 模拟升级（但不升级任何包）

```sh
apt -s upgrade
```

## 列出已安装

```sh
apt list --installed | grep 关键字
```

或者

```sh
dpkg -L | grep 关键字
```

## 搜索

```sh
apt search --names-only 关键字  ##精准匹配
```

```sh
apt search 关键字
```

或者

```sh
apt list | grep 关键字
```

## 详细信息

### 显示包的详细信息

```sh
apt show 包名
```

### 获取详细信息

```sh
apt info 包名
```

## apt

```sh
用法： apt [选项] 命令

命令行软件包管理器 apt 提供软件包搜索，管理和信息查询等功能。
它提供的功能与其他 APT 工具相同（像 apt-get 和 apt-cache），
但是默认情况下被设置得更适合交互。

常用命令：
  list - 根据名称列出软件包
  search - 搜索软件包描述
  show - 显示软件包细节
  install - 安装软件包
  reinstall - 重新安装软件包
  remove - 移除软件包
  autoremove - 卸载所有自动安装且不再使用的软件包
  update - 更新可用软件包列表
  upgrade - 通过 安装/升级 软件来更新系统
  full-upgrade - 通过 卸载/安装/升级 来更新系统
  edit-sources - 编辑软件源信息文件
  satisfy - 使系统满足依赖关系字符串

参见 apt(8) 以获取更多关于可用命令的信息。
程序配置选项及语法都已经在 apt.conf(5) 中阐明。
欲知如何配置软件源，请参阅 sources.list(5)。
软件包及其版本偏好可以通过 apt_preferences(5) 来设置。
关于安全方面的细节可以参考 apt-secure(8).
                                         本 APT 具有超级牛力。
```

## apt-get

```sh
用法： apt-get [选项] 命令
　　　 apt-get [选项] install|remove 软件包1 [软件包2 ...]
　　　 apt-get [选项] source 软件包1 [软件包2 ...]

apt-get 可以从认证软件源下载软件包及相关信息，以便安装和升级软件包，
或者用于移除软件包。在这些过程中，软件包依赖会被妥善处理。

常用命令：
  update - 取回更新的软件包列表信息
  upgrade - 进行一次升级
  install - 安装新的软件包（注：软件包名称应当类似 libc6 而非 libc6.deb）
  reinstall - 重新安装软件包（注：软件包名称应当类似 libc6 而非 libc6.deb）
  remove - 卸载软件包
  purge - 卸载并清除软件包的配置
  autoremove - 卸载所有自动安装且不再使用的软件包
  dist-upgrade - 发行版升级，见 apt-get(8)
  dselect-upgrade - 根据 dselect 的选择来进行升级
  build-dep - 为源码包配置所需的编译依赖关系
  satisfy - 使系统满足依赖关系字符串
  clean - 删除所有已下载的包文件
  autoclean - 删除已下载的旧包文件
  check - 核对以确认系统的依赖关系的完整性
  source - 下载源码包文件
  download - 下载指定的二进制包到当前目录
  changelog - 下载指定软件包，并显示其变更日志（changelog）

参见 apt-get(8) 以获取更多关于可用命令的信息。
程序配置选项及语法都已经在 apt.conf(5) 中阐明。
欲知如何配置软件源，请参阅 sources.list(5)。
软件包及其版本偏好可以通过 apt_preferences(5) 来设置。
关于安全方面的细节可以参考 apt-secure(8).
                                         本 APT 具有超级牛力。
```

## apt-cache

```sh
用法： apt-cache [选项] 命令
       apt-cache [选项] show 软件包1 [软件包2 ...]

apt-cache 可以查询和显示已安装和可安装软件包的可用信息。
它专门工作在本地的数据缓存上，而这些缓存可以通过比如
apt-get 的 'update' 命令来更新。如果距离上一次更新的时间太久，
那么它显示的信息可能就会过时。不过作为交换，apt-cache 不依赖
当前软件源的可用性（比如：离线状态）。

常用命令：
  showsrc - 显示源文件的各项记录
  search - 根据正则表达式搜索软件包列表
  depends - 显示该软件包的依赖关系信息
  rdepends - 显示所有依赖于该软件包的软件包名字
  show - 以便于阅读的格式介绍该软件包
  pkgnames - 列出所有软件包的名字
  policy - 显示软件包的安装设置状态

参见 apt-cache(8) 以获取更多关于可用命令的信息。
程序配置选项及语法都已经在 apt.conf(5) 中阐明。
欲知如何配置软件源，请参阅 sources.list(5)。
软件包及其版本偏好可以通过 apt_preferences(5) 来设置。
关于安全方面的细节可以参考 apt-secure(8).
```

## 安装 apt-fast

1、将 APT-Fast 软件源添加到系统

```sh
sudo add-apt-repository ppa:apt-fast/stable
```

2、更新

```sh
sudo apt update
```

3、安装 apt-fast

```sh
sudo apt install apt-fast
```

4、选择软件包管理器

推荐选择 apt

5、最大连接数

默认值为 5（可以设置10或者20）

6、是否略过 APT-Fast 确认对话框

7、配置 APT-Fast

```sh
sudo vim /etc/apt-fast.conf
```

- 最大连接数

```sh
_MAXNUM=10
```

- Aria2

```sh
_DOWNLOADER='aria2c --no-conf -c -j ${_MAXNUM} -x ${_MAXCONPERSRV} -s ${_SPLITCON} --min-split-size=${_MINSPLITSZ} --stream-piece-selector=${_PIECEALGO} -i ${DLLIST} --connect-timeout=600 --timeout=600 -m0 --header "Accept: */*"'
```

- Axel

```sh
_DOWNLOADER='axel -n ${_MAXNUM}'
```

- 镜像源

```sh
MIRRORS=( 'http://archive.ubuntu.com/ubuntu, https://mirrors.cloud.tencent.com/ubuntu, https://mirrors.aliyun.com/ubuntu' )
```

8、使用 APT-Fast

- 安装

```sh
sudo apt-fast install 
```

- 更新

```sh
sudo apt-fast update
```

- 升级

```sh
sudo apt-fast upgrade
```

- 系统升级

```sh
sudo apt-fast dist-upgrade
```

## apt-fast --help

```sh
apt
Usage: apt command [options]
       apt help command [options]

Commands:
  add-repository   - Add entries to apt sources.list
  autoclean        - Erase old downloaded archive files
  autopurge        - Remove packages with their configuration files and automatically remove all unused packages
  autoremove       - Remove automatically all unused packages
  build            - Build binary or source packages from sources
  build-dep        - Configure build-dependencies for source packages
  changelog        - View a package's changelog
  check            - Verify that there are no broken dependencies
  clean            - Erase downloaded archive files
  contains         - List packages containing a file
  content          - List files contained in a package
  deb              - Install a .deb package
  depends          - Show raw dependency information for a package
  dist-upgrade     - Upgrade the system by removing/installing/upgrading packages
  download         - Download the .deb file for a package
  edit-sources     - Edit /etc/apt/sources.list with your preferred text editor
  dselect-upgrade  - Follow dselect selections
  full-upgrade     - Same as 'dist-upgrade'
  held             - List all held packages
  help             - Show help for a command
  hold             - Hold a package
  install          - Install/upgrade packages
  list             - List packages based on package names
  policy           - Show policy settings
  purge            - Remove packages and their configuration files
  recommends       - List missing recommended packages for a particular package
  rdepends         - Show reverse dependency information for a package
  reinstall        - Download and (possibly) reinstall a currently installed package
  remove           - Remove packages
  search           - Search for a package by name and/or expression
  show             - Display detailed information about a package
  showhold         - Same as 'held'
  showsrc          - Display all the source package records that match the given package name
  source           - Download source archives
  sources          - Same as 'edit-sources'
  unhold           - Unhold a package
  update           - Download lists of new/upgradable packages
  upgrade          - Perform a safe upgrade
  version          - Show the installed version of a package
```

## 安装 nala

1、添加「Volian Scar 源」

```sh
echo "deb [arch=amd64,arm64,armhf] http://deb.volian.org/volian/ scar main" | sudo tee /etc/apt/sources.list.d/volian-archive-scar-unstable.list
```

2、添加 GPG 密钥

```sh
wget -qO - https://deb.volian.org/volian/scar.key | sudo tee /etc/apt/trusted.gpg.d/volian-archive-scar-unstable.gpg > /dev/null
```

3、更新

```sh
sudo apt update
```

4、安装 nala

```sh
sudo apt install nala
```

5、nala 常用命令

- 安装

```sh
sudo nala install 包名
```

- 删除

```sh
sudo nala remove 包名
```

- 更新

```sh
sudo nala update
```

- 升级

```sh
sudo nala upgrade
```

- 命令记录

```sh
nala history
```

- 自动测速软件源

```sh
sudo nala fetch
```

- 配置文件位置

```sh
sudo vim /etc/apt/sources.list.d/nala-sources.list
```

## nala

```sh
命令：

install: 安装包
remove: 删除包
purge: 清除包
update：更新包列表，升级系统
upgrade: 更新别名
fetch：获取快速镜像以加快下载速度
show: 显示包详情
history: 显示命令历史
clean：清除检索到的包文件的本地存储库

可选参数：

-h, --help: 显示帮助信息并退出
-y, --assume-yes: 假设所有提示为“是”并以非交互方式运行
-d, --download-only: 包文件只被检索，不解包或安装
-v, --verbose: 记录额外的调试信息
--no-update: 跳过更新包列表
--no-autoremove: 阻止 Nala 自动删除包
--remove-essential：允许删除基本包
--raw-dpkg: 跳过所有格式并获得原始dpkg输出
--update：更新包列表
--debug: 记录额外的调试信息
--version: 显示程序的版本号并退出
--license: 读取编译入软件的许可证，然后读取 GPLv3
```
