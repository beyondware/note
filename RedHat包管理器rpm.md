## rpm --help

```sh
用法: rpm [选项...]

查询/验证软件包选项：
  -a, --all                          查询/验证所有软件包
  -f, --file                         query/verify package(s) owning installed
                                     file
      --path                         query/verify package(s) owning path,
                                     installed or not
  -g, --group                        查询/验证组中的软件包
  -p, --package                      查询/验证一个软件包文件
      --pkgid                        根据软件包标识符查询/验证软件包
      --hdrid                        根据头部标识符查询/验证软件包
  -q, --query                        rpm 查询模式
      --triggeredby                  查找由软件包所触发的软件包
      --whatconflicts                查询/验证需要某个依赖对象的软件包
      --whatrequires                 查询/验证需要某个依赖对象的软件包
      --whatobsoletes                查询/验证废弃依赖的软件包
      --whatprovides                 查询/验证提供相关依赖的软件包
      --whatrecommends               查询/验证推荐依赖的软件包
      --whatsuggests                 查询/验证建议依赖的软件包
      --whatsupplements              查询/验证补充依赖的软件包
      --whatenhances                 查询/验证增强依赖的软件包
      --nomanifest                   不把非软件包文件作为清单处理

查询/验证文件选项：
  -c, --configfiles                  only include configuration files
  -d, --docfiles                     only include documentation files
  -L, --licensefiles                 only include license files
  -A, --artifactfiles                only include artifact files
      --noghost                      exclude %%ghost files
      --noconfig                     exclude %%config files
      --noartifact                   exclude %%artifact files

查询选项（用 -q 或 --query）：
      --dump                         转储基本文件信息
  -l, --list                         列出软件包中的文件
      --queryformat=QUERYFORMAT      使用这种格式打印信息
  -s, --state                        显示列出文件的状态

验证选项（用 -V 或 --verify）：
      --nofiledigest                 不验证文件摘要
      --nofiles                      不验证软件包中文件
      --nodeps                       不验证包依赖
      --noscript                     不执行验证脚本

安装/升级/擦除选项：
      --allfiles                     安装全部文件，甚至包含那些可能被跳过的配置文件
      --allmatches                   移除所有符合 <package>
                                     的软件包(如果 <package>
                                     被指定未多个软件包，常常会导致错误出现)
      --badreloc                     对不可重定位的软件包重新分配文件位置
  -e, --erase=<package>+             清除 (卸载) 软件包
      --excludedocs                  不安装程序文档
      --excludepath=<path>           略过以 <path> 开头的文件 
      --force                        --replacepkgs --replacefiles 的缩写
  -F, --freshen=<packagefile>+       如果软件包已经安装，升级软件包
  -h, --hash                         在软件包安装时显示由“#”符号组成的进度条 (和 -v 一起使用效果更好)
      --ignorearch                   不验证软件包架构
      --ignoreos                     不验证软件包操作系统
      --ignoresize                   在安装前不检查磁盘空间
      --noverify                     short hand for --ignorepayload
                                     --ignoresignature
  -i, --install                      安装软件包
      --justdb                       更新数据库，但不修改文件系统
      --nodb                         do not update the database, but modify
                                     the filesystem
      --nodeps                       不验证软件包依赖
      --nofiledigest                 不验证文件摘要
      --nocontexts                   不安装文件的安全上下文
      --nocaps                       don't install file capabilities
      --noorder                      不对软件包安装重新排序以满足依赖关系
      --noscripts                    不执行软件包小脚本
      --notriggers                   不执行本软件包触发的任何小脚本
      --oldpackage                   更新到软件包的旧版本(带
                                     --force 自动完成这一功能)
      --percent                      安装软件包时打印百分比
      --prefix=<dir>                 如果可重定位，便把软件包重定位到 <dir>
      --relocate=<old>=<new>         将文件从 <old> 重定位到 <new>
      --replacefiles                 忽略软件包之间的冲突的文件
      --replacepkgs                  如果软件包已经有了，重新安装软件包
      --test                         不真正安装，只是判断下是否能安装
  -U, --upgrade=<packagefile>+       升级软件包
      --reinstall=<packagefile>+     重新安装软件包
      --restore=<packagefile>+       restore package(s)

所有 rpm 模式和可执行文件的通用选项：
  -D, --define=“MACRO EXPR”          定义值为 EXPR 的 MACRO
      --undefine=MACRO               未定义的 MACRO
  -E, --eval=“EXPR”                  打印 EXPR 的宏展开
      --target=CPU-VENDOR-OS         Specify target platform
      --macros=<FILE:…>              从文件 <FILE:...>
                                     读取宏，不使用默认文件
      --load=<FILE>                  load a single macro file
      --noplugins                    不要启用任何插件
      --nodigest                     不校验软件包的摘要
      --nosignature                  不验证软件包签名
      --rcfile=<FILE:…>              从文件 <FILE:...>
                                     读取宏，不使用默认文件
  -r, --root=ROOT                    使用 ROOT 作为顶级目录 (default:
                                     "/")
      --dbpath=DIRECTORY             使用 DIRECTORY 目录中的数据库
      --querytags                    显示已知的查询标签
      --showrc                       显示最终的 rpmrc 和宏配置
      --quiet                        提供更少的详细信息输出
  -v, --verbose                      提供更多的详细信息输出
      --version                      打印使用的 rpm 版本号

Options implemented via popt alias/exec:
      --scripts                      list install/erase scriptlets from
                                     package(s)
      --conflicts                    list capabilities this package conflicts
                                     with
      --obsoletes                    list other packages removed by installing
                                     this package
      --provides                     list capabilities that this package
                                     provides
      --requires                     list capabilities required by package(s)
      --recommends                   list capabilities recommended by
                                     package(s)
      --suggests                     list capabilities suggested by package(s)
      --supplements                  list capabilities supplemented by
                                     package(s)
      --enhances                     list capabilities enhanced by package(s)
      --info                         list descriptive information from
                                     package(s)
      --changelog                    list change logs for this package
      --changes                      list changes for this package with full
                                     time stamps
      --xml                          list metadata in xml
      --triggers                     list trigger scriptlets from package(s)
      --filetriggers                 list filetrigger scriptlets from
                                     package(s)
      --last                         list package(s) by install time, most
                                     recent first
      --dupes                        list duplicated packages
      --filesbypkg                   list all files from each package
      --fileclass                    list file names with their classes
      --filecolor                    list file names with their colors
      --fileprovide                  list file names with their provides
      --filerequire                  list file names with requires
      --filecaps                     list file names with their POSIX1.e
                                     capabilities

帮助选项:
  -?, --help                         显示这个帮助信息
      --usage                        显示简短的使用说明
```
