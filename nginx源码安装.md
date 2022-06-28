## 安装依赖

```sh
sudo dnf install -y gcc zlib zlib-devel pcre pcre-devel
```

## 安装 nginx

### nginx 官网

> https://nginx.org/

### 下载 nginx Stable（稳定版）

```sh
wget https://nginx.org/download/nginx-1.22.0.tar.gz
```

### 解压

```sh
tar -zxvf nginx-1.22.0.tar.gz
```

### 进入包目录

```sh
cd nginx-1.22.0
```

### configure 生成 Makefile 文件

```sh
./configure --prefix=/usr/local/nginx
```

### 编译

```sh
make
```

### 安装

```sh
make install
```

## 使用 nginx

### 进入 nginx 安装路径

```sh
cd /usr/local/nginx/sbin
```

### 启动 nginx

```sh
./nginx
```

### 查看 nginx 是否异常

```sh
./nginx -t
```

### 停止 nginx

```sh
./nginx -s stop
```

### 执行完，再停止 nginx

```sh
./nginx -s quit
```

### 重新加载 nginx

```sh
./nginx -s reload
```

### 查看 nginx 进程

```sh
ps -ef | grep nginx
```

### 显示网络状态

```sh
netstat -ntplu | grep nginx
```

## 防火墙

### 关闭防火墙

- 无法访问 nginx，需要关闭防火墙

```sh
systemctl stop firewalld.service
```

### 禁止防火墙开机启动

```sh
systemctl disable firewalld.service
```

### 重启防火墙

```sh
firewall-cmd --reload
```

### 放行端口

```sh
firewall-cmd --zone=public -- add-port=80/tcp --permanent
```
