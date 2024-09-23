## 查看所有设置

```sh
:h option-list
```

## 用户配置文件

```sh
sudo vim ~/.vimrc
```

## 配置文件生效

```sh
source ~/.vimrc
```

## 正常

### 不兼容 vi 模式

```sh
set nocompatible
```

### 显示行号

```sh
set number 或者简化 set nu
```

### 隐藏行号

```sh
set nonumber 或者简化 set nonu
```

### 暗黑模式

```sh
set background=dark
```

### 搜索高亮显示

```sh
set hlsearch
```

### 高亮显示匹配对应的括号

```sh
set showmatch
```

### 自动保存

```sh
set autowrite
```

### vim 与系统剪贴板之间来回复制粘贴

```sh
set clipboard=unnamed
```

### 粘贴模式（防止粘贴时乱码）

```sh
set paste
```

### 退出粘贴模式

```sh
set nopaste
```

### 智能对齐

```sh
set smartindent
```

### 自动缩进

```sh
set autoindent
```

### 自动折行

```sh
set wrap
```

### 取消自动折行

```sh
set nowrap
```

### 替换前，需确认

```sh
set confirm
```

### 忽略大小写（默认区分：大小写）

```sh
set ignorecase
```

### Tab键的宽度

```sh
set tabstop=4
```

### 统一缩进为4

```sh
set softtabstop=4
set shiftwidth=4
```

### 历史纪录数（50次）

```sh
set history=50
```

### 关掉错误警报

```sh
set noerrorbells
```

### 文件监视

```sh
set autoread
```

### 底线模式，按 Tab 自动补全

```sh
set wildmenu
set wildmode=longest:list,full
```

## 报错

### 设置 hybird 主题

```sh
colorscheme hybird
```

### 显示语法高亮

```sh
syntax on
```

### 输入关键字，一起高亮显示

```sh
set incsearh
```

### 按 F2 进入粘贴模式（映射）

```sh
set pastetoggle=<F2>
```

### 文件类型检查

```sh
filetype on                     " 开启文件类型检测
filetype plugin on              " 开启插件的支持
filetype indent on              " 开启文件类型相应的缩进规则
```

