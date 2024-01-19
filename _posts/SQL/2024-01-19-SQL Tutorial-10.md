---
layout: post
title: 10. DML
categories: SQL
tags: [DB, SQL]
---

## DML
- Data Manipulation Language
1. 추가
2. 수정
3. 삭제


### INSERT
- 테이블에 행을 추가
- 입력되지 않은 값들은 NULL로 입력됨
  - 명시적으로 NULL 가능

```sql
INSERT INTO table1
VALUES(va1, val2)
```

```sql
insert into departments
select department_id + 300, department_name || '_1', null, null
from departments
where department_id <= 100;
```

### UPDATE
- 테이블의 행을 수정

```sql
UPDATE table1
SET col = val [, col1 = val1]
[WHERE cond]
```

### DELETE
- 테이블의 행을 삭제

```sql
DELETE [FROM] table1
[WHERE cond]
```

