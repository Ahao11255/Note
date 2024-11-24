

# JUnit单元测试

## 单元测试

针对Java中最小单元（方法）的测试

## 用main()方法测试的缺点

- 只有一个main()方法，不能把测试代码分离开
- 没有打印出测试结果和预期结果

## 单元测试的好处

- 确保单个方法运行正常
- 如果修改了方法代码，只需确保其对应的单元测试通过
- 测试代码本身就可以作为示例代码
- 可以自动化运行所用测试并获得报告

## JUnit特点

- 使用断言(Assertion)测试期望结果
- 可以方便地组织和运行测试
- 可以方便地查看测试结果
- 常用IDE都集成了JUnit
- 可以方便地集成到Maven

## JUnit框架导入

#### IntelliJ IDEA 安装 Junit

1. 下载 **junit-4.12.jar** 文件：https://github.com/junit-team/junit4/releases
2. 打开 IntelliJ IDEA ，菜单栏：**File菜单 –> Porject Structure 选项 –> Dependencies 标签 –> 点击 “+” 号 –> Library… –> Java 。** 选择下载的 **junit-4.12.jar** 进行添加

#### Eclipse使用JUnit

1. 自行导入jar包

   [[自行导入jar包.png]]
   
2. 使用EclipseSDK环境

   [[使用eclipseSDK环境1.png]]

   [[使用eclipseSDK环境2.png]]

   [[使用eclipseSDK环境3.png]]

## JUnit注解

| 注解          | 说明                                                           |
| :---------- | :----------------------------------------------------------- |
| @Test：      | 标识一条测试用例。 (A) (expected=XXEception.class)  (B) (timeout=xxx) |
| @Ignore:    | 忽略的测试用例。                                                     |
| @Before:    | 每一个测试方法之前运行。                                                 |
| @After :    | 每一个测试方法之后运行。                                                 |
| @BefreClass | 所有测试开始之前运行。                                                  |
| @AfterClass | 所有测试结果之后运行。                                                  |

## JUnit——assert断言

JUnit 中常用断言方法的总结与说明：

### 通用参数

- **`message`**: 可选参数，指定错误信息，便于调试。
- **`expected`**: 期望值，由用户定义。
- **`actual`**: 被测代码实际返回值。
- **`condition/object`**: 用于布尔验证或检查的变量。

------

### 断言方法

1. **`assertArrayEquals(String message, Object[] expecteds, Object[] actuals)`**

   - 比较两个数组是否相等（长度相同且每个元素都相等）。

   - 示例：

     ```java
     assertArrayEquals("数组不相等", new int[]{1, 2, 3}, new int[]{1, 2, 3});
     ```
   
2. **`assertEquals(String message, Object expected, Object actual)`**

   - 验证两个对象的值是否相等（使用 `equals()` 方法）。

   - 示例：

     ```Java
     assertEquals("值不相等", "Hello", "Hello");
     ```
   
3. **`assertSame(String message, Object expected, Object actual)`**

   - 验证两个对象是否引用同一个内存地址（使用 `==`）。

   - 示例：

     ```java
     String str = "Java";
     assertSame("引用不同", str, str);
     ```

4. **`assertNotSame(String message, Object expected, Object actual)`**

   - 验证两个对象是否不是同一个引用（使用 `!=`）。

   - 示例：

     ```Java
     assertNotSame("引用相同", new String("Java"), new String("Java"));
     ```
   
5. **`assertTrue(String message, boolean condition)`**

   - 验证条件是否为 `true`，为 `true` 则通过。

   - 示例：

     ```Java
     assertTrue("条件不为真", 5 > 3);
     ```
   
6. **`assertFalse(String message, boolean condition)`**

   - 验证条件是否为 `false`，为 `false` 则通过。

   - 示例：

     ```java
     assertFalse("条件不为假", 5 < 3);
     ```
   
7. **`assertNull(String message, Object object)`**

   - 验证对象是否为 `null`。

   - 示例：

     ```Java
     assertNull("对象不为null", null);
     ```
   
8. **`assertNotNull(String message, Object object)`**

   - 验证对象是否不是 `null`。

   - 示例：

     ```Java
     assertNotNull("对象为null", "Not Null");
     ```

------

### 使用场景总结

- **数组比较**: `assertArrayEquals`
- **值比较**: `assertEquals`
- **引用比较**: `assertSame` / `assertNotSame`

- **布尔条件验证**: `assertTrue` / `assertFalse`
- **`null` 检查**: `assertNull` / `assertNotNull`

## JUnit ——assertThat断言

### Hamcrest包

JUnit4结合Hamcrest提供了一个全新的断言语法--assertThat。程序员使用assertThat的一个断言语句并且结合Hamcrest提供的匹配符，就可以表达出全部的测试思想，这些匹配符更接近自然语言，可读性高，更加灵活

**下载Hamcrest包**

下载hamcrest-library.jar、hamcrest-core.jar包

URL： https://hamcrest.org/JavaHamcrest/distributables

#### 导入Hamcrest包

[[自行导入jar包.png]]

在测试代码段加入：

```Java
import static org.hamcrest.MatcherAssert.assertThat;
import static org.hamcrest.Matchers.*;
```

### 一般匹配符

.**allOf**

- **作用**：要求所有条件均成立，测试才通过，相当于“与”（&&）。

- 示例：

  ```java
  assertThat(testedNumber, allOf(greaterThan(4), lessThan(10)));
  ```

 **anyOf**

- **作用**：只要任意一个条件成立，测试通过，相当于“或”（||）。

- 示例：

  ```java
  assertThat(testedNumber, anyOf(greaterThan(10), lessThan(4)));
  ```

**anything**

- **作用**：永远为 `true`，无论条件如何。

- 示例：

  ```java
  assertThat(testedNumber, anything());
  ```

 **is**

- **作用**：测试对象是否等于给定的值。

- 示例：

  ```java
  assertThat(testedString, is("developerWorks"));
  ```

**not**

- **作用**：测试对象是否不等于给定的值，与 `is` 匹配符相反。

- 示例：

  ```java
  assertThat(testedString, not("developerWorks"));
  ```

### 常用字符串匹配符

**1. `containsString`**

- **作用**：检查字符串是否包含指定子字符串。

- 示例代码：

  ```java
  assertThat(testedString, containsString("developerWorks"));
  ```

------

**2. `endsWith`**

- **作用**：检查字符串是否以指定子字符串结尾。

- 示例代码：

  ```java
  assertThat(testedString, endsWith("developerWorks"));
  ```

------

**3. `startsWith`**

- **作用**：检查字符串是否以指定子字符串开头。

- 示例代码：

  ```Java
  assertThat(testedString, startsWith("developerWorks"));
  ```

------

**4. `equalTo`**

- 作用：检查两个值是否相等（支持数值、字符串或对象）。

  - 相当于 Java 中 `Object.equals` 方法。

- 示例代码：

  ```java
  assertThat(testedValue, equalTo(expectedValue));
  ```

------

**5. `equalToIgnoringCase`**

- **作用**：检查字符串在忽略大小写的情况下是否相等。

- 示例代码：

  ```Java
  assertThat(testedString, equalToIgnoringCase("developerWorks"));
  ```

------

**6. `equalToIgnoringWhiteSpace`**

- **作用**：检查字符串在忽略头尾空格的情况下是否相等（**中间的空格不被忽略**）。

- 示例代码：

  ```java
  assertThat(testedString, equalToIgnoringWhiteSpace("developerWorks"));
  ```

------

**使用场景总结**：

- **`containsString`**：子字符串匹配。
- **`startsWith` 和 `endsWith`**：检测开头或结尾匹配。
- **`equalTo`**：精准匹配。
- **`equalToIgnoringCase` 和 `equalToIgnoringWhiteSpace`**：更灵活的字符串匹配。

### 数值相关匹配符

**1. `closeTo`**

- **作用**：检查浮点型数值是否在指定范围内。

- 示例代码：

  ```java
  assertThat(testedDouble, closeTo(10.0, 0.5));
  ```

- **解释**：若 `testedDouble` 在 `10.0 ± 0.5` 范围内，测试通过。

------

**2. `greaterThan`**

- **作用**：检查数值是否大于指定值。

- 示例代码：

  ```Java
  assertThat(testedNumber, greaterThan(10.0));
  ```

- **解释**：若 `testedNumber > 10.0`，测试通过。

------

**3. `lessThan`**

- **作用**：检查数值是否小于指定值。

- 示例代码：

  ```java
  assertThat(testedNumber, lessThan(8.0));
  ```

- **解释**：若 `testedNumber < 8.0`，测试通过。

------

**4. `greaterThanOrEqualTo`**

- **作用**：检查数值是否大于等于指定值。

- 示例代码 ：

  ```java
  assertThat(testedNumber, greaterThanOrEqualTo(10.0));
  ```

- **解释**：若 `testedNumber >= 10.0`，测试通过。

------

**5. `lessThanOrEqualTo`**

- **作用**：检查数值是否小于等于指定值。

- 示例代码：

  ```Java
  assertThat(testedNumber, lessThanOrEqualTo(10.0));
  ```

- **解释**：若 `testedNumber <= 10.0`，测试通过。

------

**使用场景总结**：

- **范围匹配**：使用 `closeTo`。

- 比较大小
  - 使用 `greaterThan` 和 `lessThan` 进行严格比较。
  - 使用 `greaterThanOrEqualTo` 和 `lessThanOrEqualTo` 进行非严格比较。

### 集合相关匹配符

前置知识  列表与映射 [[Java笔记#列表和映射]]

**1. `hasItemInArray`**

- **作用**：检查数组中是否包含指定元素。

- 示例代码：

  ```Java
  assertThat(Array, hasItemInArray("element"));
  ```

- **解释**：若 `Array` 包含 `"element"`，测试通过。

------

**2. `hasItem`**

- **作用**：检查列表对象中是否包含指定元素。

- 示例代码 ：

  ```Java
  assertThat(listObject, hasItem("element"));
  ```

- **解释**：若 `listObject` 包含 `"element"`，测试通过。

------

**3. `hasItems`**

- **作用**：检查列表对象中是否至少包含多个指定元素。

- 示例代码：

  ```Java
  assertThat(listObject, hasItems("element1", "element2"));
  ```

- **解释**：若 `listObject` 至少包含 `"element1"` 和 `"element2"`，测试通过。

------

**4. `containsInAnyOrder`**

- **作用**：检查列表对象是否只包含指定元素，且顺序无关。

- 示例代码：

  ```Java
  assertThat(listObject, containsInAnyOrder("element1", "element2", "element3"));
  ```

- **解释**：若 `listObject` 包含且仅包含 `"element1"`, `"element2"`, `"element3"`（顺序无关），测试通过。

------

**5. `hasEntry`**

- **作用**：检查 Map 对象中是否包含指定的键值对。

- 示例代码：

  ```Java
  assertThat(mapObject, hasEntry("key", "value"));
  ```

- **解释**：若 `mapObject` 包含键 `"key"` 且对应值为 `"value"`，测试通过。

------

**6. `hasKey`**

- **作用**：检查 Map 对象中是否包含指定的键。

- 示例代码：

  ```Java
  assertThat(mapObject, hasKey("key"));
  ```

- **解释**：若 `mapObject` 包含键 `"key"`，测试通过。

------

**7. `hasValue`**

- **作用**：检查 Map 对象中是否包含指定的值。

- 示例代码：

  ```Java
  assertThat(mapObject, hasValue("value"));
  ```

- **解释**：若 `mapObject` 包含值 `"value"`，测试通过。

------

**使用场景总结**：

- **数组匹配**：使用 `hasItemInArray`。

- 列表对象匹配：

  - **单元素**：`hasItem`
  - **多元素**：`hasItems`
  - **全部匹配（无顺序要求）**：`containsInAnyOrder`

- Map 匹配：

  - **键值对**：`hasEntry`
  - **仅键**：`hasKey`
  - **仅值**：`hasValue`

## JUnit限时和异常测试

### 超时控制：`@Test(timeout)`

在测试一些逻辑复杂、嵌套较深的程序时，可能会因为代码问题（如死循环）导致测试无法结束。JUnit 提供了超时参数 `timeout`，可用于指定测试方法的最长允许执行时间。

**使用方法**

- **语法**：`@Test(timeout = [时间毫秒数])`

- 作用：

  - 如果测试运行时间超过设定时间，系统会强制终止方法并判定测试失败。
  - 系统会报告此测试失败的原因是 **超时**。

**示例代码**

```Java
@Test(timeout = 1000) // 1000 毫秒内必须完成
public void testTimeout() {
    while (true) {
        // 模拟死循环
    }
}
```

- **说明**：若该测试方法在 1000 毫秒内未完成，则系统强制终止，并报超时错误。

------

###  异常处理测试：`@Test(expected)`

在开发过程中，**异常捕获与处理** 是代码健壮性的重要部分。在单元测试中，除了验证正常流程，还需要测试异常场景，例如：

- 确保方法在特定条件下正确抛出异常。
- 验证程序是否在错误条件下能处理异常。

**使用方法**

- **语法**：`@Test(expected = [异常类型].class)`

- 作用：

  - 定义测试方法期望抛出的异常类型。
  - 如果方法执行时抛出了指定异常，测试通过。
  - 如果未抛出异常或抛出了其他类型异常，测试失败。

**示例代码**

```java
@Test(expected = IllegalArgumentException.class)
public void testException() {
    throw new IllegalArgumentException("Test Exception");
}
```

**场景说明**

1. **测试通过**：方法抛出了 `IllegalArgumentException` 异常。

2. 测试失败：

   - 方法未抛出任何异常。
   - 方法抛出了不同类型的异常（如 `NullPointerException`）。

------

### **总结**

1. **`timeout` 使用场景**：
   - 防止程序进入死循环或运行时间过长。
   - 提高测试效率，避免被单个测试阻塞。
2. **`expected` 使用场景**：
   - 验证异常逻辑是否符合预期。
   - 检查异常是否被正确捕获或抛出。

## **参数化测试**

------

### 步骤

**1. 使用 `@RunWith(Parameterized.class)` 注解测试类**

`@RunWith` 注解指定了运行测试的特殊运行器。`Parameterized` 是一个运行器，它可以处理参数化的测试类。通过这个注解，JUnit 会自动为每组测试数据执行测试方法。

```java
@RunWith(Parameterized.class)
public class RegisterTest {
    // 其他代码
}
```

**2. 声明变量以保存测试数据**

在测试类中，声明变量来保存每个测试的数据（例如用户名、密码、期望结果）。这些变量将在每次测试执行时由参数化测试框架自动赋值。

```Java
private String username;
private String password;
private boolean expected;
```

**3. 创建一个 `@Parameters` 注解的公共静态方法，返回测试数据集合**

`@Parameters` 注解的方法返回一个集合（`Collection`），其中每一项都是一组测试数据。在返回的集合中，每一组数据将会对应测试类的构造函数中的参数。这里使用了一个二维数组，每行代表一组测试数据，数据的顺序应该与构造函数的参数顺序一致。

```Java
@Parameters
public static Collection userData() {
    return Arrays.asList(new Object[][]{
        {"Admin", "123456", true},
        {"student", "123456", false},
        {"Admin", "123", false}
    });
}
```

**4. 声明构造函数，接受测试数据**

构造函数的参数对应于上一步返回的测试数据，每次测试运行时，JUnit 会自动将一组数据传递给构造函数。

```Java
public RegisterTest(String username, String password, boolean expected) {
    this.username = username;
    this.password = password;
    this.expected = expected;
}
```

**5. 编写测试代码，使用初始化的参数进行测试**

在测试方法中，我们使用构造函数传递的参数进行实际的测试。在这个例子中，使用 `assertEquals` 来验证 `LogOn` 方法的返回值是否与期望值一致。

```Java
@Test
public void testLogOn() {
    assertEquals(expected, register.LogOn(username, password));
}
```

### **完整示例代码**

```Java
import static org.junit.Assert.assertEquals;
import java.util.Arrays;
import java.util.Collection;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.junit.runners.Parameterized;
import org.junit.runners.Parameterized.Parameters;

@RunWith(Parameterized.class)
public class RegisterTest {
    private Register register = new Register();
    private String username;
    private String password;
    private boolean expected;

    // 测试数据集合，方法名可以随意定义，但必须用@Parameters标注
    @Parameters
    public static Collection userData() {
        return Arrays.asList(new Object[][]{
            {"Admin", "123456", true},
            {"student", "123456", false},
            {"Admin", "123", false}
        });
    }

    // 构造函数，参数赋值顺序与测试数据集合一致
    public RegisterTest(String username, String password, boolean expected) {
        this.username = username;
        this.password = password;
        this.expected = expected;
    }

    // 编写测试代码
    @Test
    public void testLogOn() {
        assertEquals(expected, register.LogOn(username, password));
    }
}
```

------

### **总结**

1. **`@RunWith(Parameterized.class)`**：指定测试类使用参数化运行器。
2. **`@Parameters`**：提供一个公共静态方法，返回一个集合，集合中包含测试数据。
3. **构造函数**：接收测试数据，并赋值给类的实例变量。
4. **测试方法**：使用构造函数传递的测试数据来进行实际测试。

## **Fred和error**

-----

在单元测试中，`Failure` 和 `Error` 都是测试执行中的常见问题，它们代表了不同类型的问题，具体的区分如下：

### **Failure (测试失败)**

- **定义**：`Failure` 是指 **预期结果与实际结果不一致**，通常是由于代码的逻辑错误导致的。测试方法运行时，测试的结果与期望的结果不匹配，从而触发断言失败，导致测试报告中显示为失败。
  
    **可能的原因**：
    
    - 代码实现存在逻辑错误，导致返回结果不符合预期。
    - 预期的测试结果（例如通过 `assertXXX()` 断言）设置错误。
    
    示例：

```Java
assertEquals("Expected value", actualValue); 
// 如果 actualValue 和 "Expected value" 不相等，则会抛出 Failure
```

- **处理方式**：
  
    - 检查代码中的实现，确保代码符合功能要求。
    - 重新评估测试数据和预期结果，确保测试条件正确。

---

### **Error (测试错误)**

- **定义**：`Error` 是指 **测试程序本身出错**，通常是由于 **代码异常** 或 **程序中的运行时错误** 引起的。这些错误通常发生在测试方法开始运行之前，或者在执行测试逻辑过程中发生异常（例如 `NullPointerException`、`ArrayIndexOutOfBoundsException` 等），导致测试未能正常进行。
  
    **可能的原因**：
    
    - 测试方法本身有错误，导致测试程序崩溃。
    - 代码中的异常未被捕获或处理。
    - 错误的输入类型或不符合预期的运行环境。
    
    **示例**：

```Java
int[] numbers = new int[5];
System.out.println(numbers[10]); 
// 触发 ArrayIndexOutOfBoundsException，导致 Error
```

- **处理方式**：
  
    - 检查测试方法中的代码，确保输入参数和数据有效且符合预期。
    - 处理异常情况，确保程序的健壮性（例如，捕获异常，提供合理的错误处理）。

---

### **总结：**

- **Failure**：测试的行为与预期不符，通常是由于代码的逻辑问题。需要通过调试或查看代码，找出逻辑错误。
- **Error**：测试程序本身出现了异常，导致测试无法执行。需要查看程序代码，处理可能的异常和错误。

## **TestRunner**

-----

在JUnit中，`TestRunner` 是负责执行测试用例的核心组件，它根据不同的需求和场景选择不同的测试运行器来执行代码。JUnit提供了多种运行器（`TestRunner`），每个运行器有其特定的功能，帮助开发者更高效地执行和组织测试。以下是一些常用的JUnit测试运行器和它们的功能说明：

### **JUnit默认Runner：`BlockJUnit4ClassRunner`**

- **功能**：`BlockJUnit4ClassRunner` 是JUnit 4的默认运行器，自动运行标注了 `@Test` 注解的方法。

- **使用**：如果没有显式指定 `@RunWith` 注解，JUnit默认使用该运行器。

  **示例**：

  ```Java
  import static org.junit.Assert.*;
  
  import org.junit.Test;
  
  public class Calculator01MainTest2 {
      private static Calculator01Main calculator = new Calculator01Main();
  
      @Test
      public void testAdd() {
          calculator.add(3, 4);
          assertEquals(7, calculator.getResult());
      }
  
      @Test
      public void testSubstract() {
          calculator.substract(10, 3);
          assertEquals(7, calculator.getResult());
      }
  }
  ```

  如果你需要明确指定 `BlockJUnit4ClassRunner`，可以这样做：

  ```java
  @RunWith(BlockJUnit4ClassRunner.class)
  public class Calculator01MainTest2 {
      // test methods
  }
  ```

### **参数化测试Runner：`Parameterized`**

- **功能**：`Parameterized` 允许你运行相同的测试方法，只是每次用不同的输入数据进行测试。这种方式非常适用于需要用不同参数组合测试同一个功能的方法。

  **步骤**：

  1. 使用 `@RunWith(Parameterized.class)` 注解来指定使用参数化测试运行器。
  2. 定义一个静态方法用 `@Parameters` 注解，返回测试数据集合。
  3. 定义测试类的构造函数，接受每个参数。

  **示例**：

  ```java
  @RunWith(Parameterized.class)
  public class RegisterTest {
      private String username;
      private String password;
      private boolean expected;
  
      @Parameters
      public static Collection userData() {
          return Arrays.asList(new Object[][] {
              {"Admin", "123456", true},
              {"student", "123456", false},
              {"Admin", "123", false}
          });
      }
  
      public RegisterTest(String username, String password, boolean expected) {
          this.username = username;
          this.password = password;
          this.expected = expected;
      }
  
      @Test
      public void testLogOn() {
          assertEquals(expected, register.LogOn(username, password));
      }
  }
  ```

### **测试套件Runner：`Suite`**

- **功能**：`Suite` 允许你将多个测试类组合成一个测试套件，一起执行所有测试方法。适用于大规模的集成测试和验证多个功能的场景。

  **示例**：

  ```java
  @RunWith(Suite.class)
  @SuiteClasses({ TestClass1.class, TestClass2.class })
  public class AllTests {}
  ```

  这将会执行 `TestClass1` 和 `TestClass2` 中的所有测试方法。

### **分类执行Runner：`Categories`**

- **功能**：`Categories` 允许你根据不同的类别（通过 `@Category` 注解）来执行特定的测试方法。可以使用 `@IncludeCategory` 或 `@ExcludeCategory` 来分别包含或排除某些类别的测试方法。

  **示例**：

  ```java
  public interface ClassifyOTests {}
  public interface ClassifyTTests {}
  
  @RunWith(Categories.class)
  @IncludeCategory(ClassifyOTests.class)
  @SuiteClasses({ AssertionsTest.class, AssertThatTest.class })
  public class AllTests {}
  ```

  这将只运行标注了 `@Category(ClassifyOTests.class)` 的方法。

  另一种情况是排除特定类别的测试：

  ```java
  @RunWith(Categories.class)
  @ExcludeCategory(ClassifyTTests.class)
  @SuiteClasses({ AssertionsTest.class, AssertThatTest.class })
  public class AllTests {}
  ```

  这将排除标注了 `@Category(ClassifyTTests.class)` 的方法，执行其它测试方法。

------

### **JUnit提供的主要测试运行器：**

1. **JUnit38ClassRunner**：用于兼容JUnit3.8的测试运行器。
2. **BlockJUnit4ClassRunner**：JUnit4的默认测试运行器，适用于绝大多数的JUnit4测试。
3. **Parameterized**：支持参数化测试，允许传入不同参数来运行同一组测试。
4. **Suite**：将多个测试类组合在一起，批量运行。
5. **Categories**：基于类别进行测试，可以选择执行某些类别的测试或排除某些类别的测试。

------

### **总结**

JUnit中的测试运行器（TestRunner）是执行测试用例的关键工具。通过 `@RunWith` 注解，你可以选择不同的运行器来满足不同的测试需求。例如，`BlockJUnit4ClassRunner` 是默认运行器，适用于大多数场景；`Parameterized` 适用于参数化测试；`Suite` 和 `Categories` 适用于测试组织和分类执行的需求。


## **测试优先级**

-----

在默认情况下，JUnit会以一种不确定的顺序执行测试方法。这种随机化行为可以帮助开发者检测代码中的潜在问题，例如测试之间的依赖关系或者共享状态。如果测试对顺序有要求（例如数据库操作或依赖测试的前后结果），JUnit提供了 `@FixMethodOrder` 注解来明确控制测试方法的执行顺序。

------

### **@FixMethodOrder 使用说明**

`@FixMethodOrder` 提供了三种排序方式，通过指定 `MethodSorters` 来控制执行顺序：

1. **`MethodSorters.JVM`**
   - 按照JVM返回的方法顺序执行，这个顺序通常与代码中定义的顺序一致。
   - 但是，不保证在不同的JVM实现中方法顺序相同。
2. **`MethodSorters.DEFAULT`**
   - JUnit默认的执行顺序（通常是随机顺序）。
   - 不建议在测试依赖顺序的场景中使用。
3. **`MethodSorters.NAME_ASCENDING`**
   - 按照方法名的字母顺序执行。
   - 适用于需要严格控制执行顺序的场景，推荐使用这种方式。

------

### **示例代码**

#### ** 默认执行顺序**

以下代码未指定 `@FixMethodOrder`，测试方法可能会以随机顺序执行。

```java
import static org.junit.Assert.*;
import org.junit.Before;
import org.junit.Test;

public class CalculatorTest {
    private static Calculator calculator = new Calculator();

    @Before
    public void setUp() throws Exception {
        calculator.clear();
    }

    @Test
    public void testAdd() {
        calculator.add(3, 4);
        assertEquals(7, calculator.getResult());
    }

    @Test
    public void testSubstract() {
        calculator.substract(10, 3);
        assertEquals(7, calculator.getResult());
    }

    @Test
    public void testMultiply() {
        calculator.multiply(5, 5);
        assertEquals(25, calculator.getResult());
    }

    @Test
    public void testDivide() {
        calculator.divide(8, 2);
        assertEquals(4, calculator.getResult());
    }
}
```

执行结果中，方法的顺序可能会是随机的，比如：

- `testMultiply`
- `testSubstract`
- `testAdd`
- `testDivide`

------

#### **指定执行顺序**

通过添加 `@FixMethodOrder` 注解，指定按方法名的字母顺序执行。

```java
import static org.junit.Assert.*;
import org.junit.Before;
import org.junit.FixMethodOrder;
import org.junit.Test;
import org.junit.runners.MethodSorters;

@FixMethodOrder(MethodSorters.NAME_ASCENDING) // 按字母顺序执行
public class CalculatorTest {
    private static Calculator calculator = new Calculator();

    @Before
    public void setUp() throws Exception {
        calculator.clear();
    }

    @Test
    public void testAdd() {
        calculator.add(3, 4);
        assertEquals(7, calculator.getResult());
    }

    @Test
    public void testDivide() {
        calculator.divide(8, 2);
        assertEquals(4, calculator.getResult());
    }

    @Test
    public void testMultiply() {
        calculator.multiply(5, 5);
        assertEquals(25, calculator.getResult());
    }

    @Test
    public void testSubstract() {
        calculator.substract(10, 3);
        assertEquals(7, calculator.getResult());
    }
}
```

执行顺序会严格按照方法名的字母顺序：

1. `testAdd`
2. `testDivide`
3. `testMultiply`
4. `testSubstract`

------

### **控制顺序的最佳实践**

- **使用 `MethodSorters.NAME_ASCENDING`**：
  - 测试方法可以根据功能的重要性或依赖性进行命名，例如 `test01Setup`、`test02Insert`、`test03Query` 等。
- **避免测试之间的依赖**：
  - 如果测试用例必须按照顺序执行，可能意味着它们之间存在某种依赖关系。应尽量设计独立的测试用例，使用 `@Before` 和 `@After` 来清理测试环境。
- **对于复杂的依赖逻辑**：
  - 考虑使用 `@RunWith` 和自定义 Runner 来控制执行顺序，或者通过构建测试套件（`@Suite`）来分离依赖性强的测试。

------

### **总结**

通过 `@FixMethodOrder`，你可以为测试方法的执行顺序提供明确的规则，尤其是在测试对顺序有严格要求的情况下非常有用。通常推荐使用 `MethodSorters.NAME_ASCENDING`，因为它提供了最可预测且容易管理的排序方式。但同时，也应该尽量保证测试用例的独立性，减少对顺序的依赖性。


