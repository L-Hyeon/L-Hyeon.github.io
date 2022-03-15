---
layout: post
title: 알고리즘 - 3
categories: Algorithm
tags: [CS, Algorithmm]
---

# 알고리즘 - 3

### Analyzing Algorithms and Problems(Cont.)

##### Space Usage and Simplicity

- Space Usage
  - Amout of Space Used depends on Input
    - 인풋 타입, 크기에 따라 변화 == Worst, Average 분석 가능
  - Time and Space **Tradeoff(반비례)**
- Simplicity is Virture(미덕)
  - Correctness 분석이 쉬워짐
  - 가독성이 높아 프로그램 작성, 디버깅, 수정이 쉬워짐

##### Problem Complexity

_모든 문제가 고유한 복잡도를 가지고 있음_

- How to Analyze Problem Complexity
  - 알고리즘의 클래스 선택
    - 어떤 연산으로 해결할 것인지
    - Basic Operation 선택
  - 문제를 해결하기 위해 필요한 **기본연산의 최소 횟수**
- Optimal
  - 가능한 최고의 알고리즘 == Best Possible

##### How To Show an Algorithm is Optimal

알고리즘 A의 Worst-Case Complexity $$W_A(n)$$, 문제의 Complexity $$F(n)$$

- if W_A(n) == F(n)
  알고리즘 A is **Optimal**
- else
  - 더 좋은 알고리즘이 존재할 수 있다
- or
  더 좋은 **Lower Bound**(Complexity of Problem)가 존재할 수 있다

##### ex. Matrix Multiplication

- 두 행렬의 곱셈
- 하나의 원소를 계산하기 위해 곱셈 n번, 덧셈 n-1번 필요 == $$O(n)$$ time
  결과 행렬은 nxn이고, $$n^2$$개의 원소를 가지기 때문에 $$O(n^3)$$ Time
  == Upper Bound = $$O(n^3)$$ Time
- 현재 Upper Bound = $$O(n^{2.3728596})$$

##### ex. Devise A

- Problem
  - Find the Largest Entry in Array E sized n

```c
  int findMax(int[] E, int n){
    int max = E[0];
    for (int i = 1; i < n; i++){
      if (max < E[i])
        max = E[i];
    }
    return max;
  }
```

- Basic Operation

  - 배열의 원소 E[i]와 현재까지 가장 큰 원소 max를 비교하는 연산

- Worst-Case

  - n-1번의 비교를 해야 함 == $$W(n) = n - 1$$

- Problem Complexity

  - Class of Algorithms
    - copy, compare
  - Finding F(n)

    1. 배열에서 중복이 없다고 가정
    2. n개의 다른 원소들에서 n-1개의 원소들은 최대값이 아님
    3. 한 원소가 최대값이 아님을 알기 위해서는 최소 1번은 다른 원소와 비교를 해야 함
    4. n-1개의 원소들은 각각 1번씩은 다른 원소와 비교해야 최대값이 아님을 알게 될 수 있음
    5. 최소 n-1번의 기본연산(비교)가 필요함
    6. $$F(n)=n-1$$

- 결론
  - $$W(n) == F(n)$$이므로 알고리즘은 Optimal

### Classifying Functions by Their Asymptotic Growth Rates

##### Classifying Functions

_계수와 상수를 제외한 함수들을 비교하고 분류_

- Big Omega

  - $$\Omega(g)$$
  - 적어도 함수 g보다는 증가율이 **같거나 빠른** 함수들의 집합

- Big Theta

  - $$\theta(g)$$
  - 적어도 함수 g보다는 증가율이 **같은** 함수들의 집합

- Big Oh

  - $$O(g)$$
  - 적어도 함수 g보다는 증가율이 **같거나 느린** 함수들의 집합

##### Big X sets

양수에 대한 함수 $$f, g$$
상수 $$c$$, 자연수 $$n_0$$

- $$O(n)=f(n)\leq c \times g(n)\,for\,n \geq n_0$$ == Upper Bound
- $$\Omega(n)=f(n)\geq c \times g(n)\,for \,n \geq n_0$$ == Lower Bound
- $$\theta(n)=O(g) \cap \omega(n)$$

##### Little x sets

- $$o(g), \omega(g)$$ = 같은 경우 제외
