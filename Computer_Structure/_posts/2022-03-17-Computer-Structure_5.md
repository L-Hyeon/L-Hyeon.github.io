---
layout: post
title: 컴퓨터 구조론 - 5
categories: Structure
tags: [CS, Computer Structure]
---

# 구조론 - 5

{:toc}

### Logical Operations

<img src="https://github.com/L-Hyun/L-Hyun.github.io/blob/main/assets/CS/5-1.png?raw=true" />

- Not 연산자는 1111로 XOR 하면 됨

##### Shift Logical

- SLL, SRL
- 비트를 움직인 후 빈자리는 0으로 채움

##### Shift Right

- SRL의 경우 맨왼쪽의 부호 비트 관계없이 비트 이동
- **Shift Right Arithmetic(SRA)**, 부호비트는 두고 나머지 비트 이동

<img src="https://github.com/L-Hyun/L-Hyun.github.io/blob/main/assets/CS/5-2.png?raw=true" />

##### Shift Opertaions

<img src="https://github.com/L-Hyun/L-Hyun.github.io/blob/main/assets/CS/5-2.png?raw=true" />

- I-format과 비슷함
- shamt = Shift Amount

### Conditional Operations

- beq
  - beq, rs1, rs2, L1
  - if (rs1 == rs2): goto L1
- bne
  - bne rs1, rs2, L1
  - if (rs1 != rs2): goto L1
- blt
  - blt rs1, rs2, L1
  - if (rs1 < rs2): goto L1
- bge

  - bge rs1, rs2, L1
  - if (rs1 >= rs2): goto L1

- rs1, rs2의 위치를 조정해 blt, bge만 사용

- bltu, bgeu
  - blt와 bge의 unsigned 버전

##### Ex

```c
if (i == j) f = g + h;
else f = g - h;
```

- 만족하지 않는 경우 다른 위치로 이동해야 함
- bne 사용

```assembly
x22, x23, Else
  bne x22(i), x23(j) Else
  add x19(f), x20(g), x21(h)
  beq x0, x0, Exit // unconditional == 무조건 실행
Else:
  sub x19, x20, x21
Exti:
...

```

##### Loop Statements

```c
while (save[i] == k) i += 1;
```

```assembly
Loop:
  slli x10, x22, 2
  add x10, x10, x25
  lw x9, 0(x10)
  bne x9, x24, Exit
  addi x22, x22, 1
  beq x0, x0, Loop
```

##### 연습문제

```c
for(i = 0; i < n; i++)
  a += 2;
```

i = x5, n = x6, a = x7

```assembly
Loop:
  bge x5(i), x6(n), End
  add x7(a), x7, 2
  add x5, x5, 1
  beq x0, x0, Loop
End:
  ...
```

### Procedure Calling

- Execute Correct Sequence of Instructions
- Pass Arguments and Obtain Return Value
- Preserve Caller's Registers

##### Procedure Call Instructions

- jal x1, Label
  - 다음 명령어의 주소를 x1에 저장
  - Label로 이동
- jalr x0, 0(x1)
  - jal과 비슷하지만 0+x1값으로 이동
  - x0값은 바뀔 수 없으므로 rd로 사용
  - 다시 돌아올 때 사용
