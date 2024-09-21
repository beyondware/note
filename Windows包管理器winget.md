# winget 安装

1、打开开发者模式

> 设置→系统→开发者选项→开发者模式（打开）

2、参考

> https://github.com/microsoft/winget-cli

> https://docs.microsoft.com/zh-cn/windows/package-manager/winget/

# 软件库

1、winget-pkgs：官方库

> https://github.com/microsoft/winget-pkgs

2、winstall：第三方库

> https://winstall.app/

> https://github.com/MehediH/winstall

# 换源

1、更换源（以管理员身份运行）

```sh
winget source remove winget
```

```sh
winget source add winget https://mirror.nju.edu.cn/winget-source --trust-level trusted
```

2、重置为官方源

```sh
winget source reset winget
```

3、参考

> https://help.mirrors.cernet.edu.cn/winget-source/

# 常用命令

1、安装

```sh
winget install
```

2、卸载

```sh
winget uninstall
```

3、升级

```sh
winget upgrade
```

4、搜索

```sh
winget search
```

5、详细信息

```sh
winget show
```

6、列出当前源

```sh
winget source list
```

# winget --help

```sh
Windows 程序包管理器 v1.8.1911
版权所有 (C) Microsoft Corporation。保留所有权利。

WinGet 命令行实用工具可从命令行安装应用程序和其他程序包。

使用情况: winget  [<命令>] [<选项>]

下列命令有效:
  install    安装给定的程序包
  show       显示包的相关信息
  source     管理程序包的来源
  search     查找并显示程序包的基本信息
  list       显示已安装的程序包
  upgrade    显示并执行可用升级
  uninstall  卸载给定的程序包
  hash       哈希安装程序的帮助程序
  validate   验证清单文件
  settings   打开设置或设置管理员设置
  features   显示实验性功能的状态
  export     导出已安装程序包的列表
  import     安装文件中的所有程序包
  pin        管理包钉
  configure  将系统配置为所需状态
  download   从给定的程序包下载安装程序
  repair     修复所选包

如需特定命令的更多详细信息，请向其传递帮助参数。 [-?]

下列选项可用：
  -v,--version                显示工具的版本
  --info                      显示工具的常规信息
  -?,--help                   显示选定命令的帮助信息
  --wait                      提示用户在退出前按任意键
  --logs,--open-logs          打开默认日志位置
  --verbose,--verbose-logs    启用 WinGet 的详细日志记录
  --nowarn,--ignore-warnings  禁止显示警告输出
  --disable-interactivity     禁用交互式提示
  --proxy                     设置要用于此执行的代理
  --no-proxy                  禁止对此执行使用代理

可在此找到更多帮助: "https://aka.ms/winget-command-help"
```
