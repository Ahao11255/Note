# 一.选择器

## 1.组选择器

1.1有多个标签（添加相同的`css`样式）

1.2在样式表

```css
选择器1，选择器2，选择器3{
声明
}
i,b,em{
colo:red
}
```

## 2.符选择器

1.1固定用法（建议放在第一行）

```css
*{
    外边距
    margin:0px;
    内边距
    padding:0px;
}
```

## 3代选择器

前面是父级后面是子代
父级选择器>子代选择器{
    声明
}

```css
.app>.box{
     width: 200px;
      height: 200px;
      background-color: green;
}
```

## 4.后代选择器

外层包裹内层

外层选择空格内层选择器{

​	声明

}

```css
.app1 .box{
    width: 200px;
    height: 200px;
    background-color: red;
}
```

# 二.伪类选择器

## 1.:link为访问的状态

```css
a:link{
    colo:ren;
}
```

## 2.:vistited访问后的状态

```css
a:{
    colo:green;
}
```

## 3.:hover鼠标移入后的状态

```css
a:hover{
    colo:pink;
}
```

1.1通过鼠标移入父元素让子元素发生变化

父元素选择器:hover 子元素选择器{

鼠标移入后执行的代码

}

```css
.app:hover p{
    witdth:300px;
    height:300px;
    background-colo:brack;
}
```

**1.2注意：不可以通过鼠标移入子元素让父元素发生改变**

## 4.:active鼠标按下的状态

```css
a:active{
    colo:yellow
}
```

# 三.文本字体属性

## 1,font-size(大小)

### 	1.1属性值：

​				1.1.1数值加单位

​				1.1.2网页默认字体16px

​				1.1.3网页支持最小字体12px

​				1.1.4 font-size设置为0px是表示隐藏

```css
div{
    font-size:10px
}
```

### 	1.2网页单位：

|  px  |          像素          |
| :--: | :--------------------: |
|  em  | 相对于父级进行倍数运算 |
| rem  |     移动端常用单位     |

## 2,font-family(字体)

### 	2.1属性值：

​			2.1.1 中文 英文

​			2.1.2 中文必须要用引号

​			2.1.3 浏览器默认微软雅黑

```css
div{
    font-family:"宋体"
}
```

## 3,font-weight(加粗)

### 	3.1属性值：

|  bold  |               加粗                |
| :----: | :-------------------------------: |
| bolder |         更加粗（起强调）          |
| normal | 不加粗，一般清除b和strong的默认值 |

​		3.1.1  100-300(细) 400-500(正常) 600-900(加粗)

```css
div{
    font-weight:bold
    font-weight:bolder
    font-weight:100px
    font-weight:normal
}
```

## 4,font-style(倾斜)

### 	4.1属性值:

|   italic    |             倾斜             |
| :---------: | :--------------------------: |
| **oblique** |   **更加倾斜 （起强调）**    |
| **normal**  | **不倾斜 清除i和em的默认值** |

```css
div{
    font-style:italic
    font-style:oblique
    font-style:normal
}
```

## 5,line-height (文本行高(垂直对齐))

### 5.1属性值

相对于当前标签高度

|   行高=标签高度   |    居中    |
| :---------------: | :--------: |
| **行高>标签高度** | **中篇下** |
| **行高<标签高度** | **中篇下** |

```css
div{
    line-heigth:100px
}
```

## 6,text-align(水平对齐方式)

### 6.1属性值

|    left    | 左（默认值） |
| :--------: | :----------: |
| **right**  |    **右**    |
| **center** |    **中**    |

```css
div{
    text-align:left
    text-align:right
    text-align:center
}
```

## 7,text-indent(首行缩进)

```css
div{
    text-indent:15px
}
```

