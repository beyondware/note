1、更新 Rocky Linux

```sh
sudo dnf upgrade --refresh
```

2、检查是否安装 RPM Fusion

```sh
dnf repolist | grep rpmfusion
```

3、安装 EPEL

```sh
sudo dnf install --nogpgcheck https://dl.fedoraproject.org/pub/epel/epel-release-latest-$(rpm -E %rhel).noarch.rpm
```

4、RPM Fusion

- 安装

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

- 删除

```sh
rpm -qa 'rpmfusion*'
```

```sh
sudo dnf remove rpmfusion-free-release
sudo dnf remove rpmfusion-nonfree-release
```

5、RPM Fusion Testing Updates

- 启用

```sh
sudo dnf config-manager --set-enabled rpmfusion-free-updates-testing
sudo dnf config-manager --set-enabled rpmfusion-nonfree-updates-testing
```

- 禁用

```sh
sudo dnf config-manager --set-disabled rpmfusion-free-updates-testing
sudo dnf config-manager --set-disabled rpmfusion-nonfree-updates-testing
```

6、RPM Fusion Tainted

- 安装

```sh
sudo dnf install rpmfusion-free-release-tainted
sudo dnf install rpmfusion-nonfree-release-tainted
```

- 删除

```sh
sudo dnf remove rpmfusion-free-release-tainted
sudo dnf remove rpmfusion-nonfree-release-tainted
```

7、查看添加的存储库列表

```sh
dnf repolist
```

8、参考网站

> https://rpmfusion.org/Configuration