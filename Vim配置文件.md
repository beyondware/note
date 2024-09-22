## 用户配置文件

```sh
sudo vim ~/.vimrc
```

## 配置文件生效

```sh
source ~/.vimrc
```

### 显示行号

```sh
:set number 或者简化 :set nu
```

```sh
:set nonumber 或者简化 :set nonu
```

### 设置 hybird 主题

```sh
:colorscheme hybird
```

### 显示语法高亮

```sh
:syntax on
```

### 搜索高亮显示

```sh
:set hlsearch
```

### 输入关键字，一起高亮显示

```sh
:set incsearh
```

### 高亮显示匹配对应的括号

```sh
:set showmatch
```

### 自动保存

```sh
:set autowrite
```

### vim 与系统剪贴板之间来回复制粘贴

```sh
:set clipboard=unnamed
```

### 按 F2 进入粘贴模式（映射）

```sh
:set pastetoggle=<F2>
```

### 粘贴模式（防止粘贴时乱码）

```sh
:set paste
```

```sh
:set nopaste
```

### 自动缩进

```sh
:set autoindent
```

### 替换前，需确认

```sh
:set confirm
```

### 忽略大小写（默认区分大小写）

```sh
:set  ignorecase
```
