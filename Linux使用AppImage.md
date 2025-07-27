# 常见问题

1、报错信息

```sh
dlopen(): error loading libfuse.so.2

AppImages require FUSE to run. 
You might still be able to extract the contents of this AppImage 
if you run it with the --appimage-extract option. 
See https://github.com/AppImage/AppImageKit/wiki/FUSE 
for more information
```

解决方法

## Arch

```sh
sudo pacman -S fuse2
```

## Ubuntu

```sh
sudo apt install libfuse2
```
