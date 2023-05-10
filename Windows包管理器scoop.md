## 安装 scoop

```sh
Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://ghproxy.com/https://raw.githubusercontent.com/scoopinstaller/install/master/install.ps1')
```

> Scoop was installed successfully! //表示安装成功

- 验证结果

```sh
scoop --version
```

## 卸载 scoop

```sh
scoop uninstall scoop //警告：包括scoop在内所有软件全部删除
```

> Scoop has been uninstalled. //表示卸载成功

## 升级 scoop

```sh
scoop update
```

## 添加源

```sh
scoop bucket add '源名'
```

## scoop --help

```sh
Usage: scoop <command> [<args>]

Available commands are listed below.

Type 'scoop help <command>' to get more help for a specific command.

Command    Summary
-------    -------
alias      Manage scoop aliases
bucket     Manage Scoop buckets
cache      Show or clear the download cache
cat        Show content of specified manifest.
checkup    Check for potential problems
cleanup    Cleanup apps by removing old versions
config     Get or set configuration values
create     Create a custom app manifest
depends    List dependencies for an app, in the order they'll be installed
download   Download apps in the cache folder and verify hashes
export     Exports installed apps, buckets (and optionally configs) in JSON format
help       Show help for a command
hold       Hold an app to disable updates
home       Opens the app homepage
import     Imports apps, buckets and configs from a Scoopfile in JSON format
info       Display information about an app
install    Install apps
list       List installed apps
prefix     Returns the path to the specified app
reset      Reset an app to resolve conflicts
search     Search available apps
shim       Manipulate Scoop shims
status     Show status and check for new app versions
unhold     Unhold an app to enable updates
uninstall  Uninstall an app
update     Update apps, or Scoop itself
virustotal Look for app's hash or url on virustotal.com
which      Locate a shim/executable (similar to 'which' on Linux)
```
