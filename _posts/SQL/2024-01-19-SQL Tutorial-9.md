---
layout: post
title: 9. 분석 함수
categories: SQL
tags: [DB, SQL]
---

## 분석 함수
- 테이터를 용도에 맞게 분석하여 결과를 반환하는 함수

```sql
SELECT Analytic_Func(arguments)
  OVER ([Partition By col] [ORDER BY ...] [Windowing ...])
FROM table1
```

### Ranking Family

|함수|설명|
|-|-|
|RANK|순위|
|DENSE_RANK|순위, 동순위와 관계없이 +1|
|ROW_NUMBER|ORDER BY에 의해서 정렬된 순서에 맞게 rownum 지정|
|NTILE|행을 그룹별로 구분하여 행 번호 부여|
|RATIO_TO_REPORT|전체 합계 대비 백분율|
|LISTAGG|여러 행을 하나의 행으로 출력|

##### ROW_NUMBER VS rownum
- rownum은 테이블에 저장되어 있는 순서
  - ORDER BY에 영향을 받지 않음
- ROW_NUMBER는 ORDER BY 이후에 행 순서

### Window Aggregate Family
- 윈도우를 근간으로 정렬된 ROW의 집계 값 반환
- SUM, AVG, COUNT, MAX, MIN을 추가해 확장한 형태

|함수|설명|
|-|-|
|FIRST, LAST|행 추출|
|PIVOT/UNPIVOT|가로, 세로 데이터 바꾸기|