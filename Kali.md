### ssh

```sh
sudo vim /etc/ssh/sshd_config
```

```sh
PermitRootLogin prohibit-password
```

改成

```sh
PermitRootLogin yes
```

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
deb https://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib
deb-src https://mirrors.ustc.edu.cn/kali kali-rolling main non-free contrib
```

### 更新

```sh
sudo apt update
```

### 参考

> https://mirrors.ustc.edu.cn/help/kali.html
