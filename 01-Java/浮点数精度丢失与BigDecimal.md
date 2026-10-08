---
title: 浮点数精度丢失与 BigDecimal
tags:
  - Java
  - Java/精度
  - BigDecimal
aliases:
  - Java中浮点数的精度丢失问题和解决方法
  - 浮点数精度
---

# 浮点数精度丢失与 BigDecimal

> [!info] 本文讨论 Java 中 `double` / `float` 的精度丢失问题，以及用 `BigDecimal` 精确计算的方法。

- 原因：*浮点数无法使用二进制进行精确表示*。CPU 表示浮点数由两部分组成：指数和尾数，这样的表示方法一般会失去一定的精确度，有些浮点数也会产生一定的误差。

## BigDecimal 类介绍

在处理金额交易和科学计算时，我们需要精确的结果，此时一般采用 `java.math.BigDecimal` 类来进行精确计算。

### 使用步骤

1. 用 `double`、`String`、`int` 等变量构建 `BigDecimal` 对象。通常使用 `BigDecimal` 的构造方法，或静态方法 `BigDecimal.valueOf(double)` 把基本类型的变量构建成 `BigDecimal` 对象。
2. 通过调用 `BigDecimal` 的加、减、乘、除等对应的方法进行算术运算。
3. 把 `BigDecimal` 对象转换成 `float`、`double`、`int` 等类型。

> [!warning] 重要
> `BigDecimal` 是**不可变类**：`add` / `subtract` / `multiply` / `divide` 都不会修改原对象，而是**返回一个新的 `BigDecimal` 对象**，必须用变量接收返回值。

### BigDecimal 类的构造方法

```java
BigDecimal(int var)    // 创建一个具有参数所指定整数值的对象。
BigDecimal(double var) // 创建一个具有参数所指定双精度值的对象。
BigDecimal(long var)   // 创建一个具有参数所指定长整数值的对象。
BigDecimal(String var) // 创建一个具有参数所指定以字符串表示的数值的对象。
```

### BigDecimal 类的加、减、乘、除等相应的方法

```java
BigDecimal add(BigDecimal augend)            // 加法运算
BigDecimal subtract(BigDecimal subtrahend)   // 减法运算
BigDecimal multiply(BigDecimal multiplicand) // 乘法运算
BigDecimal divide(BigDecimal divisor)        // 除法运算
```

> [!note] 注意
> - `BigDecimal(double var)` 构造方法的结果有一定的不可预知性。有人可能认为在 Java 中写入 `new BigDecimal(0.1)` 所创建的 `BigDecimal` 正好等于 0.1，但它实际上等于 `0.1000000000000000055511151231257827021181583404541015625`。这是因为 0.1 无法准确地表示为 `double`（或者说对于该情况，不能表示为任何有限长度的二进制小数），因此传入到构造方法的值不会正好等于 0.1（虽然表面上等于该值）。
> - `BigDecimal(String var)` 的 String 参数构造方法是完全可预知的：写入 `new BigDecimal("0.1")` 将创建一个正好等于预期的 0.1 的 `BigDecimal`。因此比较而言，通常建议优先使用 String 构造方法，或使用 `BigDecimal.valueOf(double)`。
> - `divide` 在除不尽时（如 `1 / 3`）会抛出 `ArithmeticException: Non-terminating decimal expansion`，此时必须指定精度和舍入模式，例如 `b1.divide(b2, 2, RoundingMode.HALF_UP)`。

使用 `BigDecimal(double val)` 构造函数时仍会存在精度丢失问题，建议使用 `BigDecimal(String val)`。这就需要先把 `double` 转换为字符串，再作为 `BigDecimal(String val)` 构造函数的参数。转换为 `BigDecimal` 对象之后再进行加减乘除操作，这样精度就不会出现问题了。

*实例代码：*

```java
import java.math.BigDecimal;

public class Test {
    public static void main(String[] args) {

        double d1 = 0.06;
        double d2 = 0.01;
        BigDecimal b1 = new BigDecimal(Double.toString(d1));
        BigDecimal b2 = new BigDecimal(Double.toString(d2));
        System.out.println(b1.add(b2).doubleValue()); // 0.07

        double d3 = 1.0;
        double d4 = 0.42;
        BigDecimal b3 = new BigDecimal(Double.toString(d3));
        BigDecimal b4 = new BigDecimal(Double.toString(d4));
        System.out.println(b3.subtract(b4).doubleValue()); // 0.58

        double d5 = 4.015;
        double d6 = 100;
        BigDecimal b5 = new BigDecimal(Double.toString(d5));
        BigDecimal b6 = new BigDecimal(Double.toString(d6));
        System.out.println(b5.multiply(b6).doubleValue()); // 401.5

        double d7 = 303.1;
        double d8 = 1000;
        BigDecimal b7 = new BigDecimal(Double.toString(d7));
        BigDecimal b8 = new BigDecimal(Double.toString(d8));
        System.out.println(b7.divide(b8).doubleValue()); // 0.3031
    }
}
```

## 相关笔记

- [[Java基础笔记]] —— 数据类型与字面量基础
- [[Java面向对象编程]] —— BigDecimal 是对象，依赖面向对象知识
