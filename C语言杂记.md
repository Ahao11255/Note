# C语言杂记

## 变量

### 局部变量和全局变量

在函数内定义的的是局部变量，在函数外定义的是全局变量

当局部变量和全局变量名字相同的情况下，局部变量优先

不建议局部变量和全局变量同名；

#### 作用域

是程序设计的概念，通常来说，一段代码中所用到的名字并不总是有效/可用的

而限定这个名字的可用性的代码范围就是这个名字的作用域；

1.局部变量的作用域是变量所在的局部范围；

2.全局变量的作用域是整个工程；

例：

```c
int main()
{
	{
		int a=10;
		printf("a=%d\n",a);
	}
    //a为局部变量，作用域为上方大括号内
    //故下面的printf无法运行
	printf("a=%d\n",a);
}
```



### 初始化

变量在创建时应初始化为一个值，否则会被赋予一个随机值；

## 函数

### scanf函数和scanf_s函数

scanf_s函数是VS编译器自己提供的函数，非标准C函数，只有在VS环境下才能运行

跨平台用scanf函数；

## 关键字

### extern

**此变量/函数是在别处定义的，要在此处引用**

如果在定义点之前的函数想引用该全局变量，则应该在引用之前用关键字 extern 对该变量作“外部变量声明”，表示该变量是一个已经定义的外部变量。有了此声明，就可以从“声明”处起，合法地使用该外部变量。

例：

```c
#include <stdio.h>
int max(int x,int y);
int main(void)
{
    int result;
    /*外部变量声明*/
    extern int g_X;
    extern int g_Y;
    result = max(g_X,g_Y);
    printf("the max value is %d\n",result);
    return 0;
}
/*定义两个全局变量*/
int g_X = 10;
int g_Y = 20;
int max(int x, int y)
{
    return (x>y ? x : y);
}
```

如果整个工程由多个源文件组成，在一个源文件中想引用另外一个源文件中已经定义的外部变量，同样只需在引用变量的文件中用 extern 关键字加以声明即可。

例：

```c
/****max.c****/
#include <stdio.h>
/*外部变量声明*/
extern int g_X ;
extern int g_Y ;
int max()
{
    return (g_X > g_Y ? g_X : g_Y);
}

/***main.c****/
#include <stdio.h>
/*定义两个全局变量*/
int g_X=10;
int g_Y=20;
int max();
int main(void)
{
    int result;
    result = max();
    printf("the max value is %d\n",result);
    return 0;
}
```

不过，需要特别注意的是，由于用 extern 引用外部变量，可以在引用的模块内修改其变量的值，因此，如果有多个文件同时要对应用的变量进行操作，而且可能会修改该变量，那就会影响其他模块的使用。因此，我们要慎重使用。

## 环境

### new c++ file.cpp

在VS的安装路径下有new c++file .cpp文件

在VS工程中创建新的.c/.cpp文件的时候，都是拷贝这个文件;

