# Java中double类型操作精度丢失问题

- 原因：*浮点数无法使用二进制进行精确表示*，计算机的CPU表示浮点数由两部分组成：指数和尾数，这样的表示方法一般会失去一定的精确度，有些浮点数也会产生一定的误差。
---
# BigDecimal类介绍

- 在处理金额交易和科学计算上，我们需要精密的结果

此时，我们一般采用*java.math.BigDecimal*类来进行精密计算

	使用步骤
1. 用*float*或者*double*变量构建BigDecimal对象。通常使用BigDecimal的构造方法或者静态方法的<font color="red"><ins>vlaueOf()</ins></font>方法把基本类型的变量构建成BigDecimal对象
2. 通过调用BigDecimal的加减乘除等对应的方法进行算术运算
3. 把BigDecimal对象转换成float,double,int等类型
---

	BigDecimal类的构造函数
```java
BigDecimal(int var)  //创建一个具有参数所指定整数值的对象。
BigDecimal(double var) //创建一个具有参数所指定双精度值的对象。
BigDecimal(long var)  //创建一个具有参数所指定长整数值的对象。
BigDecimal(String var) //创建一个具有参数所指定以字符串表示的数值的对象。
```

	BigDecimal 类的加，减，乘，除等相应的方法：

```java
BigDecimal add(BigDecimal augend)  //加法运算
BigDecimal subtract(BigDecimal subtrahend) //减法运算
BigDecimal multiply(BigDecimal multiplicand) //乘法运算
BigDecimal divide(BigDecimal divisor) //除法运算
```

---

> :memo: **注意：**
- BigDecimal(double var) 构造方法的结果有一定的不可预知性。有人可能认为在 Java 中写入 new BigDecimal(0.1) 所创建的 BigDecimal 正好等于 0.1，但是它实际上等于0.1000000000000000055511151231257827021181583404541015625。这是因为 0.1 无法准确地表示为 double（或者说对于该情况，不能表示为任何有限长度的二进制小数）。这样，传入到构造方法的值不会正好等于 0.1（虽然表面上等于该值）。

- BigDecimal(String var) 的 String 参数构造方法是完全可预知的：写入 new BigDecimal("0.1") 将创建一个 BigDecimal，它正好等于预期的 0.1。因此，比较而言，通常建议优先使用 String 构造方法。
---

	使用 BigDecimal(double val) 构造函数时仍会存在精度丢失问题，建议使用 BigDecimal(String val)。这就需要先把 double 转换为字符串然后在作为BigDecimal(String val) 构造函数的参数。转换为 BigDecimal 对象之后再进行加减乘除操作，这样精度就不会出现问题了。

*实例代码：*

```java
import java.math.BigDecimal

public class Test{
	public static void main(String [] args){
	
		double d1 = 0.06;
        double d2 = 0.01;
        BigDecimal b1 = new BigDecimal(Double.toString(d1));
        BigDecimal b2 = new BigDecimal(Double.toString(d2));
        System.out.println(b1.add(b2).doubleValue());
        
        double d3 = 1.0;
        double d4 = 0.42;
        BigDecimal b3 = new BigDecimal(Double.toString(d3));
        BigDecimal b4 = new BigDecimal(Double.toString(d4));
        System.out.println(b3.subtract(b4).doubleValue());
        
        double d5 = 4.015;
        double d6 = 100;
        BigDecimal b5 = new BigDecimal(Double.toString(d5));
        BigDecimal b6 = new BigDecimal(Double.toString(d6));
        System.out.println(b5.multiply(b6).doubleValue());
        
        double d7 = 303.1;
        double d8 = 1000;
        BigDecimal b7 = new BigDecimal(Double.toString(d7));
        BigDecimal b8 = new BigDecimal(Double.toString(d8));
        System.out.println(b7.divide(b8).doubleValue());
	
	}
}
```


