---
layout: post
title: 3. WHERE
categories: SQL
tags: [DB, SQL]
---

# WHERE
- Select에 조건을 추가

```sql
SELECT [DISTINCT] {* | column | exporession }
FROM table
WHERE expression
```

### 연산
1. FROM
2. **WHERE**
3. GROUP BY
4. HAVING
5. SELECT
6. ORDER BY

##### 연산 과정
- FROM 테이블에 접근
- 각 행에 대해서 WHERE로 판별


### 비교연산자
- =, <, >, <=, >=, <>(!=, ^=)
- BETWEEN
  - BETWEEN 20 AND 70
- IN
  - in (20, 70, 110)
- LIKE
  - 문자열에서 일부 매칭
  - %로 패턴 생성

### 논리 연산자
- AND
- OR
##### 논리 연산자 우선순위
- AND가 더 우선되어 실행

### NOT
- 해당 조건에 반대되는 경우
- IN, BETWEEN, IS NULL, LIKE 등과 사용됨

### ORDER BY
- 검색된 행들을 정렬
- Default로 ASC(오름차순) 정렬
  - DESC(내림차순)
- 항상 SELECT의 마지막에 위치
- 모든 SQL 연산에서 마지막에 실행
- NULL도 정렬 가능
  - ASC인 경우 NULLS FIRST, NULLS LAST
  - DESC인 경우 NULL은 항상 맨 위