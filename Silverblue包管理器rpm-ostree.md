## 使用范围

> 适合用于Fedora Silverblue、Fedora Kinoite、Fedora CoreOS系统

## 镜像源

> https://mirrors.sjtug.sjtu.edu.cn/docs/fedora-ostree

## rpm-ostree --help

```sh
用法：
  rpm-ostree [选项…] COMMAND

Builtin Commands:
  compose          Commands to compose a tree
  apply-live       Apply pending deployment changes to booted deployment
  cleanup          Clear cached/pending data
  db               Commands to query the RPM database
  deploy           Deploy a specific commit
  rebase           Switch to a different tree
  rollback         Revert to the previously booted tree
  status           Get the version of the booted system
  upgrade          Perform a system upgrade
  reload           Reload configuration
  cancel           Cancel an active transaction
  initramfs        Enable or disable local initramfs regeneration
  install          Overlay additional packages
  uninstall        Remove overlayed additional packages
  override         Manage base package overrides
  reset            Remove all mutations
  refresh-md       Generate rpm repo metadata
  kargs            Query or modify kernel arguments
  initramfs-etc    Add files to the initramfs
  usroverlay       Apply a transient overlayfs to /usr

帮助选项：
  -h, --help       显示帮助选项

应用程序选项：
  --version        Print version information and exit
```
