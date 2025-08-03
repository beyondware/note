# Flatpak 安装

## Debian

```sh
sudo apt install flatpak
```

### 安装 GNOME 插件

```sh
sudo apt install gnome-software-plugin-flatpak
```

### 安装 KDE 插件

```sh
sudo apt install plasma-discover-backend-flatpak
```

## Fedora

```sh
sudo dnf install flatpak
```

## Arch

```sh
sudo pacman -S flatpak
```

## 参考

https://docs.flatpak.org/en/latest/

https://flatpak.org/setup/

https://wiki.archlinux.org/title/Flatpak

# 第三方存储库

## fedora 存储库

```sh
flatpak remote-add --if-not-exists fedora oci+https://registry.fedoraproject.org
```

### 安装

```sh
flatpak install fedora 应用程序ID
```

## gnome-nightly 存储库

```sh
flatpak remote-add --if-not-exists gnome-nightly https://nightly.gnome.org/gnome-nightly.flatpakrepo
```

### 安装

```sh
flatpak install gnome-nightly 应用程序ID
```

### 列出所有

```sh
flatpak remote-ls --app gnome-nightly
```

### 参考

> https://wiki.gnome.org/Apps/Nightly

## KDE 存储库

直接从仓库下载

> https://userbase.kde.org/Tutorials/Flatpak

> https://cdn.kde.org/flatpak/

# 列出 Flatpak 存储库

```sh
flatpak remotes
```

# flatpak 常用命令

## 列出已配置的 Flatpak 仓库中的可用软件包

```sh
flatpak remote-ls
```

--updates：只显示有更新的内容

## 安装

### 方法一

```sh
flatpak install flathub com.github.tchx84.Flatseal
```

### 方法二

```sh
flatpak install https://dl.flathub.org/repo/appstream/com.github.tchx84.Flatseal.flatpakref
```

> Installation complete. //表示安装完成

> 必须全部打勾 ✔ 才能安装成功

## 安装失败，修复与本地安装不一致问题

```sh
flatpak repair
```

再重新启动 flatpak 服务

```sh
sudo systemctl restart flatpak-system-helper.service
```

## 降级

1、获取 appid

```sh
flatpak list --app
```

2、列出以前的版本并获取对应<Commit值>

```sh
flatpak remote-info --log flathub appid
```

3、降级包

```sh
sudo flatpak update --commit=<Commit值> appid
```

4、检查是否降级成功

```sh
flatpak update
```

## 卸载

### 卸载软件

```sh
flatpak uninstall appid
```

> Uninstall complete. //卸载完成

### 卸载软件和 Flatpak 相关数据（推荐）

```sh
flatpak uninstall --delete-data appid
```

### 卸载所有和 Flatpak 相关数据

```sh
flatpak uninstall --all --delete-data
```

### 删除已安装但未使用的应用程序运行时和扩展

```sh
flatpak uninstall --unused
或者
flatpak remove --unused
```

## 运行 flatpak

```sh
flatpak run appid
```

## 更新

### 更新所有

```sh
flatpak update
```

### 更新软件

```sh
flatpak update --app appid
```

## 搜索

```sh
flatpak search 关键字
```

## 列出

### 列出已安装的应用程序和运行时

```sh
flatpak list
```

### 仅列出已安装的应用程序

```sh
flatpak list --app
```

### 列出所有已安装 flatpak，包括安装类型、大小和应用程序 ID

```sh
flatpak --columns=app,name,size,installation list
```

## 查看详细信息

```sh
flatpak info appid
```

## 删除缓存

```sh
sudo rm -rf /var/tmp/flatpak-cache-*
```

# flatpak --help

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
