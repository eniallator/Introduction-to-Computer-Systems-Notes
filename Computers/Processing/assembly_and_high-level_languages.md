# Notes

## Hierarchy Of Control: Java

- The higher in the hierarchy, the higher the level of abstraction

1. High level language, e.g Java

- Goes through the Java compiler

2. JVM instructions

- Goes through the JRE

3. Assembly language

- Goes through an assembler

4. Machine Instructions

- Goes through the CPU control unit

5. Logic signals within the CPU

- Goes through the CPU/ALU

6. Finally, execution

## Assembly Language

- Provides a more convenient way to write machine language programs
  - Mnemonics for the opcodes
  - More expressive syntax for operands
  - Symbolic names for memory locations
- Assembly language is translated to machine instructions by an assembler
- E.g the following machine language program:

```text
110A
120B
5312
330C
C000
99
66
```

- Has the following equivalent in assembly language:

```text
        MOV   [int1] -> R1
        MOV   [int2] -> R2
        ADDI  R1, R2 -> R3
        MOV   R3     -> [result]
        HALT
int1:   DATA  -103   // pseudoinstructions
int2:   DATA  +102
result: DATA  0
```

## High Level Language

- Use abstraction for:
  - Greater portability
  - Greater ease of use
- Such languages offer atleast:
  - Variables holding values
  - Data types such as integers, floats, characters
  - Control structures
  - Procedures/methods as well
- Assembly language e.g:

```text
        MOV   0B     -> R0// decimal 11
        MOV   00     -> R1
        MOV   01     -> R2
        MOV   01     -> R3
loop:   JMPEQ stop, R2
        ADDI  R1, R2 -> R1
        ADDI  R2, R3 -> R2
        JMP   loop
stop:   HALT
```

- Equivalent in Java:

```java
int j = 0;
for (int i = 1; i < 11; i++) j += i;
```

## Compilers

- Translates a high-level source language, into a lower-level target language, e.g
  - Java -> JVM code
  - C -> machine language for e.g Intel Core series processors
- Compilation involves a number of steps:
  1. Lexical analysis - splitting the source into tokens, e.g `for` or `11`
  2. Syntactical analysis - grouping tokens into statements and other program structures, e.g `j = j + i;` and representing the hierarchical relationships between them
     ![Statement tree](https://i.imgur.com/Y6k05kM.png)
  3. Code generation: producing target instructions
  4. Code optimization: revising the generated code to make the program more quickly or use less memory, without affecting the results

## Some High-Level Languages

- Fortran
  - OG scientific numerical computing language
  - Imperative language which has evolved over the years and is still used for heavy duty computation
- Cobol
  - OG business computing language
  - Was used in commerical applications
  - Now mostly confined to legacy applications
- C
  - Designed for OS programming
  - Often used as a general-purpose language
  - Detailed control over machine possible
- C++
- Java
- Haskell
- Prolog
- Python
- Javascript
- Etc.

## Language Design Decisions

- Statically typed vs. dynamically typed
- Enforces safety or not?
- Compiled vs. interpreted
- Imperative (e.g procedural, OOP paradigms) vs. declarative (functional, logic)

## Trade-Offs Between Languages

- Usefulness for specific applications vs. generality
- Flexibility and range of expression vs. ease of learning
- Speed of coding vs. error checking before runtime
- Efficiency of execution vs. ease of debugging vs. portability
