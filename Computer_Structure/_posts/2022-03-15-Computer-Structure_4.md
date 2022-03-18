---
layout: post
title: 컴퓨터 구조론 - 4
categories: Structure
tags: [CS, Computer Structure]
---

# 컴퓨터 구조론 - 4

{:toc}

### Number in Computer

##### Unsigned Binary Integers

- 0 ~ $2^n - 1$
  $$x = x_{n - 1}2^{n - 1} + x_{n-2}2^{n-2}+ ... + x_02^0$$.

##### Signed Integer 2s-Complement

- 2의 보수로 표현 (0과 1을 뒤집은 후 + 1)
- $$-2^{n-1}$$ ~ $$2^{n - 1}-1$$.
  $$x = -x_{n - 1}2^{n - 1} + x_{n-2}2^{n-2}+ ... + x_02^0$$.

##### Addition

- 일반적인 이진수 덧셈과 동일
- 표현 범위를 넘어가는 캐리는 버림
- 오버플로우 발생 가능

##### Subtraction

- 빼는 숫자를 2의 보수로 바꾼 후 덧셈
- 표현 범위 넘어가는 캐리 버림
- 오버플로우 발생 가능

##### Sign Extension

- 부호를 유지한 채로 비트 수만 늘리기 위해
- Unsigned Value는 그냥 0을 붙여주면 됨
- 맨앞자리 비트를 그대로 늘려주면 됨
  ex) 0010 -> 0000 0010(2)
  ex) 1110 -> 1111 1110(-2)

##### Hexadecimal Number

- 16진수
- 16진수 1자리 = 2진수 4자리

### RISC-V Instructions

##### R format

<img src="https://github.com/L-Hyun/L-Hyun.github.io/blob/main/assets/CS/4-1.png?raw=true" />

- **rd = rs1 (연산) rs2**
- opcode: Operation code
- rd: Destination register
- funct3: 3-bit Function code(additnal)
- rs1, rs2: Source register
- funct7: 7-bit Function code(additnal)
- funct7, funct3은 opcode의 비트가 부족한 경우 사용

##### I Format

<img src="https://github.com/L-Hyun/L-Hyun.github.io/blob/main/assets/CS/4-2.png?raw=true" />

- **rd <- rs1...immediate**
- Immediate arithmetic, Load insstructions
- rs1: Source/Base Register
- Immediate: Constant or Offset added to base

ex. ld x9, 64(x22)
x9 = rd
64 = immediate
x22 = rs1

##### S Format

<img src="https://github.com/L-Hyun/L-Hyun.github.io/blob/main/assets/CS/4-3.png?raw=true" />

- **rs2 -> rs1...imediate**
- Store
- rs1: Base address
- rs2: Source Operand
- immediate: Offset added to base address

ex. sd x9, 64(x22)
x9 = rs2
64 = immediate
x22 = rs1

##### Translation to Machine Language

```c
A[30] = h + A[30] + 1;
```

```assembly
ld x9, 240(x10) //A[30] 불러오기, 30*8(32비트)=240
add x9, x21, x9 //x21 = h
addi x9, x9, 1 //1=immediate => addi 사용
sd x9, 240(x10) //A[30]에 저장
```

### Stored Program Computers

### 연습문제

##### Problem

- RISC-V machine code -> assembly
- 0100 0000 0101 0011 1000 0011 0011 0011

##### Answer

- opcode 011 0011 = add or sub
- funct7 0100 000 = sub
- rs2 0 0101 = x5
- rs1 0011 1 = x7
- funct3 000
- rd 0011 0 = x6

- **sub x6, x7, x5**
