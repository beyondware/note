## 优化工具

```sh
sudo dnf install gnome-tweaks
```

## 显示 Dock 栏

> https://extensions.gnome.org/

由于 GNOME 42 目前暂不支持，用命令安装，需要重启系统-打开才能生效。

> https://extensions.gnome.org/extension/307/dash-to-dock/

```sh
sudo dnf install gnome-shell-extension-dash-to-dock.noarch
```

## 特效扩展

- 扩展安装位置

```sh
cd ~/.local/share/gnome-shell/extensions
```

1、Compiz windows effect：晃动效果

> https://extensions.gnome.org/extension/3210/compiz-windows-effect/

2、Compiz alike magic lamp effect：魔术灯效果

> https://extensions.gnome.org/extension/3740/compiz-alike-magic-lamp-effect/

3、Coverflow Alt-Tab：组合键“Alt+Tab”切换效果

> https://extensions.gnome.org/extension/97/coverflow-alt-tab/

## 主题

> https://github.com/vinceliuice/WhiteSur-gtk-theme

```sh
git clone https://ghproxy.com/https://github.com/vinceliuice/WhiteSur-gtk-theme.git
```

```sh
cd WhiteSur-gtk-theme/
```

```sh
./install.sh
```

- 主题默认位置

```sh
cd ~/.themes
```

## 图标

> https://github.com/vinceliuice/WhiteSur-icon-theme

```sh
git clone https://ghproxy.com/https://github.com/vinceliuice/WhiteSur-icon-theme.git
```

```sh
cd WhiteSur-icon-theme/
```

```sh
./install.sh
```

- 图标默认位置

```sh
cd ~/.local/share/icons
```

## 光标

> https://github.com/vinceliuice/WhiteSur-cursors

```sh
git clone https://ghproxy.com/https://github.com/vinceliuice/WhiteSur-cursors.git
```

```sh
cd WhiteSur-cursors/
```

```sh
./install.sh
```

- 光标默认位置

```sh
 cd ~/.local/share/icons
```

## 壁纸

> https://github.com/vinceliuice/WhiteSur-wallpapers

```sh
git clone https://ghproxy.com/https://github.com/vinceliuice/WhiteSur-wallpapers.git
```

```sh
cd WhiteSur-wallpapers/
```

- 注意：需要权限

```sh
sudo ./install-gnome-backgrounds.sh
```

- 壁纸默认位置

```sh
cd /usr/share/backgrounds
```
