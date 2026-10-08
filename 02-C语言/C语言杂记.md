---
title: C 语言杂记
tags:
  - C语言
  - 语言基础
aliases:
  - C语言
  - C语言笔记
---

# C 语言杂记

## 变量

### 局部变量和全局变量

在函数**内**定义的是局部变量，在函数**外**定义的是全局变量。

当局部变量和全局变量名字相同时，**局部变量优先**。

不建议局部变量和全局变量同名。

#### 作用域

作用域是程序设计中的概念：一段代码里用到的名字并不总是有效可用的，限定这个名字可用范围的代码区间，就是这个名字的作用域。

1. 局部变量的作用域是它所在的那一段局部范围（通常是一对 `{}` 之间）；
2. 全局变量的作用域是整个工程（可以通过 `extern` 在其他源文件中引用）。

例：

```c
#include <stdio.h>

int main()
{
    {
        int a = 10;
        printf("a=%d\n", a);
    }
    // a 为局部变量，作用域为上方那对大括号之内
    // 故下面的 printf 无法通过编译：a 未声明（identifier "a" is undefined）
    printf("a=%d\n", a);
}
```

### 初始化

变量在创建时应当初始化为一个值；否则它的值是**不确定**的（局部变量在栈上，通常是内存中的残留随机值）。

## 函数

### scanf 函数和 scanf_s 函数

`scanf_s` 是微软在 VS 中提供的「安全版本」输入函数（对应 C11 附录 K 的可选边界检查接口），**不属于标准 C 的必备部分**，只有在 VS 环境下才能使用。

需要跨平台时使用标准库的 `scanf` 函数。

## 关键字

### extern

**表示此变量/函数是在别处定义的，要在此处引用。**

如果在定义点之前的函数想引用某个全局变量，则应该在引用之前用关键字 `extern` 对该变量作「外部变量声明」，表示该变量是一个已经定义的外部变量。有了此声明，就可以从「声明」处起，合法地使用该外部变量。

例：

```c
#include <stdio.h>

int max(int x, int y);

int main(void)
{
    int result;
    /*外部变量声明*/
    extern int g_X;
    extern int g_Y;
    result = max(g_X, g_Y);
    printf("the max value is %d\n", result);
    return 0;
}

/*定义两个全局变量*/
int g_X = 10;
int g_Y = 20;

int max(int x, int y)
{
    return (x > y ? x : y);
}
```

如果整个工程由多个源文件组成，在一个源文件中想引用另外一个源文件中已经定义的外部变量，同样只需在引用变量的文件中用 `extern` 关键字加以声明即可。

例：

```c
/**** max.c ****/
#include <stdio.h>

/*外部变量声明*/
extern int g_X;
extern int g_Y;

int max()
{
    return (g_X > g_Y ? g_X : g_Y);
}

/**** main.c ****/
#include <stdio.h>

/*定义两个全局变量*/
int g_X = 10;
int g_Y = 20;

int max();

int main(void)
{
    int result;
    result = max();
    printf("the max value is %d\n", result);
    return 0;
}
```

不过需要特别注意的是：由于用 `extern` 引用外部变量后，可以在引用的模块内修改其变量的值，因此如果有多个文件同时要对引用的变量进行操作，而且可能会修改该变量，那就会影响其他模块的使用。因此，我们要慎重使用。

## 环境

### new c++ file.cpp

在 VS 的安装路径下有一个 `new c++ file.cpp` 模板文件。

在 VS 工程中创建新的 `.c` / `.cpp` 文件时，都是拷贝这个文件生成的。

## 相关笔记

- [[原码反码补码]] —— 变量在内存中的二进制表示
- [[Java基础笔记]] —— 局部/成员变量作用域的对照阅读
