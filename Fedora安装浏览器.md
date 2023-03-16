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

8、删除仓库列表

```sh
dnf repolist | grep chrome
```

```sh
cd /etc/yum.repos.d
```

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
