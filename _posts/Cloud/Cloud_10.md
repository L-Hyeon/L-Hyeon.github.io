---
layout: post
title: Cloud 기반 DevOps
categories: Cloud
tags: [Cloud]
---

## DevOps

> 개발과 운영을 동시에 실행하는 개발 문화

### 역사

1. Waterfall
   - 출시 일자를 결정하고 그에 맞춰 개발
2. Agile
   - 기업마다 온 프레미스 서버 구축, 가상머신 활용
   - 코드와 빌드/테스트를 동시에 시작
   - SaaS
   - 자동화가 필수적

### 자동화

1. Code Push
2. 빌드, 테스트 자동으로 진행
3. 테스트 통과 시 배포

- 굉장히 빈번한 배포를 목적

##### DevOps 엔지니어

- 코드가 푸시된 이후 빌드, 테스트 자동화 과정을 관리

### 과정

0. plan
1. code
2. build
3. test
4. release
5. deploy
6. operate
7. mointor

### 배포 과정

1. local
2. dev
3. qa
4. staging
5. prod

## DevOps in AWS

1. CI/CD
2. Observability
   - Kubernetis
3. Infrastructure as a Code
   - Terraform
4. Monitoring

### AWS 구성

- Compute
  - EC2, Lambda
- Storage
  - S3, EBS, EFS
- Database
  - RDS, Aurora, Dynamo DB
- etc...

## CI/CD 파이프라인

### CI

- 지속적 통합
- 버그 조기 탐지

### CD

- 지속적 전달
- 배포 서버로 전달

## 관찰가능성

> 시스템 모니터링의 새로운 접근 방법

- 외부 출력만으로 내부 상태를 측정할 수 있는 기능

1. 로그 수집
2. 메트릭 수식
3. 에러 추적

### in AWS

- CloudWatch
- X-Ray
- CloudTrail
