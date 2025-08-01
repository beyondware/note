# shell

## 查看当前 shell

```sh
echo $0
或者
ps -p $$
```

## 列出已安装 shell

```sh
cat /etc/shells
```

## 设置 zsh 为默认 shell

```sh
sudo chsh -s /bin/zsh
```

退出终端，重开才能生效。

# zsh

## 安装 zsh

所需依赖

```sh
sudo dnf install git wget
```

```sh
sudo dnf install zsh
```

## 配置文件

### 全局配置

```sh
sudo vim /etc/zsh/zprofile
```

### 用户配置

```sh
sudo vim ~/.zshrc
```

## 安装 oh-my-zsh

```sh
sh -c "$(wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```

### powerlevel10k（主题）

- 安装位置

```sh
cd ~/.oh-my-zsh/custom/themes/
```

1、安装 powerlevel10k 主题

```sh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

2、编辑

```sh
vim ~/.zshrc
```

3、修改 ZSH_THEME

```sh
ZSH_THEME="powerlevel10k/powerlevel10k"
```

4、配置 powerlevel10k

```sh
p10k configure
```

5、执行生效

```sh
source ~/.zshrc
```

### zsh-autosuggestions（自动补全）

- 安装位置

```sh
cd ~/.oh-my-zsh/custom/plugins/
```

1、安装 zsh-autosuggestions

```sh
git clone https://github.com/zsh-users/zsh-autosuggestions.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

2、编辑

```sh
vim ~/.zshrc
```

3、添加

```sh
plugins 添加 zsh-autosuggestions
```

4、执行生效

```sh
source ~/.zshrc
```

5、如果高亮不明显，修改为 10

```sh
 ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE=’fg=10’
```

### zsh-syntax-highlighting（显示高亮）

- 安装位置

```sh
cd ~/.oh-my-zsh/custom/plugins/
```

1、安装 zsh-syntax-highlighting

```sh
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

2、编辑

```sh
vim ~/.zshrc
```

3、添加

```sh
plugins 添加 zsh-syntax-highlighting
```

4、执行生效

```sh
source ~/.zshrc
```

### 显示结果

```sh
plugins=(
git
sudo
zsh-autosuggestions
zsh-syntax-highlighting
)
```

### incr（自动补全、可选）

1、新建

```sh
mkdir ~/.oh-my-zsh/plugins/incr
```

2、安装

```sh
wget http://mimosa-pudica.net/src/incr-0.2.zsh
```

3、移动到

```sh
mv incr-0.2.zsh ~/.oh-my-zsh/plugins/incr
```

4、写入到 zsh

```sh
echo 'source ~/.oh-my-zsh/plugins/incr/incr\*.zsh' >> ~/.zshrc
```

5、执行生效

```sh
source ~/.zshrc
```
