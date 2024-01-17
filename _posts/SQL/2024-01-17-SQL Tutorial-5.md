---
layout: post
title: 5. 다중 행 함수
categories: SQL
tags: [DB, SQL]
---

## 다중 행 함수
- 여러 행에 대해서 연산을 진행하는 함수

### 그룹 함수
- 행 집합 연산을 수행하여 그룹별로 하나의 결과를 산출
- 인수는 하나만 가능
- NULL은 그룹함수 연산에 참여시키지 않음

|함수|설명|
|-|-|
|AVG|평균|
|COUNT|개수 세기|
|MAX|최대값|
|MIN|최소값|
|SUM|합계|
|STDDEV|표준편차|
|VARIANCE|분산|

##### COUNT
- 해당 칼럼에 데이터가 존재(NULL이 아닌)하는 행의 수
- 모든 행에 대해서 인수로 들어온 값이 NULL이 아닌 경우 +1
  - count(0) 이렇게 하면 count(*)과 동일한 결과(테이블 행의 수)

## GROUP BY
- 데이터의 소그룹 생성

```sql
SELECT column1, column2
FROM table
WHERE cond
HAVING group_cond
GROUP BY column1
ORDER BY column1
```

### HAVING
- GROUP BY로 묶은 그룹을 조건을 통해 제한
- 집계된 정보를 기반으로 제한

### ROLLUP
- 소그룹 간 통계를 계산하는 함수
- GROUP BY로 묶은 그룹의 통계와 전체 통계를 볼 수 있음
- 맨 처음 명시한 칼럼에 대해서만 소그룹 통계 표시

### CUBE
- 소그룹 간 다차원적 소계 계산
- ROLLUP과 달리 GROUP BY절에 명시한 모든 칼럼에 대해서 통계를 계산

### GROUPING SETS
- 특정 항목에 대한 통계 계산
- 앞 2개와 달리 소그룹별 통계만 표시
