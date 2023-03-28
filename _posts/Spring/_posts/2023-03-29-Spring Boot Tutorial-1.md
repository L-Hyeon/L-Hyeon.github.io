---
layout: post
title: 1. Spring Boot 설치하기
categories: Spring
tags: [Java, Spring]
---

<img src="https://github.com/L-Hyun/L-Hyun.github.io/blob/main/assets/img/headers/Spring%20Boot.png?raw=true" />

# Spring Boot 설치하기

Spring Boot를 사용하기 위해서는 우선 Java JDK와 Gradle 또는 Maven이 설치되어 있어야 합니다. 아래의 단계를 따라 Spring Boot를 설치하는 방법에 대해 알아보겠습니다.

### Java JDK 설치

Spring Boot는 Java 언어로 작성되어 있으므로 Java JDK가 먼저 설치되어 있어야 합니다. Java 8 이상의 버전이 필요합니다. JDK는 Oracle JDK, OpenJDK 등 다양한 종류가 있습니다.

### Gradle 또는 Maven 설치

Spring Boot 프로젝트를 빌드하고 실행하기 위해서는 빌드 도구인 Gradle 또는 Maven이 필요합니다. Gradle은 Groovy 언어를 사용한 빌드 도구이며, Maven은 XML을 사용한 빌드 도구입니다. 두 도구 중 어느 것을 사용하더라도 Spring Boot를 사용하는 데는 문제가 없습니다.

Gradle을 설치하려면 Gradle 공식 웹사이트(https://gradle.org/install/)에서 다운로드한 후, 압축 파일을 해제하고 환경 변수를 설정해야 합니다. Maven은 Apache Maven 공식 웹사이트(https://maven.apache.org/download.cgi)에서 다운로드하여 설치할 수 있습니다.

### Spring Boot CLI 설치

Spring Boot CLI는 명령 줄 도구로서 Spring Boot 애플리케이션을 빠르게 개발하고 실행할 수 있습니다. Spring Boot CLI를 사용하면 명령어를 통해 쉽게 프로젝트를 생성하고 실행할 수 있습니다.

Spring Boot CLI를 설치하려면 https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#getting-started-installing-the-cli 에서 다운로드하여 설치합니다. CLI를 설치한 후, CLI를 사용하여 Spring Boot 애플리케이션을 생성할 수 있습니다.

### Spring Boot 프로젝트 생성

Spring Boot CLI를 사용하거나 IDE(예: IntelliJ IDEA, Eclipse)에서 Spring Boot 프로젝트를 생성할 수 있습니다. Spring Initializr(https://start.spring.io/)를 사용하여 CLI 없이 쉽게 프로젝트를 생성할 수도 있습니다.

Spring Initializr 웹사이트에서 프로젝트의 설정 정보를 입력하고 필요한 의존성을 선택한 후, 프로젝트를 생성할 수 있습니다. 프로젝트를 생성하면 Gradle 또는 Maven 빌드 파일과 기본적인 프로젝트 구조가 생성됩니다.

### Spring Boot 애플리케이션 실행

Spring Boot 애플리케이션을 실행하려면 명령어 또는 IDE에서 실행할 수 있습니다. Spring Boot CLI를 사용하려면 명령어 "spring run"을 사용합니다.

Gradle 빌드 도구를 사용하는 경우, 아래와 같이 Gradle 명령어를 사용하여 Spring Boot 애플리케이션을 실행할 수 있습니다.

```bash
./gradlew bootRun
```

Maven을 사용하는 경우, 아래와 같이 Maven 명령어를 사용하여 Spring Boot 애플리케이션을 실행할 수 있습니다.

```bash
./mvnw spring-boot:run
```

IDE를 사용하는 경우, IDE에서 Spring Boot 애플리케이션을 실행할 수 있습니다. 일반적으로 IDE에서 Spring Boot 애플리케이션을 실행할 때 자동으로 빌드되고 실행됩니다.

위의 단계를 따르면 Spring Boot를 설치하고 실행하는 것이 가능합니다. 이제 Spring Boot 애플리케이션을 개발하여 더 많은 기능을 구현해 볼 수 있습니다.
