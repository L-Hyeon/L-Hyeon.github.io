---
layout: post
title: 컴퓨터 구조론 - 2
categories: Structure
tags: [CS, Computer Structure]
---

# 컴퓨터 구조론 - 2

### Response Time and Throughput

- Response Time
- Throughput
  - total work / unit time

### Relative Performance

- $$Performance = 1/Execution Time$$
- X is n times faster than Y
  $$Performance_x / Performance_y$$
  $$=Time_x/Time_y = n$$

### Measuring Execution Time

- Elapsed time
  - 총 반응 시간, 모든 측면 고려
- CPU Time
  - user cpu time - 순수 프로그램 실행 시간
  - system cpu time - os가 관여한 시간

### CPU Clocking

- 주기적인 클락에 따라서 운영됨
- clock period = 1/clock frequency
  \*\*cpu는 조합회로와 순차회로 구성

### CPU Time

$$CPU Time = Clock Cycles \times Cycle Time$$

- 사이클 횟수 줄이기
- 주파수 늘리기

### Cycle Per Instruction

_$$CPI = Cycle / Instruction\,Count$$_
_$$CPU\,Time = Instruction\,Count \times CPI \times Cycle Time$$_

- 프로그램에 따라 Instruction Count 달라짐

### CPI Example

Instuction Count I
A, Cycle Time = 250ps, CPI = 2.0
B, Cycle Time = 500ps, CPI = 1.2
$$Time_A = I\times250ps\times2.0 = 500ps\times I$$
$$Time_B = I\times500ps\times1.2 = 600ps\times I$$
$$Time_B/Time_A = 600ps/500ps = 1.2$$
$$B\,is\,1.2\,times\,faster\,than\,A$$

### CPI (cont.)

$$\displaystyle Clock\,Cycles = \sum_{i=1}^{n}CPI_i\times Instruction\,Time_i$$

### Affects Performance

- Algorithm
- Programming Language, Compiler, Architecture
- Processor, Memory system
- I/O

### 연습문제

$$IC = 2.389*10^{12}$$
$$Execution Time = 750s$$

a) cycle time = 0.333ns이면 CPI?
CPI = cycles/IC
$$750s/0.333ns/2.389*10^{12} = 0.943$$

b) IC 10% 증가, CPI 5% 감소 time?
$$time = CPI*IC*Cycle$$
$$1.1*0.95 = 1.045$$

### Processor Trend

- 2000년 전까지는 클럭 주파수가 계속해서 상승
- BUT, 전력 소모량 역시 계속해서 증가
- 전력소모량을 염두해 프로세서 수를 늘리는 방식 채용

$$Power = Capacity\,Load\times Voltage^2 \times Frequency$$

### Reducing Power

- 주파수를 약간만 줄여도 파워 소모량에 엄청난 변화
- 주파수를 조금만 줄이고 코어 수를 늘리자

### Summary

- CPU Time 계산
- 전력 문제로 주파수를 높일 수 없어 멀티 코어 아키텍쳐가 나옴
