---
layout: post
title: 컴퓨터 구조론 - 3
categories: Structure
tags: [CS, Computer Structure]
math: true
---

# 구조론 - 3

{:toc}

### Benchmarks

##### SPEC CPU Benchmark

- CPU 성능 측정
- Standard Performance Evaluation Corp(SPEC)
- 레퍼런스 모델을 만들어 비교 성능 보여줌

##### SPEC Power Benchmark

- 전력 소모량을 고려
- 성능 / 전력 소모량

##### TOP 500

- 슈퍼컴퓨터의 성능 비교

##### Green 500

- TOP 500의 성능 / 전력 소모량

##### HPCG 500

- 실생활에서의 성능 비교
- TOP 500과 연산하는 알고리즘에서 차이

### Amdahl's Law

- 컴퓨터 성능 향상에는 한계가 있다
- $T_{improved} = \frac{T_{affected}}{improvement factor} + T_{unaffected}$.
- 성능 향상을 시킬 수 없는 부분이 있기 때문에 한계 존재

### RISC-V Instruction Set

- UC Berkeley에서 개발
- RISC-V 재단에서 관리, 개발

##### Design Priciple

- Simplicity favors Regularity
- Smaller is Faster

##### Arithmetic Operations

- add, subtract
- add(sub) a, b, c
- a = b + c

```c
f = (g + h) - (i + j);
```

```assembly
add t0, g, h
add t1, i, j
sub f, t0, t1
```

##### Register Operands

- 32개의 32bit 레지스터
- 32bit 데이터를 word라고 함

<img src="https://github.com/L-Hyun/L-Hyun.github.io/blob/main/assets/CS/3-1.png?raw=true" />

##### Memory Operands

- 메인 메모리는 큰 데이터를 저장하는 데에 사용
- Load, Store
- Byte Addressed
- Little Endian 구조 채용 = 가장 오른쪽 비트가 메모리의 가장 앞쪽에 위치
  - Big Endian = 가장 왼쪽 비트가 메모리의 가장 앞쪽에 위치
- 정렬할 필요 없음

```c
A[12] = h + A[8];
```

```assembly
lw x9, 32(x22) // lw = Load Word, 4(byte, 32 = 4byte)*8 = 32
add x9, x9, x21 // h = x21
sw x9, 48(x22) // sw = Save Word, 4*12 = 48
```

##### Register vs Memory

- 레지스터가 더 빠름
- 메모리 데이터는 불러오고 저장하고 하는 과정 필요
  - 더 많은 명령어 필요
- 컴파일러가 가능한 레지스터를 사용하려고 함

##### Immediate Operands

- 레지스터 대신 상수를 매개로 연산 가능
- addi x22, x22, 4 //x22 = x22 + 4
- 레지스터를 하나 덜 씀, 명령어를 더 적게 사용

### Summary

- RISC-V 명령어 구조
- 32개의 32비트 레지스터
- 메모리에서 레지스터로 Load, Save
