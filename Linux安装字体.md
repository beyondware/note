# 系统字体安装位置

```sh
/usr/share/fonts
```

# 用户字体安装位置

```sh
~/.local/share/fonts
```

# 安装字体

1、在/usr/share/fonts/目录下建立子目录，例如：wqy

```sh
sudo mkdir /usr/share/fonts/wqy
```

2、切换到下载字体目录下

```sh
cd Downloads/
```

3、将字体文件复制到刚才创建的目录下（/usr/share/fonts/wqy）

```sh
sudo cp wqy-zenhei.ttf /usr/share/fonts/wqy
```

4、切换到复制的字体目录

```sh
cd /usr/share/fonts/wqy
```

5、建立字体索引信息（可选）

```sh
sudo mkfontscale   //生成fonts.scale
sudo mkfontdir    //生成fonts.dir
```

# 更新字体缓存

```sh
fc-cache -fv
```

# 验证安装的字体

```sh
fc-list | grep wqy-zenhei
```

```sh
fc-list | grep "WenQuanYi Micro Hei"
```
