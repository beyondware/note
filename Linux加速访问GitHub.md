### fastgithub

> https://github.com/dotnetcore/FastGithub

### 首次运行

- 切换到 fastgithub 目录

```sh
sudo ./fastgithub
```

- 自动生成证书文件 cacert/fastgithub.cer

### 网络设置

- 设置-网络-网络代理-自动-配置 URL

```sh
http://127.0.0.1:38457/
```

或者

```sh
export http_proxy=http://127.0.0.1:38457 或者 export https_proxy=https://127.0.0.1:38457
```

### 启动

```sh
sudo ./fastgithub start
```

### 停止

```sh
sudo ./fastgithub stop
```

### 重启

```sh
sudo ./fastgithub restart
```

### 开机启动

```sh
vim /lib/systemd/system/fastgithub.service
```

- 粘贴以下内容

```sh
[Unit]
Description=fastgithub
After=network.target
[Service]
Type=forking
User=fastgithub
Group=fastgithub
ExecStart=/fastgithub_linux-x64/fastgithub start
ExecReload=/fastgithub_linux-x64/fastgithub restart
ExecStop=/fastgithub_linux-x64/fastgithub stop
PrivateTmp=true
[Install]
WantedBy=multi-user.target
```

### 启用 fastgithub 服务

```sh
systemctl enable fastgithub.service
```

### 重启系统

```sh
reboot
```

### 查看服务状态

```sh
systemctl list-unit-files
```

- fastgithub.service 显示 enabled（启用）表示成功

### 手动启动

```sh
systemctl start fastgithub
```
