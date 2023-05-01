## 安装 winget

1、先安装 App Installer（应用安装程序）

> https://apps.microsoft.com/store/detail/app-installer/9NBLGGH4NNS1

2、再安装 winget

> https://github.com/microsoft/winget-cli

3、winget 文档

> https://docs.microsoft.com/zh-cn/windows/package-manager/winget/

4、wingetcreate：使用 Windows 程序包管理器清单创建程序

> https://github.com/microsoft/winget-create

5、winget-pkgs：Windows 程序包管理器社区存储库

> https://github.com/microsoft/winget-pkgs

6、winstall：提供 winget 软件

> https://winstall.app/

> https://github.com/MehediH/winstall

## winget --help

```sh
WinGet 命令行实用工具可从命令行安装应用程序和其他程序包。

使用情况: winget [<命令>] [<选项>]

下列命令有效:
  install    安装给定的程序包
  show       显示包的相关信息
  source     管理程序包的来源
  search     查找并显示程序包的基本信息
  list       显示已安装的程序包
  upgrade    升级给定的程序包
  uninstall  卸载给定的程序包
  hash       哈希安装程序的帮助程序
  validate   验证清单文件
  settings   打开设置或设置管理员设置
  features   显示实验性功能的状态
  export     导出已安装程序包的列表
  import     安装文件中的所有程序包

如需特定命令的更多详细信息，请向其传递帮助参数。 [-?]

下列选项可用：
  -v,--version  显示工具的版本
  --info        显示工具的常规信息

可在此找到更多帮助： https://aka.ms/winget-command-help
```
