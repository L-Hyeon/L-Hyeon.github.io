---
layout: post
title: 네트워크 실습 - 1
categories: Network
tags: [CS, Network, 네트워크]
---

<style type='text/css'>
  @font-face {
    font-family: 'Cafe24SsurroundAir';
    src: url('https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_2105_2@1.0/Cafe24SsurroundAir.woff') format('woff');
    font-weight: normal;
    font-style: normal;
  }
  .article {
    font-family: 'Cafe24SsurroundAir';
  }
  .contentsItems { color: black; }
  .contentsItems:hover {
    color: black;
    text-decoration: underline;
  }
  .title {
    font-size: 30px;
    border-bottom: 3px solid #6667ab;
    border-left: 20px solid #6667ab;
    padding-left: 5px;
    margin-bottom: 10px;
  }
  .subtitle {
    margin-top: 20px;
	  font-size: 25px;
	  color: #5e5e7d;
  }
  .subsub {
    font-size: 17px;
    color: #13356b;
  }
  .section {
    padding-left: 15px;
  }
  .define{
    font-weight: bold;
    padding-left: 15px;
  }
  .red{
    display: inline;
    color: #a12d27;
  }
  .disabled {
    display: inline;
    color: #777777;
  }
</style>

<div class="article">

<div class="title">네트워크 프로그래밍</div>

- aka 소켓 프로그래밍
- 소켓 기반으로 프로그래밍

<div class="subtitle">소켓</div>

- OS에 의해 제공되는 SW적 네트워크 연결 장치
- 프로그래머가 물리적, SW적 내용을 신경쓰지 않게 하는 연결 도구
- 서버 소켓(리스닝 소켓)
- 클라이언트 소켓

<div class="subtitle">서버 소켓 in Coding</div>
<div class="section"><div class="subsub">소켓 생성</div></div>

- socket 함수로 생성
- 송신 소켓, 수신 소켓 생성 방법은 차이가 있음

```c
socket(int domain, int type, int protocol);
```

<div class="section"><div class="subsub">소켓의 주소 할당, 연결</div></div>

```c
int bind(int sockfd, struct sockaddr *myaddr, socklen_t addrlen);
```

<div class="section"><div class="subsub">연결요청 가능한 상태의 소켓</div></div>

- Server 측에서는 서버 소켓으로 변환시켜 줘야 요청을 받을 수 있음
- Client 측은 상관 없음

```c
int listen(int sockfd, int backlog);
// 소켓을 수신 가능한 소켓으로 변환
```

<div class="section"><div class="subsub">연결요청의 수락</div></div>

- accept 함수 호출 이후 데이터 송수신 가능
- 연결 요청이 있는 경우에만 accept 함수가 반환

```c
int accept(int sockfd, struct sockaddr *addr, socklen_t *addrlen);
// 연결이 오면 소켓을 리턴

// 최초 생성한 소켓은 수신 용도로만 사용됨
// 사용자와 데이터 교환은 리턴된 소켓에서 실행
```

<div class="subtitle">클리아언트 소켓 in Coding</div>

- 소켓 생성, bind까지는 동일

<div class="section"><div class="subsub">연결 요청</div></div>

```c
int connect(int sockfd, struct sockaddr *serv_addr, socklen_t addrlen)
//연결 성공 시 1 반환, 실패 시 0 반환
```

</div>
