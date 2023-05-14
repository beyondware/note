## 官方源

1、主软件源（开源软件）

> https://download.opensuse.org/opensuse/tumbleweed/repo/oss/

2、主软件源（非开源软件）

> https://download.opensuse.org/opensuse/tumbleweed/repo/non-oss/

3、主更新源

> https://download.opensuse.org/update/tumbleweed/

4、主软件源（源代码）

> https://download.opensuse.org/source/tumbleweed/repo/

5、主调试源

> https://download.opensuse.org/debug/tumbleweed/repo/

6、字体

> https://download.opensuse.org/repositories/M17N:/fonts/openSUSE_Tumbleweed/

## 修改源

1、打开 YaST

2、点击 Software (软件) 分组中的 Software Repositories（软件源）

3、点击 Edit（编辑），替换**三个**官方源 oss、non-oss，update（部分源未更新）

```sh
https://download.opensuse.org
```

修改为

```sh
https://mirrors.cernet.edu.cn/opensuse
```

> https://help.mirrors.cernet.edu.cn/opensuse/

## 安装

```sh
sudo zypper install 或者 sudo zypper in
```

## 移除

```sh
sudo zypper remove 或者 sudo zypper rm
```

## 更新

```sh
sudo zypper update 或者 sudo zypper up
```

## 刷新

```sh
sudo zypper refresh 或者 sudo zypper ref
```

## 搜索

```sh
sudo zypper search 或者 sudo zypper se
```

### 查找所有本地安装程序

```sh
sudo zypper search --installed-only
```
### 列出与 xx 相关的本地安装软件

```sh
sudo zypper search --installed-only | grep xx
```

## 详细信息

```sh
sudo zypper info 或者 sudo zypper if
```

## 清理本地包缓存

```sh
sudo zypper clean 或者 sudo zypper cc
```

## zypper --help

```sh
用法：

    zypper [--全局选项] <命令> [--命令选项] [参数]
    zypper <子命令> [--命令选项] [参数]

全局选项：

    --help, -h              帮助。
    --version, -V           输出版本号。
    --promptids             输出 zypper 的用户提示列表。
    --config, -c <文件>     使用指定而非默认的配置文件。
    --userdata <字符串>     用户自定义的用于历史和插件中的事务 ID。
    --quiet, -q             压制正常输出，仅打印错误消息。
    --verbose, -v           增加消息的详细程度（调试模式）。
    --color
    --no-color              若 tty 支持是否使用有颜色输出。
    --no-abbrev, -A         在表格中不要缩写文本。 Default: false
    --table-style, -s <整数>
                            表格样式 (0-11)。
    --non-interactive, -n   不询问任何选择，自动使用默认回复。 Default: false
    --non-interactive-include-reboot-patches
                            不把那些设置了"建议重启"旗标
                            的补丁视为可与用户交互的。 Default: false
    --xmlout, -x            切换到 XML 输出。
    --ignore-unknown, -i    忽略未知软件包。 Default: false
    --terse, -t             供程序阅读的简洁输出。这意味着 —no-abbrev 和
                            —no-color。


    --reposd-dir, -D <文件夹>
                            使用另一个软件源定义文件文件夹。
    --cache-dir, -C <文件夹>
                            为全部缓存使用另一个文件夹。
    --raw-cache-dir <文件夹>
                            使用另一个原始元数据缓存文件夹。
    --solv-cache-dir <文件夹>
                            使用另一个 solv 文件缓存文件夹。
    --pkg-cache-dir <文件夹>
                            使用另一个软件包缓存文件夹。

  软件源选项

    --no-gpg-checks         忽略失败的 GPG 校验并继续。 Default: false
    --gpg-auto-import-keys  自动信任并导入新软件源签名密钥。
    --plus-repo, -p <URI>   使用一个附加软件源。
    --plus-content <标签>   也使用提供指定关键字的已禁用软件源。可尝试使用
                            ‘--plus-content debug’
                            来临时启用表明其提供了侦错软件包的软件源。
    --disable-repositories  不从软件源读取元数据。
    --no-refresh            不刷新软件源。
    --no-cd                 忽略 CD/DVD 软件源。
    --no-remote             忽略远程软件源。
    --releasever            设置全部 .repo 文件中 $releasever
                            的值（默认：发行版版本号）

  目标选项

    --root, -R <文件夹>     在一个不同的根目录下操作。
    --installroot <文件夹>  在一个不同的根目录下操作，但与主机共享软件源。
    --disable-system-resolvables
                            不读取已安装软件包。

命令：

      help, ?               打印 zypper 帮助
      shell, sh             一次性接受多个命令。

  软件源管理：

      repos, lr             列出全部已定义的软件源。
      addrepo, ar           添加一个新软件源。
      removerepo, rr        移除指定软件源。
      renamerepo, nr        重命名指定软件源。
      modifyrepo, mr        修改指定软件源。
      refresh, ref          刷新全部软件源。
      clean, cc             清理本地缓存。

  服务管理：

      services, ls          列出全部已定义服务。
      addservice, as        添加一个新服务。
      modifyservice, ms     修改指定服务。
      removeservice, rs     移除指定服务。
      refresh-services, refs
                            刷新全部服务。

  软件管理：

      install, in           安装软件包。
      remove, rm            移除软件包。
      removeptf, rmptf      移除（不局限于）PTF。
      verify, ve            校验软件包的依赖关系完整性。
      source-install, si    安装源代码包及其编译依赖。
      install-new-recommends, inr
                            安装已安装软件包推荐的新增软件包。

  更新管理：

      update, up            用新版本更新已安装软件包。
      list-updates, lu      列出可用更新。
      patch                 安装所需补丁。
      list-patches, lp      列出可获得的补丁。
      dist-upgrade, dup     执行发行版升级。
      patch-check, pchk     检查补丁。

  查询：

      search, se            搜索匹配一个模式的软件包。
      info, if              显示指定软件包的完整信息。
      patch-info            显示指定补丁的完整信息。
      pattern-info          显示指定软件集的完整信息。
      product-info          显示指定产品的完整信息。
      patches, pch          列出全部可用补丁。
      packages, pa          列出全部可用软件包。
      patterns, pt          列出全部可用软件集。
      products, pd          列出全部可用产品。
      what-provides, wp     列出能够提供指定功能的软件包。

  软件包锁定：

      addlock, al           添加一个软件包锁定。
      removelock, rl        移除一个软件包锁定。
      locks, ll             列出当前软件包锁定。
      cleanlocks, cl        移除无用的锁定。

  区域管理：

      locales, lloc         列出所请求区域 (语言代码)。
      addlocale, aloc       添加区域到所请求区域。
      removelocale, rloc    从所请求区域中移除区域。

  其它命令：

      versioncmp, vcmp      比较两个版本字符串。
      targetos, tos         打印目标操作系统 ID 字符串。
      licenses              打印已安装软件包的许可证和最终用户协议的汇总报告。
      download              下载通过命令行指定的 RPM 到本地文件夹。
      source-download       下载全部已安装软件包的源代码 RPM 到一个本地文件夹。
      needs-rebooting       检查需要重启旗标是否设置。
      ps
                            列出可能仍使用着被最近升级删除的文件和函数库的运行中进程。
      purge-kernels         移除旧内核。

  子命令：

      subcommand            列出可用子命令。
      appstream-cache       <没有 "zypper-appstream-cache" 的手册页入口>

输入 'zypper help <COMMAND>' 获取具体命令的帮助。
```
