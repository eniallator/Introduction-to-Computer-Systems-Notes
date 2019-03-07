# Notes

## Kinds Of Programming

- Scientific number-crunching
- Business data-crunching
- Document processing
- Information search and communication
- Multimedia
- tl;dr constant flexing

## The CPU

- Central Processing Unit
- Contains a control unit (CU) and an arithmetic processing unit (ALU) as well as cache memory and registers
- Modern CPUs usually have 16 registers in them

## The ALU

- Does most of the data processing
- Can do:
  - Arithmetic
  - Logic
  - Comparisons
- Can also have a floating point unit (FPU) but not gonna cover it

---

- Built from CMOS transistors
- Set of operations are hardwired into the circuitry
- 2 types of inputs:
  - Data
  - Control signals
- If the ALU is 64 bit, the input has 64 different bits in it
- Uses the same sort of configuration per line

### Multiplexer

- Kinda like a selector
- Takes control signals
- They say which of the input signals go into the output

### XOR Operation

- Truth table:

| A   | B   | Out |
| --- | --- | --- |
| 0   | 0   | 0   |
| 1   | 0   | 1   |
| 0   | 1   | 1   |
| 1   | 1   | 0   |

### Binary Addition Of Integers

- For example:

| Addition |
| -------- |
| 011 - A  |
| 001 - B  |
| ---      |
| 100      |

- Uses carry in as well, for the column to the right of the current column
- Ofc for the first colummn, no carry in
- Then also involves a carry out, leading to the column to the left's carry in

#### Adder

##### Half Adder

- Logic diagram:

![Half adder logic diagram](http://www.theorycircuit.com/wp-content/uploads/2018/04/half-adder-circuit.png)

- Truth table

| A   | B   |     | Sum | Carry |
| --- | --- | --- | --- | ----- |
| 0   | 0   |     | 0   | 0     |
| 1   | 0   |     | 1   | 0     |
| 0   | 1   |     | 1   | 0     |
| 1   | 1   |     | 0   | 1     |

##### Full Adder

![Full adder logic diagram](http://www.theorycircuit.com/wp-content/uploads/2018/07/full-adder-circuit.png)

- Truth table:

| A   | B   | C<sub>in</sub> |     | Sum | C<sub>out</sub> |
| --- | --- | -------------- | --- | --- | --------------- |
| 0   | 0   | 0              |     | 0   | 0               |
| 1   | 0   | 0              |     | 1   | 0               |
| 0   | 1   | 0              |     | 1   | 0               |
| 1   | 1   | 0              |     | 0   | 1               |
| 0   | 0   | 1              |     | 1   | 0               |
| 1   | 0   | 1              |     | 0   | 1               |
| 0   | 1   | 1              |     | 0   | 1               |
| 1   | 1   | 1              |     | 1   | 1               |

- It adds the 3 inputs (A, B and C<sub>in</sub>)
  - Then the Sum output is the 1s column and then the C<sub>out</sub> is the 2s column (Binary addition)

### Operations

- Types:
  - AND
  - OR
  - XOR
  - Addition
  - Subtraction
  - Comparison
- All applied to multi-bit inputs (8 - 64 bits)
- Some ALUs perform more complex things like floating point arithmetic
