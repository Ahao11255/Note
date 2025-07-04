# Selenium简介

selenium是一个用于测试web网页的自动化测试工具，它直接运行在浏览器中，模拟用户的操作。

- 支持多种浏览器，如：Chrome、Firefox、IE、Safari等
- 跨平台，如Windows、Linux、Mac等
- 支持多语言，如：python、java、ruby、c#等

## 安装selenium

1. 在Windows中，通过pip直接安装

```sh
pip install selenium
```
2. 在ArchLinux中，通过包管理器安装
```sh
sudo pacman -S python-selenium
```

# Webdriver

		webdriver则是selenium里最重要的东西，它是按照client/server模式设计的，通过驱动程序与浏览器进行通信。而selenium代码与浏览器驱动程序之间是通过http协议进行数据交互的，这种方式，不在乎客户端是什么样的形式，只要数据的格式和协议是服务端能够解析的就可以，因此它可以跨平台，支持多语言多浏览器。

-  client：编程语言客户端，比如说python selenium客户端
-  server：浏览器驱动程序，用来接收客户端的请求并驱动浏览器执行操作然后返回结果。

## 通信步骤

 1. Webdriver启动浏览器驱动程序，并设置侦听端口号
 2. webdriver客户端与浏览器端建立连接
 3. 连接成功之后，所有的操作（比如查找元素、点击等）都是客户端通过commandExecuter发送http请求到服务端，服务端根据收到的请求做相应的操作并返回结果

## 三大浏览器及驱动

- Chrome：[chromedriver](https://googlechromelabs.github.io/chrome-for-testing/#stable)
- IE： ieserverdriver
- Firefox：geckodriver

## 驱动配置

1. 在Windows中，可将驱动文件放在Python安装目录的根目录中(或者配置环境变量)，后可以直接使用
```python
from selenium inport webdriver

driver=webdriver.Chrome()
driver.get("[your_project_path]")
```

2. 在ArchLinux中，通过AUR安装
 ```sh
 yay -S chromedriver
 chromedriver --version #验证安装
```

**Selenium 并不会自动从系统 PATH 中查找 chromedriver 的位置（或者它查的是空的 PATH），所以你必须在代码中明确指定 chromedriver 的路径。**

```python
from selenium import webdriver
from selenium.webdriver.chrome.service import Service

service = Service('/usr/bin/chromedriver')
driver = webdriver.Chrome(service=service)
```





