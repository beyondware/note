## 安装依赖

### Fedora

```sh
sudo dnf install -y gcc zlib zlib-devel pcre pcre-devel
```

### Debian

```sh
sudo apt install build-essential libpcre3-dev libssl-dev zlib1g-dev libgd-dev
```

## 下载源码

> https://nginx.org/

1、下载 nginx Stable（稳定版）

```sh
wget https://nginx.org/download/nginx-1.22.0.tar.gz
```

2、解压软件包

```sh
tar -zxvf nginx-1.22.0.tar.gz
```

3、进入包目录

```sh
cd nginx-1.22.0
```

## 配置 nginx 选项

```sh
./configure --prefix=/var/www/html --sbin-path=/usr/sbin/nginx --conf-path=/etc/nginx/nginx.conf --http-log-path=/var/log/nginx/access.log --error-log-path=/var/log/nginx/error.log --with-pcre  --lock-path=/var/lock/nginx.lock --pid-path=/var/run/nginx.pid --with-http_ssl_module --with-http_image_filter_module=dynamic --modules-path=/etc/nginx/modules --with-http_v2_module --with-http_v3_module --with-stream=dynamic --with-http_addition_module --with-http_mp4_module
```

## 编译

```sh
make
```

## 安装

```sh
make install
```

## 创建 nginx 系统服务

1、创建 systemd 服务文件

```sh
sudo vim /etc/systemd/system/nginx.service
```

- 将以下内容添加到文件中

```sh
[Unit]
Description=The NGINX HTTP and reverse proxy server
After=syslog.target network-online.target remote-fs.target nss-lookup.target
Wants=network-online.target

[Service]
Type=forking
PIDFile=/var/run/nginx.pid
ExecStartPre=/usr/sbin/nginx -t
ExecStart=/usr/sbin/nginx
ExecReload=/usr/sbin/nginx -s reload
ExecStop=/bin/kill -s QUIT $MAINPID
PrivateTmp=true

[Install]
WantedBy=multi-user.target
```

2、重新加载 systemd 守护进程

```sh
sudo systemctl daemon-reload
```

3、启动 nginx 服务

```sh
sudo systemctl start nginx
```

4、立即启动

```sh
sudo systemctl enable nginx --now
```

5、自启动 nginx 服务

```sh
sudo systemctl enable nginx
```

6、重启 nginx 服务

```sh
sudo systemctl restart nginx
```

7、查看 nginx 状态

```sh
systemctl status nginx
```

8、验证 nginx 是否正常运行

```sh
http://localhost
```

9、显示网络状态

```sh
netstat -ntplu | grep nginx
```

## 防火墙

1、关闭防火墙

- 无法访问 nginx，需关闭防火墙

```sh
systemctl stop firewalld.service
```

2、禁止防火墙开机启动

```sh
systemctl disable firewalld.service
```

3、重启防火墙

```sh
firewall-cmd --reload
```

4、放行端口

```sh
firewall-cmd --zone=public -- add-port=80/tcp --permanent
```
