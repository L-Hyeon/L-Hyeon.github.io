---
layout: post
title: 1. DBMS, SQL
categories: SQL
tags: [DB, SQL]
---


## DBMS

### Database
- 데이터 저장소
##### 관계형 데이터베이스
- 2차원 표의 형태로 데이터를 저장

### Database Management System
- DB를 관리하고 운영하는 시스템
- 다수의 사람이 접근할 수 있도록 허용
##### EX
- MySQL
- MS SQL

## SQL
- 관계형 DB 작동을 위한 ANSI 표준 언어

### DML (Data Manipulation Language)
- INSERT
  - 행 삽입
- UPDATE
  - 행 갱신
- DELETE
  - 행 삭제
- MERGE
  - 병합

### DDL (Data Define Language)
- CREATE
  - 테이블 생성
- ALTER
  - 테이블 변경
- DROP
  - 테이블 자체를 삭제
- TRUNCATE
  - 테이블 형태는 유지하되 내용을 전체 삭제
- RENAME
  - 이름 변경
- COMMENT

### DCL (Data Control Language)
- GRANT
  - 권한 부여
- REVOKE
  - 권한 회수

### TCL (Transaction Control Language)
- COMMIT
  - 트랜젝션 확정
- ROLLBACK
  - 트랜젝션 취소(되돌리기)
- SAVEPOINT

