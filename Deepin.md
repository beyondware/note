## Deepin 换源

1、编辑

```sh
sudo vim /etc/apt/sources.list
```

- 文件最前面添加以下内容

```sh
deb [by-hash=force] https://mirrors.nju.edu.cn/deepin/ apricot main contrib non-free
```

2、更新

```sh
sudo apt update
```

3、参考源

> https://developer.aliyun.com/mirror/deepin

## Kali 换源

1、修改

```sh
sudo vim /etc/apt/sources.list
```

```sh
deb http://http.kali.org/kali kali-rolling main contrib non-free
deb-src http://http.kali.org/kali kali-rolling main contrib non-free
```

改成

```sh
deb https://mirrors.cernet.edu.cn/kali kali-rolling main non-free contrib
deb-src https://mirrors.cernet.edu.cn/kali kali-rolling main non-free contrib
```

2、更新

```sh
sudo apt update
```

3、参考

> https://help.mirrors.cernet.edu.cn/kali/

> https://mirrors.ustc.edu.cn/help/kali.html
