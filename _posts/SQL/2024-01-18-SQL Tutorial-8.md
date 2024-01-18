---
layout: post
title: 8. 서브쿼리
categories: SQL
tags: [DB, SQL]
---

## 서브 쿼리
- Query 안에 위치하는 쿼리
- Main Query 이전에 실행되어 값으로 활용됨
- 괄호로 묶어 사용

### 위치
- GROUP BY를 제외한 모든 위치에 가능
- 보통 WHERE, FROM에 사용

### SubQuery in SELECT
```sql
select col1, count((select * from table1))
from table1
```

##### 인덱스
- SELECT에서 서브 쿼리를 넣는 경우 모든 행마다 서브쿼리 연산 실행
  - 성능에 치명적인 영향
- 테이블에서 Read 속도 향상을 위해 사용
- 특정 조건을 만족하는 행의 Row ID를 저장하고 있음
  - 해당 조건이 들어오면 Row ID를 활용해 바로 접근

### SubQuery in FROM
```sql
select * 
from (select department_id, round(avg(salary)) as sal
  from employees
  where department_id is not null
  group by department_id
  order by sal desc)
where rownum < 4
```
- 서브쿼리 쓰지 않고 rownum 제한하면 처음 select에서 4개만 가져와서 정상 출력 안 됨
- FROM 절에 서브쿼리를 쓰는 경우 *을 잘 쓰지 않음
  - 서브쿼리의 내용을 정상적인 칼럼으로 사용하지 못함
  - as를 통해 다시 명명해야 함

##### Row Num
- 반환되는 행이 결과의 몇 번째 행인지 표시
- WHERE rownum <= 3으로 표시하면 3개의 결과만 표시

### SubQuery in WHERE
- Main Query 실행 전 미리 실행한 후 결과만 이용
- 가독성을 위해서 서브쿼리는 연산자 오른쪽에 위치
 
### 상호 연관 서브쿼리
- 메인 쿼리의 결과가 서브 쿼리 실행에 영향을 주는 쿼리
- 서브쿼리에서는 메인 쿼리의 칼럼 사용 가능하나 반대는 불가

1. 메인 1행 실행
2. 서브쿼리 실행
3. 메인에 결과 반영
4. 다음 행 실행

##### EXISTS 연산자
- 상관 서브쿼리에서만 사용 가능
- 메인 쿼리에서 검색된 값이 서브쿼리의 집합에 존재하는 지 확인
- 존재하면 TRUE Flag 반환
  - 상세 비교를 하지 않아서 IN보다 속도가 빠름
- 대부분은 IN으로 바꿔 쓸 수 있음
  - NOT EXISTS는 NULL에 대해 True, NOT IN은 False 반환

##### IN 연산자
- 유무 확인
- a in b => a = b[0] or a = b[1] ...

### WITH
- SELECT에 서브쿼리를 넣으면 여러번 처리되어 속도가 감소하는 것을 개선
- 먼저 연산해서 임시 테이블로 저장해놓고 그 결과를 활용
