## 环境变量

### 系统环境变量（root 权限）

- 不推荐

```sh
vi /etc/profile
```

重新加载

```sh
source /etc/profile
```

- 推荐

```sh
vi /etc/profile.d
```

### 用户环境变量

- 推荐

```sh
vi ~/.bash_profile
```

- 不推荐

```sh
vi ~/.bashrc
```

## PATH 环境变量

- 查看所有环境变量

```sh
echo $PATH
```

```sh
export PATH="$PATH:路径1:路径2"
```

- 验证

```sh
echo $?
```

1、上一步，执行正确
返回值：0

2、上一步，执行错误
返回值：非 0

### JAVA 环境变量配置

```sh
export JAVA_HOME=JAVA安装路径
export PATH=$JAVA_HOME/bin:$PATH
```

### 执行优先级

> /etc/profile -> /etc/profile.d -> /etc/bashrc -> ~/.bash_profile -> ~/.bashrc
