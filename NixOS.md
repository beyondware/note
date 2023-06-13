# 下载 NixOS ISO

> https://channels.nixos.org/

- ISO 镜像源

> https://help.mirrors.cernet.edu.cn/nixos-images/

# 安装 NixOS

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、添加（修改镜像源）

```sh
{ config, lib, pkgs, ... }:
{
  nix.settings.substituters = [ "https://mirror.sjtu.edu.cn/nix-channels/store" ];
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

# Nix 配置文件

## 选项

### OpenSSH

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、添加

```sh
  # Enable the OpenSSH daemon.
  services.openssh.enable = true;
```

3、配置生效

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

3、配置生效

```sh
sudo nixos-rebuild switch
```

4、添加 Flatpak存储库

```sh
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

### 更改主机名

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、修改

```sh
  networking.hostName = "主机名"; # Define your hostname.
```

3、配置生效

```sh
sudo nixos-rebuild switch
```

### 更改时区

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、修改

```sh
  # Set your time zone.
  time.timeZone = "Asia/Shanghai";
```

3、配置生效

```sh
sudo nixos-rebuild switch
```

## 安装软件

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、添加

### 用户

```sh
  # Define a user account. Don't forget to set a password with ‘passwd’.
  users.users.pc = {
    isNormalUser = true;
    description = "pc";
    extraGroups = [ "networkmanager" "wheel" ];
    packages = with pkgs; [
      firefox
    #  thunderbird
    ];
  };
```

### 系统

```sh
  # List packages installed in system profile. To search, run:
  # $ nix search wget
  environment.systemPackages = with pkgs; [
  #  vim # Do not forget to add an editor to edit configuration.nix! The Nano editor is also installed by default.
  #  wget
    open-vm-tools
  ];
```

3、配置生效

```sh
sudo nixos-rebuild switch
```

## home-manager

### 添加 nix-channel

```sh
sudo nix-channel --add https://ghproxy.com/https://github.com/nix-community/home-manager/archive/master.tar.gz home-manager
```

```sh
sudo nix-channel --update
```

### 编辑 configuration.nix

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、添加 home-manager/nixos

```sh
  imports =
    [ # Include the results of the hardware scan.
      ./hardware-configuration.nix
      <home-manager/nixos>
    ];
```

3、文尾继续添加（必须添加 home.stateVersion，否则报错）

```sh
  home-manager.users.用户名 = { pkgs, ... }: {
  home.stateVersion = "23.05";  
  home.packages = with pkgs; [htop];
  programs.bash.enable = true;
  };
```

4、更新配置

```sh
sudo nixos-rebuild switch
```

