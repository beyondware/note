## 下载 Meslo 字体（只安装 MesloLGM Nerd Font 即可）

- 最新版

> https://ghproxy.com/https://github.com/ryanoasis/nerd-fonts/releases/latest/download/Meslo.zip

> https://ghproxy.com/https://github.com/ryanoasis/nerd-fonts/releases/download/v3.0.0/Meslo.zip

- PowerShell——外观——字体：（选择）MesloLGM Nerd Font

##  Microsoft Store 商店在线安装

> https://apps.microsoft.com/store/detail/ohmyposh/XP8K0HKJFRXGCK

## 安装 oh-my-posh（winget 安装）

```sh
winget install JanDeDobbeleer.OhMyPosh -s winget
```

## 创建配置文件

```sh
New-Item -Path $PROFILE -Type File -Force
```

### 编辑 PowerShell 配置文件

```sh
notepad $PROFILE
```

### 指定主题（如：jandedobbeleer）

```sh
& ([ScriptBlock]::Create((oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\jandedobbeleer.omp.json" --print) -join "`n"))
```

### 随机主题（推荐）

```sh
$theme = Get-ChildItem $env:UserProfile\\AppData\\Local\\Programs\\oh-my-posh\\themes\\ | Get-Random
echo "hello! today's lucky theme is: $theme :)"
oh-my-posh --init --shell pwsh --config $theme.FullName | Invoke-Expression
```

### 重新加载，配置文件

```sh
. $PROFILE
```

### 报错信息

```sh
The term 'oh-my-posh' is not recognized as a name of a cmdlet, function, script file, or executable program.
Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
```

1、将 oh-my-posh 安装路径加入到环境变量中


```sh
C:\Users\pc\AppData\Local\Programs\oh-my-posh\bin
```

2、关闭终端，重新加载。

## 安装文件图标库

```sh
Install-Module -Name Terminal-Icons -Repository PSGallery
```

### 编辑配置文件

```sh
notepad $PROFILE
```

### 追加配置

```sh
Import-Module -Name Terminal-Icons
```

### 重新加载，配置文件

```sh
. $PROFILE
```

## VSCode 终端显示

- VSCode 字体设置与 PowerShell 字体一样（如：MesloLGM Nerd Font）

## 参考

> https://ohmyposh.dev/docs/

## oh-my-posh --help

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
  disable     Disable a feature
  enable      Enable a feature
  font        Manage fonts
  get         Get a value from oh-my-posh
  help        Help about any command
  init        Initialize your shell and config
  notice      Print the upgrade notice when a new version is available.
  print       Print the prompt/context
  prompt      Set up the prompt for your shell (deprecated)
  toggle      Toggle a segment on/off
  version     Print the version

Flags:
  -c, --config string   config file path
  -h, --help            help for oh-my-posh
  -i, --init            init (deprecated)
  -s, --shell string    shell (deprecated)
      --version         version

Use "oh-my-posh [command] --help" for more information about a command.
```
