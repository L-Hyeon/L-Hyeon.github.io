---
layout: post
title: 네트워크 실습 - 3
categories: Network
tags: [CS, Network]
---

# 네트워크 실습 - 3

{:toc}

### TCP 서버의 함수 호출 순서

1. socket()
2. bind()
3. listen()
4. accecpt()
5. read()/write()
6. close()

##### listen()

```c
int listen(int sock, int backlog);
// 성공 0, 실패 -1 반환
```

- SYN이 오면 SYN ACK를 보내줌
- sock = 연결 대기 상태에 두고자 하는 소켓, 리스닝 소켓
- backlog = 연결 대기 큐에 크기 정보
  - SYN ACK를 보내고 연결을 대기하는 큐의 크기

##### accept()

```c
int accecpt(int sock, strcut sockaddr * addr, socklen_t * adddrlen);
// 성공 시 디스크립터, 실패 -1 반환
```

- SYN ACK에 대한 ACK를 받은 이후
- 클라이언트만와 연결할 소켓을 새로 반환
  - 리스닝 소캣과 별개
- sock = 서버 소켓의 파일 디스크립터
- addr = 클라이언트의 IP주소 구조체
- addrlen = 구조체의 크기

### TCP 클라이언트의 함수 호출 순서

1. socket()
2. connect()
3. read()/write()
4. close()

##### connect()

```c
int connect(int sock, const struct sockaddr * servaddr, socklen_t addrlen);
// 성공 시 디스크립터, 실패 -1 반환
```

- SYN을 보내줌
- 서버와의 연결을 위한 새로운 소켓 반환
- servaddr = 서버의 IP주소 구조체

### 서버, 클라이언트의 함수 호출 관계

<img src="https://github.com/L-Hyun/L-Hyun.github.io/blob/main/assets/Network/T3-1.png?raw=true"/>

- 서버에서 accecpt()이 코드 흐름을 block
  - SYN ACK에 대한 ACK를 받으면 재개

### Iterative 서버

- Echo Server
- 서버는 close하지 않고 반복적으로 클라이언트 상대
- 한 번에 하나의 클라이언트 서비스
