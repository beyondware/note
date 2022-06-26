---
title: 用Linux使用flatpak
author: beyondware
tags:
  - [flatpak]
categories:
  - [Linux]
---

## 基本操作

### 安装 Flatpak

- Fedora(默认已安装)

```sh
sudo dnf install flatpak
```

- Ubuntu

```sh
sudo apt install flatpak
```

### 提供额外插件

- GNOME 提供了 Flatpak 插件

```sh
sudo apt install gnome-software-plugin-flatpak
```

- KDE 提供了 Flatpak 插件

```sh
sudo apt install plasma-discover-backend-flatpak
```

## 远程仓库

### 添加远程仓库

> error: No remote refs found similar to ‘flathub’ //未发现类似于 "flathub" 的远程引用

- 添加 Flathub 仓库

```sh
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

- Flabhub Beta

```sh
flatpak remote-add --if-not-exists flathub-beta https://flathub.org/beta-repo/flathub-beta.flatpakrepo
```

```sh
flatpak install flathub 软件名ID
```

- 添加 fedora 仓库

```sh
flatpak remote-add --if-not-exists fedora oci+https://registry.fedoraproject.org
```

- fedora testing

```sh
flatpak remote-add --if-not-exists fedora-testing oci+https://registry.fedoraproject.org#testing
```

```sh
flatpak install fedora 软件名ID
```

- 添加 GNOME nightly 仓库

```sh
flatpak remote-add --if-not-exists gnome-nightly https://nightly.gnome.org/gnome-nightly.flatpakrepo
```

```sh
flatpak install gnome-nightly 软件名ID
```

- 添加 KDE nightly 仓库

```sh
flatpak remote-add --if-not-exists kdeapps --from https://distribute.kde.org/kdeapps.flatpakrepo
```

```sh
flatpak install kdeapps 软件名ID
```

### 删除远程仓库

```sh
flatpak remote-delete
```

- 例如：flathub

```sh
flatpak remote-delete flathub
```

### 查看远程仓库

1、查看已添加的软件远程仓库

```sh
flatpak remotes
```

2、列出可安装的应用程序

```sh
flatpak remote-ls --app
```

3、列出可安装的应用程序和运行时环境

```sh
flatpak remote-ls
```

## 常用命令

### 查看

1、查找远程仓库中的应用

```sh
flatpak search
```

2、查看已安装的应用程序

```sh
flatpak list --app
```

3、查看已安装的应用程序和运行时环境

```sh
flatpak list
```

4、查看已安装应用程序的详细信息

```sh
flatpak info
```

### 安装

1、安装

```sh
flatpak install
```

2、安装（多种方式）

```sh
flatpak install flathub com.github.tchx84.Flatseal
```

```sh
flatpak install https://dl.flathub.org/repo/appstream/com.github.tchx84.Flatseal.flatpakref
```

> Installation complete. //表示安装完成

> 必须全部打勾 ✔ 才能安装成功

3、报错（网络环境问题，需要多次安装尝试）

> error: Unable to load summary from remote flathub: Could not connect: 拒绝连接

### 运行

```sh
flatpak run
```

### 卸载

```sh
flatpak uninstall
```

> Uninstall complete. //卸载完成

### 更新

- 更新远程仓库的元数据

```sh
flatpak update
```

### 帮助

- 参考 Flatpak 帮助

```sh
flatpak --help
```

### 构建

- Fedora

```sh
sudo dnf install flatpak-builder
```

- Ubuntu

```sh
sudo add-apt-repository ppa:alexlarsson/flatpak
```

```sh
sudo apt update
```

```sh
sudo apt install flatpak-builder elfutils
```

## 参考文档

1、Flatpak

> https://flatpak.org/setup/

> https://docs.flatpak.org/zh_CN/latest/

2、Flathub

> https://www.flathub.org/apps

3、上海交通大学镜像源（**慎用**：好像没有同步更新了）

> https://mirrors.sjtug.sjtu.edu.cn/docs/flathub

4、gnome-nightly

> https://wiki.gnome.org/Apps/Nightly

5、kdeapps

> https://community.kde.org/Guidelines_and_HOWTOs/Flatpak

## 全部命令

```sh
Usage:
  flatpak [OPTION…] COMMAND

Builtin Commands:
 Manage installed applications and runtimes
  install                Install an application or runtime
  update                 Update an installed application or runtime
  uninstall              Uninstall an installed application or runtime
  mask                   Mask out updates and automatic installation
  pin                    Pin a runtime to prevent automatic removal
  list                   List installed apps and/or runtimes
  info                   Show info for installed app or runtime
  history                Show history
  config                 Configure flatpak
  repair                 Repair flatpak installation
  create-usb             Put applications or runtimes onto removable media

 Find applications and runtimes
  search                 Search for remote apps/runtimes

 Manage running applications
  run                    Run an application
  override               Override permissions for an application
  make-current           Specify default version to run
  enter                  Enter the namespace of a running application
  ps                     Enumerate running applications
  kill                   Stop a running application

 Manage file access
  documents              List exported files
  document-export        Grant an application access to a specific file
  document-unexport      Revoke access to a specific file
  document-info          Show information about a specific file

 Manage dynamic permissions
  permissions            List permissions
  permission-remove      Remove item from permission store
  permission-set         Set permissions
  permission-show        Show app permissions
  permission-reset       Reset app permissions

 Manage remote repositories
  remotes                List all configured remotes
  remote-add             Add a new remote repository (by URL)
  remote-modify          Modify properties of a configured remote
  remote-delete          Delete a configured remote
  remote-ls              List contents of a configured remote
  remote-info            Show information about a remote app or runtime

 Build applications
  build-init             Initialize a directory for building
  build                  Run a build command inside the build dir
  build-finish           Finish a build dir for export
  build-export           Export a build dir to a repository
  build-bundle           Create a bundle file from a ref in a local repository
  build-import-bundle    Import a bundle file
  build-sign             Sign an application or runtime
  build-update-repo      Update the summary file in a repository
  build-commit-from      Create new commit based on existing ref
  repo                   Show information about a repo

Help Options:
  -h, --help              Show help options

Application Options:
  --version               Print version information and exit
  --default-arch          Print default arch and exit
  --supported-arches      Print supported arches and exit
  --gl-drivers            Print active gl drivers and exit
  --installations         Print paths for system installations and exit
  --print-updated-env     Print the updated environment needed to run flatpaks
  --print-system-only     Only include the system installation with --print-updated-env
  -v, --verbose           Show debug information, -vv for more detail
  --ostree-verbose        Show OSTree debug information
```
