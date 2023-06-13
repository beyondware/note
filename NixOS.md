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

# NixOS options

## 更改主机名

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

## 网络

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、修改

```sh
  # Enable networking
  networking.networkmanager.enable = true;
```

3、配置生效

```sh
sudo nixos-rebuild switch
```

## 时区

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

## 中文设置

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、修改

```sh
  # Select internationalisation properties.
  i18n.defaultLocale = "zh_CN.UTF-8";

  i18n.extraLocaleSettings = {
    LC_ADDRESS = "zh_CN.UTF-8";
    LC_IDENTIFICATION = "zh_CN.UTF-8";
    LC_MEASUREMENT = "zh_CN.UTF-8";
    LC_MONETARY = "zh_CN.UTF-8";
    LC_NAME = "zh_CN.UTF-8";
    LC_NUMERIC = "zh_CN.UTF-8";
    LC_PAPER = "zh_CN.UTF-8";
    LC_TELEPHONE = "zh_CN.UTF-8";
    LC_TIME = "zh_CN.UTF-8";
  };
```

3、配置生效

```sh
sudo nixos-rebuild switch
```

## 启用 OpenSSH

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

## Flatpak

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

4、添加 Flatpak 存储库

```sh
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

## 减少交换

1、检查系统的默认交换值

```sh
cat /proc/sys/vm/swappiness
```

2、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

3、添加（建议降低到 10）

```sh
boot.kernel.sysctl = { "vm.swappiness" = 10;};
```

4、配置生效

```sh
sudo nixos-rebuild switch
```

5、再次检查系统的交换值（确认更改成功）

```sh
cat /proc/sys/vm/swappiness
```

## 垃圾回收

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、添加

```sh
# Automatic Garbage Collection
nix.gc = {
                automatic = true;
                dates = "weekly";
                options = "--delete-older-than 7d";
        };
```

3、配置生效

```sh
sudo nixos-rebuild switch
```

4、列出活动计时器（nix-gc.timer，下一次清理的时间）

```sh
systemctl list-timers
```

## 自动更新

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、添加

```sh
# Auto system update
system.autoUpgrade = {
      enable = true;
};
```

3、配置生效

```sh
sudo nixos-rebuild switch
```

4、列出活动计时器（nixos-upgrade.timer，下一次升级的时间）

```sh
systemctl list-timers
```

# Nix packages

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、添加

## 用户

```sh
  # Define a user account. Don't forget to set a password with ‘passwd’.
  users.users.用户名 = {
    isNormalUser = true;
    description = "用户名";
    extraGroups = [ "networkmanager" "wheel" ];
    packages = with pkgs; [
      firefox
    #  thunderbird
    ];
  };
```

## 系统

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

# home-manager

> https://nix-community.github.io/home-manager/

> https://github.com/nix-community/home-manager

## 系统

1、添加 nix-channel

```sh
sudo nix-channel --add https://ghproxy.com/https://github.com/nix-community/home-manager/archive/master.tar.gz home-manager
```

```sh
sudo nix-channel --update
```

2、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

3、添加 home-manager/nixos

```sh
  imports =
    [ # Include the results of the hardware scan.
      ./hardware-configuration.nix
      <home-manager/nixos>
    ];
```

4、文尾继续添加（必须添加 home.stateVersion，否则报错）

```sh
  home-manager.users.用户名 = { pkgs, ... }: {
  home.stateVersion = "23.05";  
  home.packages = with pkgs; [htop];
  programs.bash.enable = true;
  };
```

5、配置更新

```sh
sudo nixos-rebuild switch
```

## 用户

1、添加 nix-channel

```sh
nix-channel --add https://ghproxy.com/https://github.com/nix-community/home-manager/archive/master.tar.gz home-manager
```

```sh
nix-channel --update
```

2、安装 home-manager（报错，重启系统再试）

```sh
nix-shell '<home-manager>' -A install
```

3、编辑

```sh
vim /home/$USER/.config/nixpkgs/home.nix
```

4、添加

```sh
home.packages = with pkgs; [htop];
```

5、配置更新

```sh
home-manager switch
```

# 输入法

## ibus（推荐）

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、添加

```sh
  i18n.inputMethod = {
    enabled = "ibus";
    ibus.engines = with pkgs.ibus-engines; [libpinyin];
  };
```

3、配置更新

```sh
sudo nixos-rebuild switch
```

- 首次使用，需要执行

```sh
ibus-setup
```

## fcitx5

1、编辑

```sh
sudo vim /etc/nixos/configuration.nix
```

2、添加

```sh
i18n.inputMethod = {
  enabled = "fcitx5";
  fcitx5.addons = with pkgs; [fcitx5-chinese-addons fcitx5-configtool fcitx5-gtk];
};
```

3、配置更新

```sh
sudo nixos-rebuild switch
```
