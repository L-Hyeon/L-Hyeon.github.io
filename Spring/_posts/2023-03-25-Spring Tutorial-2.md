---
layout: post
title: 2. Spring 아키텍쳐
categories: Spring
tags: [Java, Spring]
---

### Java Spring 아키텍처 및 핵심 개념

이 섹션에서는 Java Spring의 아키텍처와 핵심 개념을 살펴볼 것입니다. Spring의 주요 모듈 및 컨테이너에 대해 설명하고, IoC (Inversion of Control) 및 DI (Dependency Injection)에 대한 이해를 돕기 위해 간단한 예제도 제공합니다.

##### Java Spring 아키텍처

Java Spring은 다양한 모듈로 구성되어 있으며, 이러한 모듈은 개별적으로 사용하거나 조합하여 사용할 수 있습니다. Spring의 주요 아키텍처 구성 요소는 다음과 같습니다.

- Spring Core: Spring 프레임워크의 핵심 기능을 제공합니다.
- Spring AOP (Aspect-Oriented Programming): Aspect-Oriented Programming 지원을 제공합니다.
- Spring MVC (Model-View-Controller): 웹 애플리케이션을 구축하는 데 사용되는 Model-View-Controller 아키텍처를 구현합니다.
- Spring Data Access / Integration: 다양한 데이터 액세스 기술과 외부 API와의 통합을 지원합니다.
- Spring Security: 인증 및 권한 부여 기능을 제공합니다.

이러한 모듈은 Java Spring이 처리하는 다양한 기능을 처리하는 데 사용됩니다.

##### Java Spring 컨테이너

Java Spring은 IoC (Inversion of Control) 기반의 컨테이너입니다. Spring 컨테이너는 개발자가 작성한 Java 객체의 생성, 구성 및 관리를 처리합니다. Spring 컨테이너는 객체의 라이프사이클을 관리하고 객체 간의 의존성을 관리합니다.

##### IoC (Inversion of Control)

IoC (Inversion of Control)는 Spring의 핵심 개념 중 하나입니다. IoC는 객체를 생성하고 관리하는 책임을 개발자가 아닌 Spring 컨테이너에게 위임하는 것을 의미합니다. 이는 객체 간의 결합도를 줄이고 코드의 재사용성을 높이는 데 도움이 됩니다.

##### DI (Dependency Injection)

DI (Dependency Injection)는 객체 간의 의존성을 처리하는 Spring의 핵심 개념 중 하나입니다. DI는 객체가 필요로 하는 의존성을 Spring 컨테이너에서 주입 받는 것을 의미합니다. 이를 통해 객체 간의 결합도를 낮추고 테스트 가능성을 높일 수 있습니다.

다음 섹션에서는 Java Spring을 사용하여 간단한 예제를 작성하는 방법을 설명합니다.
