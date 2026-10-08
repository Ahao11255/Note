---
title: Java 基础笔记
tags:
  - Java
  - Java/基础
  - 语言基础
aliases:
  - Java笔记
  - Java基础
---

# Java 基础笔记

## Java 的三大使用平台

### Java SE

Java 语言的（标准版），用于桌面应用的开发，**是其他两个版本的基础**。

### Java ME

Java 语言的（小型版），用于嵌入式设备或者小型移动设备。

### Java EE

Java 语言的（企业版），用于 Web 方向的网站开发。

## 关键字

**被 Java 赋予特定含义的英文单词**

关键字的字母都是小写的。

常见的代码编辑器中，对关键字有特殊颜色标记。

### class

class：用于（创建/定义）一个类，类是 Java 最基本的组成单元。

后面跟随类名。

例：

```java
public class HelloWorld {

}
```

### private

- private 关键字是一个权限修饰符
- 可以修饰成员（成员变量和成员方法）
- 被 private 修饰的成员只能在本类中被访问
- 针对 private 修饰的成员变量，如果需要被其他类使用，提供对应的操作
- 提供 `setXxx(参数)` 方法，用于给成员变量赋值，方法用 public 修饰
- 提供 `getXxx()` 方法，用于获取成员变量的值，方法用 public 修饰

例：

```java
package com.ahao.test;

// JavaBean 类，用于创建对象
public class BoyFriend {
    private String name;
    private String id;
    private String gender;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getId() {
        return id;
    }

    public void setGender(String gender) {
        this.gender = gender;
    }

    public String getGender() {
        return gender;
    }
}
```

```java
package com.ahao.test;

// 测试类
public class BoyFriendTest {
    public static void main(String[] args) {
        BoyFriend ahao = new BoyFriend();

        ahao.setName("Ahao");
        ahao.setId("114514");
        ahao.setGender("man");

        System.out.println(ahao.getName());
        System.out.println(ahao.getId());
        System.out.println(ahao.getGender());
    }
}
```

### this

避免就近原则，区分局部变量和成员变量，指向成员变量。

例：

```java
public class Test {
    private String name;

    public void setName(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }
}
```

#### this 关键字内存原理

this 的本质是代表方法调用者的地址值。

例：

```java
public class Student {
    private String name;

    public Student() {}

    public Student(String name) {
        this.name = name;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

```java
public class TestStudent {
    public static void main(String[] args) {
        Student stu1 = new Student();
        stu1.setName("Ahao");
        // setName 方法中的 this 关键字指代的是 stu1 的内存地址
        Student stu2 = new Student();
        stu2.setName("Aha");
        // setName 方法中的 this 关键字指代的是 stu2 的内存地址
        System.out.println(stu1.getName() + "......" + stu2.getName());
    }
}
```

输出：

```text
Ahao......Aha
```

## 字面量

**告诉程序员：数据在程序中的书写格式**

### 分类

整数，小数，字符串，字符，布尔，空

### 一些特殊字面量的书写

#### `'\t'`

表示制表符：打印时把当前位置补齐到下一个制表位（每 8 列为一个制表位，即把前面字符串的长度补齐到 8 或者 8 的整数倍）。所以最少补 1 个空格，最多补 8 个空格。

#### null

空值，**只能赋值给引用数据类型**（如 String、数组、对象），不能赋给基本数据类型，也不能直接以基本类型的形式使用。

## 变量

### 定义格式

```text
数据类型 变量名 = 数据值;
```

### 使用变量

- 输出打印
- 参与计算
- 修改记录的值

### 使用场景

- 重复使用某个值
- 某个数据经常发生改变

### 注意事项

- 变量只能存在一个值
- 变量名不能重复
- 一条语句可以定义多个变量
- 使用前一定要赋值

## 成员变量和局部变量

|     区别     |                 成员变量                  |                   局部变量                    |
| :----------: | :---------------------------------------: | :-------------------------------------------: |
| 类中位置不同 |                类中，方法外               |              方法内，方法声明上               |
| 初始化值不同 |              有默认初始化值               |             没有，使用之前必须赋值            |
| 内存位置不同 |                  堆内存                   |                    栈内存                     |
| 生命周期不同 | 随着对象的创建而存在，随着对象的消失而消失 | 随着方法的调用而存在，随着方法运行的结束而消失 |
|    作用域    |               整个类内有效                |                当前方法内有效                 |

## 不同进制位在代码中的表现形式

### 二进制

由 0 和 1 组成，代码中以 `0b` 开头

### 十进制

由 0~9 组成，前面不加任何前缀

### 八进制

由 0~7 组成，代码中以 `0` 开头

### 十六进制

由 0~9 和 a~f 组成，代码中以 `0x` 开头

## Java 数据类型

### 基本数据类型

| 分类     | 类型                              |
| -------- | --------------------------------- |
| 整数     | byte（-128~127）、short、int、long |
| 浮点数   | float、double                     |
| 字符     | char                              |
| 布尔     | boolean                           |

> [!note] 注意
> `String` **不是基本数据类型**，而是引用数据类型（字符串类型）。

#### long 类型数据

如果要定义 long 类型数据的变量，要在数据值的后面加 `L`，大小写不限。

**建议用大写。**

#### float 类型数据

如果要定义 float 类型数据的变量，要在数据值的后面加 `F`，大小写不限。

**建议用大写。**

### 基本数据类型和引用数据类型

#### 基本数据类型

- 整数类型
- 浮点数类型
- 布尔类型
- 字符类型

#### 引用数据类型

- 字符串类型
- 数组

基本数据类型存储的是**真实的数据**。

引用数据类型存储的是变量 or 常量在堆内存中的**内存地址值**，使用其他空间的数据。

### 数据取值范围大小

```text
byte < short < int < long < float < double
```

（`char` 参与运算时会先提升为 `int`。）

## IDEA

### IDEA 项目结构介绍

```text
project（项目）
    module（模块）
        package（包）
            class（类）
```

### 快捷键

| 快捷键                    | 作用                 |
| ------------------------- | -------------------- |
| ctrl + alt + L            | 自动格式化代码       |
| ctrl + /                  | 单行注释，再次使用取消 |
| ctrl + shift + /          | 多行注释，再次使用取消 |
| ctrl + alt + M            | 自动抽取方法         |
| alt + insert 或 alt + Fn + insert | 快速生成构造方法 |

### IDEA 快速遍历数组

数组名 `.for i`

## 数据类型的转换

```text
（要强转的数据类型）（数据）
```

例：

```java
int number = 100;
number = (int) (number * 0.9);
```

### 隐式转换

自动类型提升：取值范围小的数 → 取值范围大的数

### 隐式转换的两种提升规则

- 取值范围小的和取值范围大的进行计算，小的会提升为大的，再进行计算
- byte、short、char 三种类型的数据进行计算的时候，都会直接提升为 int，然后再进行计算

### 强制转换

取值范围大的数 → 取值范围小的数

## 三元运算符

格式：

```text
关系表达式 ? 表达式1 : 表达式2
```

如果关系表达式结果为真，那么结果为表达式 1，反之则为表达式 2。

三元运算符的结果必须被使用。

## JDK12 中 switch 新特性

例：

```java
import java.util.Scanner;

public class TestSwitch {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int number = sc.nextInt();
        switch (number) {
            case 1 -> {
                System.out.println("1");
            }
            case 2 -> {
                System.out.println("2");
            }
            case 3 -> {
                System.out.println("3");
            }
            default -> {
                System.out.println("err");
            }
        }
    }
}
```

如果大括号里只有一行代码，那么大括号可以省略。

## Java 随机数

Java 帮我们写好一个类 `Random`，这个类可以生成一个随机数。

例：

```java
import java.util.Random;

Random r = new Random();
int number = r.nextInt(范围); // 范围是一个正整数
```

在小括号中，书写的是生成随机数的范围。

这个范围一定是从 0 开始的，到这个数 -1 结束。

例：

```java
import java.util.Random;

Random r = new Random();
// 生成 0~99 之间的随机数
int number = r.nextInt(100);
```

## 数组

### 定义

```java
int[] array; // 数据类型 [] 数组名
```

```java
int array[]; // 数据类型 数组名 []
```

***根据阿里巴巴编码规范，应使用第一种定义方式。***

### 初始化

#### 静态初始化

```text
数据类型[] 数组名 = new 数据类型[]{元素1, 元素2, .......}
```

```java
int[] array = new int[]{11, 22, 33};
```

简化格式：

```text
数据类型[] 数组名 = {元素1, 元素2, .......}
```

```java
int[] array = {11, 22, 33};
```

#### 动态初始化

初始化时只指定数组长度，由系统分配默认的初始值。

数组默认初始化值的规律：

| 类型                            | 默认值      |
| ------------------------------- | ----------- |
| byte、short、int、long          | 0           |
| float、double                   | 0.0         |
| char                            | `'\u0000'`  |
| boolean                         | false       |
| 引用数据类型                    | null        |

> [!note] `'\u0000'` 是一个空字符（编码为 0），并不是空格字符 `' '`。

格式：

```text
数据类型[] 数组名 = new 数据类型[数组长度];
```

```java
int[] arr = new int[10];
```

#### 区别

只明确元素个数、不明确具体数值时，推荐使用动态初始化。

需求中已经明确了要操作的具体数据时，直接静态初始化即可。

### 问题

**索引越界异常** `ArrayIndexOutOfBoundsException`：访问了不存在的索引。

### JVM 内存注意事项

```java
// 两个数组指向同一片内存
// int[] arr 在栈内存中存储的是数组的内存地址
// int[] arr1 = arr; 是将 int[] arr 在栈内存中存储的数组内存地址赋值给 arr1
int[] arr = {1, 2, 3, 4, 5};
int[] arr1 = arr;
```

当两个数组指向同一片堆内存空间时，其中一个数组对堆内存空间中的值做出改变后，其他数组再次访问得到的就是改变之后的值。

## 二维数组

***当需要对数据进行分组管理的时候，就要用到二维数组。***

### 静态初始化

```text
数据类型[][] 数组名 = new 数据类型[][]{{元素1, 元素2, ......}, {元素1, 元素2, ......}};
```

```java
int[][] arr = new int[][]{{1, 2, 3}, {1, 2, 3}};
```

**简写**

```text
数据类型[][] 数组名 = {{元素1, 元素2, ......}, {元素1, 元素2, ......}};
```

```java
int[][] arr = {{1, 2, 3}, {1, 2, 3}};
```

**为了增强可读性，一般把每个一维数组分行写**

```java
int[][] arr = {
    {1, 2, 3},
    {1, 2, 3, 4}
};
```

***获取元素***

```java
int[][] arr = {
    {1, 2, 3},
    {4, 5, 6, 7, 8}
};
System.out.println(arr[i][j]);
// i 表示二维数组的索引，表示获取二维数组中的一维数组
// j 表示一维数组的索引，表示获取一维数组中的元素
```

例：

```java
int[][] arr = {
    {1, 2, 3},
    {4, 5, 6, 7, 8}
};
System.out.println(arr[0][1]);
// sout:2
```

***遍历***

```java
int[][] arr = {
    {1, 2, 3},
    {4, 5, 6, 7, 8}
};
// 外循环：遍历二维数组，得到一个一维数组
for (int i = 0; i < arr.length; i++) {
    // 内循环：遍历一维数组，得到每一个元素
    for (int j = 0; j < arr[i].length; j++) {
        System.out.print(arr[i][j] + " ");
    }
    System.out.println();
}
```

### 动态初始化

```text
数据类型[][] 数组名 = new 数据类型[m][n];
```

- m：表示这个二维数组中可以存放 m 个一维数组
- n：表示每个一维数组中可以存放 n 个元素

```java
int[][] arr = new int[2][3];
```

### 内存原理

https://www.bilibili.com/video/BV17F411T7Ao?t=1496.4&p=80

## 列表和映射

### 列表（List）

#### 概述

- **List** 是一种有序集合，允许重复元素。
- 常见的实现类有 `ArrayList` 和 `LinkedList`。

#### 创建列表

```java
import java.util.*;

public class ListExample {
    public static void main(String[] args) {
        // 创建一个 ArrayList
        List<String> list = new ArrayList<>();

        // 添加元素
        list.add("Apple");
        list.add("Banana");
        list.add("Cherry");

        // 打印列表
        System.out.println(list); // 输出: [Apple, Banana, Cherry]
    }
}
```

#### 常用方法

- `add(E e)`：向列表添加元素。
- `get(int index)`：获取指定位置的元素。
- `set(int index, E element)`：替换指定位置的元素。
- `remove(int index)`：移除指定位置的元素。
- `size()`：获取列表的元素数量。
- `contains(Object o)`：检查列表是否包含指定元素。
- `isEmpty()`：检查列表是否为空。

#### 访问列表中的元素

```java
List<String> list = new ArrayList<>();
list.add("Apple");
list.add("Banana");

// 通过索引获取元素
String firstItem = list.get(0); // 获取第一个元素 "Apple"

// 使用增强 for 循环遍历
for (String item : list) {
    System.out.println(item); // 输出: Apple, Banana
}
```

#### 遍历列表

```java
List<String> list = new ArrayList<>();
list.add("Apple");
list.add("Banana");

// 普通 for 循环
for (int i = 0; i < list.size(); i++) {
    System.out.println(list.get(i)); // 输出列表中的元素
}

// 使用 Java 8 Lambda 表达式
list.forEach(item -> System.out.println(item)); // 输出: Apple, Banana
```

---

### 映射（Map）

#### 概述

- **Map** 是一种键值对集合，不能包含重复的键，每个键对应一个值。
- 常见的实现类有 `HashMap`、`TreeMap` 和 `LinkedHashMap`。

#### 创建映射

```java
import java.util.*;

public class MapExample {
    public static void main(String[] args) {
        // 创建一个 HashMap
        Map<String, Integer> map = new HashMap<>();

        // 添加键值对
        map.put("Apple", 1);
        map.put("Banana", 2);
        map.put("Cherry", 3);

        // 打印映射
        System.out.println(map); // 输出: {Apple=1, Banana=2, Cherry=3}
    }
}
```

#### 常用方法

- `put(K key, V value)`：将指定的键值对放入映射中。
- `get(Object key)`：根据键获取对应的值。
- `remove(Object key)`：根据键移除键值对。
- `containsKey(Object key)`：检查映射中是否包含指定的键。
- `containsValue(Object value)`：检查映射中是否包含指定的值。
- `keySet()`：返回映射中所有的键。
- `values()`：返回映射中所有的值。
- `entrySet()`：返回映射中所有的键值对（`Map.Entry`）。

#### 访问映射中的元素

```java
Map<String, Integer> map = new HashMap<>();
map.put("Apple", 1);
map.put("Banana", 2);

// 获取某个键对应的值
int appleValue = map.get("Apple"); // 返回 1

// 检查映射中是否包含某个键
boolean hasBanana = map.containsKey("Banana"); // 返回 true

// 获取所有键
Set<String> keys = map.keySet();
System.out.println(keys); // 输出: [Apple, Banana]

// 获取所有值
Collection<Integer> values = map.values();
System.out.println(values); // 输出: [1, 2]
```

#### 遍历映射

```java
Map<String, Integer> map = new HashMap<>();
map.put("Apple", 1);
map.put("Banana", 2);

// 使用增强 for 循环遍历键值对
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + ": " + entry.getValue());
}
// 输出:
// Apple: 1
// Banana: 2

// 使用 Java 8 Lambda 表达式
map.forEach((key, value) -> System.out.println(key + ": " + value));
// 输出:
// Apple: 1
// Banana: 2
```

---

### 总结

1. **列表（List）**
   - 有序集合，允许重复元素。
   - 常用实现：`ArrayList`、`LinkedList`。
   - 使用 `add()`、`get()`、`remove()` 等方法操作列表。
2. **映射（Map）**
   - 键值对集合，键唯一，值可以重复。
   - 常用实现：`HashMap`、`TreeMap`、`LinkedHashMap`。
   - 使用 `put()`、`get()`、`remove()` 等方法操作映射。

## Java 内存分配

- 栈：存储变量、方法运行时使用的内存，比如 main 方法进入方法栈中执行
- 堆：存储对象或数组，`new` 来创建的都存储在堆内存
- 方法区：存储可以运行的 class 文件
- 本地方法栈：JVM 在使用系统功能的时候使用，和开发无关
- 寄存器：给 CPU 使用，和开发无关

***在 JDK7 之前，堆和方法区是一块连续的空间。***

## 方法

### 方法的重载

在同一个类中，定义了多个同名的方法，这些同名的方法具有同种的功能。

每个方法具有不同的参数类型、参数个数或参数顺序，这些同名的方法就构成了重载关系。

### 方法值的传递

**传递**基本数据类型时，传递的是**真实的数据**，形参的改变不会影响到真实的值。

**传递**引用数据类型时，传递的是**地址值**，形参的改变会影响到真实的值。

## 构造方法

**作用**

创建对象的时候，由 JVM 虚拟机自动调用，给成员变量进行初始化。

**类别**

- 无参构造方法：初始化对象时，成员变量的数据均采用默认值
- 有参构造方法：在初始化对象时，同时为对象进行赋值

**注意！**

任何类定义出来，默认自带了无参构造器。

一旦定义了有参构造器，无参构造器就消失了，此时要自己写无参构造器。

建议任何时候都手动写上带全部参数和无参构造方法。

---

## 相关笔记

- [[Java面向对象编程]] —— 封装、继承、多态与对象内存图
- [[JUnit单元测试]] —— 单元测试框架
- [[浮点数精度丢失与BigDecimal]] —— 浮点数精度问题
- [[原码反码补码]] —— 数据在计算机中的表示
