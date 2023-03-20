## 系统

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

## Fedora

```sh
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo dnf install https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

## Silverblue、Kinoite、CoreOS

```sh
sudo rpm-ostree install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm
sudo rpm-ostree install https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```

## Rocky、CentOS Stream

### EPEL

1、启用 CRB 存储库

```sh
sudo dnf config-manager --set-enabled crb
```

2、导入 EPEL

```sh
sudo dnf install --nogpgcheck https://dl.fedoraproject.org/pub/epel/epel-release-latest-$(rpm -E %rhel).noarch.rpm
```

- CentOS Stream 需要添加，Rocky 不需要

```
sudo dnf install --nogpgcheck https://dl.fedoraproject.org/pub/epel/epel-next-release-latest-$(rpm -E %rhel).noarch.rpm
```

### RPM Fusion

1、安装

```sh
sudo dnf install --nogpgcheck https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-$(rpm -E %rhel).noarch.rpm
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

2、删除

```sh
rpm -qa 'rpmfusion*'
```

```sh
sudo dnf remove rpmfusion-free-release
sudo dnf remove rpmfusion-nonfree-release
```

### RPM Fusion Testing Updates

1、启用

```sh
sudo dnf config-manager --set-enabled rpmfusion-free-updates-testing
sudo dnf config-manager --set-enabled rpmfusion-nonfree-updates-testing
```

2、禁用

```sh
sudo dnf config-manager --set-disabled rpmfusion-free-updates-testing
sudo dnf config-manager --set-disabled rpmfusion-nonfree-updates-testing
```

### RPM Fusion Tainted

1、安装

```sh
sudo dnf install rpmfusion-free-release-tainted
sudo dnf install rpmfusion-nonfree-release-tainted
```

2、删除

```sh
sudo dnf remove rpmfusion-free-release-tainted
sudo dnf remove rpmfusion-nonfree-release-tainted
```

## 参考文档

> https://docs.fedoraproject.org/en-US/epel/

> https://rpmfusion.org/Configuration
