## 安装 winget

### 在线安装

App Installer（应用安装程序）

> https://apps.microsoft.com/store/detail/app-installer/9NBLGGH4NNS1

### 离线包安装

- Windows 设置——隐私和安全性——开发者选项：（打开）开发者模式

> https://github.com/microsoft/winget-cli

## 文档

- winget 文档

> https://docs.microsoft.com/zh-cn/windows/package-manager/winget/

- wingetcreate：使用 Windows 程序包管理器清单创建程序

> https://github.com/microsoft/winget-create

## 软件库

- winget-pkgs：官方库

> https://github.com/microsoft/winget-pkgs

- winstall：第三方库

> https://winstall.app/

> https://github.com/MehediH/winstall

## 镜像源

1、更换源（以管理员身份运行终端）

```sh
winget source remove winget
```

```sh
winget source add winget https://mirrors.ustc.edu.cn/winget-source
```

2、重置为官方源

```sh
winget source reset winget
```

3、参考

> https://unicom.mirrors.ustc.edu.cn/help/winget-source.html

## winget --help

```sh
Windows 程序包管理器 v1.4.10173
版权所有 (C) Microsoft Corporation。保留所有权利。

WinGet 命令行实用工具可从命令行安装应用程序和其他程序包。

使用情况: winget [<命令>] [<选项>]

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

如需特定命令的更多详细信息，请向其传递帮助参数。 [-?]

下列选项可用：
  -v,--version              显示工具的版本
  --info                    显示工具的常规信息
  -?,--help                 显示选定命令的帮助信息
  --wait                    提示用户在退出前按任意键
  --verbose,--verbose-logs  启用 WinGet 的详细日志记录
  --disable-interactivity   禁用交互式提示

可在此找到更多帮助: "https://aka.ms/winget-command-help"
```
