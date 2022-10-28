## yay

> https://github.com/Jguer/yay

### yay 禁止 root 编译

```sh
==> ERROR: Running makepkg as root is not allowed as it can cause permanent,
catastrophic damage to your system.
```

- 不能使用 root 账号安装

### yay 安装

1、安装依赖

```sh
sudo pacman -S base-devel git
```

2、克隆 yay（推荐 yay-bin）

```sh
git clone https://aur.archlinux.org/yay-bin.git
```

3、编译

```sh
cd yay-bin
```

```sh
makepkg -si
```

### go 换源

- 临时换源（yay 安装失败）

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

### yay 常用命令

1、安装

```sh
yay -S 包名
```

2、删除

```sh
yay -R 包名
```

3、系统升级

```sh
yay -Syu
```

4、更新软件库

```sh
yay -Syy
```

5、获取系统信息

```sh
yay -Ps
```

6、搜索

```sh
yay -Ss
```

7、清理所有缓存

```sh
yay -Scc
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

## paru

> https://github.com/morganamilo/paru

### paru 安装

1、安装依赖

```sh
sudo pacman -S base-devel git
```

2、克隆 paru（推荐 paru-bin）

```sh
git clone https://aur.archlinux.org/paru-bin.git
```

3、编译

```sh
cd paru-bin
```

```sh
makepkg -si
```

### paru 常用命令

1、安装

```sh
paru 包名
```

2、系统升级

```sh
paru -Syu
```

或者

```sh
paru -
```

3、仅升级 AUR 包

```sh
paru -Sua
```

4、可更新 AUR 包

```sh
paru -Qua
```

### 修改 paru 配置

```sh
sudo vim /etc/pacman.conf
```

1、启用颜色

- 取消 Color 注释

2、反转搜索顺序

- 取消 BottomUp 注释

### paru -h

```sh
Usage:
    paru
    paru <operation> [...]
    paru <package(s)>

Pacman operations:
    paru {-h --help}
    paru {-V --version}
    paru {-D --database}    <options> <package(s)>
    paru {-F --files}       [options] [package(s)]
    paru {-Q --query}       [options] [package(s)]
    paru {-R --remove}      [options] <package(s)>
    paru {-S --sync}        [options] [package(s)]
    paru {-T --deptest}     [options] [package(s)]
    paru {-U --upgrade}     [options] [file(s)]

New operations:
    paru {-P --show}        [options]
    paru {-G --getpkgbuild} [package(s)]

If no arguments are provided 'paru -Syu' will be performed

Options without operation:
    -c --clean            Remove unneeded dependencies
       --gendb            Generates development package DB used for updating

New options:
       --repo              Assume targets are from the repositories
    -a --aur               Assume targets are from the AUR
    --aururl    <url>      Set an alternative AUR URL
    --clonedir  <dir>      Directory used to download and run PKGBUILDs

    --makepkg   <file>     makepkg command to use
    --mflags    <flags>    Pass arguments to makepkg
    --pacman    <file>     pacman command to use
    --git       <file>     git command to use
    --gitflags  <flags>    Pass arguments to git
    --sudo      <file>     sudo command to use
    --sudoflags <flags>    Pass arguments to sudo
    --asp       <file>     asp command to use
    --bat       <file>     bat command to use
    --batflags  <flags>    Pass arguments to bat
    --gpg       <file>     gpg command to use
    --gpgflags  <flags>    Pass arguments to gpg
    --fm        <file>     File manager to use for PKGBUILD review
    --fmflags   <flags>    Pass arguments to file manager

    --completioninterval   <n> Time in days to refresh completion cache
    --sortby    <field>    Sort AUR results by a specific field during search
    --searchby  <field>    Search for packages using a specified field
    --limit     <limit>    Limits the number of items returned in a search
    -x --regex             Enable regex for aur search

    --skipreview           Skip the review process
    --review               Don't skip the review process
    --[no]upgrademenu      Show interactive menu to skip upgrades
    --[no]removemake       Remove makedepends after install
    --[no]cleanafter       Remove package sources after install
    --[no]rebuild          Always build target packages
    --[no]redownload       Always download PKGBUILDs of targets

    --[no]pgpfetch         Prompt to import PGP keys from PKGBUILDs
    --[no]useask           Automatically resolve conflicts using pacman's ask flag
    --[no]savechanges      Commit changes to pkgbuilds made during review
    --[no]newsonupgrade    Print new news during sysupgrade
    --[no]combinedupgrade  Refresh then perform the repo and AUR upgrade together
    --[no]batchinstall     Build multiple AUR packages then install them together
    --[no]provides         Look for matching providers when searching for packages
    --[no]devel            Check development packages during sysupgrade
    --[no]installdebug     Also install debug packages when a package provides them
    --[no]sudoloop         Loop sudo calls in the background to avoid timeout
    --[no]chroot           Build packages in a chroot
    --[no]failfast         Exit as soon as building an AUR package fails
    --[no]keepsrc          Keep src/ and pkg/ dirs after building packages
    --[no]sign             Sign packages with gpg
    --[no]signdb           Sign databases with gpg
    --localrepo            Build packages into a local repo
    --nocheck              Don't resolve checkdepends or run the check function
    --develsuffixes        Suffixes used to decide if a package is a devel package
    --bottomup             Shows AUR's packages first and then repository's
    --topdown              Shows repository's packages first and then AUR's

show specific options:
    -c --complete         Used for completions
    -s --stats            Display system package statistics
    -w --news             Print arch news

getpkgbuild specific options:
    -p --print            Print pkgbuild to stdout
    -c --comments         Print AUR comments for pkgbuild
    -s --ssh              Clone package using SSH

upgrade specific options:
    -i --install          Install package as well as building
```

## pamac

### yay 安装（推荐安装）

1、安装 pamac-aur

```sh
yay -Syu pamac-aur
```

2、运行 pamac-manager

```sh
pamac-manager
```

### 源码安装

#### 安装 libpamac

> https://gitlab.manjaro.org/applications/libpamac

1、克隆 libpamac（推荐 libpamac-aur）

```sh
git clone https://aur.archlinux.org/libpamac-aur.git
```

2、编译

```sh
cd libpamac-aur
```

```sh
makepkg -si
```

#### 安装 pamac

> https://gitlab.manjaro.org/applications/pamac

1、克隆 pamac（推荐 pamac-aur）

```sh
git clone https://aur.archlinux.org/pamac-aur.git
```

2、编译

```sh
cd pamac-aur
```

```sh
makepkg -si
```

3、运行

```sh
pamac-manager
```

### pamac -h

```sh
可用操作:
  pamac --version     
  pamac --help, -h     [操作]
  pamac search         [选项] <软件包>
  pamac list           [选项] <软件包>
  pamac info           [选项] <软件包>
  pamac install        [选项] <软件包>
  pamac reinstall      [选项] <软件包>
  pamac remove         [选项] [软件包]
  pamac checkupdates   [选项]
  pamac update,upgrade [选项]
  pamac clone          [选项] <软件包>
  pamac build          [选项] [软件包]
  pamac clean          [选项]
```
