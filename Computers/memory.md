# Notes

- Analogue devices may be able to store information, but do not have discrete states like digital computers

## Requirements For Memory

- System with discrete states
- Stability: an ability to persist in a particular state
- Way to change state, i.e write to the memory
- Way to measure the state, i.e read from the memory

### Desirable Properties

- Properties:
  - Low error rate
  - High information capacity
  - Small physical size
  - High speed
  - Low power consumption
  - Low cost
- All memory design involves trade-offs between these properties

## CMOS Technology

- Complimentary-symmetrical metal-oxide-semiconductor
- Dominant technology for digital logic circuits and fast memory
- Combined use of two different types of transistor
- A transistor is a semiconductor based on materials that give it dynamic electrical properties. Transistors are often used as electrical switches or to amplify signals
- Advantages of transistors over other technologies:
  - Small
  - Lightweight
  - Low power consumption
  - Less heat emission
  - Robust

### Inverter

- A CMOS inverter is in one of two states, so is a binary device (like almost all elements of a digital computer)
  - Inverts signals going to it

![inverter img](https://www.tutorialspoint.com/vlsi_design/images/cmos_inverter_circuit.jpg)

- Made from a complementary and symmetrical pair of p-type and n-type metal oxide semiconductor field effect transistors
  - Transistors have 3 connections and act as switches
  - When "In" is at a **positive** voltage, the (upper) p-type transistor's channel is in a high resistance state and the (lower) n-type transistor's channel is in a low resistance state, so the output is at the **ground** voltage
  - The opposite happens when "In" is at the **ground** voltage
- Truth table for an inverter is very simple:

| Input | Output |
| ----- | ------ |
| 0     | 1      |
| 1     | 0      |

### NAND Gate

- A NAND logic gate as below has two inputs, (A and B in the diagram) and one output

![NAND img](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e2/CMOS_NAND.svg/255px-CMOS_NAND.svg.png)

- With CMOS, if there are two p-type transistors in parallel then there must be two corresponding n-type transistors in series

### Static RAM

- A static inverter is not persistent but with two inverters connected into eachother, feedback maintains a constant state
- This is called a "latch" or a "flip-flop". With some extra circuitry, it's state can be changed by either the 'set' or 'reset' input being pulsed high (with the other input held low)
- In practice, static random access memory (SRAM) cell storing a single bit turns out to need 6 transistors
- Dynamic RAM is the other main type of computer memory, and is implemented differently

![Latch img](https://www.dummies.com/wp-content/uploads/310547.image1.jpg)

## Integrated Circuits

- In an integrated circuit, each component is made by depositing materials onto a wafer of silicon
- Small size is important for high speed and capacity. Practical limitations on size include current leakage and the wavelength of light used for lithography
- In current technology, the distance between transistor centres on a chip is about 50nm (nanometres), roughly equivalent to 250 atoms of silicon
- Wafers are discs up to 300 mm across. After the circuitry is deposited onto the wafers, they are diced into pieces. Each die forms an integrated circuit, which is then packaged
