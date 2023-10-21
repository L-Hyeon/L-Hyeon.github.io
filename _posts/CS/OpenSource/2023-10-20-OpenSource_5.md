---
layout: post
title: 5. 스타일 가이드
categories: Open Source
tags: [CS, Open Source]
---

## 스타일 가이드?

> 코드를 어떻게 작성할지에 대한 전반적 내용을 담은 문서
{: .prompt-tip }

- 높은 가독성
- 적절한 주석
- 간결한 구조

### #define Guard

```c++
#ifndef PROJECT_PATH_FILE_H
#define PROJECT PATH FILE H
#endif
```

### Include 순서

- C 시스템 파일
- C++ 시스템 파일
- 외부 프로젝트 헤더
- 내부 프로젝트 헤더

### inline 함수

- 10줄 이내의 함수만 사용

### 변수

- 항상 초기화와 선언을 같이 하라
- 변수의 이름은 소문자와 언더바(\_)를 활용

### 클래스

- 초기화 리스트를 사용하라
- public, protected, private 순서

##### 선언 순서

- typedef
- 상수
- 생성자
- 소멸자
- method
- 데이터 멤버

### 레퍼런스 인자

- 변수가 참조자로 지정되면 const 붙여라
- 컨테이너는 항상 &로 넘겨라

### 형 변환

- static_cast를 사용하라

### 반복문

- 가능한 한 이터레이터를 사용하라

### 파일 이름

- 소문자와 -, \_를 활용하라

### 타입 이름

- 대문자로 시작하는 카멜케이스를 활용하라
- 함수 이름, 클래스, 구조체, 열거형 동일

### 상수 이름

- k로 시작하고 대문자와 카멜케이스 활용하라
