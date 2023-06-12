### 多进程

```sh
sudo vim /etc/pacman.conf
```

> MaxParallelDownloads = 5 //取消#注释，并行下载数

> ParallelDownloads = 5

### 系统

1、全部升级

```sh
sudo pacman -Syu
```

2、强制更新（软件包数据库）

```sh
sudo pacman -Syy
```

3、全部强制升级

```sh
sudo pacman -Syyu
```

### 安装

1、安装多个包，用空格隔开

```sh
sudo pacman -S 包1 包2
```

2、更新（包数据库）

```sh
sudo pacman -Sy 包名
```

3、安装过程，显示执行信息

```sh
sudo pacman -Sv 包名
```

4、安装本地包，扩展名：pkg.tar.gz 或 pkg.tar.xz

```sh
sudo pacman -U 本地包
```

5、安装远程包（不在官方源）

```sh
sudo pacman -U 软件包URL
```

6、只下载，不安装

```sh
sudo pacman -Sw 包名
```

### 删除

1、删除，保留依赖

```sh
sudo pacman -R 包名
```

2、删除不需要的依赖

```sh
sudo pacman -Rs 包名
```

> pacman -Rs 被拒，可以尝试

```sh
sudo pacman -Rsu 包名
```

3、删除依赖、配置文件

```sh
sudo pacman -Rsn 包名
```

4、删除包、依赖（警告）

```sh
sudo pacman -Rsc 包名
```

5、删除包、依赖和配置文件

```sh
sudo pacman -Rscn 包名
```

6、删除包，跳过检查

```sh
sudo pacman -Rd 包名
```

7、强制删除，跳过所有检查（务必谨慎）

```sh
sudo pacman -Rdd 包名
```

### 清理缓存

1、清理未安装包，位于/var/cache/pacman/pkg

```sh
sudo pacman -Sc
```

2、清理所有缓存

```sh
sudo pacman -Scc
```

### 搜索

1、搜索含*关键字*的包

```sh
sudo pacman -Ss 关键字
```

2、显示包的详尽信息

```sh
sudo pacman -Si 包名
```

3、搜索所属组的所有包

```sh
sudo pacman -Sg 组名
```

### 列出

1、列出所有已安装包

```sh
pacman -Q
```

2、列出所有已安装包，不显示版本号（-q：省略版本号）

```sh
pacman -Qq
```

3、列出所有已安装包，包括安装路径（-l：列表）

```sh
pacman -Ql
```

4、搜索*关键字*匹配的已安装包

```sh
pacman -Qs 关键字
```

5、列出已安装包的详细信息

```sh
pacman -Qi 包名
```

6、列出所有显式安装（-e：显式安装）

```sh
pacman -Qqe
```

7、列出作为依赖项自动安装的包（-d：依赖项）

```sh
pacman -Qqd
```

8、列出孤立的包（-t：不再被依赖）

```sh
pacman -Qqdt
```

### pacman -h

```sh
用法:  pacman <操作> [...]
操作:
    pacman {-h --help}
    pacman {-V --version}
    pacman {-D --database} <选项> <软件包>
    pacman {-F --files}    [选项] [文件]
    pacman {-Q --query}    [选项] [软件包]
    pacman {-R --remove}   [选项] <软件包>
    pacman {-S --sync}     [选项] [软件包]
    pacman {-T --deptest}  [选项] [软件包]
    pacman {-U --upgrade}  [选项] <文件>

使用 'pacman {-h --help}' 及某个操作以查看可用选项
```

#### pacman -D -h

```sh
用法:  pacman {-D --database} <选项> <软件包>
选项:
  -b, --dbpath <路径>  指定另外的数据库位置
  -k, --check          检查本地数据库有效性 (-kk 以同步数据库)
  -q, --quiet          不显示成功消息的输出
  -r, --root <路径>    指定另外的安装根目录
  -v, --verbose        显示详细信息
      --arch <架构>    设定另外的架构
      --asdeps         标记为非明确指定安装的软件包
      --asexplicit     标记为明确指定安装的软件包
      --cachedir <dir> 指定另外的软件包缓存位置
      --color <when>   彩色化输出
      --config <路径>  指定另外的配置文件
      --confirm        总是询问确认
      --debug          显示调试信息
      --disable-download-timeout
                       下载时用宽松的超时
      --gpgdir <路径>  设定 GnuPG 的其他主目录
      --hookdir <目录>  指定另外的钩子位置
      --logfile <路径> 指定另外的日志文件
      --noconfirm      不询问确认
      --sysroot        在一个已挂载的 guest 系统操作（仅 root）
```

#### pacman -F -h

```sh
用法:  pacman {-F --files} [选项] [文件]
选项:
  -b, --dbpath <路径>  指定另外的数据库位置
  -l, --list           列出被查询软件包的内容
  -q, --quiet          在查询或搜索时显示较少的信息
  -r, --root <路径>    指定另外的安装根目录
  -v, --verbose        显示详细信息
  -x, --regex          启用正则表达式进行搜索
  -y, --refresh        从服务器下载新的软件包数据库
                       (-yy 强制更新软件包数据库)
      --arch <架构>    设定另外的架构
      --cachedir <dir> 指定另外的软件包缓存位置
      --color <when>   彩色化输出
      --config <路径>  指定另外的配置文件
      --confirm        总是询问确认
      --debug          显示调试信息
      --disable-download-timeout
                       下载时用宽松的超时
      --gpgdir <路径>  设定 GnuPG 的其他主目录
      --hookdir <目录>  指定另外的钩子位置
      --logfile <路径> 指定另外的日志文件
      --machinereadable
                       产生机器可读输出
      --noconfirm      不询问确认
      --sysroot        在一个已挂载的 guest 系统操作（仅 root）
```

#### pacman -Q -h

```sh
用法:  pacman {-Q --query} [选项] [软件包]
选项:
  -b, --dbpath <路径>  指定另外的数据库位置
  -c, --changelog      查看某软件包的更新日志
  -d, --deps           列出所有作为依赖关系安装的软件包 [过滤器]
  -e, --explicit       列出所有单独指定安装的软件包 [过滤器]
  -g, --groups         查看某软件包组所属的所有软件包
  -i, --info           查看软件包信息 (-ii 查看备份文件)
  -k, --check          检查软件包的文件存在(-kk检查文件属性)
  -l, --list           列出被查询软件包的内容
  -m, --foreign        列出没有在同步数据库时找到的已安装软件包 [过滤器]
  -n, --native         列出只在(同步)数据库中的已安装软件包 [过滤]
  -o, --owns <文件>    查询哪个软件包拥有<文件>
  -p, --file <软件包>  从某个软件包而不是数据库查询
  -q, --quiet          在查询或搜索时显示较少的信息
  -r, --root <路径>    指定另外的安装根目录
  -s, --search <regex> 搜寻符合指定字符串的已安装本地的软件包
  -t, --unrequired     列出不被任何软件包(可选)要求的软件包(-tt 忽略可选依赖) [过滤器]
  -u, --upgrades       列出所有可升级的软件包 [过滤器]
  -v, --verbose        显示详细信息
      --arch <架构>    设定另外的架构
      --cachedir <dir> 指定另外的软件包缓存位置
      --color <when>   彩色化输出
      --config <路径>  指定另外的配置文件
      --confirm        总是询问确认
      --debug          显示调试信息
      --disable-download-timeout
                       下载时用宽松的超时
      --gpgdir <路径>  设定 GnuPG 的其他主目录
      --hookdir <目录>  指定另外的钩子位置
      --logfile <路径> 指定另外的日志文件
      --noconfirm      不询问确认
      --sysroot        在一个已挂载的 guest 系统操作（仅 root）
```

#### pacman -R -h

```sh
用法:  pacman {-R --remove} [选项] <软件包>
选项:
  -b, --dbpath <路径>  指定另外的数据库位置
  -c, --cascade        删除软件包及所有依赖于此的软件包
  -d, --nodeps         跳过依赖关系的版本检查 (-dd 跳过所有检查)
  -n, --nosave         删除配置文件
  -p, --print          打印目标而不是执行操作
  -r, --root <路径>    指定另外的安装根目录
  -s, --recursive      删除不需要的依赖关系
                       (-ss 包括单独指定安装的依赖关系)
  -u, --unneeded       删除不需要的软件包
  -v, --verbose        显示详细信息
      --arch <架构>    设定另外的架构
      --assume-installed <package=version>
                       添加一个虚拟包用以满足依赖要求
      --cachedir <dir> 指定另外的软件包缓存位置
      --color <when>   彩色化输出
      --config <路径>  指定另外的配置文件
      --confirm        总是询问确认
      --dbonly         仅修改数据库条目，而非软件包文件
      --debug          显示调试信息
      --disable-download-timeout
                       下载时用宽松的超时
      --gpgdir <路径>  设定 GnuPG 的其他主目录
      --hookdir <目录>  指定另外的钩子位置
      --logfile <路径> 指定另外的日志文件
      --noconfirm      不询问确认
      --noprogressbar  下载文件时不显示进度条
      --noscriptlet    不执行安装小脚本
      --print-format <字符串>
                       指定如何打印目标
      --sysroot        在一个已挂载的 guest 系统操作（仅 root）
```

#### pacman -S -h

```sh
用法:  pacman {-S --sync} [选项] [软件包]
选项:
  -b, --dbpath <路径>  指定另外的数据库位置
  -c, --clean          从缓存目录中删除旧软件包 (-cc 清除所有)
  -d, --nodeps         跳过依赖关系的版本检查 (-dd 跳过所有检查)
  -g, --groups         查看某软件包组所属的所有软件包
                       (-gg 查看所有软件包组和所属于它们的软件包)
  -i, --info           查看软件包信息 (-ii 查看更多信息)
  -l, --list <repo>    查看在该软件库中的软件包清单
  -p, --print          打印目标而不是执行操作
  -q, --quiet          在查询或搜索时显示较少的信息
  -r, --root <路径>    指定另外的安装根目录
  -s, --search <正则表达式> 按照指定字符串查询远端软件库
  -u, --sysupgrade     升级所有已安装的软件包 (-uu 可启用降级)
  -v, --verbose        显示详细信息
  -w, --downloadonly   下载但不安装/升级软件包
  -y, --refresh        从服务器下载新的软件包数据库
                       (-yy 强制更新软件包数据库)
      --arch <架构>    设定另外的架构
      --asdeps         作为非单独指定安装的软件包安装
      --asexplicit     作为单独指定安装的软件包安装
      --assume-installed <package=version>
                       添加一个虚拟包用以满足依赖要求
      --cachedir <dir> 指定另外的软件包缓存位置
      --color <when>   彩色化输出
      --config <路径>  指定另外的配置文件
      --confirm        总是询问确认
      --dbonly         仅修改数据库条目，而非软件包文件
      --debug          显示调试信息
      --disable-download-timeout
                       下载时用宽松的超时
      --gpgdir <路径>  设定 GnuPG 的其他主目录
      --hookdir <目录>  指定另外的钩子位置
      --ignore <软件包>   升级时忽略某个软件包 (可多次使用)
      --ignoregroup <软件包组>
                         升级时忽略某个软件包组 (可多次使用)
      --logfile <路径> 指定另外的日志文件
      --needed         不重新安装已是最新的软件包
      --noconfirm      不询问确认
      --noprogressbar  下载文件时不显示进度条
      --noscriptlet    不执行安装小脚本
 --overwrite <glob>
                        覆盖冲突的文件（可以指定多次）
      --print-format <字符串>
                       指定如何打印目标
      --sysroot        在一个已挂载的 guest 系统操作（仅 root）
```

#### pacman -T -h

```sh
用法:  pacman {-T --deptest} [选项] [软件包]
选项:
  -b, --dbpath <路径>  指定另外的数据库位置
  -r, --root <路径>    指定另外的安装根目录
  -v, --verbose        显示详细信息
      --arch <架构>    设定另外的架构
      --cachedir <dir> 指定另外的软件包缓存位置
      --color <when>   彩色化输出
      --config <路径>  指定另外的配置文件
      --confirm        总是询问确认
      --debug          显示调试信息
      --disable-download-timeout
                       下载时用宽松的超时
      --gpgdir <路径>  设定 GnuPG 的其他主目录
      --hookdir <目录>  指定另外的钩子位置
      --logfile <路径> 指定另外的日志文件
      --noconfirm      不询问确认
      --sysroot        在一个已挂载的 guest 系统操作（仅 root）
```

#### pacman -U -h

```sh
用法:  pacman {-U --upgrade} [选项] <文件>
选项:
  -b, --dbpath <路径>  指定另外的数据库位置
  -d, --nodeps         跳过依赖关系的版本检查 (-dd 跳过所有检查)
  -p, --print          打印目标而不是执行操作
  -r, --root <路径>    指定另外的安装根目录
  -v, --verbose        显示详细信息
  -w, --downloadonly   下载但不安装/升级软件包
      --arch <架构>    设定另外的架构
      --asdeps         作为非单独指定安装的软件包安装
      --asexplicit     作为单独指定安装的软件包安装
      --assume-installed <package=version>
                       添加一个虚拟包用以满足依赖要求
      --cachedir <dir> 指定另外的软件包缓存位置
      --color <when>   彩色化输出
      --config <路径>  指定另外的配置文件
      --confirm        总是询问确认
      --dbonly         仅修改数据库条目，而非软件包文件
      --debug          显示调试信息
      --disable-download-timeout
                       下载时用宽松的超时
      --gpgdir <路径>  设定 GnuPG 的其他主目录
      --hookdir <目录>  指定另外的钩子位置
      --ignore <软件包>   升级时忽略某个软件包 (可多次使用)
      --ignoregroup <软件包组>
                         升级时忽略某个软件包组 (可多次使用)
      --logfile <路径> 指定另外的日志文件
      --needed         不重新安装已是最新的软件包
      --noconfirm      不询问确认
      --noprogressbar  下载文件时不显示进度条
      --noscriptlet    不执行安装小脚本
 --overwrite <glob>
                        覆盖冲突的文件（可以指定多次）
      --print-format <字符串>
                       指定如何打印目标
      --sysroot        在一个已挂载的 guest 系统操作（仅 root）
```

### 显示包的依赖树

```sh
pactree 包名
```

### pactree --help

```sh
pactree v1.9.0

Package dependency tree viewer.

Usage: pactree [options] <package>

Options:
  -a, --ascii             use ASCII characters for tree formatting
  -c, --color             colorize output
      --config <path>     set an alternate configuration file
  -b, --dbpath <path>     set an alternate database location
      --debug             display debug messages
  -d, --depth <#>         limit the depth of recursion
      --gpgdir <path>     set an alternate home directory for GnuPG
  -g, --graph             generate output for graphviz's dot
  -l, --linear            enable linear output
  -o, --optional[=depth]  controls at which depth to stop printing optional deps
                          (-1 for no limit)
  -r, --reverse           list packages that depend on the named package
  -s, --sync              search sync databases instead of local
  -u, --unique            show dependencies with no duplicates (implies -l)
  -h, --help              display this help message and exit
  -V, --version           display version information and exit
```
