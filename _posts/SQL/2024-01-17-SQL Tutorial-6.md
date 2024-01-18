---
layout: post
title: 6. JOIN
categories: SQL
tags: [DB, SQL]
---

## JOIN
- 서로 다른 테이블을 합쳐서 표시
- Equal Join(Natural)
- Equal Join(on), Non-Equal Join
- Equal Join(using)
- Outer Join
- Cross Join
##### ANSI 비표준(Oracle 고유의 조인)
```sql
SELECT table1.col1, table2.col2, table1.pk
FROM table1, table2
WHERE table1.pk = table2.pk
```

### 모호한 칼럼의 이름 구분
- 테이블 접두어를 사용해서 열 이름 구분
- 접두어 사용 시 구문 분석 속도 향상

### NATURAL JOIN
- 공통된 이름의 모든 칼럼을 기준으로 두 테이블을 병합
- INNER JOIN과 달리 공통된 칼럼을 한 번만 표시
- JOIN의 키가 되는 칼럼은 접두어를 사용할 수 없음

```sql
SELECT *
FROM table1 NATURAL JOIN table2
```

### USING
- JOIN에 참여하는 칼럼을 선택
- 조건으로 사용되지 않음
- JOIN의 키가 되는 칼럼은 접두어를 사용할 수 없음

```sql
SELECT pk table1.col1, table2.col2
FROM table1 JOIN table2 USING (pk)
```

### ON
- 임의의 JOIN 조건을 지정하거나 조인할 열을 지정 가능
- equi join, non-equi join 둘 다 사용 가능
  - 조건을 상세하게 설정 가능

```sql
SELECT table1.col1, table2.col2, pk
FROM table1 JOIN table2 ON table1.pk = table2.pk
```

```sql
SELECT table1.col1, table2.col2. table1.money
FROM table1 JOIN table2 ON table1.money BETWEEN table2.max AND table2.min
```

### USING vs ON vs NATURAL JOIN

| |USING|ON|NATURAL|
|-|-|-|
|JOIN에 참여하는 칼럼 선택|O|O|X|
|Non-Equi Join|X|O|X|

### OUTER JOIN
- JOIN을 할 때는 항상 공통된 값이 존재하는 행만 표시됨
- 공통된 값이 존재하지 않더라도 결과값으로 필요한 경우 존재

##### ANSI 표준 Ex
```sql
SELECT pk, table1.col1, table2.col2
FROM table1 LEFT OUTER JOIN table2 ON table1.pk = table2.pk
```
- table1의 내용이지만 pk가 같지 않아 JOIN이 되지 않는 것들도 표시
  - table2.col2는 NULL 값으로 들어감

##### Oracle Ex
- (+)가 붙은 쪽이 NULL 가능
- 양쪽에 (+)를 붙일 수는 없음

```sql
SELECT pk table1.col1, table2.col2
FROM table1, table2
WHERE table1.pk(+) = table2.pk
```

### Cartesian Product
- CROSS JOIN
- JOIN 조건이 생략된 경우
- 모든 행이 JOIN
  - table1의 행 개수 * table2의 행 개수 만큼의 결과가 나옴