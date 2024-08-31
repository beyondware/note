# pacman-mirrors

> https://wiki.manjaro.org/index.php/Pacman-mirrors

1、查看状态

```sh
pacman-mirrors --status
```

2、配置国内源

```sh
sudo pacman-mirrors -i -c China -m rank
```

3、更新数据

```sh
sudo pacman -Syyu
```
