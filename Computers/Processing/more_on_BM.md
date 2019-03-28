# Notes

## Conditional Instructions

- The original BM instruction set has one basic conditional instruction
  - `JMPEQ xy, Rm`
  - Jumps to address `xy` if the contents of register `Rm` are equal to the contents of register `R0`
- Also has an unconditional jump as well
  - `JMP xy`
  - Always jumps to address `xy`

### More Conditional Instructions

- The conditional jumps can be extended to more conditional instructions
  - `JMPNE` - jump not equal
  - below are integer comparisons
  - `JMPGE` - jump greater than or equal
  - `JMPLE` - jump less than or equal
  - `JMPGT` - jump greater than
  - `JMPLT` - jump less than

![JMPLT equivalent in if-then high level code](https://i.imgur.com/cH8fPq7.png)

## Loops

- Most high level languages implement a looping construct (e.g `for`, `while`, `do while`, `recursion`)

![While loop version](https://i.imgur.com/mbChmIV.png)

## Addressing Memory

- Suppose a byte of data is to be transferred from memory to a register. There are many ways to specify the data

### Immediate Addressing

- The data is part of the instruction
- The data is fixed, unless the program itself is changed
- In the BM, the opcode 2 instruction uses immediate addressing
- E.g load into register 3 the bit pattern represented by `AB`:
  - `MOV AB -> R3`

### Direct Addressing

- The data is at a fixed memory address
  - The address is part of the instruction
- The address of the data is fixed, unless the program is changed
- In the BM, the opcode 1 instruction uses direct addressing
- E.g load into register 5 the contents of the memory at address `DE`
  - `MOV [DE] -> R5`

### Register Indirect Addressing

- The data is somewhere in memory. The address of that memory location is held in a register
- The address in register can change as the result of a computation
- The extended BM instruction set has this addressing mode
  - E.g load into register 4, the data whose address is in register 2:

```text
      MOV  [R2]    -> R4
```

- Or the machine instruction version:

| Opcode | Register A | Register B |
| :----: | :--------: | :--------: |
|   D0   |     4      |     2      |

## Assembly Programming Example

- Goal - to recreate the following Java code in the BM programming language:

```java
int i, j;
j = 0;
for (i = 1; i < 11; i = i+1) {
  j = j + 1;
}
```

- BM code:

```text
      MOV   0B     -> R0 // max iterations is 11
      MOV   01     -> R1 // constant 1
      MOV   00     -> R2 // j
      MOV   01     -> R3 // i
loop: JMPEQ done,  R3
      ADDI  R2, R3 -> R2
      ADDI  R3, R1 -> R3
      JMP   loop
done: MOV   R2     -> [20]
      HALT
```
