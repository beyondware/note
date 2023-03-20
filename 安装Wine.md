## Fedora

### 方案一（推荐）

1、安装与删除

```sh
sudo dnf install wine wine.i686
sudo dnf autoremove wine wine.i686
```

2、确认版本

```sh
wine --version
```

3、配置

```sh
winecfg
```

4、升级

```sh
sudo dnf --enablerepo=updates-testing update wine
```

### 方案二

1、添加存储库

```sh
sudo dnf config-manager --add-repo https://dl.winehq.org/wine-builds/fedora/$(rpm -E %fedora)/winehq.repo
```

2、安装与删除

#### 稳定版（推荐）

```sh
sudo dnf install winehq-stable
sudo dnf autoremove winehq-stable
```

#### 暂存版

```sh
sudo dnf install winehq-staging
sudo dnf autoremove winehq-staging
```

#### 开发版

```sh
sudo dnf install winehq-devel
sudo dnf autoremove winehq-devel
```

3、确认版本

```sh
wine --version
```

4、配置

```sh
winecfg
```

5、删除存储库

```sh
sudo rm /etc/yum.repos.d/winehq.repo
```

