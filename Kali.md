### 换源

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

### 更新

```sh
sudo apt update
```

### 参考

> https://help.mirrors.cernet.edu.cn/kali/

> https://mirrors.ustc.edu.cn/help/kali.html

