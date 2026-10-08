---
title: Java 面向对象编程
tags:
  - Java
  - Java/面向对象
aliases:
  - 面向对象
  - OOP
---

# Java 面向对象编程

## 面向对象的三大特征

封装、继承、多态

## 类和对象

### 类

类：是对一类事物共同特征的描述。

类名首字母大写，需要见名知义，采用驼峰命名。

在一个 Java 文件中可以定义多个 class 类，***但只能有一个类是 public 修饰的，且 public 修饰的类名必须与 Java 文件名相同。***

***实际开发中，一个文件定义一个 class 类。***

例：

```java
public class 类名 {
    1. 成员变量（代表属性）;
    // 成员变量完整定义格式：修饰符 数据类型 变量名 = 初始化值;
    // 一般不需要初始化值，成员变量存在默认值

    2. 成员方法（代表行为）;
}
```

成员变量默认初始化值：

| 数据类型 | 明细                   | 默认值     |
| :------: | :--------------------: | :--------: |
| 基本类型 | byte, short, int, long | 0          |
|          | float, double          | 0.0        |
|          | boolean                | false      |
|          | char                   | `'\u0000'` |
| 引用类型 | 类、接口、数组、String | null       |

#### JavaBean 类

用来描述一类事物的类，叫 ***JavaBean 类***。

在 JavaBean 类中，**不写 main 方法**。

IDEA 中使用 PTG 插件生成标准 JavaBean。

##### 标准 JavaBean 类

1. 类名要见名知意
2. 成员变量要用 `private` 修饰
3. 提供至少两个构造方法
   - 无参构造方法
   - 带全部参数的构造方法
4. 成员方法
   - 提供每一个成员变量对应的 `setXxx()` 和 `getXxx()`
   - 如果还有其他行为，也要写上

#### 测试类

编写 `main` 方法的类，叫 ***测试类***。

我们可以在测试类中创建 JavaBean 类的对象并进行赋值、调用。

#### 实际开发中类的设计

https://www.bilibili.com/video/BV17F411T7Ao?t=1334.4&p=82

### 对象

对象：是真实存在的具体实例。

#### 获取对象

```java
public class 类名 {
    1. 成员变量（代表属性的，一般是名词）;
    2. 成员方法（代表行为的，一般为动词）;
}
```

```java
类名 对象名 = new 类名();
```

例：

```java
package com.ahao.test;

public class Phone {
    String brand;
    double price;

    public void call() {
        System.out.println("打电话");
    }

    public void playGames() {
        System.out.println("玩游戏");
    }
}
```

```java
package com.ahao.test;

public class PhoneTest {
    public static void main(String[] args) {
        Phone p = new Phone();

        p.brand = "HuaWei";
        p.price = 8999.00;

        p.call();
        p.playGames();
    }
}
```

#### 拿到对象后能干什么？

- 对成员变量进行赋值
- 使用成员方法

## 封装

封装：对象代表什么，就得封装对应的数据，并提供数据对应的行为。

例：https://www.bilibili.com/video/BV17F411T7Ao?t=191.7&p=83

## 对象内存图

***过程***

有多个对象时不会重复加载 `.class` 文件。

1. 加载 class 文件
2. 声明局部变量
3. 在堆内存中开辟一个空间
4. 默认初始化
5. 显式初始化
6. 构造方法初始化
7. 将堆内存中的地址值赋值给左边的局部变量

例：

```java
Student student1 = new Student();
// student1 存储的是堆空间中的内存地址值
```

详细：

[面向对象-07-三种情况的对象内存图_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV17F411T7Ao?p=87&vd_source=4c986c16973a6ead6f61ebaad5af8682)

### 当两个引用指向同一个对象时

有一个变量对堆空间中的值发生改变后，其他变量再访问得到的就是改变后的值。

例：

```java
public class Student {
    String name;
    int age;

    public void study() {
        System.out.println("好好学习");
    }
}
```

```java
public class TestStudent {
    public static void main(String[] args) {
        Student stu1 = new Student();
        stu1.name = "Ahao";

        Student stu2 = stu1;
        // 将 stu1 的地址值赋值给 stu2

        stu2.name = "Aha";
        System.out.println(stu1.name + "......" + stu2.name);

        stu1 = null;
        // 将 stu1 中存储的地址值覆盖为 null，使其不再指向堆内存中的对象
        System.out.println(stu1.name); // 此处抛出空指针异常，程序中断
        System.out.println(stu2.name); // 上一行已中断，这行不会执行

        stu2 = null;
    }
}
```

输出：

```text
Aha......Aha
Exception in thread "main" java.lang.NullPointerException: Cannot read field "name" because "stu1" is null
	at TestStudent.main(TestStudent.java:17)
```

注意：程序在 `System.out.println(stu1.name);` 处中断，所以 `stu2.name` 并没有被打印。若把这行注释掉，`stu2` 仍然指向原来那个对象，会输出 `Aha`。

## 相关笔记

- [[Java基础笔记]] —— 前置：语法、数组、方法
- [[JUnit单元测试]] —— 给写好的类补测试
