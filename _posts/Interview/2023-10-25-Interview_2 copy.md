---
layout: post
title: 인터뷰 준비 - 알고리즘
categories: Interview
tags: [CS, Interview]
math: true
---

## 정렬

| 이름      | 최선          | 평균          | 최악          | 비고                            |
| --------- | ------------- | ------------- | ------------- | ------------------------------- |
| Selection | $O(n)$        | $O(n^2)$      | $O(n^2)$      |                                 |
| Insertion | $O(n)$        | $O(n^2)$      | $O(n^2)$      |                                 |
| Bubble    | $O(n)$        | $O(n^2)$      | $O(n^2)$      |                                 |
| Merge     | $O(n \log n)$ | $O(n \log n)$ | $O(n \log n)$ |                                 |
| Quick     | $O(n \log n)$ | $O(n \log n)$ | $O(n \log n)$ | Merge에 비해 메모리 사용량 적음 |
| Tim       | $O(n)$        | $O(n \log n)$ | $O(n \log n)$ |                                 |

##### Selection Sort

##### Insertion Sort

- 길이가 작은 경우 효과적

##### Bubble Sort

##### Merge Sort

##### Quick Sort

##### Count Sort

##### Timsort

- Java, Python, cPython에서 사용
- Insertion과 Merge의 결합
- 현실 데이터와 같이 어느정도 정렬된 부분이 있는 경우를 고려

1. 작은 부분으로 분할
2. 각각을 Insertion Sort 실행
3. 다시 전체 결합
