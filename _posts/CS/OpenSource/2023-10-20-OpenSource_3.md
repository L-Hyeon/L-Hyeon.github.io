---
layout: post
title: 3. Docker
categories: Open Source
tags: [CS, Open Source]
---

## Docker?

> 개발, 실행, 공유를 위한 개방형 플랫폼
{: .prompt-tip }

- 격리된 환경인 컨테이너에서 앱을 패키징, 실행
- 호스트 환경에 종속적이지 않고 실행

### 컨테이너

- 소스코드와 모든 종속성을 패키징하는 표준 SW 단위
- 프로세스 가상화(OS 레벨)
- 호스트 OS의 커널 공유
- 빠름

##### 가상머신

- 하드웨어 가상화
- 게스트 OS를 따로 실행시킴

### 도커 아키텍쳐

- 클라이언트-서버 구조

##### 도커 데몬

- API 요청을 수신하고 이미지, 컨테이너 같은 도커 객체 관리
- 다른 데몬과의 통신으로 도커 서비스 관리

##### 도커 클라이언트

- 사용자와 도커 간 상호작용
- 사용자의 명령어를 도커 데몬에게 API 형태로 전달
- 여러 데몬과 통신 가능

##### 도커 레지스트리

- 도커 이미지를 저장하는 공간
- 대표적인 예시) 도커 허브
- 4가지 구성요소
  - docker.io(이미지가 저장된 주소)
  - diamol(작성자)
  - golang(레포지토리 이름)
  - lastest(태그)

##### 도커 객체

- 이미지
  - 컨테이너 생성 지침이 포함된 읽기 전용 템플릿
  - 도커 파일을 통해 생성
  - 여러 레이어로 구성
- 컨테이너
  - 이미지의 실행 인스턴스
  - 휘발성

### 기술 변화

1. 리눅스 컨테이너 기반
2. OCI 표준
3. 도커 데몬, 도커 컨테이너, runC OCI

### 이미지 명령어

- pull, push
- docker image save, load
  - 이미지를 tar 파일로 저장, 불러오기
- docker image ls, docker images
  - 이미지 모록 나열
- docker image inspect
  - inspect = 도커 객체의 세부정보를 JSON으로 반환
- docker image history
- docker image tag
  - 태그 = 이름:버전
  - 존재하는 이미지의 이름과 버전을 새로 설정(기존 거 복사해서 새로 만들기)
- docker image rm, docker rmi
  - 이미지 삭제
- docker image prune, 사용하지 않는 이미지 모두 삭제

### 컨테이너

- 읽기 전용 이미지 레이어 위에 R/W 레이어를 추가
- 가상의 격리된 공간에서 독립된 프로세스로 실행

##### 명령어

- create
- start
- stop
- rm
- run
  - create + start
- attach
  - 실행중인 컨테이너에 접속
  - 표준 입출력을 컨테이너에 붙임
- ps
  - 실행 중인 컨테이너 표시
  - -a로 정지된 것도 같이 표시

### 데이터 관리

- UFS(Union File System)
  - 하나의 이미지로 여러 컨테이너 생성
  - 컨테이너 = 이미지 + R/W 레이어
- 도커 볼륨을 통해 컨테이너의 상태와 무관하게 데이터 저장

### 도커 볼륨

- 컨테이너간 데이터 공유
- 호스트에서 직접 접근
- 컨테이너가 삭제되어도 데이터 유지

##### volume

- 도커가 관리하는 영역에 볼륨 생성
- 여러 컨테이너에 동시 마운트 가능
- 도커 명령어를 통해 관리

##### bind mount

- 호스트 파일 시스템에 생성
- 직접 마운트 해야 함
- volume에 비해 제한적

##### tmpfs mount

- 메모리 공간에 볼륨 생성
- 휘발성
- 중요 파일 임시 저장

### 도커 파일

- FROM [image]
- RUN [명령어]
  - 생성한 뒤 먼저 실행할 명렁어들 선언
  - apt install의 경우 -y 붙어야 정상 작동
- WORKDIR [디렉토리]
  - pwd 설정
- COPY, ADD [파일명] [디렉토리]
  - 호스트 환경에서 컨테이너로 복사
  - ADD는 외부 링크도 사용 가능
- CMD, ENTRYPONT ["python", "run.py"]
  - 컨테이너 실행 시 수행할 명령어
  - 둘 다 있으면 CMD가 ENTRYPOINT의 파라미터로 사용
    - ENTRYPOINT ["python"] CMD ["run.py"]

##### 빌드

- docker build -t [이미지명:태그] -f [파일이름] [경로 | URL | 압축파일]
- -f는 Dockerfile이 아닌 경우에 사용

##### 예시

```
FROM ubuntu:18.04
RUN apt update
RUN apt-get install python -y
```
