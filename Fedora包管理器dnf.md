## dnf

### 安装

1、在线安装

```sh
sudo dnf install 包名
```

2、本地安装

```sh
sudo dnf localinstall xxx.rpm
```

### 列出所有已安装

```sh
dnf list installed
```

### 删除

1、指定删除

```sh
sudo dnf remove 包名
```

2、自动删除（包括：不需要的依赖）

```sh
sudo dnf autoremove 包名
```

3、清理所有

```sh
dnf clean all
```

4、清理未安装的包

```sh
dnf clean packages
```

### 关键匹配删除

1、列出与`关键字`匹配的已安装软件

```sh
dnf list installed | grep 关键字
```

或者

```sh
rpm -qa | grep 关键字
```

2、删除相关（完整包名）

```sh
sudo dnf remove 完整的包名
```

### 搜索

1、搜索

```sh
dnf search 包名
```

2、搜索匹配`关键字`的软件包

```sh
dnf repoquery 关键字
```

3、查找提供`指定内容`的软件包

```sh
dnf provides 关键字
```

### 更新软件

```sh
sudo dnf update 包名
```

### 详细信息

```sh
dnf info 包名
```

### 别名

```sh
dnf alias
```

### 列出

1、列表所有（远程仓库）

```sh
dnf list
```

2、列出已配置（远程仓库）

```sh
dnf repolist
```

3、列出与`关键字`匹配软件源

```sh
dnf list | grep 关键字
```

4、列出与`关键字`匹配的已安装软件

```sh
dnf list installed | grep 关键字
```

### 路径

1、显示命令及相关文件的路径

```sh
whereis
```

2、查找命令文件

```sh
which
```

3、根据路径和条件搜索指定文件

```sh
find
```

## 组

1、组列出

```sh
dnf grouplist
```

2、组安装

```sh
sudo dnf groupinstall
```

组安装 "Development tools"

```sh
sudo dnf groupinstall "Development tools"
```

3、组删除

```sh
sudo dnf groupremove
```

4、组更新

```sh
sudo dnf groupupdate
```

## 系统

1、删除旧内核

```sh
sudo dnf remove --oldinstallonly
```

2、列出已安装最新版本

```sh
sudo dnf distro-sync
```

3、检查可升级

```sh
dnf check-update
```

## 手册

1、安装手册页

```sh
sudo dnf install man-db
```

2、构建手册页缓存

```sh
sudo mandb
```

## dnf --help

```sh
usage: dnf [options] COMMAND

主要命令列表：

alias                     列出或创建命令别名
autoremove                删除所有原先因为依赖关系安装的不需要的软件包
check                     在包数据库中寻找问题
check-update              检查是否有软件包升级
clean                     删除已缓存的数据
deplist                   [已弃用，请使用 repoquery --deplist] 列出软件包的依赖关系和提供这些软件包的源
distro-sync               同步已经安装的软件包到最新可用版本
downgrade                 降级包
group                     显示或使用组信息
help                      显示一个有帮助的用法信息
history                   显示或使用事务历史
info                      显示关于软件包或软件包组的详细信息
install                   向系统中安装一个或多个软件包
list                      列出一个或一组软件包
makecache                 创建元数据缓存
mark                      在已安装的软件包中标记或者取消标记由用户安装的软件包。
module                    与模块交互。
provides                  查找提供指定内容的软件包
reinstall                 重装一个包
remove                    从系统中移除一个或多个软件包
repolist                  显示已配置的软件仓库
repoquery                 搜索匹配关键字的软件包
repository-packages       对指定仓库中的所有软件包运行命令
search                    在软件包详细信息中搜索指定字符串
shell                     运行一个交互式的 DNF shell
swap                      运行一个交互式的 DNF mod 以删除或安装 spec
updateinfo                显示软件包的参考建议
upgrade                   升级系统中的一个或多个软件包
upgrade-minimal           升级，但只有“最新”的软件包已修复可能影响你的系统的问题

插件命令列表：

builddep                  Install build dependencies for package or spec file
changelog                 查看软件包的改变日志数据
config-manager            管理 dnf 配置选项和软件仓库
copr                      与 Copr 仓库交互。
debug-dump                转储已安装的 RPM 软件包信息至文件
debug-restore             恢复调试用转储文件中的软件包记录
debuginfo-install         安装调试信息软件包
download                  下载软件包至当前目录
groups-manager            创建并编辑组元数据文件
needs-restarting          判断所升级的二进制文件是否需要重启
offline-distrosync        准备系统的离线 distrosync
offline-upgrade           准备系统的离线升级
playground                与 Playground 仓库交互。
repoclosure               显示仓库中未被解决的依赖关系的列表
repodiff                  列出两组仓库中的不同
repograph                 以点线图方式输出完整的软件包依赖关系图
repomanage                管理 RPM 软件包目录
reposync                  下载远程仓库中的全部软件包
system-upgrade            为升级至新发布版本准备系统

General DNF options:
  -c [config file], --config [config file]
                        配置文件位置
  -q, --quiet           静默执行
  -v, --verbose         详尽执行
  --version             显示 DNF 的版本并退出
  --installroot [path]  设置目标根目录
  --nodocs              不要安装文档
  --noplugins           禁用所有插件
  --enableplugin [plugin]
                        启用指定名称的插件
  --disableplugin [plugin]
                        禁用指定名称的插件
  --releasever RELEASEVER
                        覆盖在配置文件和仓库文件中 $releasever 的值
  --setopt SETOPTS      设置任意配置和仓库选项
  --skip-broken         通过跳过软件包来解决依赖问题
  -h, --help, --help-cmd
                        显示命令帮助
  --allowerasing        允许解决依赖关系时删除已安装软件包
  -b, --best            在事务中尝试最佳软件包版本。
  --nobest              不将事务限制在最佳候选
  -C, --cacheonly       完全从系统缓存运行，不升级缓存
  -R [minutes], --randomwait [minutes]
                        最大命令等待时间
  -d [debug level], --debuglevel [debug level]
                        调试输出级别
  --debugsolver         转储详细解决结果至文件
  --showduplicates      在 list/search 命令下，显示仓库里重复的条目
  -e ERRORLEVEL, --errorlevel ERRORLEVEL
                        错误输出级别
  --obsoletes           对 upgrade 启用 dnf 的过期处理逻辑，或对 info、list 和 repoquery 启用软件包过期的显示功能
  --rpmverbosity [debug level name]
                        rpm调试输出等级
  -y, --assumeyes       全部问题自动应答为是
  --assumeno            全部问题自动应答为否
  --enablerepo [repo]   Temporarily enable repositories for the purpose of the current dnf command.
                        Accepts an id, a comma-separated list of ids, or a glob of ids. This option can
                        be specified multiple times.
  --disablerepo [repo]  Temporarily disable active repositories for the purpose of the current dnf
                        command. Accepts an id, a comma-separated list of ids, or a glob of ids. This
                        option can be specified multiple times, but is mutually exclusive with `--repo`.
  --repo [repo], --repoid [repo]
                        启用指定 id 或 glob 的仓库，可以指定多次
  --enable              使用 config-manager 命令启用 repos (自动保存)
  --disable             使用 config-manager 命令禁用 repos (自动保存)
  -x [package], --exclude [package], --excludepkgs [package]
                        用全名或通配符排除软件包
  --disableexcludes [repo], --disableexcludepkgs [repo]
                        禁用 excludepkgs
  --repofrompath [repo,path]
                        附加仓库所要使用的标签和路径（与 baseurl 中的路径一致），可以指定多次。
  --noautoremove        禁用删除不再被使用的依赖软件包
  --nogpgcheck          禁用 gpg 签名检查 (如果 RPM 策略允许)
  --color COLOR         配置是否使用颜色
  --refresh             在运行命令之前将元数据标记为过期
  -4                    仅解析 IPv4 地址
  -6                    仅解析 IPv6 地址
  --destdir DESTDIR, --downloaddir DESTDIR
                        设置软件包要复制到的目录
  --downloadonly        仅下载软件包
  --comment COMMENT     为事务添加一个注释
  --bugfix              在更新中包括与 bug 修复有关的软件包
  --enhancement         在更新中包括与功能增强有关的软件包
  --newpackage          在更新中包括与新软件包有关的软件包
  --security            在更新中包括与安全有关的软件包
  --advisory ADVISORY, --advisories ADVISORY
                        在更新中包括修复指定公告所必须的软件包
  --bz BUGZILLA, --bzs BUGZILLA
                        在更新中包括修复给定 BZ 所必须的软件包
  --cve CVES, --cves CVES
                        在更新中包括修复给定 CVE 所必须的软件包
  --sec-severity {Critical,Important,Moderate,Low}, --secseverity {Critical,Important,Moderate,Low}
                        在更新中包括匹配给定安全等级的安全相关的软件包
  --forcearch ARCH      强制使用一个架构
```

## copr

1、安装 dnf-plugins-core（必选）

```sh
sudo dnf install dnf-plugins-core
```

2、启用

```sh
sudo dnf copr enable 用户名/项目名
```

3、禁用

```sh
sudo dnf copr disable 用户名/项目名
```

4、删除

```sh
sudo dnf copr remove 用户名/项目名
```

5、安装

```sh
sudo dnf install 项目名
```

## dnf copr --help

```sh
usage: dnf copr [-c [config file]] [-q] [-v] [--version]
                [--installroot [path]] [--nodocs] [--noplugins]
                [--enableplugin [plugin]] [--disableplugin [plugin]]
                [--releasever RELEASEVER] [--setopt SETOPTS] [--skip-broken]
                [-h] [--allowerasing] [-b | --nobest] [-C] [-R [minutes]]
                [-d [debug level]] [--debugsolver] [--showduplicates]
                [-e ERRORLEVEL] [--obsoletes]
                [--rpmverbosity [debug level name]] [-y] [--assumeno]
                [--enablerepo [repo]] [--disablerepo [repo] | --repo [repo]]
                [--enable | --disable] [-x [package]]
                [--disableexcludes [repo]] [--repofrompath [repo,path]]
                [--noautoremove] [--nogpgcheck] [--color COLOR] [--refresh]
                [-4] [-6] [--destdir DESTDIR] [--downloadonly]
                [--comment COMMENT] [--bugfix] [--enhancement] [--newpackage]
                [--security] [--advisory ADVISORY] [--bz BUGZILLA]
                [--cve CVES]
                [--sec-severity {Critical,Important,Moderate,Low}]
                [--forcearch ARCH]
                [--installed | --enabled | --disabled | --available-by-user NAME]
                [--hub HUB]
                {help,enable,disable,remove,list,search} [arg ...]

与 Copr 仓库交互。

General DNF options:
  -c [config file], --config [config file]
                        配置文件位置
  -q, --quiet           静默执行
  -v, --verbose         详尽执行
  --version             显示 DNF 的版本并退出
  --installroot [path]  设置目标根目录
  --nodocs              不要安装文档
  --noplugins           禁用所有插件
  --enableplugin [plugin]
                        启用指定名称的插件
  --disableplugin [plugin]
                        禁用指定名称的插件
  --releasever RELEASEVER
                        覆盖在配置文件和仓库文件中 $releasever 的值
  --setopt SETOPTS      设置任意配置和仓库选项
  --skip-broken         通过跳过软件包来解决依赖问题
  -h, --help, --help-cmd
                        显示命令帮助
  --allowerasing        允许解决依赖关系时删除已安装软件包
  -b, --best            在事务中尝试最佳软件包版本。
  --nobest              不将事务限制在最佳候选
  -C, --cacheonly       完全从系统缓存运行，不升级缓存
  -R [minutes], --randomwait [minutes]
                        最大命令等待时间
  -d [debug level], --debuglevel [debug level]
                        调试输出级别
  --debugsolver         转储详细解决结果至文件
  --showduplicates      在 list/search 命令下，显示仓库里重复的条目
  -e ERRORLEVEL, --errorlevel ERRORLEVEL
                        错误输出级别
  --obsoletes           对 upgrade 启用 dnf 的过期处理逻辑，或对 info、list 和 repoquery
                        启用软件包过期的显示功能
  --rpmverbosity [debug level name]
                        rpm调试输出等级
  -y, --assumeyes       全部问题自动应答为是
  --assumeno            全部问题自动应答为否
  --enablerepo [repo]   基于当前的dnf指令目前可用的仓库，可以接受一个id，一个由分隔符分割的id列表或一个id的glob。该选项
                        可以被多次指定。
  --disablerepo [repo]  基于当前的dnf指令目前不可用的仓库，可以接受一个id，一个由分隔符分割的id列表或一个id的glob。该选
                        项可以被多次指定，但使用"--repo"显式互斥。
  --repo [repo], --repoid [repo]
                        启用指定 id 或 glob 的仓库，可以指定多次
  --enable              使用 config-manager 命令启用 repos (自动保存)
  --disable             使用 config-manager 命令禁用 repos (自动保存)
  -x [package], --exclude [package], --excludepkgs [package]
                        用全名或通配符排除软件包
  --disableexcludes [repo], --disableexcludepkgs [repo]
                        禁用 excludepkgs
  --repofrompath [repo,path]
                        附加仓库所要使用的标签和路径（与 baseurl 中的路径一致），可以指定多次。
  --noautoremove        禁用删除不再被使用的依赖软件包
  --nogpgcheck          禁用 gpg 签名检查 (如果 RPM 策略允许)
  --color COLOR         配置是否使用颜色
  --refresh             在运行命令之前将元数据标记为过期
  -4                    仅解析 IPv4 地址
  -6                    仅解析 IPv6 地址
  --destdir DESTDIR, --downloaddir DESTDIR
                        设置软件包要复制到的目录
  --downloadonly        仅下载软件包
  --comment COMMENT     为事务添加一个注释
  --bugfix              在更新中包括与 bug 修复有关的软件包
  --enhancement         在更新中包括与功能增强有关的软件包
  --newpackage          在更新中包括与新软件包有关的软件包
  --security            在更新中包括与安全有关的软件包
  --advisory ADVISORY, --advisories ADVISORY
                        在更新中包括修复指定公告所必须的软件包
  --bz BUGZILLA, --bzs BUGZILLA
                        在更新中包括修复给定 BZ 所必须的软件包
  --cve CVES, --cves CVES
                        在更新中包括修复给定 CVE 所必须的软件包
  --sec-severity {Critical,Important,Moderate,Low}, --secseverity {Critical,Important,Moderate,Low}
                        在更新中包括匹配给定安全等级的安全相关的软件包
  --forcearch ARCH      强制使用一个架构

Copr command-specific options:
  --installed           列出所有安装的 Copr 仓库（默认）
  --enabled             列出启动的 Copr 仓库
  --disabled            列出禁用的 Copr 仓库
  --available-by-user NAME
                        按照用户 NAME 列出可用的 Copr 仓库
  --hub HUB             指定需要使用的 Copr 实例

  {help,enable,disable,remove,list,search}
  arg
```

