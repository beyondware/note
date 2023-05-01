## apt

```sh
用法： apt [选项] 命令

命令行软件包管理器 apt 提供软件包搜索，管理和信息查询等功能。
它提供的功能与其他 APT 工具相同（像 apt-get 和 apt-cache），
但是默认情况下被设置得更适合交互。

常用命令：
  list - 根据名称列出软件包
  search - 搜索软件包描述
  show - 显示软件包细节
  install - 安装软件包
  reinstall - 重新安装软件包
  remove - 移除软件包
  autoremove - 卸载所有自动安装且不再使用的软件包
  update - 更新可用软件包列表
  upgrade - 通过 安装/升级 软件来更新系统
  full-upgrade - 通过 卸载/安装/升级 来更新系统
  edit-sources - 编辑软件源信息文件
  satisfy - 使系统满足依赖关系字符串

参见 apt(8) 以获取更多关于可用命令的信息。
程序配置选项及语法都已经在 apt.conf(5) 中阐明。
欲知如何配置软件源，请参阅 sources.list(5)。
软件包及其版本偏好可以通过 apt_preferences(5) 来设置。
关于安全方面的细节可以参考 apt-secure(8).
                                         本 APT 具有超级牛力。
```

## apt-get

```sh
用法： apt-get [选项] 命令
　　　 apt-get [选项] install|remove 软件包1 [软件包2 ...]
　　　 apt-get [选项] source 软件包1 [软件包2 ...]

apt-get 可以从认证软件源下载软件包及相关信息，以便安装和升级软件包，
或者用于移除软件包。在这些过程中，软件包依赖会被妥善处理。

常用命令：
  update - 取回更新的软件包列表信息
  upgrade - 进行一次升级
  install - 安装新的软件包（注：软件包名称应当类似 libc6 而非 libc6.deb）
  reinstall - 重新安装软件包（注：软件包名称应当类似 libc6 而非 libc6.deb）
  remove - 卸载软件包
  purge - 卸载并清除软件包的配置
  autoremove - 卸载所有自动安装且不再使用的软件包
  dist-upgrade - 发行版升级，见 apt-get(8)
  dselect-upgrade - 根据 dselect 的选择来进行升级
  build-dep - 为源码包配置所需的编译依赖关系
  satisfy - 使系统满足依赖关系字符串
  clean - 删除所有已下载的包文件
  autoclean - 删除已下载的旧包文件
  check - 核对以确认系统的依赖关系的完整性
  source - 下载源码包文件
  download - 下载指定的二进制包到当前目录
  changelog - 下载指定软件包，并显示其变更日志（changelog）

参见 apt-get(8) 以获取更多关于可用命令的信息。
程序配置选项及语法都已经在 apt.conf(5) 中阐明。
欲知如何配置软件源，请参阅 sources.list(5)。
软件包及其版本偏好可以通过 apt_preferences(5) 来设置。
关于安全方面的细节可以参考 apt-secure(8).
                                         本 APT 具有超级牛力。
```

## apt-cache

```sh
用法： apt-cache [选项] 命令
       apt-cache [选项] show 软件包1 [软件包2 ...]

apt-cache 可以查询和显示已安装和可安装软件包的可用信息。
它专门工作在本地的数据缓存上，而这些缓存可以通过比如
apt-get 的 'update' 命令来更新。如果距离上一次更新的时间太久，
那么它显示的信息可能就会过时。不过作为交换，apt-cache 不依赖
当前软件源的可用性（比如：离线状态）。

常用命令：
  showsrc - 显示源文件的各项记录
  search - 根据正则表达式搜索软件包列表
  depends - 显示该软件包的依赖关系信息
  rdepends - 显示所有依赖于该软件包的软件包名字
  show - 以便于阅读的格式介绍该软件包
  pkgnames - 列出所有软件包的名字
  policy - 显示软件包的安装设置状态

参见 apt-cache(8) 以获取更多关于可用命令的信息。
程序配置选项及语法都已经在 apt.conf(5) 中阐明。
欲知如何配置软件源，请参阅 sources.list(5)。
软件包及其版本偏好可以通过 apt_preferences(5) 来设置。
关于安全方面的细节可以参考 apt-secure(8).
```

## dpkg --help

```sh
用法：dpkg [<选项>...] <命令>

命令：
  -i|--install       <.deb 文件名> ... | -R|--recursive <目录> ...
  --unpack           <.deb 文件名> ... | -R|--recursive <目录> ...
  -A|--record-avail  <.deb 文件名> ... | -R|--recursive <目录> ...
  --configure        <软件包名>    ... | -a|--pending
  --triggers-only    <软件包名>    ... | -a|--pending
  -r|--remove        <软件包名>    ... | -a|--pending
  -P|--purge         <软件包名>    ... | -a|--pending
  -V|--verify <软件包名> ...       检查包的完整性。
  --get-selections [<表达式> ...]  把已选中的软件包列表打印到标准输出。
  --set-selections                 从标准输入里读出要选择的软件。
  --clear-selections               取消选中所有非必需的软件包。
  --update-avail <软件包文件>      替换现有可安装的软件包信息。
  --merge-avail  <软件包文件>      把文件中的信息合并到系统中。
  --clear-avail                    清除现有的软件包信息。
  --forget-old-unavail             忘却已被卸载的不可安装的软件包。
  -s|--status      <软件包名> ...  显示指定软件包的详细状态。
  -p|--print-avail <软件包名> ...  显示可供安装的软件版本。
  -L|--listfiles   <软件包名> ...  列出属于指定软件包的文件。
  -l|--list  [<表达式> ...]        简明地列出软件包的状态。
  -S|--search <表达式> ...         搜索含有指定文件的软件包。
  -C|--audit [<表达式> ...]        检查是否有软件包残损。
  --yet-to-unpack                  列出标记为待解压的软件包。
  --predep-package                 列出待解压的预依赖。
  --add-architecture    <体系结构> 添加 <体系结构> 到体系结构列表。
  --remove-architecture <体系结构> 从体系结构列表中移除 <体系结构>。
  --print-architecture             显示 dpkg 体系结构。
  --print-foreign-architectures    显示已启用的异质体系结构。
  --assert-<特性>                  对指定特性启用断言支持。
  --validate-<属性> <字符串>       验证一个 <属性>的 <字符串>。
  --compare-versions <a> <关系> <b> 比较版本号 - 见下。
  --force-help                     显示本强制选项的帮助信息。
  -Dh|--debug=help                 显示有关出错调试的帮助信息。

  -?, --help                       显示本帮助信息。
      --version                    显示版本信息。

可验证的属性：pkgname, archname, trigname, version.

调用 dpkg 并带参数 -b, --build, -c, --contents, -e, --control, -I, --info,
  -f, --field, -x, --extract, -X, --vextract, --ctrl-tarfile, --fsys-tarfile
是针对归档文件的。 (输入 dpkg-deb --help 获取帮助)

Options:
  --admindir=<directory>     Use <directory> instead of /var/lib/dpkg.
  --root=<directory>         Install on a different root directory.
  --instdir=<directory>      Change installation dir without changing admin dir.
  --pre-invoke=<command>     Set a pre-invoke hook.
  --post-invoke=<command>    Set a post-invoke hook.
  --path-exclude=<pattern>   Do not install paths which match a shell pattern.
  --path-include=<pattern>   Re-include a pattern after a previous exclusion.
  -O|--selected-only         Skip packages not selected for install/upgrade.
  -E|--skip-same-version     Skip packages whose same version is installed.
  -G|--refuse-downgrade      Skip packages with earlier version than installed.
  -B|--auto-deconfigure      Install even if it would break some other package.
  --[no-]triggers            Skip or force consequential trigger processing.
  --verify-format=<format>   Verify output format (supported: 'rpm').
  --no-pager                 Disables the use of any pager.
  --no-debsig                Do not try to verify package signatures.
  --no-act|--dry-run|--simulate
                             Just say what we would do - don't do it.
  -D|--debug=<octal>         Enable debugging (see -Dhelp or --debug=help).
  --status-fd <n>            Send status change updates to file descriptor <n>.
  --status-logger=<command>  Send status change updates to <command>'s stdin.
  --log=<filename>           Log status changes and actions to <filename>.
  --ignore-depends=<package>[,...]
                             Ignore dependencies involving <package>.
  --force-<thing>[,...]      Override problems (see --force-help).
  --no-force-<thing>[,...]   Stop when problems encountered.
  --refuse-<thing>[,...]     Ditto.
  --abort-after <n>          Abort after encountering <n> errors.
  --robot                    Use machine-readable output on some commands.

可供--compare-versions 使用的比较运算符有：
 lt le eq ne ge gt        (如果版本号为空，那么就认为它先于任意版本号)；
 lt-nl le-nl ge-nl gt-nl  (如果版本号为空，那么就认为它后于任意版本号)；
 < << <= = >= >> >        (仅仅是为了与主控文件的语法兼容)。

'apt' 和 'aptitude' 提供了更为便利的软件包管理。
```
