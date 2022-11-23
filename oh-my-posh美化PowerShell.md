## 安装字体（MesloLGL Nerd Font）

> https://github.com/ryanoasis/nerd-fonts/releases/download/v2.1.0/Meslo.zip

## 安装 oh-my-posh（Windows）

```sh
winget install JanDeDobbeleer.OhMyPosh -s winget
```

### 创建配置文件

```sh
New-Item -Path $PROFILE -Type File -Force
```

### 编辑 PowerShell 配置文件脚本

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

### 重新加载配置文件

```sh
. $PROFILE
```

## 安装文件图标库

```sh
Install-Module -Name Terminal-Icons -Repository PSGallery
```

### 编辑配置文件脚本

```sh
notepad $PROFILE
```

### 追加 $PROFILE 配置文件

```sh
Import-Module -Name Terminal-Icons
```

### 再次加载配置文件

```sh
. $PROFILE
```

## VSCode终端显示

- 将字体设置一样，即可显示（如：MesloLGL Nerd Font）

## oh-my-posh 命令

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
  font        Manage fonts
  get         Get a value from oh-my-posh
  help        Help about any command
  init        Initialize your shell and config
  print       Print the prompt/context
  prompt      Set up the prompt for your shell (deprecated)
  toggle      Toggle a segment on/off
  version     Print the version

Flags:
  -c, --config string   config (required)
  -h, --help            help for oh-my-posh
  -i, --init            init (deprecated)
  -s, --shell string    shell (deprecated)
      --version         version

Use "oh-my-posh [command] --help" for more information about a command.
```

## 参考文档

> https://ohmyposh.dev/docs/
