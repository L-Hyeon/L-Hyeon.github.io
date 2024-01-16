---
layout: post
title: 4. 단일 행 함수
categories: SQL
tags: [DB, SQL]
---

## 단일 행 함수
- 각 행에 개별적으로 실행되며 하나의 값 반환
- SELECT, WHERE, ORDER BY에 사용 가능
- 중첩 사용 가능

### 다중 행 함수
- 집계함수, 그룹함수, 윈도우 함수로 구성
- 여러 행에 대해 종합적으로 실행
  - COUNT(집계), CUBE(그룹), RANK(윈도우) 등

### 문자 함수
-  인수가 문자인 함수, 문자/숫자 반환

|함수 | 설명 | 
|-|-|
|LOWER | 모든 문자를 소문자로|
|UPPER| 모든 문자를 대문자로|
|INITCAP| 단어 첫 글자만 대문자로|
|CONTCAT| 문자열 결합|
|SUBSTR| 문자열 추출|
|LENGTH| 문자의 길이 반환|
|INSTAR|문자열 내 특정 패턴의 위치를 반환|
|LAPD, RPAD | 왼쪽 오른쪽 패딩|
|REPLACE | 문자열 대체|


### 숫자 함수
- 인수가 숫자이며 숫자를 반환

|함수 | 설명 | 
|-|-|
|ROUND | 반올림|
|TRUNC|  버림|
|MOD | 나머지 값 반환|
|SIGN | 음, 양수 판별(1, 0, -1)|
|ABS| 절대값 반환|
|FLOOR|정수부 버림|
|CEIL | 정수부 올림|

### 날짜 함수
- 시스템이 저장하고 있는 값
  - 내부 숫자 형식(세기, 연도, 월, 일, 시, 분, 초)
  - timestamp는 초단위 아래도 포함
- +, - 연산 가능

|함수 | 설명 | 
|-|-|
|SYSDATE| 시스템에 저장된 현재 날짜 반환|
|SYSTIMESTAMP| 시스템에 저장된 현재 날짜를 Timestamp 타입으로 반환|
|CURRENT_DATE| 현재 Session의 날짜 반환|
|CURRENT_TIMESTAMP| 현재 Session의 날짜를 Timestamp 타입을 반환|

### 날짜 조작 함수

|함수 | 설명 | 
|-|-|
|MONTHS_BETWEEN(D1, D2) | D1, D2 두 날짜 간의 개월 수|
|ADD_MONTHS(D1, N) | D1에 N개월을 더함|
|NEXT_DAY(D1, 'CHAR') | D1보다 이후 날짜이며 지정한 요일에 해당하는 날짜 |
|LAST_DAY(D1) | D1 날짜 월에 마지막 날짜를 리턴
|ROUND(D1, 'dd')|날짜 반올림, default는 dd(시간에서 반올림)|
|TRUNC(D1, dd')|날짜 버림|

## 변환 함수
- 데이터 타입을 변환하는 함수
- 암시적 변환
  - 쿼리 실행기에서 자동으로 데이터 변환
- 명시적 변환
  - 사용자가 쿼리에 데이터 변환을 명시

### 암시적 데이터 유형 변환
- 자동으로 데이터 타입을 변환
- VARCHAR2/CHAR <-> 숫자/날짜
- 권장되지 않음

##### 숫자/날짜 => 문자 변환
- 아래 경우를 제외하고는 존재하지 않음
1. ||(연결 연산자)
2. LIKE
3. 문자 함수

### 명시적 데이터 유형 변환

|함수|Source|Target|
|-|-|-|
|TO_NUMBER|VARCHAR2/CHAR|NUMBER|
|TO_DATE|VARCHAR2/CHAR|DATE|
|TO_CHAR|NUMBER|VARCHAR2/CHAR|
|TO_CHAR|DATE|VARCHAR2/CHAR|

##### 날짜 형태 Format
- 포멧 사용 시 기본적으로 RPAD 붙음
  - 결과값으로 나올 수 있는 가장 긴 문자열 기준
  -  포멧문 앞에 fm을 붙이면 PAD 삭제 가능
- 'NLS_DATE_LANGUAGE=ENGLISH'로 언어 변경 가능

|Format|설명|
|-|-|
|YYYY|년도|
|RRRR|세기 정보를 포함한 년도(00~49 = 이전 세기, 50~99 = 이후 세기)|
|YEAR|영어 년도, PAD 有|
|MM|월|
|MONTH / MON|영어 월, PAD 有|
|DAY / DY|영어 요일, PAD 有|
|Q|분기|
|WW / W|일년 주차 / 한달 주차|
|DD|일자|
|AM / PM|오전/오후, 둘 중 아무거나 써도 됨|
|HH / HH24|시간|
|MI|분|
|SS|초|
|D|일주일 중 몇 번째 날인지|

##### 숫자 형태 Format
- 9를 통해서 Formatting하는 경우 문자로 변환함에도 불구하고 우측 정렬

|Format|설명|
|-|-|
|9|일반 숫자(0~9), 길이가 충분해야 표시 가능|
|0|0(Zero Pad), 0이 있으면 9가 뒤에 붙어도 자릿수 고정|
|$|부동 달러 기호 표시|
|L|부동 로컬(OS 기준) 통화 기호 표시|
|, / G|천 단위 구분자 쉼표|
|. / D|소수점 구분자|

##### TO_NUMBER, TO_DATE
- TO_NUMBER(CHAR[, 'format'])
- 변환할 문자열에 해당하는 포멧을 전달해 확실하게 변환
- TO_DATE를 사용하는 경우 선언하지 않으면 00으로 변경
  - 정확한 비교를 위해서 범위 비교, TRUNC, 테이블 값을 문자로 변경 등을 이용한다.


##### 기타 함수
- NVL(expr1, expr2)
  - NULL 값을 실제 값으로 변환
  - expr1이 NULL인 경우 expr2 값을 사용
  - expr1과 expr2의 데이터 타입은 동일해야 한다.
- NVL2(expr1, expr2, expr3)
  - (expr1 IS NULL) ? expr2 : expr3
- NULLIF(expr1, expr2)
  - expr1과 expr2이 같으면 NULL, 다르면 expr1 반환
  - expr1은 NULL일 수 없음
- COALESCE(expr1, expr2, ... exprn)
  - 최초로 NULL이 아닌 것을 반환
  - 리스트에 들어가는 모든 식은 동일한 타입이어야 함

## 조건부 표현식
- SQL 쿼리에서 IF-THEN-ELSE의 조건식을 사용

### DECODE
- Oracle에서만 지원하는 함수
- col|expr에 해당하는 것이 searchN과 같으면 resN을 반환
- default는 NULL

```sql
DECODE(col | expr, search1, res1
  [, search2, res2, ...]
  [, default]
)
```

### CASE
- ANSI 표준 조건문
- CASE ... WHEN ... THEN... ELSE ... 형태

```sql
CASE expr
  WHEN comp1 THEN ret1
  [WHEN comp1 THEN ret2
  ELSE else_ret]
```
