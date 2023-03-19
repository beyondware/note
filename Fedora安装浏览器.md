## Firefox

1、查看安装情况

```sh
dnf list installed | grep firefox
```

2、删除

```sh
sudo dnf autoremove firefox
```

## Google Chrome

### 稳定版（推荐）

1、下载

```sh
wget https://dl.google.com/linux/direct/google-chrome-stable_current_x86_64.rpm
```

2、安装

```sh
sudo dnf install google-chrome-stable_current_x86_64.rpm
```

3、启动

```sh
google-chrome
```

4、删除本地下载包

```sh
rm google-chrome-stable_current_x86_64.rpm
```

5、删除

```sh
sudo dnf autoremove google-chrome-stable
```

6、禁用

```sh
sudo dnf config-manager --set-disabled google-chrome*
```

7、启用

```sh
sudo dnf config-manager --set-enabled google-chrome*
```

8、删除存储库

① 查看

```sh
dnf repolist | grep chrome
```

② 切换到目录

```sh
cd /etc/yum.repos.d
```

③ 删除

```sh
sudo rm google-chrome.repo
```

### 测试版

1、下载

```sh
wget https://dl.google.com/linux/direct/google-chrome-beta_current_x86_64.rpm
```

2、安装

```sh
sudo dnf install google-chrome-beta_current_x86_64.rpm
```

3、删除

```sh
sudo dnf autoremove google-chrome-beta
```

4、禁用

```sh
sudo dnf config-manager --set-disabled google-chrome-beta
```

5、启用

```sh
sudo dnf config-manager --set-enabled google-chrome-beta
```

### 不稳定版

1、下载

```sh
wget https://dl.google.com/linux/direct/google-chrome-unstable_current_x86_64.rpm
```

2、安装

```sh
sudo dnf install google-chrome-unstable_current_x86_64.rpm
```

3、删除

```sh
sudo dnf autoremove google-chrome-unstable
```

4、禁用

```sh
sudo dnf config-manager --set-disabled google-chrome-unstable
```

5、启用

```sh
sudo dnf config-manager --set-enabled google-chrome-unstable
```

## Microsoft Edge

1、导入GPG密钥

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
```

2、添加存储库

```sh
sudo dnf config-manager --add-repo https://packages.microsoft.com/yumrepos/edge
```

3、正式开始

### 稳定版（推荐）

① 安装

```sh
sudo dnf install microsoft-edge-stable
```

② 启动

```sh
microsoft-edge
```

③ 删除

```sh
sudo dnf autoremove microsoft-edge
```

### 测试版

① 安装

```sh
sudo dnf install microsoft-edge-beta
```
② 启动

```sh
microsoft-edge-beta
```

③ 删除

```sh
sudo dnf autoremove microsoft-edge-beta
```

### 开发版

① 安装

```sh
sudo dnf install microsoft-edge-dev
```
② 启动

```sh
microsoft-edge-dev
```

③ 删除

```sh
sudo dnf autoremove microsoft-edge-stable-dev
```

4、删除存储库

① 切换到目录

```sh
cd /etc/yum.repos.d
```

② 删除

```sh
sudo rm packages.microsoft.com_yumrepos_edge.repo microsoft-edge.repo
```

## LibreWolf

1、添加存储库

```sh
sudo dnf config-manager --add-repo https://rpm.librewolf.net/librewolf-repo.repo
```

2、安装

```sh
sudo dnf install librewolf
```

3、启动

```sh
librewolf
```

4、删除

```sh
sudo dnf autoremove librewolf
```

5、删除存储库

① 切换到目录

```sh
cd /etc/yum.repos.d
```

② 删除

```sh
sudo rm librewolf-repo.repo
```

6、参考网站

> https://librewolf.net/installation/fedora/

