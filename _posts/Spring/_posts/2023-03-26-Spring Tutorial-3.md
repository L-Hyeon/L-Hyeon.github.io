---
layout: post
title: 3. 간단한 예제
categories: Spring
tags: [Java, Spring]
---

<img src="https://images.velog.io/images/hanblueblue/post/52532500-601b-4ee4-a0b1-070f11154ad3/OG-Spring.png" />

# 간단한 Java Spring 예제

이 섹션에서는 Java Spring을 사용하여 간단한 예제를 작성하는 방법을 설명합니다. 이 예제는 Spring의 IoC와 DI 개념을 보여줍니다.

### 예제 소개

이 예제는 간단한 계산기 애플리케이션을 구현합니다. 이 애플리케이션은 두 개의 숫자를 입력받아 덧셈, 뺄셈, 곱셈 또는 나눗셈을 수행합니다.

### Spring 프로젝트 설정

먼저 Spring 프로젝트를 설정해야 합니다. Maven을 사용하여 프로젝트를 설정하면 다음과 같이 Spring 의존성을 추가할 수 있습니다.

```xml
<dependencies>
   <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-context</artifactId>
      <version>5.3.3</version>
   </dependency>
</dependencies>
```

### Calculator 인터페이스 작성

다음으로, Calculator 인터페이스를 작성합니다. 이 인터페이스는 두 개의 숫자를 입력받아 계산을 수행하는 메소드를 정의합니다.

```java
public interface Calculator {
   public int calculate(int num1, int num2);
}
```

### CalculatorImpl 클래스 작성

Calculator 인터페이스를 구현하는 CalculatorImpl 클래스를 작성합니다. 이 클래스는 입력받은 두 개의 숫자를 더하거나 뺄셈, 곱셈, 나눗셈을 수행합니다.

```java
public class CalculatorImpl implements Calculator {
   public int calculate(int num1, int num2) {
      // addition
      return num1 + num2;
   }
}
```

### Spring 구성 파일 작성

Spring 구성 파일은 Spring 컨테이너에서 사용할 객체를 정의하는 역할을 합니다. 이 예제에서는 CalculatorImpl 객체를 정의합니다.

```xml
<beans xmlns="http://www.springframework.org/schema/beans"
   xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="http://www.springframework.org/schema/beans
   http://www.springframework.org/schema/beans/spring-beans-3.0.xsd">

   <bean id="calculator" class="com.example.CalculatorImpl"/>

</beans>
```

### Main 클래스 작성

마지막으로 Main 클래스를 작성하여 Spring 컨테이너를 초기화하고 CalculatorImpl 객체를 사용하여 계산을 수행합니다.

```java
public class Main {
   public static void main(String[] args) {
      ApplicationContext context =
         new ClassPathXmlApplicationContext("applicationContext.xml");

      Calculator calculator = (Calculator)context.getBean("calculator");
      System.out.println("Addition: " + calculator.calculate(10, 5));
   }
}
```

### 예제 실행 및 결과

예제를 실행하면 다음과 같은 결과가 출력됩니다.

```makefile
Addition: 15
```

이 예제에서는 Spring 컨테이너에서 CalculatorImpl 객체를 가져와서 사용했습니다. 이렇게 Spring 컨테이너에서 객체를 가져오는 것을 IoC(Inversion of Control)라고 합니다. 또한, CalculatorImpl 객체를 생성할 때 필요한 의존성을 Spring 컨테이너가 주입해주는 것을 DI(Dependency Injection)라고 합니다.

이 예제에서는 간단한 덧셈만 수행했지만, Spring을 사용하면 보다 복잡한 애플리케이션을 개발할 때 매우 유용합니다. 다음 섹션에서는 Spring의 핵심 개념인 IoC와 DI에 대해 더 자세히 살펴보겠습니다.
