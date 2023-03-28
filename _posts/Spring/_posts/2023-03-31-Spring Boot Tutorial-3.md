---
layout: post
title: 3. Spring Boot 아키텍쳐
categories: Spring
tags: [Java, Spring]
---

<img src="assets\img\headers\Spring Boot.png" />

# Spring Boot 아키텍쳐

Spring Boot는 Spring Framework를 기반으로 하며, Spring Framework와 비슷한 아키텍처를 가지고 있습니다. 그러나 Spring Boot는 내장형 서버와 자동 설정 기능 등의 차이점이 있습니다.

Spring Boot 애플리케이션의 아키텍처는 크게 다음과 같이 나눌 수 있습니다.

1. 의존성 관리
   Spring Boot는 의존성 관리 기능을 제공합니다. 이 기능을 통해 필요한 라이브러리들을 자동으로 관리할 수 있습니다.

2. 자동 설정
   Spring Boot는 자동 설정 기능을 제공하여, 애플리케이션의 설정을 자동으로 구성합니다. 개발자는 별도의 설정 없이도 간단하게 애플리케이션을 구성할 수 있습니다.

3. 내장형 서버
   Spring Boot는 내장형 서버(Tomcat, Jetty, Undertow)를 사용하여, 별도의 외부 서버를 설치하지 않고도 애플리케이션을 실행할 수 있습니다.

4. 실행 환경 구성
   Spring Boot는 실행 환경 구성 기능을 제공하여, 다양한 환경에서 실행할 수 있는 애플리케이션을 개발할 수 있습니다.

5. 스프링 프레임워크와 연동
   Spring Boot는 스프링 프레임워크와 연동하여, 스프링 프레임워크에서 제공하는 다양한 기능들을 사용할 수 있습니다.

6. 외부 라이브러리와 연동
   Spring Boot는 다양한 외부 라이브러리와 연동할 수 있습니다. 이를 위해 스프링 부트에서는 스프링 Data, 스프링 Security, 스프링 Batch, 스프링 Integration 등의 모듈을 제공합니다.

Spring Boot의 아키텍처는 이러한 요소들이 조합되어, 개발자가 간편하게 애플리케이션을 개발할 수 있는 환경을 제공합니다.
