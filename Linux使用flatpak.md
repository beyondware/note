## 安装 Flatpak

### Fedora（默认：已安装）

```sh
sudo dnf install flatpak
```

### Ubuntu

```sh
sudo apt install flatpak
```

- GNOME 提供 Flatpak 插件

```sh
sudo apt install gnome-software-plugin-flatpak
```

- KDE 提供 Flatpak 插件

```sh
sudo apt install plasma-discover-backend-flatpak
```

### Arch

```sh
sudo pacman -Syu
```

```sh
sudo pacman -S flatpak
```

## 添加远程仓库，需重启系统

> error: No remote refs found similar to ‘flathub’ //未发现类似于 "flathub" 的远程引用

### 添加 Flathub 仓库

```sh
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

- 添加 Flabhub Beta 仓库

```sh
flatpak remote-add --if-not-exists flathub-beta https://flathub.org/beta-repo/flathub-beta.flatpakrepo
```

- 安装

```sh
flatpak install flathub 应用程序ID
```

### 添加 fedora 仓库

```sh
flatpak remote-add --if-not-exists fedora oci+https://registry.fedoraproject.org
```

- 添加 fedora testing 仓库

```sh
flatpak remote-add --if-not-exists fedora-testing oci+https://registry.fedoraproject.org#testing
```

- 安装

```sh
flatpak install fedora 应用程序ID
```

### 添加 GNOME nightly 仓库

```sh
flatpak remote-add --if-not-exists gnome-nightly https://nightly.gnome.org/gnome-nightly.flatpakrepo
```

- 安装

```sh
flatpak install gnome-nightly 应用程序ID
```

### 添加 KDE nightly 仓库

```sh
flatpak remote-add --if-not-exists kdeapps --from https://distribute.kde.org/kdeapps.flatpakrepo
```

- 安装

```sh
flatpak install kdeapps 应用程序ID
```

## 删除远程仓库

```sh
flatpak remote-delete
```

- 例如：删除 flathub 仓库

```sh
flatpak remote-delete flathub
```

## 列出已添加的软件远程仓库

```sh
flatpak remotes
```

## 常用命令

### 搜索远程仓库中的应用程序

```sh
flatpak search 关键字
```

### 列出

1、列出所有安装

```sh
flatpak list
```

2、列出已安装

```sh
flatpak list --app
```

### 查看详细信息

```sh
flatpak info 应用程序ID
```

### 安装

1、安装（多种安装方式）

```sh
flatpak install flathub com.github.tchx84.Flatseal
```

```sh
flatpak install https://dl.flathub.org/repo/appstream/com.github.tchx84.Flatseal.flatpakref
```

> Installation complete. //表示安装完成

> 必须全部打勾 ✔ 才能安装成功

2、安装报错（网络环境问题，需要多次安装尝试）

> error: Unable to load summary from remote flathub: Could not connect: 拒绝连接

### 运行程序

```sh
flatpak run 应用程序ID
```

### 卸载

1、卸载特定

```sh
flatpak uninstall 应用程序ID
```

> Uninstall complete. //卸载完成

- 卸载和删除特定应用程序的数据

```sh
flatpak uninstall --delete-data 应用程序ID
```

2、卸载所有

```sh
flatpak uninstall --all
```

- 卸载和删除所有与Flatpak相关数据

```sh
flatpak uninstall --all --delete-data
```

3、卸载未使用

```sh
flatpak uninstall --unused
```

### 更新

1、更新所有

```sh
flatpak update
```

2、更新特定

```sh
flatpak update --app 应用程序ID
```

## 构建

### Fedora

```sh
sudo dnf install flatpak-builder
```

### Ubuntu

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

## 帮助

```sh
flatpak --help
```

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
