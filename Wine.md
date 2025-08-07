# Debian

## 启用 32 位架构（可选）

```sh
sudo dpkg --add-architecture i386
```

## 导入密钥

```sh
curl -s https://dl.winehq.org/wine-builds/winehq.key | sudo gpg --dearmor | sudo tee /usr/share/keyrings/winehq.gpg > /dev/null
```

## 导入 WineHQ 存储库

```sh
echo deb [signed-by=/usr/share/keyrings/winehq.gpg] http://dl.winehq.org/wine-builds/ubuntu/ $(lsb_release -cs) main | sudo tee /etc/apt/sources.list.d/winehq.list
```

## 更新

```sh
sudo apt update
```

## 安装

```sh
sudo apt install --install-recommends winehq-stable
```

--install-recommends：安装 WineHQ 推荐的依赖项

## 验证已安装的 Wine 版本

```sh
wine --version
```

## 启动 Wine 配置对话框

```sh
winecfg
```

## 帮助 Wine 更流畅地运行 Windows 软件

```sh
sudo apt install winetricks
```

使用 Wine 运行安装文件，请右键单击 .exe 文件，选择“使用其他应用程序打开”，然后从应用程序列表中选择 Wine。

## 删除

```sh
sudo apt remove winehq-stable
```

## 删除存储库

```sh
sudo rm /etc/apt/sources.list.d/winehq.list
```

## 删除密钥

```sh
sudo rm /usr/share/keyrings/winehq.gpg
```

## 找不到 “Open With Wine Windows Program Loader” 选项

```sh
sudo ln -s /usr/share/doc/wine/examples/wine.desktop /usr/share/applications/
```

## Wine 卸载应用程序

```sh
wine uninstaller
```

# Fedora

## 方案一（推荐）

1、安装

```sh
sudo dnf install wine wine.i686
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

## 方案二

1、添加存储库

```sh
sudo dnf config-manager --add-repo https://dl.winehq.org/wine-builds/fedora/$(rpm -E %fedora)/winehq.repo
```

2、安装

```sh
sudo dnf install winehq-stable
```

3、删除

```sh
sudo dnf autoremove winehq-stable
```

4、确认版本

```sh
wine --version
```

5、配置

```sh
winecfg
```

6、删除存储库

```sh
sudo rm /etc/yum.repos.d/winehq.repo
```

7、删除 Wine 安装的软件

```sh
wine uninstaller
```

## Winetricks

1、使用Wine打开微信无法看到输入框内容

### 方案一（推荐）

从Windows系统中

```sh
C:\Windows\System32
```

```sh
C:\Windows\SysWOW64
```

分别复制riched20.dll、riched32.dll到Linux系统

```sh
/home/$USER/.wine/drive_c/windows/system32/
```

```sh
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

### winetricks --help

```sh
Usage: /usr/bin/winetricks [options] [command|verb|path-to-verb] ...
Executes given verbs.  Each verb installs an application or changes a setting.

Options:
    --country=CC      Set country code to CC and don't detect your IP address
-f, --force           Don't check whether packages were already installed
    --gui             Show gui diagnostics even when driven by commandline
    --gui=OPT         Set OPT to kdialog or zenity to override GUI engine
    --isolate         Install each app or game in its own bottle (WINEPREFIX)
    --self-update     Update this application to the last version
    --update-rollback Rollback the last self update
-k, --keep_isos       Cache isos (allows later installation without disc)
    --no-clean        Don't delete temp directories (useful during debugging)
-q, --unattended      Don't ask any questions, just install automatically
-r, --ddrescue        Retry hard when caching scratched discs
-t  --torify          Run downloads under torify, if available
    --verify          Run (automated) GUI tests for verbs, if available
-v, --verbose         Echo all commands as they are executed
-h, --help            Display this message and exit
-V, --version         Display version and exit

Commands:
list                  list categories
list-all              list all categories and their verbs
apps list             list verbs in category 'applications'
benchmarks list       list verbs in category 'benchmarks'
dlls list             list verbs in category 'dlls'
fonts list            list verbs in category 'fonts'
games list            list verbs in category 'games'
settings list         list verbs in category 'settings'
list-cached           list cached-and-ready-to-install verbs
list-download         list verbs which download automatically
list-manual-download  list verbs which download with some help from the user
list-installed        list already-installed verbs
arch=32|64            create wineprefix with 32 or 64 bit, this option must be
                      given before prefix=foobar and will not work in case of
                      the default wineprefix.
prefix=foobar         select WINEPREFIX=/home/pc/.local/share/wineprefixes/foobar
annihilate            Delete ALL DATA AND APPLICATIONS INSIDE THIS WINEPREFIX
```

# Flatpak 安装 Wine（不推荐）

1、安装一些依赖

```sh
sudo flatpak install \
    org.freedesktop.Platform/x86_64/22.08 \
    org.freedesktop.Platform.Compat.i386/x86_64/22.08 \
    org.freedesktop.Platform.GL32.default/x86_64/22.08 \
    org.freedesktop.Platform.VAAPI.Intel/x86_64/22.08 \
    org.freedesktop.Platform.VAAPI.Intel.i386/x86_64/22.08
```

2、安装 Wine

```sh
flatpak install flathub org.winehq.Wine
```

3、查询版本

```sh
flatpak run org.winehq.Wine --version
```

4、配置

```sh
flatpak run org.winehq.Wine winecfg
```

## 解决微信

1、在 Windows 系统复制 riched20.dll 和 riched32.dll 文件到

```sh
/root/.wine/drive_c/windows/system32/
```

2、执行 winecfg 标签“函数库”-“新增函数库顶替”选择添加

riched20.dll和riched32.dll

