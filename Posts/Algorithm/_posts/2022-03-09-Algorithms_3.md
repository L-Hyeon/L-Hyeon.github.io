---
layout: post
title: 알고리즘 - 3
categories: Algorithm
tags: [CS, Algorithmm, 알고리즘]
---

<style type='text/css'>
  @font-face {
    font-family: 'Cafe24SsurroundAir';
    src: url('https://cdn.jsdelivr.net/gh/projectnoonnu/noonfonts_2105_2@1.0/Cafe24SsurroundAir.woff') format('woff');
    font-weight: normal;
    font-style: normal;
  }
  .article {
    font-family: 'Cafe24SsurroundAir';
  }
  .contentsItems { color: black; }
  .contentsItems:hover {
    color: black;
    text-decoration: underline;
  }
  .title {
    font-size: 30px;
    border-bottom: 3px solid #6667ab;
    border-left: 20px solid #6667ab;
    padding-left: 5px;
    margin-bottom: 10px;
    margin-top: 30px;
  }
  .subtitle {
    margin-top: 20px;
	  font-size: 25px;
	  color: #5e5e7d;
  }
  .subsub {
    font-size: 17px;
    color: #13356b;
  }
  .section {
    padding-left: 15px;
  }
  .define{
    font-weight: bold;
    padding-left: 15px;
  }
  .red{
    display: inline;
    color: #a12d27;
  }
  .disabled {
    display: inline;
    color: #777777;
  }
</style>

<div class="title">Contents</div>

- <div class="disabled">Introdcution</div>
- <div class="disabled">Mathematical Background</div>
- <div href="#Analyzing" class="contentsItems">Analyzing Algorithms and Problems</div>
- <div href="#Asymptotic" class="contentsItems">Classifying Functions by Their Asymptotic Growth Rates</div>
- <div class="disabled">Searching an Ordered Array</div>

<div id="Analyzing" class="title">Analyzing Algorithms and Problems(Cont.)</div>

<div class="subtitle">Space Usage and Simplicity</div>
<div class="section">
  <div class="subsub">Space Usage</div>
  - Amout of Space Used depends on Input
      - 인풋 타입, 크기에 따라 변화 == Worst, Average 분석 가능
  - Time and Space <div class="red">Tradeoff(반비례)</div>
  <div class="subsub">Simplicity is Virture(미덕)</div>
  - Correctness 분석이 쉬워짐
  - 가독성이 높아 프로그램 작성, 디버깅, 수정이 쉬워짐
</div>

<div class="subtitle">Problem Complexity</div>
<div class="define">모든 문제가 고유한 복잡도를 가지고 있음</div>

<div class="subsub">How to Analyze Problem Complexity</div>
- 알고리즘의 클래스 선택
    - 어떤 연산으로 해결할 것인지
    - Basic Operation 선택
- 문제를 해결하기 위해 필요한 <div class="red">기본연산의 최소 횟수</div>
<div class="subsub">Optimal</div>
<div class="define">가능한 최고의 알고리즘 == Best Possible</div>

<div class="subtitle">How To Show an Algorithm is Optimal</div>
<div class="section">

알고리즘 A의 Worst-Case Complexity $W_A(n)$, 문제의 Complexity $F(n)$

  <div class="subsub">if W_A(n) == F(n)</div>
  알고리즘 A is <div class="red">Optimal</div>
  <div class="subsub">else</div>
  - 더 좋은 알고리즘이 존재할 수 있다
  <div class="subsub">or</div>
  더 좋은 <div class="red">Lower Bound</div>(Complexity of Problem)가 존재할 수 있다
</div>

<div class="subtitle">ex. Matrix Multiplication</div>
<div class="section">

- 두 행렬의 곱셈
- 하나의 원소를 계산하기 위해 곱셈 n번, 덧셈 n-1번 필요 == $O(n)$ time
  결과 행렬은 nxn이고, $n^2$개의 원소를 가지기 때문에 $O(n^3)$ Time
  == Upper Bound = $O(n^3)$ Time
- 현재 Upper Bound = $O(n^{2.3728596})$
</div>

<div class="subtit">ex. Devise A</div>
<div class="section">
  <div class="subsub">Problem</div>
  Find the Largest Entry in Array E sized n
  <div class="subsub">Pseudo Code</div>

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

  <div class="subsub">Basic Operation</div>
  배열의 원소 E[i]와 현재까지 가장 큰 원소 max를 비교하는 연산

  <div class="subsub">Worst-Case</div>

n-1번의 비교를 해야 함 == $W(n) = n - 1$

  <div class="subsub">Problem Complexity</div>

- Class of Algorithms
  - copy, compare
- Finding F(n)

  1. 배열에서 중복이 없다고 가정
  2. n개의 다른 원소들에서 n-1개의 원소들은 최대값이 아님
  3. 한 원소가 최대값이 아님을 알기 위해서는 최소 1번은 다른 원소와 비교를 해야 함
  4. n-1개의 원소들은 각각 1번씩은 다른 원소와 비교해야 최대값이 아님을 알게 될 수 있음
  5. 최소 n-1번의 기본연산(비교)가 필요함
  6. $F(n)=n-1$

  <div class="subsub">결론</div>

$W(n) == F(n)$이므로 알고리즘은 Optimal

</div>

<div id="Asymptotic" class="title">Classifying Functions by Their Asymptotic Growth Rates</div>
<div class="subtitle">Classifying Functions</div>
<div class="define">계수와 상수를 제외한 함수들을 비교하고 분류</div>
<div class="section">
<div class="subsub">Big Omega</div>

- $\Omega(g)$
- 적어도 함수 g보다는 증가율이 <div class="red">같거나 빠른</div> 함수들의 집합

<div class="subsub">Big Theta</div>

- $\theta(g)$
- 적어도 함수 g보다는 증가율이 <div class="red">같은</div> 함수들의 집합

<div class="subsub">Big Oh</div>

- $O(g)$
- 적어도 함수 g보다는 증가율이 <div class="red">같거나 느린</div> 함수들의 집합

</div>

<div class="subtitle">Big X sets</div>
<div class="section">

양수에 대한 함수 $f, g$
상수 $c$, 자연수 $n_0$

- $O(n)=f(n)\leq c \times g(n)\,for\,n \geq n_0$ == Upper Bound
- $\Omega(n)=f(n)\geq c \times g(n)\,for \,n \geq n_0$ == Lower Bound
- $\theta(n)=O(g) \cap \omega(n)$

</div>

<div class="subtitle">Little x sets</div>

- $o(g), \omega(g)$ = 같은 경우 제외