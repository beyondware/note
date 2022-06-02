---
title: oh-my-posh 使用方法
author: beyondware
tags:
  - [oh-my-posh]
categories:
  - [Windows]
---

## 安装 oh-my-posh

- winget

```sh
winget install oh-my-posh
```

## 升级 oh-my-posh

```sh
winget upgrade oh-my-posh
```

## 查看 oh-my-posh 安装位置

```sh
(Get-Command oh-my-posh).Source
```

## 配置文件

1、新建

```sh
if (!(Test-Path -Path $PROFILE )) { New-Item -Type File -Path $PROFILE -Force }
```

2、打开

```sh
notepad.exe $PROFILE
```

3、添加到配置文件

```
oh-my-posh init pwsh | Invoke-Expression
```

4、加载生效

```sh
. $PROFILE
```

## oh-my-posh 主题

- 查看主题路径

```sh
Get-PoshThemes
```

- 修改主题

1、打开

```sh
notepad.exe $PROFILE
```

2、添加（比如：jandedobbeleer 主题）

```
 oh-my-posh init pwsh --config C:\Users\beyondware\AppData\Local\Programs\oh-my-posh\themes/jandedobbeleer.omp.json | Invoke-Expression
```

3、加载生效

```sh
. $PROFILE
```

## 显示图标

下载 `MesloLGM NF` 字体

> https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/Meslo.zip

在 Windows Terminal 中字体设置为 `MesloLGM NF`

在 Visual Studio Code 中字体同样设置为 `MesloLGM NF`

## 命令

```sh
oh-my-posh is a cross platform tool to render your prompt.
It can use the same configuration everywhere to offer a consistent
experience, regardless of where you are. For a detailed guide
on getting started, have a look at the docs at https://ohmyposh.dev

Usage:
  oh-my-posh [flags]
  oh-my-posh [command]

Available Commands:
  cache       Interact with the oh-my-posh cache
  completion  Generate the autocompletion script for the specified shell
  config      Interact with the config
  debug       Print the prompt in debug mode
  get         Get a value from oh-my-posh
  help        Help about any command
  init        Initialize your shell and config
  print       Print the prompt/context
  prompt      Set up the prompt for your shell (deprecated)
  version     Print the version

Flags:
  -c, --config string   config (required)
  -h, --help            help for oh-my-posh
  -i, --init            init (deprecated)
  -s, --shell string    shell (deprecated)
      --version         version

Use "oh-my-posh [command] --help" for more information about a command.
```

## 参考

> https://ohmyposh.dev/docs
