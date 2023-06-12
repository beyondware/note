# 手册

> https://nix.dev/

> https://nixos.org/manual/nixos/stable/

> https://nixos.org/manual/nix/stable/

> https://nixos.org/manual/nix/stable/command-ref/nix-env.html

> https://nixos.org/manual/nixpkgs/stable/

> https://nixos.wiki/

> https://github.com/nix-community/wiki

# 常用命令

## 安装

```sh
nix-env -i 包名 或者 nix-env --install 包名
```

```sh
nix-env -iA nixos.包名（NixOS） 或者 nix-env -iA nixpkgs.包名（非NixOS）
```

## 删除

```sh
nix-env -e 包名 或者 nix-env --uninstall 包名
```

## 缓存

### 清理缓存

```sh
nix-collect-garbage
```

### 垃圾回收

```sh
nix-store --gc
```

### 删除旧 profile 版本

```sh
nix-env --delete-generations
```

## 更新

### 更新包

```sh
nix-env -u 包名
```

### 更新系统

```sh
nix-env -u
```

## 列出

### 列出所有版本

```sh
nix-env --list-generations
```

### 滚回上一个版本

```sh
nix-env --rollback
```

### 切换到某一个版本

```sh
nix-env --switch-generation 版本号
```

## 列出已安装的软件包

```sh
nix-env -q
```

## 搜索

### 搜索关键字（获取：包名）

```sh
nix-env -qaP --description 关键字
```

```sh
nix-env -qaP | grep 关键字
```

### 搜索

```sh
nix-env -qa 包名
```

### 搜索软件包

```sh
nix search nixpkgs 包名
```

## nix-channel

### 列出存储库

```sh
nix-channel --list
```

### 添加存储库

```sh
nix-channel --add URL
```

- 例如：

```sh
nix-channel --add https://nixos.org/channels/nixpkgs-unstable
```

```sh
nix-channel --update
```

### 删除存储库

```sh
nix-channel --remove 名称
```

### 更新存储库

```sh
nix-channel --update
```

- 升级所有

```sh
sudo nixos-rebuild switch --upgrade-all
```

### 回滚到上一版本

```sh
sudo nixos-rebuild --rollback
```

# nix --help

```sh
      | Warning 
      | This program is experimental and its interface is subject to change.

Name

    nix - a tool for reproducible and declarative configuration management

Synopsis

    nix [option...] subcommand

    where subcommand is one of the following:

    Main commands:

      · nix build - build a derivation or fetch a store path 
      · nix develop - run a bash shell that provides the build environment of a derivation 
      · nix flake - manage Nix flakes 
      · nix help - show help about nix or a particular subcommand 
      · nix profile - manage Nix profiles 
      · nix repl - start an interactive environment for evaluating Nix expressions 
      · nix run - run a Nix application 
      · nix search - search for packages 
      · nix shell - run a shell in which the specified packages are available 

    Infrequently used commands:

      · nix bundle - bundle an application so that it works outside of the Nix store 
      · nix copy - copy paths between Nix stores 
      · nix edit - open the Nix expression of a Nix package in $EDITOR 
      · nix eval - evaluate a Nix expression 
      · nix fmt - reformat your code in the standard style 
      · nix log - show the build log of the specified packages or paths, if available 
      · nix path-info - query information about store paths 
      · nix registry - manage the flake registry 
      · nix why-depends - show why a package has another package in its closure 

    Utility/scripting commands:

      · nix daemon - daemon to perform store operations on behalf of non-root clients 
      · nix describe-stores - show registered store types and their available options 
      · nix hash - compute and convert cryptographic hashes 
      · nix key - generate and convert Nix signing keys 
      · nix nar - create or inspect NAR files 
      · nix print-dev-env - print shell code that can be sourced by bash to reproduce the build environment of
        a derivation 
      · nix realisation - manipulate a Nix realisation 
      · nix show-config - show the Nix configuration 
      · nix show-derivation - show the contents of a store derivation 
      · nix store - manipulate a Nix store 

    Commands for upgrading or troubleshooting your Nix installation:

      · nix doctor - check your system for potential problems and print a PASS or FAIL for each check 
      · nix upgrade-nix - upgrade Nix to the stable version declared in Nixpkgs 

Examples

      · Create a new flake:
        
          | # nix flake new hello
          | # cd hello
    
      · Build the flake in the current directory:
        
          | # nix build
          | # ./result/bin/hello
          | Hello, world!
    
      · Run the flake in the current directory:
        
          | # nix run
          | Hello, world!
    
      · Start a development shell for hacking on this flake:
        
          | # nix develop
          | # unpackPhase
          | # cd hello-*
          | # configurePhase
          | # buildPhase
          | # ./hello
          | Hello, world!
          | # installPhase
          | # ../outputs/out/bin/hello
          | Hello, world!

Description

    Nix is a tool for building software, configurations and other artifacts in a reproducible and declarative
    way. For more information, see the Nix homepage or the Nix manual.

Installables

    Many nix subcommands operate on one or more installables. These are command line arguments that represent
    something that can be built in the Nix store. Here are the recognised types of installables:

      · Flake output attributes: nixpkgs#hello
        
        These have the form flakeref[#attrpath], where flakeref is a flake reference and attrpath is an
        optional attribute path. For more information on flakes, see the nix flake manual page. Flake
        references are most commonly a flake identifier in the flake registry (e.g. nixpkgs), or a raw path
        (e.g. /path/to/my-flake or . or ../foo), or a full URL (e.g. github:nixos/nixpkgs or path:.)
        
        When the flake reference is a raw path (a path without any URL scheme), it is interpreted as a path: or
        git+file: url in the following way:
        
          · If the path is within a Git repository, then the url will be of the form 
            git+file://[GIT_REPO_ROOT]?dir=[RELATIVE_FLAKE_DIR_PATH] where GIT_REPO_ROOT is the path to the
            root of the git repository, and RELATIVE_FLAKE_DIR_PATH is the path (relative to the directory
            root) of the closest parent of the given path that contains a flake.nix within the git repository.
            If no such directory exists, then Nix will error-out. 
        
        Note that the search will only include files indexed by git. In particular, files which are matched by 
        .gitignore or have never been git add-ed will not be available in the flake. If this is undesirable,
        specify path:<directory> explicitly;
        
        For example, if /foo/bar is a git repository with the following structure:  . └── baz ├──
        blah │  └── file.txt └── flake.nix 
        
        Then /foo/bar/baz/blah will resolve to git+file:///foo/bar?dir=baz
        
          · If the supplied path is not a git repository, then the url will have the form path:FLAKE_DIR_PATH
            where FLAKE_DIR_PATH is the closest parent of the supplied path that contains a flake.nix file
            (within the same file-system). If no such directory exists, then Nix will error-out. 
        
        For example, if /foo/bar/flake.nix exists, then /foo/bar/baz/ will resolve to path:/foo/bar
        
        If attrpath is omitted, Nix tries some default values; for most subcommands, the default is packages.syste>
        (e.g. packages.x86_64-linux.default), but some subcommands have other defaults. If attrpath is
        specified, attrpath is interpreted as relative to one or more prefixes; for most subcommands, these are
        packages.system, legacyPackages.*system* and the empty prefix. Thus, on x86_64-linux nix build
        nixpkgs#hello will try to build the attributes packages.x86_64-linux.hello, 
        legacyPackages.x86_64-linux.hello and hello.
    
      · Store paths: /nix/store/v5sv61sszx301i0x6xysaqzla09nksnd-hello-2.10
        
        These are paths inside the Nix store, or symlinks that resolve to a path in the Nix store.
    
      · Store derivations: /nix/store/p7gp6lxdg32h4ka1q398wd9r2zkbbz2v-hello-2.10.drv
        
        By default, if you pass a store derivation path to a nix subcommand, the command will operate on the 
        output paths of the derivation.
        
        For example, nix path-info prints information about the output paths:
        
          | # nix path-info --json /nix/store/p7gp6lxdg32h4ka1q398wd9r2zkbbz2v-hello-2.10.drv
          | [{"path":"/nix/store/v5sv61sszx301i0x6xysaqzla09nksnd-hello-2.10",…}]
        
        If you want to operate on the store derivation itself, pass the --derivation flag.
    
      · Nix attributes: --file /path/to/nixpkgs hello
        
        When the -f / --file path option is given, installables are interpreted as attribute paths referencing
        a value returned by evaluating the Nix file path.
    
      · Nix expressions: --expr '(import <nixpkgs> {}).hello.overrideDerivation (prev: { name = "my-hello"; })'.
        
        When the --expr option is given, all installables are interpreted as Nix expressions. You may need to
        specify --impure if the expression references impure inputs (such as <nixpkgs>).

    For most commands, if no installable is specified, the default is ., i.e. Nix will operate on the default
    flake output attribute of the flake in the current directory.

## Derivation output selection

    Derivations can have multiple outputs, each corresponding to a different store path. For instance, a
    package can have a bin output that contains programs, and a dev output that provides development artifacts
    like C/C++ header files. The outputs on which nix commands operate are determined as follows:

      · You can explicitly specify the desired outputs using the syntax installable^output1,...,outputN. For
        example, you can obtain the dev and static outputs of the glibc package:
        
          | # nix build 'nixpkgs#glibc^dev,static'
          | # ls ./result-dev/include/ ./result-static/lib/
          | …
        
        and likewise, using a store path to a "drv" file to specify the derivation:
        
          | # nix build '/nix/store/gzaflydcr6sb3567hap9q6srzx8ggdgg-glibc-2.33-78.drv^dev,static'
          | …
    
      · You can also specify that all outputs should be used using the syntax installable^*. For example, the
        following shows the size of all outputs of the glibc package in the binary cache:
        
          | # nix path-info -S --eval-store auto --store https://cache.nixos.org 'nixpkgs#glibc^*'
          | /nix/store/g02b1lpbddhymmcjb923kf0l7s9nww58-glibc-2.33-123                 33208200
          | /nix/store/851dp95qqiisjifi639r0zzg5l465ny4-glibc-2.33-123-bin             36142896
          | /nix/store/kdgs3q6r7xdff1p7a9hnjr43xw2404z7-glibc-2.33-123-debug          155787312
          | /nix/store/n4xa8h6pbmqmwnq0mmsz08l38abb06zc-glibc-2.33-123-static          42488328
          | /nix/store/q6580lr01jpcsqs4r5arlh4ki2c1m9rv-glibc-2.33-123-dev             44200560
        
        and likewise, using a store path to a "drv" file to specify the derivation:
        
          | # nix path-info -S '/nix/store/gzaflydcr6sb3567hap9q6srzx8ggdgg-glibc-2.33-78.drv^*'
          | …
    
      · If you didn't specify the desired outputs, but the derivation has an attribute meta.outputsToInstall,
        Nix will use those outputs. For example, since the package nixpkgs#libxml2 has this attribute:
        
          | # nix eval 'nixpkgs#libxml2.meta.outputsToInstall'
          | [ "bin" "man" ]
        
        a command like nix shell nixpkgs#libxml2 will provide only those two outputs by default.
        
        Note that a store derivation doesn't have any attributes like meta, and thus this case doesn't apply to
        it.
    
      · Otherwise, Nix will use all outputs of the derivation.

Nix stores

    Most nix subcommands operate on a Nix store.

    TODO: list store types, options

Options

    Logging-related options:

      · --debug
        
        Set the logging verbosity level to 'debug'.
    
      · --log-format format
        
        Set the format of log output; one of raw, internal-json, bar or bar-with-logs.
    
      · --print-build-logs / -L
        
        Print full build logs on standard error.
    
      · --quiet
        
        Decrease the logging verbosity level.
    
      · --verbose / -v
        
        Increase the logging verbosity level.

    Miscellaneous global options:

      · --help
        
        Show usage information.
    
      · --offline
        
        Disable substituters and consider all previously downloaded files up-to-date.
    
      · --option name value
        
        Set the Nix configuration setting name to value (overriding nix.conf).
    
      · --refresh
        
        Consider all previously downloaded files out-of-date.
    
      · --version
        
        Show version information.

    Options to override configuration settings:

      · --accept-flake-config
        
        Enable the accept-flake-config setting.
    
      · --access-tokens value
        
        Set the access-tokens setting.
    
      · --allow-dirty
        
        Enable the allow-dirty setting.
    
      · --allow-import-from-derivation
        
        Enable the allow-import-from-derivation setting.
    
      · --allow-new-privileges
        
        Enable the allow-new-privileges setting.
    
      · --allow-symlinked-store
        
        Enable the allow-symlinked-store setting.
    
      · --allow-unsafe-native-code-during-evaluation
        
        Enable the allow-unsafe-native-code-during-evaluation setting.
    
      · --allowed-impure-host-deps value
        
        Set the allowed-impure-host-deps setting.
    
      · --allowed-uris value
        
        Set the allowed-uris setting.
    
      · --allowed-users value
        
        Set the allowed-users setting.
    
      · --auto-allocate-uids
        
        Enable the auto-allocate-uids setting.
    
      · --auto-optimise-store
        
        Enable the auto-optimise-store setting.
    
      · --bash-prompt value
        
        Set the bash-prompt setting.
    
      · --bash-prompt-prefix value
        
        Set the bash-prompt-prefix setting.
    
      · --bash-prompt-suffix value
        
        Set the bash-prompt-suffix setting.
    
      · --build-hook value
        
        Set the build-hook setting.
    
      · --build-poll-interval value
        
        Set the build-poll-interval setting.
    
      · --build-users-group value
        
        Set the build-users-group setting.
    
      · --builders value
        
        Set the builders setting.
    
      · --builders-use-substitutes
        
        Enable the builders-use-substitutes setting.
    
      · --commit-lockfile-summary value
        
        Set the commit-lockfile-summary setting.
    
      · --compress-build-log
        
        Enable the compress-build-log setting.
    
      · --connect-timeout value
        
        Set the connect-timeout setting.
    
      · --cores value
        
        Set the cores setting.
    
      · --diff-hook value
        
        Set the diff-hook setting.
    
      · --download-attempts value
        
        Set the download-attempts setting.
    
      · --download-speed value
        
        Set the download-speed setting.
    
      · --eval-cache
        
        Enable the eval-cache setting.
    
      · --experimental-features value
        
        Set the experimental-features setting.
    
      · --extra-access-tokens value
        
        Append to the access-tokens setting.
    
      · --extra-allowed-impure-host-deps value
        
        Append to the allowed-impure-host-deps setting.
    
      · --extra-allowed-uris value
        
        Append to the allowed-uris setting.
    
      · --extra-allowed-users value
        
        Append to the allowed-users setting.
    
      · --extra-experimental-features value
        
        Append to the experimental-features setting.
    
      · --extra-extra-platforms value
        
        Append to the extra-platforms setting.
    
      · --extra-hashed-mirrors value
        
        Append to the hashed-mirrors setting.
    
      · --extra-ignored-acls value
        
        Append to the ignored-acls setting.
    
      · --extra-nix-path value
        
        Append to the nix-path setting.
    
      · --extra-platforms value
        
        Set the extra-platforms setting.
    
      · --extra-plugin-files value
        
        Append to the plugin-files setting.
    
      · --extra-sandbox-paths value
        
        Append to the sandbox-paths setting.
    
      · --extra-secret-key-files value
        
        Append to the secret-key-files setting.
    
      · --extra-substituters value
        
        Append to the substituters setting.
    
      · --extra-system-features value
        
        Append to the system-features setting.
    
      · --extra-trusted-public-keys value
        
        Append to the trusted-public-keys setting.
    
      · --extra-trusted-substituters value
        
        Append to the trusted-substituters setting.
    
      · --extra-trusted-users value
        
        Append to the trusted-users setting.
    
      · --fallback
        
        Enable the fallback setting.
    
      · --filter-syscalls
        
        Enable the filter-syscalls setting.
    
      · --flake-registry value
        
        Set the flake-registry setting.
    
      · --fsync-metadata
        
        Enable the fsync-metadata setting.
    
      · --gc-reserved-space value
        
        Set the gc-reserved-space setting.
    
      · --hashed-mirrors value
        
        Set the hashed-mirrors setting.
    
      · --http-connections value
        
        Set the http-connections setting.
    
      · --http2
        
        Enable the http2 setting.
    
      · --id-count value
        
        Set the id-count setting.
    
      · --ignore-try
        
        Enable the ignore-try setting.
    
      · --ignored-acls value
        
        Set the ignored-acls setting.
    
      · --impersonate-linux-26
        
        Enable the impersonate-linux-26 setting.
    
      · --keep-build-log
        
        Enable the keep-build-log setting.
    
      · --keep-derivations
        
        Enable the keep-derivations setting.
    
      · --keep-env-derivations
        
        Enable the keep-env-derivations setting.
    
      · --keep-failed
        
        Enable the keep-failed setting.
    
      · --keep-going
        
        Enable the keep-going setting.
    
      · --keep-outputs
        
        Enable the keep-outputs setting.
    
      · --log-lines value
        
        Set the log-lines setting.
    
      · --max-build-log-size value
        
        Set the max-build-log-size setting.
    
      · --max-free value
        
        Set the max-free setting.
    
      · --max-jobs value
        
        Set the max-jobs setting.
    
      · --max-silent-time value
        
        Set the max-silent-time setting.
    
      · --min-free value
        
        Set the min-free setting.
    
      · --min-free-check-interval value
        
        Set the min-free-check-interval setting.
    
      · --nar-buffer-size value
        
        Set the nar-buffer-size setting.
    
      · --narinfo-cache-negative-ttl value
        
        Set the narinfo-cache-negative-ttl setting.
    
      · --narinfo-cache-positive-ttl value
        
        Set the narinfo-cache-positive-ttl setting.
    
      · --netrc-file value
        
        Set the netrc-file setting.
    
      · --nix-path value
        
        Set the nix-path setting.
    
      · --no-accept-flake-config
        
        Disable the accept-flake-config setting.
    
      · --no-allow-dirty
        
        Disable the allow-dirty setting.
    
      · --no-allow-import-from-derivation
        
        Disable the allow-import-from-derivation setting.
    
      · --no-allow-new-privileges
        
        Disable the allow-new-privileges setting.
    
      · --no-allow-symlinked-store
        
        Disable the allow-symlinked-store setting.
    
      · --no-allow-unsafe-native-code-during-evaluation
        
        Disable the allow-unsafe-native-code-during-evaluation setting.
    
      · --no-auto-allocate-uids
        
        Disable the auto-allocate-uids setting.
    
      · --no-auto-optimise-store
        
        Disable the auto-optimise-store setting.
    
      · --no-builders-use-substitutes
        
        Disable the builders-use-substitutes setting.
    
      · --no-compress-build-log
        
        Disable the compress-build-log setting.
    
      · --no-eval-cache
        
        Disable the eval-cache setting.
    
      · --no-fallback
        
        Disable the fallback setting.
    
      · --no-filter-syscalls
        
        Disable the filter-syscalls setting.
    
      · --no-fsync-metadata
        
        Disable the fsync-metadata setting.
    
      · --no-http2
        
        Disable the http2 setting.
    
      · --no-ignore-try
        
        Disable the ignore-try setting.
    
      · --no-impersonate-linux-26
        
        Disable the impersonate-linux-26 setting.
    
      · --no-keep-build-log
        
        Disable the keep-build-log setting.
    
      · --no-keep-derivations
        
        Disable the keep-derivations setting.
    
      · --no-keep-env-derivations
        
        Disable the keep-env-derivations setting.
    
      · --no-keep-failed
        
        Disable the keep-failed setting.
    
      · --no-keep-going
        
        Disable the keep-going setting.
    
      · --no-keep-outputs
        
        Disable the keep-outputs setting.
    
      · --no-preallocate-contents
        
        Disable the preallocate-contents setting.
    
      · --no-print-missing
        
        Disable the print-missing setting.
    
      · --no-pure-eval
        
        Disable the pure-eval setting.
    
      · --no-require-sigs
        
        Disable the require-sigs setting.
    
      · --no-restrict-eval
        
        Disable the restrict-eval setting.
    
      · --no-run-diff-hook
        
        Disable the run-diff-hook setting.
    
      · --no-sandbox
        
        Disable sandboxing.
    
      · --no-sandbox-fallback
        
        Disable the sandbox-fallback setting.
    
      · --no-show-trace
        
        Disable the show-trace setting.
    
      · --no-substitute
        
        Disable the substitute setting.
    
      · --no-sync-before-registering
        
        Disable the sync-before-registering setting.
    
      · --no-trace-function-calls
        
        Disable the trace-function-calls setting.
    
      · --no-trace-verbose
        
        Disable the trace-verbose setting.
    
      · --no-use-case-hack
        
        Disable the use-case-hack setting.
    
      · --no-use-cgroups
        
        Disable the use-cgroups setting.
    
      · --no-use-registries
        
        Disable the use-registries setting.
    
      · --no-use-sqlite-wal
        
        Disable the use-sqlite-wal setting.
    
      · --no-warn-dirty
        
        Disable the warn-dirty setting.
    
      · --plugin-files value
        
        Set the plugin-files setting.
    
      · --post-build-hook value
        
        Set the post-build-hook setting.
    
      · --pre-build-hook value
        
        Set the pre-build-hook setting.
    
      · --preallocate-contents
        
        Enable the preallocate-contents setting.
    
      · --print-missing
        
        Enable the print-missing setting.
    
      · --pure-eval
        
        Enable the pure-eval setting.
    
      · --relaxed-sandbox
        
        Enable sandboxing, but allow builds to disable it.
    
      · --require-sigs
        
        Enable the require-sigs setting.
    
      · --restrict-eval
        
        Enable the restrict-eval setting.
    
      · --run-diff-hook
        
        Enable the run-diff-hook setting.
    
      · --sandbox
        
        Enable sandboxing.
    
      · --sandbox-build-dir value
        
        Set the sandbox-build-dir setting.
    
      · --sandbox-dev-shm-size value
        
        Set the sandbox-dev-shm-size setting.
    
      · --sandbox-fallback
        
        Enable the sandbox-fallback setting.
    
      · --sandbox-paths value
        
        Set the sandbox-paths setting.
    
      · --secret-key-files value
        
        Set the secret-key-files setting.
    
      · --show-trace
        
        Enable the show-trace setting.
    
      · --stalled-download-timeout value
        
        Set the stalled-download-timeout setting.
    
      · --start-id value
        
        Set the start-id setting.
    
      · --store value
        
        Set the store setting.
    
      · --substitute
        
        Enable the substitute setting.
    
      · --substituters value
        
        Set the substituters setting.
    
      · --sync-before-registering
        
        Enable the sync-before-registering setting.
    
      · --system value
        
        Set the system setting.
    
      · --system-features value
        
        Set the system-features setting.
    
      · --tarball-ttl value
        
        Set the tarball-ttl setting.
    
      · --timeout value
        
        Set the timeout setting.
    
      · --trace-function-calls
        
        Enable the trace-function-calls setting.
    
      · --trace-verbose
        
        Enable the trace-verbose setting.
    
      · --trusted-public-keys value
        
        Set the trusted-public-keys setting.
    
      · --trusted-substituters value
        
        Set the trusted-substituters setting.
    
      · --trusted-users value
        
        Set the trusted-users setting.
    
      · --use-case-hack
        
        Enable the use-case-hack setting.
    
      · --use-cgroups
        
        Enable the use-cgroups setting.
    
      · --use-registries
        
        Enable the use-registries setting.
    
      · --use-sqlite-wal
        
        Enable the use-sqlite-wal setting.
    
      · --user-agent-suffix value
        
        Set the user-agent-suffix setting.
    
      · --warn-dirty
        
        Enable the warn-dirty setting.
```
