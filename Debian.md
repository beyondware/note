## 桌面右击无法打开终端

```sh
sudo apt install nautilus-open-terminal
```

## lxappearance（GTK+ 主题更换工具）

> https://github.com/lxde/lxappearance

```sh
sudo apt install lxappearance
```

## gnome-tweaks

```sh
sudo apt install gnome-tweaks
```

## Extension Manager

> https://github.com/mjakeman/extension-manager

```sh
sudo apt install gnome-shell-extension-manager
```

或者

```sh
sudo apt install gnome-shell-extensions
```

## Dash to Dock

```sh
sudo apt install gnome-shell-extension-dashtodock
```

## open-vm-tools

1、安装

```sh
sudo apt install open-vm-tools open-vm-tools-desktop
```

2、无法复制和粘贴

```sh
vmware-user
```

3、警告

```sh
(vmware-user:2932): Gtk-WARNING **: 15:26:01.197: gtk_disable_setlocale() must be called before gtk_init()
```

解决方法：

```sh
sudo vim /usr/share/gnome/autostart/vmware-user.desktop
```

添加

```sh
[Desktop Entry]
Type=Application
Name=VMware User Agent
Exec=vmware-user
Icon=system-run
Comment=VMware User Agent
X-GNOME-Autostart-enabled=true
```

## Zorin OS 系统升级

```sh
sudo apt install zorin-os-upgrader
```

- 如果没有任何升级选项，执行以下命令：

```sh
gsettings set com.zorin.desktop.upgrader show-test-upgrades true
```

## 系统升级

1、系统升级（推荐）

```sh
sudo apt update && sudo apt full-upgrade
```

或者（覆盖配置文件）

```sh
sudo apt update && sudo apt dist-upgrade
```

2、一键纯净更新

```sh
sudo apt update -y && apt full-upgrade -y && apt autoremove -y && apt autoclean -y
```

3、删除不必要的 rc 包（配置文件）

```sh
sudo dpkg --purge $(dpkg -l | awk '/^rc/{print $2}')
```

## 内核

1、查看当前内核

```sh
uname -r
```

2、查看已安装的内核

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

## apt-fast

1、安装 apt-fast

```sh
sudo add-apt-repository ppa:apt-fast/stable
sudo apt update
sudo apt install apt-fast
```

2、选择软件包管理器

推荐选择 apt

3、最大连接数

默认值为 5（可以设置10或者20）

4、是否略过 APT-Fast 确认对话框

5、配置 APT-Fast

```sh
sudo vim /etc/apt-fast.conf
```

最大连接数

```sh
_MAXNUM=10
```

### Aria2

```sh
_DOWNLOADER='aria2c --no-conf -c -j ${_MAXNUM} -x ${_MAXCONPERSRV} -s ${_SPLITCON} --min-split-size=${_MINSPLITSZ} --stream-piece-selector=${_PIECEALGO} -i ${DLLIST} --connect-timeout=600 --timeout=600 -m0 --header "Accept: */*"'
```

### Axel

```sh
_DOWNLOADER='axel -n ${_MAXNUM}'
```

### 镜像源

```sh
MIRRORS=( 'http://archive.ubuntu.com/ubuntu, https://mirrors.cloud.tencent.com/ubuntu, https://mirrors.aliyun.com/ubuntu' )
```

## apt-fast 常用命令

1、安装

```sh
sudo apt-fast install 
```

2、更新

```sh
sudo apt-fast update
```

3、升级

```sh
sudo apt-fast upgrade
```

4、系统升级

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

## nala

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

## nala 常用命令

1、安装

```sh
sudo nala install 包名
```

2、删除

```sh
sudo nala remove 包名
```

3、更新

```sh
sudo nala update
```

4、升级

```sh
sudo nala upgrade
```

5、命令记录

```sh
nala history
```

6、自动测速软件源

```sh
sudo nala fetch
```

7、配置文件位置

```sh
sudo vim /etc/apt/sources.list.d/nala-sources.list
```

## nala --help

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
