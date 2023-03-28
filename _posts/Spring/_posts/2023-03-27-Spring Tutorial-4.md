---
layout: post
title: 4. Spring 핵심 개념
categories: Spring
tags: [Java, Spring]
---

<img src="assets\img\headers\Spring.png" />

# Java Spring 핵심 개념 - IoC와 DI

이 섹션에서는 Spring의 핵심 개념 중 하나인 IoC(Inversion of Control)와 DI(Dependency Injection)에 대해 자세히 살펴보겠습니다.

### IoC (Inversion of Control)

IoC란, 제어의 역전이라는 뜻으로, 객체의 생성과 관리를 개발자가 아니라 프레임워크가 담당하는 것을 의미합니다. 이를 통해 객체 간의 결합도를 낮출 수 있습니다.

일반적으로 개발자가 객체를 생성하고 필요에 따라 호출하는 것이 일반적인 방법입니다. 하지만, 이렇게 하면 객체 간의 결합도가 높아져서 유지보수와 확장이 어려워집니다. 객체 간의 결합도를 낮추기 위해서는 객체 생성과 관리를 개발자가 아닌 프레임워크가 담당하도록 해야 합니다.

Spring에서는 객체의 생성과 관리를 Spring 컨테이너가 담당합니다. 따라서, 객체 간의 결합도를 낮추어 유지보수와 확장이 용이하도록 만들 수 있습니다.

### DI (Dependency Injection)

DI란, 의존성 주입이라는 뜻으로, 객체 간의 의존성을 줄이기 위해 사용합니다. 일반적으로 객체는 다른 객체에 의존하게 되는데, DI를 사용하면 객체 간의 의존성을 낮추어 유지보수와 확장이 용이하도록 만듭니다.

DI는 세 가지 방식으로 구현할 수 있습니다.

1. 생성자 주입
2. Setter 주입
3. 필드 주입

생성자 주입은 생성자를 통해 의존성을 주입하는 방식입니다. Setter 주입은 Setter 메소드를 통해 의존성을 주입하는 방식입니다. 필드 주입은 필드에 직접 값을 할당하는 방식입니다.

Spring에서는 주로 Setter 주입을 사용합니다. Setter 주입을 사용하면 객체 생성 후에도 의존성을 변경할 수 있기 때문입니다.

### Spring 컨테이너

Spring 컨테이너는 Spring 프레임워크의 핵심입니다. Spring 컨테이너는 IoC와 DI를 구현하며, 객체의 생성과 관리를 담당합니다.

Spring 컨테이너는 크게 두 가지로 나눌 수 있습니다.

1. BeanFactory
2. ApplicationContext

BeanFactory는 가장 기본적인 컨테이너로, 객체 생성과 관리를 담당합니다. ApplicationContext는 BeanFactory의 기능에 추가적인 기능을 제공합니다. 예를 들어, 메시지 인터셉터, 이벤트 등을 처리할 수 있습니다.

ApplicationContext는 XML 파일, Java Configuration 파일 또는 어노테이션을 이용하여 설정할 수 있습니다. Spring Boot를 사용하면 자동 설정 기능을 제공하여 보다 간편하게 ApplicationContext를 설정할 수 있습니다.

### AOP (Aspect-Oriented Programming)

AOP는 관점 지향 프로그래밍이라는 뜻으로, 코드의 관점을 기반으로 프로그래밍하는 방식입니다. AOP를 사용하면 여러 모듈에서 공통으로 사용하는 기능을 분리하여 재사용성과 유지보수성을 향상시킬 수 있습니다.

Spring에서는 AOP를 지원합니다. 예를 들어, Logging, Security 등의 공통 기능을 별도의 모듈로 분리하여 재사용할 수 있습니다. 이를 통해 코드의 중복을 줄이고 유지보수성을 향상시킬 수 있습니다.

### Spring MVC (Model-View-Controller)

Spring MVC는 Spring 프레임워크의 Web 애플리케이션 개발을 위한 모듈입니다. Spring MVC는 Model-View-Controller 아키텍처 패턴을 따르며, 다양한 기능을 제공합니다.

Model은 애플리케이션에서 사용되는 데이터를 나타냅니다. View는 데이터를 화면에 출력하는 부분을 나타냅니다. Controller는 클라이언트의 요청을 처리하고, Model과 View를 연결하는 역할을 합니다.

Spring MVC는 DispatcherServlet을 이용하여 클라이언트의 요청을 처리합니다. DispatcherServlet은 클라이언트의 요청을 받고, 적절한 Controller를 선택하여 처리합니다.

### Spring Boot

Spring Boot는 Spring 프레임워크를 사용하여 웹 애플리케이션을 빠르고 간편하게 개발할 수 있도록 도와주는 도구입니다. Spring Boot를 사용하면 별도의 설정 없이 간단한 애플리케이션을 빠르게 개발할 수 있습니다.

Spring Boot는 자동 설정 기능을 제공합니다. 자동 설정 기능을 사용하면, 별도의 설정 없이 기본적인 설정을 적용할 수 있습니다. 또한, 스프링 프레임워크에서 사용되는 다양한 모듈을 쉽게 사용할 수 있습니다.

Spring Boot는 내장형 서버를 제공합니다. 내장형 서버를 사용하면, 별도의 웹 서버를 설치하거나 설정할 필요가 없습니다.

### 결론

이번 글에서는 Java Spring의 개요와 핵심 개념을 살펴보았습니다. Java Spring은 다양한 모듈을 제공 하여 개발자가 웹 애플리케이션을 보다 쉽게 개발할 수 있도록 도와줍니다. DI, AOP, Spring MVC 등의 개념을 이해하고 적절하게 활용하면, 개발 속도와 유지보수성을 향상시킬 수 있습니다.

특히, Spring Boot를 사용하면 설정의 번거로움을 줄이고 빠르게 개발할 수 있으므로, 웹 개발에 대한 입문자나 초급 개발자에게 추천합니다.

Java Spring은 현재도 많은 기업에서 사용되고 있으며, 더욱 발전하고 있는 프레임워크입니다. 앞으로도 Java Spring을 잘 활용하여 웹 개발을 보다 쉽게 할 수 있도록 노력해보세요!
