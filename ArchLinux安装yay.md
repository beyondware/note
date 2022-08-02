### 安装依赖

```sh
sudo pacman -S base-devel git
```

### 禁止 root 账号安装

```sh
==> ERROR: Running makepkg as root is not allowed as it can cause permanent,
catastrophic damage to your system.
```

### 安装 yay（普通账号）

> https://github.com/Jguer/yay

1、克隆 yay

```sh
git clone https://aur.archlinux.org/yay.git
```

2、修改目录所有者

```sh
sudo chown -R 用户名:用户组 ./yay
```

- 不知道用户组，命令查询

```sh
id 用户名
```

3、编译

```sh
cd yay
```

```sh
makepkg -si
```

### go 换源

- 临时换源

```sh
export GO111MODULE=on
export GOPROXY=https://goproxy.cn
```

- 永久换源

```sh
echo "export GO111MODULE=on" >> ~/.profile
echo "export GOPROXY=https://goproxy.cn" >> ~/.profile
source ~/.profile
```

### yay 命令

1、安装

```sh
yay -S 包名
```

2、删除

```sh
yay -Rns 包名
```

3、系统升级

```sh
yay -Syu
```

4、获取系统信息

```sh
yay -Ps
```

5、搜索

```sh
yay -Ss
```

### 安装 pamac

```sh
yay -S pamac-aur
```

运行

```sh
pamac-manager
```

### yay -h

```sh
Usage:
    yay
    yay <operation> [...]
    yay <package(s)>

operations:
    yay {-h --help}
    yay {-V --version}
    yay {-D --database}    <options> <package(s)>
    yay {-F --files}       [options] [package(s)]
    yay {-Q --query}       [options] [package(s)]
    yay {-R --remove}      [options] <package(s)>
    yay {-S --sync}        [options] [package(s)]
    yay {-T --deptest}     [options] [package(s)]
    yay {-U --upgrade}     [options] <file(s)>

New operations:
    yay {-Y --yay}         [options] [package(s)]
    yay {-P --show}        [options]
    yay {-G --getpkgbuild} [options] [package(s)]

If no arguments are provided 'yay -Syu' will be performed
If no operation is provided -Y will be assumed

New options:
       --repo             Assume targets are from the repositories
    -a --aur              Assume targets are from the AUR

Permanent configuration options:
    --save                Causes the following options to be saved back to the
                          config file when used

    --aururl      <url>   Set an alternative AUR URL
    --builddir    <dir>   Directory used to download and run PKGBUILDS
    --editor      <file>  Editor to use when editing PKGBUILDs
    --editorflags <flags> Pass arguments to editor
    --makepkg     <file>  makepkg command to use
    --mflags      <flags> Pass arguments to makepkg
    --pacman      <file>  pacman command to use
    --git         <file>  git command to use
    --gitflags    <flags> Pass arguments to git
    --gpg         <file>  gpg command to use
    --gpgflags    <flags> Pass arguments to gpg
    --config      <file>  pacman.conf file to use
    --makepkgconf <file>  makepkg.conf file to use
    --nomakepkgconf       Use the default makepkg.conf

    --requestsplitn <n>   Max amount of packages to query per AUR request
    --completioninterval  <n> Time in days to refresh completion cache
    --sortby    <field>   Sort AUR results by a specific field during search
    --searchby  <field>   Search for packages using a specified field
    --answerclean   <a>   Set a predetermined answer for the clean build menu
    --answerdiff    <a>   Set a predetermined answer for the diff menu
    --answeredit    <a>   Set a predetermined answer for the edit pkgbuild menu
    --answerupgrade <a>   Set a predetermined answer for the upgrade menu
    --noanswerclean       Unset the answer for the clean build menu
    --noanswerdiff        Unset the answer for the edit diff menu
    --noansweredit        Unset the answer for the edit pkgbuild menu
    --noanswerupgrade     Unset the answer for the upgrade menu
    --cleanmenu           Give the option to clean build PKGBUILDS
    --diffmenu            Give the option to show diffs for build files
    --editmenu            Give the option to edit/view PKGBUILDS
    --upgrademenu         Show a detailed list of updates with the option to skip any
    --nocleanmenu         Don't clean build PKGBUILDS
    --nodiffmenu          Don't show diffs for build files
    --noeditmenu          Don't edit/view PKGBUILDS
    --noupgrademenu       Don't show the upgrade menu
    --askremovemake       Ask to remove makedepends after install
    --removemake          Remove makedepends after install
    --noremovemake        Don't remove makedepends after install

    --cleanafter          Remove package sources after successful install
    --nocleanafter        Do not remove package sources after successful build
    --bottomup            Shows AUR's packages first and then repository's
    --topdown             Shows repository's packages first and then AUR's
    --singlelineresults   List each search result on its own line
    --doublelineresults   List each search result on two lines, like pacman

    --devel               Check development packages during sysupgrade
    --nodevel             Do not check development packages
    --rebuild             Always build target packages
    --rebuildall          Always build all AUR packages
    --norebuild           Skip package build if in cache and up to date
    --rebuildtree         Always build all AUR packages even if installed
    --redownload          Always download pkgbuilds of targets
    --noredownload        Skip pkgbuild download if in cache and up to date
    --redownloadall       Always download pkgbuilds of all AUR packages
    --provides            Look for matching providers when searching for packages
    --noprovides          Just look for packages by pkgname
    --pgpfetch            Prompt to import PGP keys from PKGBUILDs
    --nopgpfetch          Don't prompt to import PGP keys
    --useask              Automatically resolve conflicts using pacman's ask flag
    --nouseask            Confirm conflicts manually during the install
    --combinedupgrade     Refresh then perform the repo and AUR upgrade together
    --nocombinedupgrade   Perform the repo upgrade and AUR upgrade separately
    --batchinstall        Build multiple AUR packages then install them together
    --nobatchinstall      Build and install each AUR package one by one

    --sudo                <file>  sudo command to use
    --sudoflags           <flags> Pass arguments to sudo
    --sudoloop            Loop sudo calls in the background to avoid timeout
    --nosudoloop          Do not loop sudo calls in the background

    --timeupdate          Check packages' AUR page for changes during sysupgrade
    --notimeupdate        Do not check packages' AUR page for changes

show specific options:
    -c --complete         Used for completions
    -d --defaultconfig    Print default yay configuration
    -g --currentconfig    Print current yay configuration
    -s --stats            Display system package statistics
    -w --news             Print arch news

yay specific options:
    -c --clean            Remove unneeded dependencies
       --gendb            Generates development package DB used for updating

getpkgbuild specific options:
    -f --force            Force download for existing ABS packages
    -p --print            Print pkgbuild of packages
```
