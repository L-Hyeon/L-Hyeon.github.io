---
layout: post
title: 네트워크 실습 - 1
categories: Network
tags: [CS, Network]
---

# 네트워크 실습 - 1

{:toc}

### 네트워크 프로그래밍

- aka 소켓 프로그래밍
- 소켓 기반으로 프로그래밍

##### 소켓

- OS에 의해 제공되는 SW적 네트워크 연결 장치
- 프로그래머가 물리적, SW적 내용을 신경쓰지 않게 하는 연결 도구
- 서버 소켓(리스닝 소켓)
- 클라이언트 소켓

### 서버 소켓 in Coding

##### 소켓 생성

- socket 함수로 생성
- 송신 소켓, 수신 소켓 생성 방법은 차이가 있음

```c
socket(int domain, int type, int protocol);
```

##### 소켓의 주소 할당, 연결

```c
int bind(int sockfd, struct sockaddr *myaddr, socklen_t addrlen);
```

##### 연결요청 가능한 상태의 소켓

- Server 측에서는 서버 소켓으로 변환시켜 줘야 요청을 받을 수 있음
- Client 측은 상관 없음

```c
int listen(int sockfd, int backlog);
// 소켓을 수신 가능한 소켓으로 변환
```

##### 연결요청의 수락

- accept 함수 호출 이후 데이터 송수신 가능
- 연결 요청이 있는 경우에만 accept 함수가 반환

```c
int accept(int sockfd, struct sockaddr *addr, socklen_t *addrlen);
// 연결이 오면 소켓을 리턴

// 최초 생성한 소켓은 수신 용도로만 사용됨
// 사용자와 데이터 교환은 리턴된 소켓에서 실행
```

### 클리아언트 소켓 in Coding

- 소켓 생성, bind까지는 동일

##### 연결 요청

```c
int connect(int sockfd, struct sockaddr *serv_addr, socklen_t addrlen)
//연결 성공 시 1 반환, 실패 시 0 반환
```
