## Python 自定义安装

1、选择“Customize installation”（自定义安装）

2、一定要勾选“Add Python to PATH”（添加到环境变量)

3、高级选项：勾选“Install for users”（所有人可用）

> 显示“Setup was successful”（表示安装成功）

### 验证结果

```sh
python --version
```

```sh
pip --version
```

## 解决 Python 没有安装 pip 的问题

```sh
Failed to find python3-pip;21.3.1-2.fc36;noarch;fedora
```

> 一般 Linux 自带 python，但是没有安装 pip 报错。

- 解决方法

```sh
python -m ensurepip --upgrade
```

```sh
python -m pip install --upgrade pip
```

## PyCharm

> https://www.jetbrains.com/pycharm/

## pip 换镜像源

```sh
python -m pip install -i https://mirrors.cernet.edu.cn/pypi/web/simple --upgrade pip
```

```sh
pip config set global.index-url https://mirrors.cernet.edu.cn/pypi/web/simple
```

### 配置多个镜像源

```sh
pip config set global.extra-index-url "https://mirrors.cernet.edu.cn/pypi/web/simple https://mirror.nju.edu.cn/pypi/web/simple"
```

### 查看当前源

```sh
cat ~/.config/pip/pip.conf
```

### 参考

> https://help.mirrors.cernet.edu.cn/pypi/

> https://mirror.nju.edu.cn/help/pypi

## pip 升级

### 升级指定程序包

```sh
pip install --upgrade 包名
```

### 升级所有软件包

```sh
pip install --upgrade $(pip freeze | awk -F= '{print $1}')
```

## pip --help

```sh
Usage:
  pip <command> [options]

Commands:
  install                     Install packages.
  download                    Download packages.
  uninstall                   Uninstall packages.
  freeze                      Output installed packages in requirements format.
  list                        List installed packages.
  show                        Show information about installed packages.
  check                       Verify installed packages have compatible dependencies.
  config                      Manage local and global configuration.
  search                      Search PyPI for packages.
  cache                       Inspect and manage pip's wheel cache.
  index                       Inspect information available from package indexes.
  wheel                       Build wheels from your requirements.
  hash                        Compute hashes of package archives.
  completion                  A helper command used for command completion.
  debug                       Show information useful for debugging.
  help                        Show help for commands.

General Options:
  -h, --help                  Show help.
  --debug                     Let unhandled exceptions propagate outside the main subroutine, instead of logging them
                              to stderr.
  --isolated                  Run pip in an isolated mode, ignoring environment variables and user configuration.
  --require-virtualenv        Allow pip to only run in a virtual environment; exit with an error otherwise.
  -v, --verbose               Give more output. Option is additive, and can be used up to 3 times.
  -V, --version               Show version and exit.
  -q, --quiet                 Give less output. Option is additive, and can be used up to 3 times (corresponding to
                              WARNING, ERROR, and CRITICAL logging levels).
  --log <path>                Path to a verbose appending log.
  --no-input                  Disable prompting for input.
  --proxy <proxy>             Specify a proxy in the form [user:passwd@]proxy.server:port.
  --retries <retries>         Maximum number of retries each connection should attempt (default 5 times).
  --timeout <sec>             Set the socket timeout (default 15 seconds).
  --exists-action <action>    Default action when a path already exists: (s)witch, (i)gnore, (w)ipe, (b)ackup,
                              (a)bort.
  --trusted-host <hostname>   Mark this host or host:port pair as trusted, even though it does not have valid or any
                              HTTPS.
  --cert <path>               Path to PEM-encoded CA certificate bundle. If provided, overrides the default. See 'SSL
                              Certificate Verification' in pip documentation for more information.
  --client-cert <path>        Path to SSL client certificate, a single file containing the private key and the
                              certificate in PEM format.
  --cache-dir <dir>           Store the cache data in <dir>.
  --no-cache-dir              Disable the cache.
  --disable-pip-version-check
                              Don't periodically check PyPI to determine whether a new version of pip is available for
                              download. Implied with --no-index.
  --no-color                  Suppress colored output.
  --no-python-version-warning
                              Silence deprecation warnings for upcoming unsupported Pythons.
  --use-feature <feature>     Enable new functionality, that may be backward incompatible.
  --use-deprecated <feature>  Enable deprecated functionality, that will be removed in the future.
```
