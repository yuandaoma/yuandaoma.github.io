# Junit5

## 1 概览

### 1.1 什么是Junit5

Junit 5 = Junit Platform + Junit Jupiter + Junit Vintage

* Junit Platform

  是在 JVM 上启动测试框架的基础。

* Junit Jupiter

  JUnit Jupiter 是新的编程模型和扩展模型的组合，用于在 JUnit 5 中编写测试和扩展。Jupiter 子项目提供了一个 TestEngine，用于在平台上运行基于 Jupiter 的测试。

* Junit Vintage

  JUnit Vintage 提供了一个 TestEngine，用于在平台上运行基于 JUnit 3 和 JUnit 4 的测试。

### 1.2 支持的Java版本

Junit5需要 Java8 或更高的Java运行时环境，但是你任然能够对之前JDK版本编译的代码进行测试

## 2. 编写Tests用例

> 第一个测试用例

```java
import static org.junit.jupiter.api.Assertions.assertEquals;

import example.util.Calculator;

import org.junit.jupiter.api.Test;

class MyFirstJUnitJupiterTests {

    private final Calculator calculator = new Calculator();

    @Test
    void addition() {
        assertEquals(2, calculator.add(1, 1));
    }

}
```

## 2.1 常用注解

注解的位置：包`org.junit.jupiter.api` ，模块：`junit-jupiter-api`

| 注解                   | 描述                                                         |
| ---------------------- | ------------------------------------------------------------ |
| @Test                  | 表明注解的方法是一个测试方法，区别于Junit4的 `@Test`注解，Junit5的注解没有定义任何属性，因为 |
| @ParameterizedTest     |                                                              |
| @RepeatedTest          | 表示方法是重复测试的测试模板。 这些方法是继承的，除非它们被覆盖。 |
| @TestFactory           |                                                              |
| @TestTemplate          |                                                              |
| @TestMethodOrder       | 用于为注解的测试类配置测试方法执行顺序； 类似于 JUnit 4 的 @FixMethodOrder。 这样的注释是继承的。 |
| @TestInstance          |                                                              |
| @DisplayName           | 声明测试类或测试方法的自定义显示名称。 此类注释不会被继承    |
| @DisplayNameGeneration |                                                              |
| @BeforeEach            |                                                              |
| @AfterEach             |                                                              |
| @BeforeAll             |                                                              |
| @AfterAll              |                                                              |
| @Nested                |                                                              |
| @Tag                   |                                                              |
| @Disable               |                                                              |
| @Timeout               |                                                              |
| @ExtendWith            |                                                              |
| @RegisterExtention     |                                                              |
| @TempDir               |                                                              |

#### 2.1.1 元注解和组合注解

JUnit Jupiter 注解可以用作元注解。这意味着您可以定义自己的组合注解，该注解将自动继承其元注解的语义。

### 2.2 测试类和方法

**测试类**

​	任何包含至少一个测试方法的顶级类、静态成员类或 @Nested 类。测试类不能是抽象的，并且必须有一个构造函数。

**测试方法**

任何直接用`@Test`，`@RepeatedTest`，`@ParameterizedTest` ,`@TestFactory`，`@TestTemplate`注解或元注解的实例方法

**生命周期方法**

任何直接用`@BeforeAll`，`@AfterAll`，`@BeforeEach` ,`@AfterEach`注解或元注解的实例方法

* 测试方法和生命周期方法可以在当前测试类中声明，从超类继承，或从接口继承。

* 测试方法和生命周期方法不能是抽象的。
* 测试方法和生命周期方法不能有返回值。
