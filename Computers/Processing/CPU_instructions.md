# Notes

- Instruction set architecture
  - How the CPU appears from the outside

## Basic Operatin Cycle

- Get an instruction from memory and hold it in a special register
- Decode and execute the instruction
- Update the program counter

## Instruction Set Types

### CISC - Complex Instruction Set Computer

- CIS ERMAHGERD REEEEEEEEEEEEEEEEEEEEEEEEE
  ![ermahgerd](https://media1.tenor.com/images/fa66c649ecc29ab1d943c264a4aade55/tenor.gif)
- Large variety of instructions, each can be doing something complex (e.g copying chunks of memory, arithmetic on strings of decimal digits)
- Requires a lot of transistors for decoding/executing - adds expense
- Clock speed limited to the slowest instruction sub-step
- Powerful instructions can make programs more compact and CPU needs to fetch instructions less frequently
- Instructions may have a large range of effects so they must be executed in order

### RISC - Reduced Instruction Set Computer

- Smaller, simpler instruction set
- Needs fewer transistors
- Clock speeds can be fast since instructions are fast
- Programs occupy my memory so more fetching/decoding
- Each instruction is more predictable so the CPU can take shortcuts when executing them

## RISC vs CISC

- CISC was the more dominant approach, supported by microcoding technology
- RISC now more dominant using speed-up techniques like:
  - Instruction piplining
  - Out-of-order execution
- Intel Core/XEON processors are CISC but are essentially RISC inside
  - 😮 TOP 10 ANIME BETRAYALS

## Kinds Of CPU Instructions

### Data Transfer

- Often named 'MOVE' instructions
  - LOAD: copy data from memory to register
  - STORE: copy data from register to memory
  - Copy data from register to another register
  - Set register to constant value given in instruction
- May also handle I/O

### Arithmetic And Logic

- NOT
- AND
- OR
- Addition, etc.
- And put the result in a register

### Control

- Take the contents of 2 registers; if they be equal, change the program counter to a specified value
  - More than just equality, i.e greater than, less than ...
- Halt

## Instruction Formats

- Typically, a machine instruction takes up a few bytes of memory
  - First 1 or 2 bytes identifies the instruction (opcode)
  - Further bytes give the value (operand)
- CISC machines:
  - Instruction length varies depending on the operation and what extra info is needed
  - Hard work for the CPU since it needs to decode the instruction before it knows what extra info is needed
- RISC machines
  - Instruction lengths are usually the same so a standard number of bytes can be fetched
