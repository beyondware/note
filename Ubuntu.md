### 镜像源

#### Ubuntu

```sh
sudo vim /etc/apt/sources.list
```

官方源

> http://archive.ubuntu.com/ubuntu/

阿里云

> https://developer.aliyun.com/mirror/ubuntu

清华大学

> https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/




### 系统

```sh
sudo apt update && sudo apt upgrade
```

```sh
sudo apt autoremove --purge
```

### 常用命令

#### 安装

```sh
sudo apt install 包名
```

#### 本地安装

```sh
sudo apt install 包.deb
```

或者

```sh
sudo dpkg -i 包.deb
```

- 报错的话，需要修复依赖项

```sh
sudo apt install -f
```

#### 卸载

```sh
sudo apt remove 包名
```

或者

```sh
dpkg uninstall 包名
```

- 自动卸载

```sh
sudo apt autoremove 包名
```

- 删除包和依赖

```sh
sudo apt purge 包名
```

#### 列出已安装

```sh
sudo apt list --installed | grep -i 关键字
```

或者

```sh
dpkg -L | grep 关键字
```

#### 升级

1、升级到最新版本

```sh
sudo apt upgrade 包名
```

- 自动处理依赖项升级包

```sh
sudo apt full-upgrade 包名
```

2、查看可升级的软件包

```sh
apt list --upgradable
```

3、仅升级指定的软件包

```sh
sudo apt install --only-upgrade 包名
```

4、模拟升级（但不升级任何包）

```sh
apt -s upgrade
```

#### 搜索

```sh
apt search 包名
```

#### 详细信息

1、显示包的详细信息

```sh
apt show 包名
```

2、获取详细信息

```sh
apt info 包名
```

### 终端美化

终端-点击“三杠”-配置文件首选项

- 文本和背景颜色：Solarized
- 调色板：Solarized

### 浏览器

#### Firefox

1、查看

```sh
dpkg -L | grep firefox
```

- 三个关联包：firefox、firefox-locale-en、firefox-locale-zh-hans

2、删除

```sh
sudo dpkg -P firefox firefox-locale-en firefox-locale-zh-hans
```

#### Chromium

1、安装

```sh
sudo apt install chromium-browser
```

2、删除

```sh
sudo apt remove chromium-browser
```

#### Chrome

1、下载

```sh
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

2、安装

```sh
sudo apt install google-chrome-stable_current_amd64.deb
```

3、删除下载包

```sh
rm google-chrome-stable_current_amd64.deb
```
