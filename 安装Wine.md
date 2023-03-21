## Wine

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

## Winetricks

1、使用Wine打开微信无法看到输入框内容

### 方案一（推荐）

从Windows系统中

```sh
C:\Windows\System32
C:\Windows\SysWOW64
```

分别复制riched20.dll、riched32.dll到Linux系统

```sh
/home/$USER/.wine/drive_c/windows/system32/
/home/$USER/.wine/drive_c/windows/syswow64/
```

Wine Configuration-函数库-新增函数库顶替-添加riched20、riched32

### 方案二

```sh
sudo dnf install winetricks
```

```sh
winetricks riched20
```

- 安装失败，解决方法：

W2KSP4_EN.EXE放到win2ksp4目录下

> http://x3270.bgp.nu/download/specials/W2KSP4_EN.EXE

```sh
/home/$USER/.cache/winetricks/win2ksp4/
```

InstMsiW.exe放到msls31目录下

```sh
/home/$USER/.cache/winetricks/msls31/
```


