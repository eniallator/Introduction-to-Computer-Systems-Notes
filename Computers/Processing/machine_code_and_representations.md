# Notes

## Entering And Running Machine Code

- Early machines had switches that let you enter machine code - entered binary using switches
- Typing machine code using hexadecimal on a keyboard (as for the brookshear machine) is much quicker and less error-prone
- The brookshear machine is an "idealized" machine - it has never existed in hardware. We are running it using an emulator, which provides a programming environment with the following facilities
  - Visualisation of memory and register contents
  - Built in conversion between data representations
  - Assembler and disassembler
  - Instruction single stepping
  - Instruction undo

## Number Representations

- Binary addition for positive integers: no problem, apart from overflow if the result is too large for it's destination
- Negative numbers: use a bit sign
  - Most efficient (less logic needed)
  - If negative numbers are represented in **two's complement** form
  - For 8-bit numbers, it means:

| Bit pattern | Number |
| ----------- | ------ |
| 00000000    | 0      |
| 00000001    | 1      |
| 00000010    | 2      |
| ...         | ...    |
| 01111111    | 127    |
| 10000000    | -128   |
| 10000001    | -127   |
| 10000010    | -126   |
| ...         | ...    |
| 11111110    | -2     |
| 11111111    | -1     |

- Algorithm for negating a number
  - Invert each bit
  - Add 1
- In BM code:

```text

// Negate two’s complement integer in location 12
// Register usage:
// R1: holds the integerbeing processed
// R2: holds the value FF
// R3: holds the value 01
// Algorithm: invert each bit and add 1
//
1112 // Load the dataatlocation 12 into R1
22FF // Load FF into R2
2301 // Load 01 into R3
9112 // Invert bit pattern in R1 by XORing with FF
5113 // Add 1 to R1 (as integers)
3112  // Store R1 in location 12
```

- The subtraction operation `a - b` can be implemented as `a + (- b)`
- Can do arithmetic on an integer representing a memory address, interpreting it as an **unsigned integer**

### Floating Point Numbers

- Can represent a wider range of integers, with the possibility of fractional parts
- The BM has 8 bit floating point numbers, real computers have 32, 64 or 128 floating point numbers
- The BM uses the 8 bits as follows:

| Sign | Exponent | Mantissa |
| ---- | -------- | -------- |
| 0    | 101      | 1101     |

- Sign: 0 means positive, 1 is negative
- Exponent: interpret as an unsigned integer and subtract 8, call this `e`
- Mantissa: interpret as an unsigned integer, call this `m`
- The magnitude of the float being represented is `m*2`<sup>`e`</sup>
- For example 01011101<sub>2</sub> represents the float 13\*2<sup>-3</sup> or 1.625<sub>10</sub>
- Format is an international standard for floating point number representations: `IEEE 754`
- Floating point representations are not exact and can be error prone

## Character Representations

- ASCII is an international standard in 1963, encoding 128 chars
  - The `ISO-8859-1`, `-2`, etc. standards extend this to 256
- Having many standards is unsatisfactory, and 256 chars is way too little for many of the world's languages
- Latest standard is UNICODE which provides 1,114,112 code points (from 0 to 10FFFF), of which around 138,000 are assigned to named characters
- The most common encoding for unicode is UTF-8. UTF-8 encodes all ASCII characters in a single byte with the same binary value, and can represent any unicode character using 1, 2, 3 or 4 bytes
