## Watt Toolkit

> https://steampp.net/

> https://github.com/BeyondDimension/SteamTools

导入证书 SteamTools.Certificate.cer

> /home/$USER/.local/share/Steam++

Microsoft Edge：设置-隐私、搜索和服务-安全性-管理证书-颁发机构

## FastGithub

> https://github.com/dotnetcore/FastGithub

### 生成证书

- 切换到 fastgithub 目录

```sh
sudo ./fastgithub
```

- 自动向系统安装CA证书cacert/fastgithub.crt

### 网络代理

```sh
export http_proxy=http://127.0.0.1:38457
```

### 查看状态

```sh
systemctl list-unit-files
```

- fastgithub.service 显示 enabled（启用）表示成功

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
sudo vim /lib/systemd/system/fastgithub.service
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
