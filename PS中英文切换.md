- PS 路径

```sh
D:\Adobe\Adobe Photoshop 2021\Locales
```

将 zh_CN 文件夹复制一份改名为 en_US

将 en_US\Support Files 里面 tw10428_Photoshop_zh_CN.dat 删除

- 打开 en_US\Support Files\pack.inf

```sh
prefstring=Simplified Chinese
localeid=zh_CN
```

改为

```sh
prefstring=English
localeid=en_US
```

- 打开 PS，编辑-首选项-界面-用户界面语言，切换中英文，重启 PS。
