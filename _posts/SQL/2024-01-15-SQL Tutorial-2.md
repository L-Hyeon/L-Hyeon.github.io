---
layout: post
title: 2. SELECT
categories: SQL
tags: [DB, SQL]
---

# SELECT
- 테이블에서 조건에 맞는 행들을 선택하여 보여주는 것

```sql
SELECT [DISTINCT] {* | column | exporession }
FROM table
```

### SQL 작성
- 대소문자 구분 안 함
- 여러 줄에 입력 가능
- 세미 콜론으로 문장 구분
- 들여쓰기 사용
  - 오라클 권장은 항목끼리의 맞춤


### 연산
- From으로 지정한 테이블에 먼저 접근
- Select문에 특정 Column을 지정했어도 전체 Column에 대해서 엑세스 발생

### NULL
- 사용할 수 없거나, 할당되지 않은 값
- 0과 공백과는 다른 별도의 타입
- 식과 연계되어도 NULL 유지

### Column 제목 규칙
- 하나의 단어
- 첫 번째 글자는 숫자나 특수문자로 시작할 수 없음
- 대문자로 시작

### 리터럴 값
- SELECT 절 Column 부분에 오는 상수 값
- 모든 행에 동일하게 표시됨

### 연결 연산자 ||
- 열이나 문자열을 다른 열에 연결
- str + 와 유사한 기능

### char vs varchar
- char는 고정된 길이의 문자열 타입
- varchar는 가변 길이의 문자열 타입
- varchar는 최대 길이보다 작을 수 있으나 char는 공백으로 채움

### Expression in Select
##### 좁은 의미
- Select 절 기술 가능한 것 중 순수한 칼럼을 제외한 모든 것
##### 넓은 의미
- 순수한 칼럼을 포함

### DISTINCT
- 중복 행 제거
- DISTINCT 다음으로 오는 항목에 대해서 모두 중복 제거

