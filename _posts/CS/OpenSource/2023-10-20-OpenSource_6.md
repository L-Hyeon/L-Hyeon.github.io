---
layout: post
title: 6. 코드리뷰
categories: Open Source
tags: [CS, Open Source]
---

## 코드리뷰?

> 코드를 작성자 이외의 사람이 검수하는 것
{: .prompt-tip }

- 최선의 코드를 위한 공동의 노력

##### 필요성

- 버그, 설계 결함 예방
- 문서화, 코드 개선
- 실전 경험

##### 관련 오해

- 완벽함을 추구하지 않음
- 모두가 책임을 가지지는 않음
- 오직 교육 목적은 아님

### 과정

1. 코드 수정
2. 리뷰 요청
3. 코멘트 작성
4. 코멘트 반영
5. 수정 허용
6. 수정

##### LGTM

- 코멘트 과정에서 수락을 의미
- 나에게는 괜찮아 보인다는 표면적 의미

##### clang-format

- 코드 스타일을 위한 대표적 도구
- 기본적인 포멧 조정

### Bad Smells

- 가독성, 확장성, 유연성이 부족한 코딩 패턴
- 스타일 가이드의 적용으로 일부는 쉽게 제거 가능