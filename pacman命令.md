### 更新

1、全部升级

```sh
pacman -Syu
```

2、强制更新（软件包数据库）

```sh
pacman -Syy
```

3、全部强制升级

```sh
pacman -Syyu
```

### 安装

1、安装：多个安装包，需以空格隔开

```sh
pacman -S 包名
```

2、更新（软件包数据库）

```sh
pacman -Sy 包名
```

3、安装过程，显示执行信息

```sh
pacman -Sv 包名
```

4、安装本地包，扩展名：pkg.tar.gz 或 pkg.tar.xz

```sh
pacman -U 本地包
```

5、安装远程包（不在官方源）

```sh
pacman -U 软件包下载链接
```

### 删除

1、只删除包，保留依赖

```sh
pacman -R 包名
```

2、删除不需要的依赖

```sh
pacman -Rs 包名
```

3、-Rs 被拒，可以尝试

```sh
pacman -Rsu 包名
```

4、删除包和所有依赖（警告）

```sh
pacman -Rsc 包名
```

5、删除包，跳过检查

```sh
pacman -Rd 包名
```

6、强制删除，跳过所有检查（务必谨慎）

```sh
pacman -Rdd 包名
```

### 清理

1、清理未安装包，位于/var/cache/pacman/pkg

```sh
pacman -Sc
```

2、清理所有缓存

```sh
pacman -Scc
```

3、只下载，不安装

```sh
pacman -Sw 包名
```

### 查询

1、搜索含关键字的包

```sh
pacman -Ss 关键字
```

2、显示包的详尽信息

```sh
pacman -Si 包名
```

3、查看包所属组的所有软件包

```sh
pacman -Sg 包名
```

4、搜索已安装的包

```sh
pacman -Qs 关键字
```

5、显示已安装包的详细信息

```sh
pacman -Qi 包名
```

6、获取已安装包的文件列表

```sh
pacman -Ql 包名
```

7、显示包的依赖树

```sh
pactree 包名
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

pacman -D -h
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

pacman -F -h
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

pacman -Q -h
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

pacman -R -h
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

pacman -S -h
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

pacman -T -h
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

pacman -U -h
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
