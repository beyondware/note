## 安装 Python

> https://www.python.org/downloads/

- 安装的时候记得勾选 **PATH**

```sh
python --version 或者 python -V
```

```sh
pip --version 或者 pip -V
```

## 配置镜像源

- 以南京大学镜像源为例

```sh
pip install pip -U
```

```sh
pip config set global.index-url https://mirror.nju.edu.cn/pypi/web/simple
```

## 安装 playwright

```sh
pip install --upgrade pip
```

```sh
pip install playwright
```

```sh
playwright install //需要较长时间，请耐心等待
```

## 运行程序

- 以下代码修改好后保存为`.py`格式，执行即可。

```python
from playwright.sync_api import sync_playwright

USERNAME = '用户名'
PASSWORD = '登陆密码'
GITEE_PAGES_URL = 'https://gitee.com/用户名/仓库名/pages'


def main():
    with sync_playwright() as p:
        browser = p.chromium.launch(headless=False)
        page = browser.new_page()
        page.goto('https://gitee.com/login')
        page.click('input[name="user[login]"]');
        page.fill('input[name="user[login]"]', USERNAME);
        page.click('input[name="user[login]"]');
        page.fill('input[name="user[password]"]', PASSWORD);
        page.click("input[value='登 录']")
        page.wait_for_timeout(5000)
        page.goto(GITEE_PAGES_URL)
        page.on("dialog", lambda dialog: dialog.accept())
        page.click(".update_deploy")
        page.wait_for_selector('span:text("已开启 Gitee Pages 服务")', timeout=60 * 1000, state='visible')
        #browser.close()


if __name__ == '__main__':
    main()
```
