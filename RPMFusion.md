# 系统

1、升级

```sh
sudo dnf upgrade --refresh
```

2、检查是否安装 RPM Fusion

```sh
dnf repolist | grep rpmfusion
```

3、查看存储库列表

```sh
dnf repolist
```

# Fedora

## free

```sh
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
```

## nonfree

```sh
sudo dnf install https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

# Silverblue、Kinoite、CoreOS

## free

```sh
sudo rpm-ostree install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
```

## nonfree

```sh
sudo rpm-ostree install https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

# Rocky、CentOS

## EPEL

1、启用 CRB 存储库

```sh
sudo dnf config-manager --set-enabled crb
```

2、导入 EPEL

```sh
sudo dnf install --nogpgcheck https://dl.fedoraproject.org/pub/epel/epel-release-latest-$(rpm -E %rhel).noarch.rpm
```

CentOS 额外添加，Rocky 不需要

```
sudo dnf install --nogpgcheck https://dl.fedoraproject.org/pub/epel/epel-next-release-latest-$(rpm -E %rhel).noarch.rpm
```

## RPM Fusion

```sh
sudo dnf install --nogpgcheck https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-$(rpm -E %rhel).noarch.rpm
```

```sh
sudo dnf install --nogpgcheck https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-$(rpm -E %rhel).noarch.rpm
```

- 安装 RPM Fusion AppStream 元数据，为 GNOME 和 KDE Discover 提供软件包

```sh
sudo dnf groupupdate core
```

- 启用 GStreamer 的应用程序安装多媒体包

```sh
sudo dnf groupupdate multimedia --setop="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin
```

- 安装某些应用程序所需的声音和视频包

```sh
sudo dnf groupupdate sound-and-video
```

# 参考

https://docs.fedoraproject.org/en-US/epel/

https://rpmfusion.org/Configuration

