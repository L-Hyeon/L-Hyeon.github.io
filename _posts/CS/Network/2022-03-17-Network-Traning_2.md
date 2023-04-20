---
layout: post
title: 네트워크 실습 - 2
categories: Network
tags: [CS, Network]
---

# 네트워크 실습 - 2

{:toc}

### 리눅스 기반 파일 조작

- 소켓 프로그래밍이 파일 조작과 동일

##### 저수준 파일 입출력

- ANSI 표준이 아닌 리눅스 자체 제공 함수 기반
- 소켓도 파일로 간주하기 때문에 이를 통해 데이터 송, 수신 가능

##### 파일 디스크립터

- OS가 만든 파일(and 소켓)을 구분하기 위한 숫자
- 0, 1, 2는 이미 규정되어 있음
  - 0, Standard Input
  - 1, Standard Output
  - 2, Standard Error
- 소켓이나 파일을 만들게 되면 3번부터

##### 파일 열기, 닫기

```c
int open(const char *path, int flag);
//성공 시 파일 디스크립터, 실패 시 -1 반환
//path = 파일 주소, flag = 오픈 모드
```

```c
int close(int fd);
//fd = 파일 디스크립터
//성공 0, 실패 -1 반환
```

##### 파일에 데이터 쓰기

```c
ssize_t write(int fd, const void * buf, size_t nbytes);
//fd = 파일 디스크립터, buf, 전송할 데이터가 있는 주소값
//nbytes = 전송할 데이터의 바이트 수
//성공 시 전달한 바이트 수, 실패 시 -1 반환

//실제 사용
write(fd, buf, sizeof(buf))
```

- 터미널에서 cat file.txt 하면 파일의 내용 보여줌

##### 파일 데이터 읽기

```c
ssize_t read(int fd, void *buf, size_t nbytes);
//buf = 읽어온 데이터를 저장할 공간
//성공 시 읽어온 바이트 수, 실패 시 -1 반환
```

### 소켓 생성

##### 프로토콜

- 컴퓨터 상호 간 데이터 송수신에 필요한 통신 규약
- 소켓을 생성할 때 프로토콜을 명시해야 함

##### 소켓 타입

- SOCK_STREAM, 연결 지향형
  - TCP
  - 데이터 손실 보장
  - 데이터의 경계가 없음
  - 1대1 구조
- SOCK_DGRAM 비 연결 지향형
  - UDP
  - 데이터 손실 보장 X
  - 데이터의 경계 있음
  - 한 번에 전송 가능한 데이터 크기 제한

```c
int tcp_socket = socket(PF_INET, SOCK_STREAM, IPPROTO_TCP);
// TCP 소켓

int udp_socket = socket(PF_INET, SOCK_DGRAM, IPPROTO_UDP);
// UDP 소켓
```

- 1, 2번 인자에서 사실상 결정되기 때문에 3번 인자는 0이어도 되긴 함

##### 데이터의 경계

- 송신자가 데이터를 보낸 횟수와 수신자가 데이터를 읽는 횟수와의 관계
- tcp는 데이터를 몇 번 보내던지 수신자가 한 번에 읽을 수 있음 => **경계 없음**
- udp는 보낸 횟수만큼 읽어야 함 => **경계 있음**

### 주소 정보의 표현

##### IP 구조체, sockaddr_in

```c
struct sockaddr_in {
  sa_family_t sin_family; //주소체계
  uint16_t sin_port; //Port번호, 16비트 unsigned int
  struct in_addr sin_addr; //32비트 IP 주소
  char sin_zero[8]; //사용되지 않음
}

struct in_addr {
  in_addr_t s_addr; //32비트 ipv4 주소, 32비트 unsigned int
}
```

- sin_family
  - AF_INET(ipv4), AF_INET6(ipv6), AF_LOCAL 3중 1
- sin_port
  - 16비트 포트 번호
  - 네트워크 바이트 순서대로 저장
- sin_addr
  - 32비트 IP주소
  - 네트워크 바이트 순서대로 저장
  - struct지만 사실상 32비트 unsigned int 자료형

##### IP 구조체 활용

```c
bind (serv_sock, (struct sockaddr*) &serv_addr, sizeof(serv_addr))
```

- bind 함수의 인자로서 사용
- 원래 bind 함수는 sockaddr을 인수로 받음
  - sockaddr은 다양한 주소 체계를 담기 위한 구조체
- **IPv4**의 주소정보를 쉽게 담기 위해서 sockaddr_in을 사용

```c
struct sockaddr{
  sa_family_t sin_family;
  char sa_data[14];
}
```

### 네트워크 바이트 순서

##### CPU에 따라 정수 저장 방식

- Little Endian
  - 상위 바이트를 큰 번지수에 저장
- Big Endian
  - 상위 바이트를 작은 번지수에 저장

##### 네트워크 바이트 순서

- 시스템마다 다른 방식을 통일
- 통신에서는 빅 엔디안 방식 채용
- 바이트 변환 함수를 통해 변환
- h = 호스트(시스템), n = 네트워크(빅 엔디안, 네트워크 바이트 순서)
- **전송할 데이터는 무조건 변환을 하고, 받은 데이터도 변환을 해야 함**
- short는 주로 포트 번호, long은 주로 ip주소

```c
unsigned short htons(unsigned short);
unsigned short ntohs(unsigned short);
unsigned long htonl(unsigned long);
unsigned long ntohl(unsigned long);
```

##### 문자열을 네트워크 바이트 순서로 변환

- "127.0.0.1"같은 문자열을 네트워크 바이트 순서의 32비트 unsigned int로 변환

```c
in_addr_t inet_addr(const char * string);
```

```c
int inet_aton(const char * string, struct in_addr * addr);
```

- inet_addr과 기능상 동일
- inet_addr은 변환된 int 반환
- inet_aton은 인수로 넣은 구조체에 넣어주고 1 or 0(실패) 반환

```c
int inet_ntoa(struct in_addr addr);
```

- inet_aton의 반대
- 구조체를 인수로 IP주소 문자열 반환

##### INADDR_ANY

- 실행중인 컴퓨터의 IP를 소켓에 부여할 때 사용
- 서버 프로그램 구현에 주로 사용
