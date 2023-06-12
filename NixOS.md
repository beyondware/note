# 下载 NixOS ISO

> https://channels.nixos.org/

- ISO 镜像源

> https://help.mirrors.cernet.edu.cn/nixos-images/

# 安装 NixOS（先修改镜像源）

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、添加

```sh
{ config, lib, pkgs, ... }:
{
  nix.settings.substituters = [ "https://mirror.sjtu.edu.cn/nix-channels/store" ];
  environment.systemPackages = [
    pkgs.vim
    pkgs.open-vm-tools
  ];
}
```

3、重建配置文件并切换（配置生效）

```sh
sudo nixos-rebuild switch
```

4、参考（推荐：上交大）

> https://mirrors.sjtug.sjtu.edu.cn/docs/nix-channels/store

> https://help.mirrors.cernet.edu.cn/nix-channels/

> https://mirrors.tuna.tsinghua.edu.cn/help/nix-channels/

> https://mirrors.ustc.edu.cn/help/nix-channels.html

> https://cache.nixos.org/

# 搜索市场

> https://search.nixos.org/packages

> https://search.nixos.org/options

> https://search.nixos.org/flakes

# Nix 配置

## 选项

### OpenSSH

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、添加

```sh
services.openssh.enable = true;
```

3、重建配置文件并切换（配置生效）

```sh
sudo nixos-rebuild switch
```

### Flatpak

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、添加

```sh
services.flatpak.enable = true;
```

3、重建配置文件并切换（配置生效）

```sh
sudo nixos-rebuild switch
```

4、添加 Flatpak存储库

```sh
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

## Nix 配置安装软件

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、添加

### 用户

```sh
users.users.用户名 = {
    isNormalUser = true;
    description = "用户名";
    extraGroups = [ "networkmanager" "wheel" ];
    packages = with pkgs; [
      包名1
      包名2
    ];
  };
```

### 系统

```sh
environment.systemPackages = with pkgs; [
包名1
包名2
];
```

3、重建配置文件并切换（配置生效）

```sh
sudo nixos-rebuild switch
```

## 更改主机名

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、修改

```sh
networking.hostName = "主机名";
```

3、重建配置文件并切换（配置生效）

```sh
sudo nixos-rebuild switch
```
