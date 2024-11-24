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

   ![](D:\笔记\JUnit单元测试\图片\屏幕截图 2024-11-21 154513.png)

2. 使用EclipseSDK环境

   ![屏幕截图 2024-11-21 154849](D:\笔记\JUnit单元测试\图片\屏幕截图 2024-11-21 154849.png)

   ![屏幕截图 2024-11-21 154907](D:\笔记\JUnit单元测试\图片\屏幕截图 2024-11-21 154907.png)

   ![屏幕截图 2024-11-21 154920](D:\笔记\JUnit单元测试\图片\屏幕截图 2024-11-21 154920.png)

## JUnit注解

| 注解        | 说明                                                         |
| :---------- | :----------------------------------------------------------- |
| @Test：     | 标识一条测试用例。 (A) (expected=XXEception.class)  (B) (timeout=xxx) |
| @Ignore:    | 忽略的测试用例。                                             |
| @Before:    | 每一个测试方法之前运行。                                     |
| @After :    | 每一个测试方法之后运行。                                     |
| @BefreClass | 所有测试开始之前运行。                                       |
| @AfterClass | 所有测试结果之后运行。                                       |

## JUnit	——assert断言

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
     java
     
     
     复制代码
     assertArrayEquals("数组不相等", new int[]{1, 2, 3}, new int[]{1, 2, 3});
     ```

2. **`assertEquals(String message, Object expected, Object actual)`**

   - 验证两个对象的值是否相等（使用 `equals()` 方法）。

   - 示例：

     ```Java
     java
     
     
     复制代码
     assertEquals("值不相等", "Hello", "Hello");
     ```

3. **`assertSame(String message, Object expected, Object actual)`**

   - 验证两个对象是否引用同一个内存地址（使用 `==`）。

   - 示例：

     ```java
     java复制代码String str = "Java";
     assertSame("引用不同", str, str);
     ```

4. **`assertNotSame(String message, Object expected, Object actual)`**

   - 验证两个对象是否不是同一个引用（使用 `!=`）。

   - 示例：

     ```Java
     java
     
     
     复制代码
     assertNotSame("引用相同", new String("Java"), new String("Java"));
     ```

5. **`assertTrue(String message, boolean condition)`**

   - 验证条件是否为 `true`，为 `true` 则通过。

   - 示例：

     ```Java
     java
     
     
     复制代码
     assertTrue("条件不为真", 5 > 3);
     ```

6. **`assertFalse(String message, boolean condition)`**

   - 验证条件是否为 `false`，为 `false` 则通过。

   - 示例：

     ```java
     java
     
     
     复制代码
     assertFalse("条件不为假", 5 < 3);
     ```

7. **`assertNull(String message, Object object)`**

   - 验证对象是否为 `null`。

   - 示例：

     ```Java
     java
     
     
     复制代码
     assertNull("对象不为null", null);
     ```

8. **`assertNotNull(String message, Object object)`**

   - 验证对象是否不是 `null`。

   - 示例：

     ```Java
     java
     
     
     复制代码
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

URL：https://hamcrest.org/JavaHamcrest/distributables#download-the-hamcrest-jar（科学上网）

#### 导入Hamcrest包

![](D:\笔记\JUnit单元测试\图片\屏幕截图 2024-11-21 154513.png)



在测试代码段加入：

```Java
import static org.hamcrest.MatcherAssert.assertThat;
import static org.hamcrest.Matchers.*;
```

### assertThat一般匹配符（JUnit）

#### 1. **allOf**

- **作用**：要求所有条件均成立，测试才通过，相当于“与”（&&）。

- 示例

  ：

  ```java
  java
  
  
  复制代码
  assertThat(testedNumber, allOf(greaterThan(4), lessThan(10)));
  ```

#### 2. **anyOf**

- **作用**：只要任意一个条件成立，测试通过，相当于“或”（||）。

- 示例

  ：

  ```java
  java
  
  
  复制代码
  assertThat(testedNumber, anyOf(greaterThan(10), lessThan(4)));
  ```

#### 3. **anything**

- **作用**：永远为 `true`，无论条件如何。

- 示例

  ：

  ```java
  java
  
  
  复制代码
  assertThat(testedNumber, anything());
  ```

#### 4. **is**

- **作用**：测试对象是否等于给定的值。

- 示例

  ：

  ```java
  java
  
  
  复制代码
  assertThat(testedString, is("developerWorks"));
  ```

#### 5. **not**

- **作用**：测试对象是否不等于给定的值，与 `is` 匹配符相反。

- 示例

  ：

  ```java
  java
  
  
  复制代码
  assertThat(testedString, not("developerWorks"));
  ```