---
title: PowerShell 使用方法
author: beyondware
tags:
  - [PowerShell]
categories:
  - [Windows]
description: 一款跨平台的shell
toc: true
pin: true
---

## PowerShell

- 参考

> https://docs.microsoft.com/zh-cn/powershell/module/powershellget

> https://docs.microsoft.com/zh-cn/powershell/module/Microsoft.PowerShell.Core

- 查看 PowerShell 版本

```sh
Get-Host | Select-Object Version
```

- 执行.ps1 脚本（管理员权限）

```sh
set-executionpolicy remotesigned
```

- 更改组策略权限

```sh
Get-ExecutionPolicy -List
```

- 允许本地脚本执行

```sh
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

- 临时使用权限

```sh
Set-ExecutionPolicy Bypass -Scope Process -Force
```

- 将 CurrentUser 设置为 RemoteSigned

### 常用命令

- 查看

```sh
Get-Module -ListAvailable
```

- 安装

```sh
Install-Module -Name
```

- 升级

```sh
Update-Module -Name
```

- 卸载

```sh
Uninstall-Module -Name
```

- 查看历史记录

```sh
Get-History
```

- 清理历史记录

```sh
Clear-History
```

> 添加 -Scope AllUsers //所有人（管理员权限）

> 添加 -Scope CurrentUser //当前用户，无需添加（默认）

> 添加 -AllowPrerelease //预览版

> 添加 -Force //表示一路确认

## 安装软件

### PSReadLine

```sh
Install-Module -Name PSReadLine
```

### Terminal-Icons

```sh
Install-Module -Name Terminal-Icons -Repository PSGallery
```

```sh
Show-TerminalIconsTheme
```

### PSFzf

```sh
Install-Module -Name PSFzf
```

### z

```sh
Install-Module -Name z
```

## 配置文件

- 新建

```sh
if (!(Test-Path -Path $PROFILE )) { New-Item -Type File -Path $PROFILE -Force }
```

- 打开

```sh
notepad.exe $PROFILE
```

- 添加到配置文件

```sh
# 设置预测文本来源为历史记录
Set-PSReadLineOption -PredictionSource History

# 每次回溯输入历史，光标定位于输入内容末尾
Set-PSReadLineOption -HistorySearchCursorMovesToEnd

# 设置 Tab 为菜单补全和 Intellisense
Set-PSReadLineKeyHandler -Key "Tab" -Function MenuComplete

# 设置 Ctrl+d 为退出 PowerShell
Set-PSReadlineKeyHandler -Key "Ctrl+d" -Function ViExit

# 设置 Ctrl+z 为撤销
Set-PSReadLineKeyHandler -Key "Ctrl+z" -Function Undo

# 设置向上键为后向搜索历史记录
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward

# 设置向下键为前向搜索历史纪录
Set-PSReadLineKeyHandler -Key DownArrow -Function HistorySearchForward

# 引入图标
Import-Module -Name Terminal-Icons
```

- 加载生效

```sh
. $PROFILE
```

## VSCode

- 如果 VSCodse 不生效，复制一份相同代码

> WindowsPowerShell\Microsoft.PowerShell_profile.ps1

> WindowsPowerShell\Microsoft.VSCode_profile.ps1

## 解决乱码

```sh
Set-Culture en-US
```
