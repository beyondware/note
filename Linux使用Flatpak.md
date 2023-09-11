## 安装 Flatpak

> https://flatpak.org/setup/

> https://docs.flatpak.org/en/latest/

### Fedora（默认：已安装）

```sh
sudo dnf install flatpak
```

### Ubuntu

```sh
sudo apt install flatpak
```

1、GNOME 提供插件

```sh
sudo apt install gnome-software-plugin-flatpak gnome-software-plugin-snap
```

2、KDE 提供插件

```sh
sudo apt install plasma-discover-backend-flatpak plasma-discover-backend-snap
```

### Arch

```sh
sudo pacman -Syyu
```

```sh
sudo pacman -S flatpak
```

## freedesktop-sdk

> https://gitlab.com/freedesktop-sdk/freedesktop-sdk

```sh
Name                     Application ID                                 Version      Branch          Installation
Freedesktop Platform     org.freedesktop.Platform                       22.08.11     22.08           system
Mesa                     org.freedesktop.Platform.GL.default            23.0.2       22.08           system
Mesa (Extra)             org.freedesktop.Platform.GL.default            23.0.2       22.08-extra     system
nvidia-390-154           org.freedesktop.Platform.GL.nvidia-390-154                  1.4             system
Intel                    org.freedesktop.Platform.VAAPI.Intel                        22.08           system
openh264                 org.freedesktop.Platform.openh264              2.1.0        2.2.0           system
```  

## 构建 Flatpak

### Fedora

```sh
sudo dnf install flatpak-builder
```

### Ubuntu

```sh
sudo add-apt-repository ppa:alexlarsson/flatpak
sudo apt update
sudo apt install flatpak-builder elfutils
```

## Flatpak 运行等级

```sh
flatpak --system（默认）
```

```sh
flatpak --user 
```

## Flatpak 存储库

### flathub

> error: No remote refs found similar to ‘flathub’ //未发现类似于 "flathub" 的远程

```sh
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

- 如果失败，可以使用如下命令：

```sh
flatpak remote-add --if-not-exists flathub https://mirror.sjtu.edu.cn/flathub/flathub.flatpakrepo
```

### flathub-beta

```sh
flatpak remote-add --if-not-exists flathub-beta https://flathub.org/beta-repo/flathub-beta.flatpakrepo
```

#### 安装

```sh
flatpak install flathub 应用程序ID
```

- 访问系统文件（慎用）

```sh
sudo flatpak override 应用程序ID --filesystem=host
```

#### 修改镜像源

> https://mirror.sjtu.edu.cn/docs/flathub

```sh
sudo flatpak remote-modify flathub --url=https://mirror.sjtu.edu.cn/flathub
```

#### 报错汇总

1、"error: Unable to load summary from remote flathub: Can't fetch summary from disabled remote 'flathub,"

```sh
flatpak remote-modify --enable flathub
```

2、XDG_DATA_DIRS is not set on fish shell. No desktop entry appears after install an app.

```sh
XDG_DATA_DIRS=报错路径1:路径2
```

- 路径

> /var/lib/flatpak/exports/share

> /home/$USER/.local/share/flatpak/exports/share

```sh
export XDG_DATA_DIRS
```

- 重启系统，查看输出结果。

```sh
echo $XDG_DATA_DIRS
```

3、error: Unable to load summary from remote flathub: Could not connect: 拒绝连接

> 网络问题，需多次安装尝试。

4、Warning: org.freedesktop.Platform.openh264 not installed

```sh
flatpak install flathub org.freedesktop.Platform.openh264
```

5、error: Unable to load summary from remote flathub: Server returned status 308: Unknown Error

#### 还原官方源

```sh
sudo flatpak remote-modify flathub --url=https://dl.flathub.org/repo/
```

### fedora

```sh
flatpak remote-add --if-not-exists fedora oci+https://registry.fedoraproject.org
```

### fedora-testing

```sh
flatpak remote-add --if-not-exists fedora-testing oci+https://registry.fedoraproject.org#testing
```

#### 安装

```sh
flatpak install fedora 应用程序ID
```

### nome-nightly

> https://wiki.gnome.org/Apps/Nightly

```sh
flatpak remote-add --if-not-exists gnome-nightly https://nightly.gnome.org/gnome-nightly.flatpakrepo
```

#### 安装

```sh
flatpak install gnome-nightly 应用程序ID
```

### kdeapps

> https://userbase.kde.org/Tutorials/Flatpak

> https://develop.kde.org/docs/packaging/flatpak/

```sh
flatpak remote-add --if-not-exists kdeapps --from https://distribute.kde.org/kdeapps.flatpakrepo
```

#### 安装

```sh
flatpak install kdeapps 应用程序ID
```

## 查看 Flatpak 存储库

```sh
flatpak remotes
```

```sh
flatpak remotes -d
```

### 查看系统源

```sh
flatpak remotes --system -d
```

### 查看用户源

```sh
flatpak remotes --user -d
```

## 删除 Flatpak 存储库

```sh
flatpak remote-delete 仓库名
```

- 例如：删除 flathub

```sh
flatpak remote-delete flathub
```

## 常用命令

### 安装

#### 方案一

```sh
flatpak install flathub com.github.tchx84.Flatseal
```

#### 方案二

```sh
flatpak install https://dl.flathub.org/repo/appstream/com.github.tchx84.Flatseal.flatpakref
```

> Installation complete. //表示安装完成

> 必须全部打勾 ✔ 才能安装成功

### 降级

1、获取应用程序ID

```sh
flatpak list --app
```

2、列出以前的版本并获取对应<Commit值>

```sh
flatpak remote-info --log flathub 应用程序ID
```

3、降级 Flatpack 包

```sh
sudo flatpak update --commit=<Commit值> 应用程序ID
```

4、检查是否降级软件包

```sh
flatpak update
```

### 卸载

#### 卸载指定软件

```sh
flatpak uninstall 应用程序ID
```

> Uninstall complete. //卸载完成

#### 卸载指定软件和Flatpak相关数据

```sh
flatpak uninstall --delete-data 应用程序ID
```

#### 卸载所有

```sh
flatpak uninstall --all
```

#### 卸载所有和Flatpak相关数据

```sh
flatpak uninstall --all --delete-data
```

#### 卸载未使用

```sh
flatpak uninstall --unused 或者 flatpak remove --unused
```

#### 删除缓存文件

```sh
sudo rm -rf /var/tmp/flatpak-cache-*
```

### 运行

```sh
flatpak run 应用程序ID
```

### 更新

1、更新所有

```sh
flatpak update
```

2、更新指定软件

```sh
flatpak update --app 应用程序ID
```

### 搜索

```sh
flatpak search 关键字
```

### 列出

1、列出所有

```sh
flatpak list
```

2、列出已安装

```sh
flatpak list --app
```

3、列出所有已安装 flatpak，包括安装类型、大小和应用程序 ID

```sh
flatpak --columns=app,name,size,installation list
```

### 详细信息

```sh
flatpak info 应用程序ID
```

## flatpak --help

```sh
用法：
  flatpak [选项…] 命令

内置命令：
 管理已安装的应用程序和运行时
  install                安装应用程序或运行时
  update                 更新已安装的应用程序或运行时
  uninstall              卸载已安装的应用程序或运行时
  mask                   屏蔽更新和自动安装
  pin                    置顶运行时以避免自动移除
  list                   列出已安装的应用和/或运行时
  info                   显示已安装应用或运行时的信息
  history                显示历史
  config                 配置 flatpak
  repair                 修复 flatpak 安装
  create-usb             将应用程序或运行时放到可移动媒体上

查找应用程序和运行时
  search                 搜索远程仓库的应用/运行时

管理正在运行的应用程序
  run                    运行应用程序
  override               覆盖应用程序的权限
  make-current           指定要运行的默认版本
  enter                  进入正在运行应用程序的命名空间
  ps                     列举正在运行的应用程序
  kill                   停止正在运行的应用程序

管理文件访问
  documents              列出导出的文件
  document-export        同意应用程序对特定文件的访问
  document-unexport      撤消对特定文件的访问
  document-info          显示有关特定文件的信息

管理动态权限
  permissions            列出权限
  permission-remove      从权限存储中移除项目
  permission-set         设置权限
  permission-show        显示应用权限
  permission-reset       重置应用权限

管理远程仓库
  remotes                列出所有已配置的远程仓库
  remote-add             添加新的远程仓库（通过网址）
  remote-modify          修改已配置远程仓库的属性
  remote-delete          删除已配置的远程仓库
  remote-ls              列出已配置远程仓库的内容
  remote-info            显示远程仓库中应用或运行时的有关信息

构建应用程序
  build-init             初始化用于构建的目录
  build                  在构建目录中运行构建命令
  build-finish           完成导出的构建目录
  build-export           将构建目录导出到仓库
  build-bundle           从本地仓库中的引用创建捆绑包文件
  build-import-bundle    导入捆绑包文件
  build-sign             签署应用程序或运行时
  build-update-repo      更新仓库中的摘要文件
  build-commit-from      基于现有引用创建新的交付
  repo                   显示仓库的有关信息

帮助选项：
  -h, --help              显示帮助选项

应用程序选项：
  --version               打印版本信息并退出
  --default-arch          显示默认架构并退出
  --supported-arches      显示支持架构并退出
  --gl-drivers            显示激活 gl 驱动并退出
  --installations         显示系统安装路径并退出
  --print-updated-env     显示运行 flatpak 应用所需的已更新环境
  --print-system-only     仅包含带有 --print-updated-env 的系统安装
  -v, --verbose           显示调试信息，-vv 显示更多详情
  --ostree-verbose        显示 OSTree 调试信息
```
