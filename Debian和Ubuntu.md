## 镜像源

### 换源

```sh
sudo vim /etc/apt/sources.list
```

#### Debian

- 官方源

> http://deb.debian.org/debian

修改为

> https://mirrors.cernet.edu.cn/debian/

- 参考

> https://help.mirrors.cernet.edu.cn/debian/

> https://mirrors.tuna.tsinghua.edu.cn/help/debian/

#### Ubuntu

- 官方源

> http://archive.ubuntu.com/ubuntu/

修改为

> https://mirrors.cernet.edu.cn/ubuntu/

- 参考

> https://help.mirrors.cernet.edu.cn/ubuntu/

> https://mirrors.tuna.tsinghua.edu.cn/help/ubuntu/

> https://developer.aliyun.com/mirror/ubuntu

#### Deepin

- 文件最前面添加以下内容

```sh
deb [by-hash=force] https://mirrors.nju.edu.cn/deepin/ apricot main contrib non-free
```

- 参考源

> https://developer.aliyun.com/mirror/deepin

#### Kali

```sh
deb http://http.kali.org/kali kali-rolling main contrib non-free
deb-src http://http.kali.org/kali kali-rolling main contrib non-free
```

改成

```sh
deb https://mirrors.cernet.edu.cn/kali kali-rolling main non-free contrib
deb-src https://mirrors.cernet.edu.cn/kali kali-rolling main non-free contrib
```

- 参考

> https://help.mirrors.cernet.edu.cn/kali/

> https://mirrors.ustc.edu.cn/help/kali.html

### 更新

```sh
sudo apt update
```

## 系统升级

```sh
sudo apt update && sudo apt upgrade
```

### 自动处理包依赖

```sh
sudo apt dist-upgrade
```

### 升级整个系统

```sh
sudo apt full-upgrade
```

## 安装

```sh
sudo apt install 包名
```

### 本地安装

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

## 删除

```sh
sudo apt remove 包名
```

或者

```sh
dpkg uninstall 包名
```

### 自动删除

```sh
sudo apt autoremove 包名
```

- 删除包和依赖

```sh
sudo apt purge 包名
```

### 自动删除和依赖

```sh
sudo apt autoremove --purge
```

## 列出已安装

```sh
sudo apt list --installed | grep -i 关键字
```

或者

```sh
dpkg -L | grep 关键字
```

## 升级

```sh
sudo apt upgrade 包名
```

### 自动处理依赖项升级包

```sh
sudo apt full-upgrade 包名
```

### 查看可升级的软件包

```sh
apt list --upgradable
```

### 仅升级指定的软件包

```sh
sudo apt install --only-upgrade 包名
```

### 模拟升级（但不升级任何包）

```sh
apt -s upgrade
```

## 搜索

```sh
apt search 包名
```

## 详细信息

### 显示包的详细信息

```sh
apt show 包名
```

### 获取详细信息

```sh
apt info 包名
```

## 终端美化

终端-点击“三杠”-配置文件首选项

- 文本和背景颜色：Solarized
- 调色板：Solarized

## 浏览器

### Firefox

1、查看

```sh
dpkg -L | grep firefox
```

- 三个关联包：firefox、firefox-locale-en、firefox-locale-zh-hans

2、删除

```sh
sudo dpkg -P firefox firefox-locale-en firefox-locale-zh-hans
```

### Chromium

1、安装

```sh
sudo apt install chromium-browser
```

2、删除

```sh
sudo apt remove chromium-browser
```

### Chrome

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
