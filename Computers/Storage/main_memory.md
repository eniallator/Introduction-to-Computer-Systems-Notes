# Notes

- 8 chips with each holding 512 megabits
  - Total 512 megabytes
- Number of bytes stored in a chip is norrmally a power of 2
- Since 10<sup>3</sup> is almost equal to 2<sup>10</sup>, when people talk about computer system sizes, they use powers of 10, however it's actually in powers of 2

## SI Units

| Decimal             | Binary              |
| ------------------- | ------------------- |
| kilo:10<sup>3</sup> | kibi:2<sup>10</sup> |
| mega:10<sup>6</sup> | mebi:2<sup>20</sup> |
| giga:10<sup>9</sup> | gibi:2<sup>30</sup> |

## Addressing Memory

- How do we get data in and out of a chip? We need to specify the address of the data, and the memory chip needs to decode this address
  - One memory **clock cycle** the data for a whole byte is put onto 8 of the input/output lines
  - Each byte has an address - bytes are numbered, starting from 0

| Address | 0        | 1        | 2   | 3   | 4   | ... |
| ------- | -------- | -------- | --- | --- | --- | --- |
| Data    | 01010101 | 10011101 | ... | ... |

- Each of the 2<sup>26</sup> bytes stored in the chip neds it's own address
- We need 26 bits to specify a unique address for each byte
- In theory, we could cimply use 26 input lines (wires) to do this
- In practice, the address is specified using fewer lines: first part of the address is given, then the rest
- The address is decoded using a circuit using a selector to select the particular byte to read or write

## A Real Example

- DDR-2 means double data rate 2
- DRAM is dynamic random access memory
  - Each bit is stored using 1 transistor and 1 capacitor
  - SRAM uses 6 transistors
  - Uses fewer components for same storage capacity
  - Slower and needs to be told to refresh frequently
- Address is split into different parts, and decoded

## Kinds Of Data In Memory

- A byte in memory may represent a variety of things
- The byte's meaning depends on what the computer is going to do with it
- It is not possible to determine what a byte represents without knowing a lot about the program that is processing it

| Data    | 00000000 | 00000001 | 00000010 | 00000011 | 00000100 | ... |
| ------- | -------- | -------- | -------- | -------- | -------- | --- |
| Meaning | ?        | ?        | ?        | ?        | ?        | ?   |

### An Integer

- Different bit patterns stand for different whole numbers
- The usual way to order them is binary counting
- A single byte can hold the numbers 0 to 255
- Bytes are grouped together to form words that has data that can be more than 256 possible values

### Part Of A Floating Point Number

- Floating point numbers are not integers and can represent an approximation of a real number
- Numbers like pi can be represented with 1 bit to represent the sign, others to represent where the decimal is and then the others to represent the number itself
- Use usually 4, 8 or even 16 bytes

### Characters

- ASCII
  - Use 1 byte
- Groups of bytes can represent characters in larger character sets

### Part Of A Machine Instruction

- Machine instructions can be complex and be several bytes long
- These instructions are sent to the CPU
- The meaning of the instruction depends on the CPU

### Other Forms Of Data

- Bytes may have many other meanings - e.g as part of a representation of an image or audio
- but usually the byte can also be thought of as an integer or a character
