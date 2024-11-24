# 一.网站的建设流程

##  1.注册域名：

​		1.1:域名就是网址(www.baidu.com)

##  2.租用空间(租服务器)

​		2.1:无需购买服务器，可以根据自己的需求租用服务器

##  3.网站建设

​		3.1:确认网站的主题

​		3.2:收集资料

​		3.3:规划网站

​		3.4:制作网页

## 4.网站推广

## 5.网站维护

## 6.网站和网页的关系

​	6.1一个网站有多个网页组成

# 二.认识窗口

1.资源管理器:![image-20231013105345167](C:\Users\desolate1\AppData\Roaming\Typora\typora-user-images\image-20231013105345167.png)（这里的数字代表未保存）

2.搜索:![image-20231013105449566](C:\Users\desolate1\AppData\Roaming\Typora\typora-user-images\image-20231013105449566.png)

3.git仓库:![image-20231013105901010](C:\Users\desolate1\AppData\Roaming\Typora\typora-user-images\image-20231013105901010.png)(可以把没写完的代码暂时的存放在这)

4.运行调试:![image-20231013110114587](C:\Users\desolate1\AppData\Roaming\Typora\typora-user-images\image-20231013110114587.png)(可以测试代码的问题)

5.下插件的地方:![image-20231013110230276](C:\Users\desolate1\AppData\Roaming\Typora\typora-user-images\image-20231013110230276.png)

6.用户:![image-20231013110313227](C:\Users\desolate1\AppData\Roaming\Typora\typora-user-images\image-20231013110313227.png)

7.设置:![image-20231013110415363](C:\Users\desolate1\AppData\Roaming\Typora\typora-user-images\image-20231013110415363.png)

# 三.常用快捷键

## 1.visual

​	1.1:英文感叹号回车会出现初始化模板

​	1.2:Ctrl+/:注释

​	1.3:Alt+B :快速开启浏览器

​	1.4:复制:shift+ alt+↓

​	1.5:移动:alt+↓

​	1.6:格式化代码规范: shift+ alt+ F

​	1.7:折叠侧边栏:CtrI+ B

​	1.8F12打开控制台

​	1.9:mac双系统的F12 = fn+F120 Ctrl+N :新建

​	1.10:Ctrl+C:复制(光标在这一 行即可)

​	1.11:CtrI + X:删除当前行

​	1.12:Ctrl+Z撤销这-次操作

​	1.13:Ctrl+Shift+Z :反撤销

## 2.typora

​	2.1:一级标题:ctrl + 1

​	2.2:二级标题:ctrl + 2

​	2.3:三级标题:ctrl + 3

​	2.4:四级标题:ctrl + 4

​	2.5:五级标题:ctrl + 5

​	2.6:六级标题:ctrl + 6

​	2.7:代码块:ctrl + shift + k

​	2.8:有序列表:ctrl + shift + [

​	2.9:无序列表:ctrl + shift + ]

​	2.10:增加缩进:ctrl + [

​	2.11:减少缩进:ctrl +]

​	2.12:插入表格:ctrl + t

​	2.13:加粗:ctrl + b

​	2.14:斜体:ctrl + i

​	2.15:下划线:ctrl + u

​	2.16:删除线:alt + shift + 5

# 四.HTML的基本结构

```html
<!-- 告诉浏览器 按照html的文档规范去解析  -->
<!DOCTYPE html>
<!-- 所有网页最大的结构 网页中所有的标签存放在html标签中 -->
<html lang="en">
<!-- 头部  不可视部分 存放页面相关的关键配置 或者 引入资源-->
<head>  
	<!-- meta标签：提供有关页面的元信息，用来设置网页的基本信息 -->
    <!-- charset：表示网页编码格式浏览器打开网页的时候会使用charset指定的编码读取整个HTML文档 -->
    <meta charset="UTF-8">
    <!-- 网页的标题信息，它会显示在浏览器标签页的标题栏中。主要用来告诉用户和搜索引擎这个网页的主要内容是什么,搜索引擎可以通过网页标题，迅速的判断出当前网页的主题。-->
    <title>Document</title>
</head>
    
<!-- 可视部分的标签内容 全部放到body标签内 -->
<body>  
    
</body>
</html>
```

## 网页定时刷新

```html
<meta http-equiv="refresh" content="0">
```