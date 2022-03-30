### RISC vs CISC

##### RISC

- Reduced Instruction Set Computer
- 명령어의 종류가 적음
- 코드가 길어짐 = Low CPI
- Simple Insturction Decoding = High Clock Frequency
- load/save에 사용하는 레지스터가 많이 필요함

##### CISC

- Complex Instruction Set Computer
- 명령어의 종류가 다양함
  - 연산할 때 사용하는 명령어의 개수가 적음 = Small Code Size
  - 하나의 명령을 실행하는 데에 걸리는 시간이 늘어날 가능성 높음
- 명령어를 저장하는 공간이 많이 필요함

### Addition Overflow

- Out of Range
- 양수 + 음수 => 오버플로우 발생 불가능
- 양수 + 양수 => 음수면 오버플로우
- 음수 + 음수 => 양수면 오버플로우

### Arithmetic for Multimedia

- 오버플로우 발생 시, 결과값을 가장 큰/작은 값으로 고정

### Multiplication

- Multiplier - shift right
- Multiplicand - shift left
- ALU - 덧셈기

1. Multiplier가 shift right해서 버리는 값을 전송 (0 or 1)
2. 1이면 Multiplicand 값을 결과에 더함
   - 0이면 그대로
3. Multiplier Shift Right
4. Multiplicand Shift Left

<img src="https://github.com/L-Hyun/L-Hyun.github.io/blob/main/assets/CS/8-1.png?raw=true" />

##### Optimized

- Multiplier, Multilicand, ALU는 독립적으로 실행됨
- 3개를 병렬로 실행시키면 Optimized
- 여전히 한 자릿수당 한 사이클이 필요 => 32비트 == 32사이클

##### Faster

- 자릿수를 맞춰준 다음 동시에 더하기
  - mplier의 32번째 비트 _ mplicnad + mplier의 31번째 비트 _ mplicand ...

<img src="https://github.com/L-Hyun/L-Hyun.github.io/blob/main/assets/CS/8-2.png?raw=true" />

##### RISC-V Multiplication

- 32비트 \* 32비트 = 64비트
  - 상위 32비트 하위 32비트 나눠서 게산
- mul - 하위 32비트
- mulh - 상위 32비트
- mulhu - unsigned끼리
- mulhsu - signed \* unsigned

### Division

- Quotient - shift left
- Divisor - shift right

<img src="https://github.com/L-Hyun/L-Hyun.github.io/blob/main/assets/CS/8-3.png?raw=true" />

##### Optimized

- 곱셈과 같이 3개를 병렬적으로 돌림
- Faster처럼은 불가능
- 나눗셈은 다른 연산보다 느림, 최소화해야 함

##### RISC-V Division

- div, rem - divide, remainder
- divu, remu - unsigned

### Summary

- Overflow Control
- Mul, Div
  - 성능과 hardware cost의 반비례(trade-off)
