# Notes

- Need to be familiar with hexadecimal

## Number Bases

| Decimal | Binary | Hexadecimal |
| ------: | -----: | ----------: |
|       0 |      0 |           0 |
|       1 |      1 |           1 |
|       2 |     10 |           2 |
|       3 |     11 |           3 |
|       4 |    100 |           4 |
|       5 |    101 |           5 |
|       6 |    110 |           6 |
|       7 |    111 |           7 |
|       8 |   1000 |           8 |
|       9 |   1001 |           9 |
|      10 |   1010 |           A |
|      11 |   1011 |           B |
|      12 |   1100 |           C |
|      13 |   1101 |           D |
|      14 |   1110 |           E |
|      15 |   1111 |           F |
|      16 |  10000 |          10 |
|      17 |  10001 |          11 |
|     ... |    ... |         ... |

### Example Conversion

- Number example: 5617
- Decimal version:

| 1000s | 100s | 10s | 1s  |
| ----- | ---- | --- | --- |
| 5     | 6    | 1   | 7   |

## Brookshear Machine

- Has main characteristics of a RISC architecture
- Has 16 registers
  - Numbered 0 to F
- Main memory with 256 locations
  - Numbered 0 to FF
- Each register/memory location holds 1 byte (or 2 hex digits)
- Uses 16 bit instructions, hence each instruction is 2 bytes long and takes 2 memory locations

![Emulator screenshot](https://i.imgur.com/2STT51l.png)

### Instruction Format

- 16 bits long
- First 4 bits for opcode (type of instruction)
- remaining 12 bits for the operand (the data for each instruction)
- In hex, first digit is the operand, the other 3 are the operand
- Examples:

|             | Opcode | Operand 1  | Operand 2  | Operand 3  |
| ----------- | ------ | ---------- | ---------- | ---------- |
| Binary      | 0110   | 1110       | 1100       | 1101       |
| Hex         | 6      | E          | C          | D          |
| Description | ADD    | register E | register C | Register D |

- Arithmetic instructions take in 2 source location operands, and then 1 destination operand

|             | Opcode | Operand 1  | Operand 2    |
| ----------- | ------ | ---------- | ------------ |
| Binary      | 0010   | 0011       | 11111111     |
| Hex         | 2      | 3          | FF           |
| Description | LOAD   | register 3 | data to load |

- Move instructions take in 1 source/destination address operand and then the data to load/store

### Instruction Set

- Has a total of 12 instructions with a few additional instructions available in the local version
- The letters r, s, t, x, y stand for hex digits

| Instruction | Description                                                                                                                                        |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| `1rxy`      | _**LOAD**_ register **r** with data at memory address **xy**                                                                                       |
| `2rxy`      | _**LOAD**_ register **r** with data **xy**                                                                                                         |
| `3rxy`      | _**STORE**_ contents of register **r** into memory address **xy**                                                                                  |
| `40rs`      | _**MOVE**_ (i.e copy) the contents of register **r** into register **s**                                                                           |
| `5rst`      | _**ADD**_ contents of register **s** and contents of register **t**, as signed (two's complement) integers, and put the result into register **r** |
| `6rst`      | _**ADD**_ the contents of register **s** to the contents of register **t**, floating point numbers and put result into register **r**              |
| `7rst`      | _**OR**_ the contents of register **s** with the contents of **t**, bit by bit, and put the result into register **t**                             |
| `8rst`      | _**AND**_ register **r** with register **s**, put result into register **t**                                                                       |
| `9rst`      | _**XOR**_ register **r** with register **t**, put result into register **t**                                                                       |
| `Ar0x`      | _**ROTATE**_ the bit pattern in register **r** one bit to the right **x** times, and put the result back into register **r**                       |
| `Brxy`      | _**JUMP**_ by setting the program counter to **xy** if the contents of register **r** are equal to the contents of register 0                      |
| `C000`      | _**HALT**_                                                                                                                                         |

### BM Instructions

- Bit batterns in memory can be interpreted as instructions, memory addresses, signed integers, unsigned integers, characters, or floating point numbers
- Combinations of logical operations (AND, OR, XOR) and ROTATE allow for any rule for manipulating bit patterns to be implemented
- The JUMP instruction causes the machine to start taking instructions from another place in memory
- The instruction `B0xy` allows for unconditional jumps, since the it compares it's contents with itself

#### Additional Instructions

- In the local version (At sussex uni), the remaining 4 opcodes (D, E, F, 0) are used for:
  - A 'no operation' instruction (NOP)
  - LOAD and STORE instructions using indirect addressing (where the data are the addresses of data are in registers rather than in the instruction)
  - JUMP instructions incorporating other kinds of tests besides equality
