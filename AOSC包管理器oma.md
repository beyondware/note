oma --help

```sh
User-friendly and performant package manager for APT repositories

Usage: oma [OPTIONS] [COMMAND]

Commands:
  install     Install package(s) from the repository [aliases: add]
  upgrade     Upgrade packages installed on the system [aliases: full-upgrade]
  download    Download package(s) from the repository
  remove      Remove the specified package(s) [aliases: del, rm, autoremove]
  refresh     Refresh repository metadata/catalog
  show        Show information on the specified package(s) [aliases: info]
  search      Search for package(s) available from the repository
  files       List files in the specified package
  provides    Search for package(s) that provide(s) certain patterns in a path
  fix-broken  Resolve broken dependencies in the system
  pick        Install specific version of a package
  mark        Mark status for one or multiple package(s)
  list        List package(s) available from the repository
  depends     Lists dependencies of one or multiple packages [aliases: dep]
  rdepends    List reverse dependency(ies) for the specified package(s)
              [aliases: rdep]
  clean       Clear downloaded package cache
  history     Show a history/log of package changes in the system [aliases: log]
  undo        Undo system changes operation
  tui         Oma tui interface
  version     Print version
  topics      Manage testing topics enrollment [aliases: topic]
  mirror      Manage Mirrors enrollment [aliases: mirrors]
  help        Print this message or the help of the given subcommand(s)

Options:
      --dry-run
          Run oma in "dry-run" mode [env: OMA_DRY_RUN=]
      --debug
          Run oma with debug output [env: OMA_DEBUG=]
      --color <COLOR>
          Represents the color preferences for program output [default: auto]
          [possible values: auto, always, never]
      --follow-terminal-color
          Output result with terminal theme color [env:
          OMA_FOLLOW_TERMINAL_COLOR=]
      --no-progress
          Do not display progress bar [env: OMA_NO_PROGRESS=]
      --no-check-dbus
          Run oma do not check dbus [env: OMA_NO_CHECK_DBUS=]
  -v, --version
          Print version
      --sysroot <SYSROOT>
          Set sysroot target directory [env: OMA_SYSROOT=] [default: /]
      --apt-options <APT_OPTIONS>
          Set apt options
      --no-bell
          Don't ring if oma completes the transaction [env: OMA_NO_BELL=]
  -h, --help
          Print help (see more with '--help')

本 oma 具有超级小熊猫力！
```
