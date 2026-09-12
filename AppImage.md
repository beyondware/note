1、提权，运行

```sj
chmod +x ./包名.AppImage
```

2、运行失败

```sh
APPIMAGE_EXTRACT_AND_RUN=1 ./包名.AppImage
```

# 更新 AppImage

> https://github.com/AppImageCommunity/AppImageUpdate

```sh
appimageupdatetool 包名.AppImage
```

# 常见问题

```sh
dlopen(): error loading libfuse.so.2

AppImages require FUSE to run. 
You might still be able to extract the contents of this AppImage 
if you run it with the --appimage-extract option. 
See https://github.com/AppImage/AppImageKit/wiki/FUSE 
for more information
```

# FUSE

AppImage 依赖 FUSE（Filesystem in Userspace） 技术将自身挂载为临时文件系统运行

> https://github.com/libfuse/libfuse

## 检查 FUSE 是否安装

```sh
fusermount -V
```

## 安装

### Arch

```sh
sudo pacman -S fuse2
```

### Ubuntu

```sh
sudo apt install libfuse2
```

## 若已安装，尝试手动加载模块

```sh
sudo modprobe fuse
```
