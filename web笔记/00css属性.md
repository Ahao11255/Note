`<style></style>(css标签)`

##### 通用属性

|      属性       |          讲述           |                 属性值 （里面可以写的东西）                  |
| :-------------: | :---------------------: | :----------------------------------------------------------: |
|      width      |           宽            |                      数值+单位（`px`）                       |
|     height      |           高            |                      数值+单位（`px`）                       |
|      color      |        文本颜色         |     颜色（英文）, `rgb`(0-255,0-255,0-255)，16色#000000      |
|    font-size    |      文本字体大小       | 数值+单位（`px`）（网页默认字体`16px`，网页支持最小字体`12px`，`0xp`表示隐藏） |
|   font-family   |        字体样式         |                  安装的字体文字（微软雅黑）                  |
|   font-weight   |        字体加粗         | `bold` 加粗，`bolder` 更加粗 起强调，`100-300`(细) `400-500`(正常) `600-900`(加粗)，`normal` 不加粗一般清除b和strong标签的默认加粗 |
|   font-style    |        字体倾斜         | `italic` 倾斜，`oblique `更加倾斜 起强调，`normal` 不倾斜 清除i和em的默认倾斜 |
|   text-align    |    文本水平对齐方式     |          `left` 默认值 左，`right` 右，`center` 中           |
|  `line-height`  | 文本行高   垂直对齐方式 | 数值+单位（`px`）（相对于当前标签高度，行高=标签高度 居中，行高>标签高度 中偏下，行高<标签高度 中偏上） |
|   text-indent   |        首行缩进         |             （首行缩进距离）`xp`，一个空格`16xp`             |
| text-decoration |        文本修饰         | `none` 不修饰 一般清除a标签的默认下划线，`underline` 下划线，`overline` 上划线，`line-through` 删除线 |
|      float      |          浮动           |                 left (左浮动)right（右浮动）                 |
|    overflow     |        溢出隐藏         | visible(默认超出不隐藏（默认值）)，hidden(溢出隐藏)，auto(超出生成滚动条)，scroll(不管超没超出生成滚动条) |
|     display     |      元素类型转换       | block（转换成块级）inline（转换成行内）inline-block（转换成行内块） |
|     opacity     |         透明度          |                             0-1                              |
|   max-height    |        最大高度         |                          数值+单位                           |
|   min-height    |        最小高度         |                          数值+单位                           |
|    min-width    |        最小宽度         |                          数值+单位                           |
|    max-width    |        最大宽度         |                          数值+单位                           |

##### 列表属性

|        属性         |                    |                            属性值                            |
| :-----------------: | :----------------: | :----------------------------------------------------------: |
|     list-style      |        样式        | `none`清除 l i 默认样式      `disc`黑色小圆点    `circle`空心小圆点    `square`黑色方块 |
|  list-style-image   | 使用图片代替列表项 |                       `url(图片路径)`                        |
| list-style-position |    列表符的位置    |                `inside` 里面，`outside` 外面                 |

##### 边框属性

|         属性          |                |                            属性值                            |
| :-------------------: | :------------: | :----------------------------------------------------------: |
|    `border-widht`     |   边框的宽度   |                      数值+单位（`px`）                       |
|     border-style      |   边框的类型   |    `solid`实线 `double`双实线 `dotted`点状先 dashed 虚线     |
|     border-color      |   边框的颜色   |                     */文本字体颜色一样/*                     |
|     border-(方向)     | 单方向边框设置 |      **方向**可填:`top`上 `right`右 `bottom`下 `left`左      |
| `border-(方向)-widht` |   边框的宽度   |                            *同上*                            |
|  border-(方向)-style  |   边框的类型   |                            *同上*                            |
| `borde-(方向)r-color` |   边框的颜色   |                            *同上*                            |
|     border-(方向)     |      简写      | 边框的宽度 边框的类型 边框的颜色(不填**方向**表示所有方向边框) |
|     border-radius     |    边框倒角    |                            数值%                             |

##### 背景属性

|         属性         |          |                            属性值                            |
| :------------------: | :------: | :----------------------------------------------------------: |
|   background-color   | 背景颜色 |                     */文本字体颜色一样/*                     |
|   background-image   | 背景图片 |                    `url(背景图片的路径)`                     |
|  background-repeat   | 背景平铺 | `no-repeat` 不平铺不重复 ，`repeat` 默认值平铺，   `repeat-x`/`repeat-y` 水平/垂直方向平铺 |
| background-position  | 背景定位 | x y（x：`left`左 `certen`居中 `right`右 ）（y：`top`上 `center`居中 `bottom`下）具体的数值加单位(可以为负值也可以为正值) |
|      background      |   简写   | 背景颜色 背景图片 背景平铺 背景定位（不分先后顺序）linear-gradient(线性渐变)radial-gradient（径向渐变）repeating-linear-gradient（重复线性渐变）repeating-radial-gradient（重复径向渐变） |
| background-attachmen | 背景固定 |                        fixed（固定）                         |

##### 边距属性

| 属性             |                |                            属性值                            |
| ---------------- | -------------- | :----------------------------------------------------------: |
| margin           | 外边距         |          数值+单位（`px`）,/`auto`**元素水平居中**/          |
| padding          | 内边距         |                      数值+单位（`px`）                       |
| margin-（方向）  | 单方向的外边距 | <**方向**:`top`上 `right`右 `bottom`下 `left`左>    <`数值`> |
| padding-（方向） | 单方向的内边距 |                            *同上*                            |
| margin           | 外边距简写     | 四种情况 `↑↓←→<一个数值>` / `↑↓<数值1> ←→<数值2>` / `↑<数值1> ↓←<数值2> →<数值3>` / `↑<数值1> →<数值2> ↓<数值3> ←<数值4>` |
| padding          | 内边距简写     |                            *同上*                            |

##### 表格属性

|     属性     |           效果           |                      数值                       |
| :----------: | :----------------------: | :---------------------------------------------: |
| width/height |          宽/高           |                      10/10                      |
|    border    |           边框           |                        1                        |
| bordercolor  |         边框颜色         |                      pink                       |
|   bgcolor    |         背景颜色         |                       red                       |
| cellspacing  | 单元格与单元格之间的缝隙 |                        0                        |
|    align     |       水平方向对齐       | left(左对齐）center(水平居中对齐) right(右对齐) |
|    valign    |       垂直对齐方式       | top(上对齐) middle(垂直居中对齐) bottom(下对齐) |
| empty-cells  |    隐藏空内容的单元格    |         hide(隐藏)，show显示（默认值）          |
| caption-side |         出现位置         |            top（上方）bottom（下方）            |

|  属性   |   效果   |
| :-----: | :------: |
| colspan | 横向合并 |
| rowspan | 纵向合并 |

##### 定位

|        属性        | 效果 |                             数值                             |
| :----------------: | :--: | :----------------------------------------------------------: |
| position: relative | 相对 | top:数值+单位，right:数值+单位，bottom:数值+单位，left:数值+单位 |
| position: absolute | 绝对 |                             同上                             |
|   position:fixed   | 固定 |                             同上                             |
|  position:sticky   | 粘性 |                             同上                             |

##### 伪类元素

|      属性      |                             效果                             |        数值        |
| :------------: | :----------------------------------------------------------: | :----------------: |
| ::first-letter |               表示给当前元素第一个字符设置样式               | 跟普通设置样式一样 |
|  ::first-line  |               表示给当前元素第一行字符设置样式               | 跟普通设置样式一样 |
|    ::before    | 表示给当前元素添加一个最前面的元素，得设置content:""和display:block才能变成块级元素 | 跟普通设置样式一样 |
|    ::after     | 表示给当前元素添加一个最后面的元素，得设置content:""和display:block才能变成块级元素 | 跟普通设置样式一样 |

##### 过度

|            属性            |       效果       |                            属性值                            |
| :------------------------: | :--------------: | :----------------------------------------------------------: |
|    transition-property     | 指定要渐变的属性 |                     all（通常都是这个）                      |
|    transition-duration     |   过度持续时间   |                        数值+单位（s）                        |
| transition-timing-function |   过度时间效果   | linear（匀速）ease-in（先慢后快）ease-out （先快后慢） ease-in-out （先慢后快再慢） |
|      transition-delay      |   延迟过度时间   |                        数值+单位（s）                        |
|         transition         |       简写       |   指定要渐变的属性 过度持续时间 过度时间效果 延迟过度时间    |

##### 转换

|       属性       |    效果    |                      属性值                      |
| :--------------: | :--------: | :----------------------------------------------: |
|    transform     |    平移    |     tranlateX（x轴平移）tranlastY（y轴平移）     |
|                  |    缩放    |              scale(x轴缩放,y轴缩放)              |
|                  |    倾斜    | skew(沿x轴倾斜) skewX(沿x轴倾斜)skewY(沿y轴倾斜) |
|                  |    旋转    |                 rotate(角度deg)                  |
| transform-origin | 设置中心点 |            参数1（x轴），参数2（y轴）            |

