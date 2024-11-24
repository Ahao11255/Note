# 一.css语法和组成

## 1.语法

```css
<!--
选择器{

属性1：属性值1

属性2：属性值2
......
}
-->
div{
            width: 200px;
            height: 200px;
            background-color: pink;
        }
```

## 2.组成

​			2.1：css是由选择器 选择符，{}花括号，组成

​			2.2：每个属性和属性值写完后都要加上 ；分号

# 二.css样式

## 1.行内样式（不推荐使用）

​			1.1：在标签里面创建s't'yle属性

​			1.2：属性值就是css的声明（css属性和属性值）

```html
<div style='width:200px;height:200px;ackground-colo:green '>
    内容
</div>
```

## 2.内部样式（一般用于小项目）

​			2.1：在head区域创建style标签

​			2.2：在style标签内部里写css语法

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <stype>
        div{
        width:200px;
        height;200px;
        colo:green:
        }
    </stype>
</head>
<body>
    <div>
        
    </div>
</body>
</html>
```

## 3.外部样式（一般用于大项目）

​			3.1：在外面创建一个.css文件

​			3.2：在head区域利用link标签引入.css文件

​			3..3：在.css文件写css语法

```css
div{
     width:200px;
      height;200px;
      colo:green:
}
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="./css/my.css">
</head>
<body>
    <div>
        外部样式
    </div>
</body>
</html>
```

## 4.扩展

​			4.1：link是代码和cs同时加载

​			4.2：@import先加载html再加载css（缺陷很大）

# 三.css样式的优先级

1.行内大于内部，行内大于外部，行内最大

2.浏览器中有黑色线划过说明有相同的代码被覆盖了

3.黄色感叹号：代表代码有错

### 1.样式表的优先级

​	1.行内样式最高，外部与内部取决与书写顺序，谁里目标进谁的优先级就越高（就进原则）

# 四.css选择器

### 1.标签选择器/元素选择器

1.1在样式表 

```css
标签名称{
    声明
}
```



### 2.id选择器/class选择器

2.1在标签中添加id/class属性（属性值就是自己取的名字）

2.2在样式表 

```css
#id选择器的名字{
    声明
}
.class{
    声明
}
```

### 3.取名规则

3.1不能数字，中文，特殊符号开头

3.2可以有字母，数字，下划线组合起来

3.3具有语义化，见名知意，规范

3.4不要使用关键字保留字