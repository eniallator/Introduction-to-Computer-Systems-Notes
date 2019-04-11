# Notes

## Parallel VS Serial Buses

- Parallel:
  - Difficult to design and build for high speed applications due to the need to ensure that all the data lines are synchronised
  - Expensive
  - Awkward to connect to a device outside the main box due to a large number of wires
  - Require arbitration when multiple devices are connected
  - Can't have wires too close together as this will create interference
- Serial buses only have a few wires so physically are more practical
  - They can also be made fast, even though a single bit is transmitted at a time E.g USB

### Example: USB 3.0

- 9 wires - 6 for data, 1 for power and 2 for ground
- Data is transmitted in 1 byte segments, each converted to a 10-bit code
- Data is sent as packets, each of which identifies it's function (e.g data transfer, control or interrupt) and which may contain some data
- Packets include data for error checking and correction
- Data rate is nominally 5 Gbit/s (4 Gbit/s after encoding and 3.2 Gbit/s achievable in practice)
- Specification structured into physical, link and protocol layers
- Organised into a tiered star topology with a root hub connecting with the main computer bus and other devices, which may also be hubs
- Devices can be added by plugging in even when the system is running - identification takes place automatically

## Interrupts

- Alternative is to continue polling whatever is sending out events
  - Keep checking if it's finished/fired an event
  - Very wasteful of CPU time
- Devices may need attention from the CPU at unpredictable times. For instance,
  - A user has pressed a key on the keyboard, or moved the mouse
  - The network interface has received a data packet
  - The disk has finished performing an input/output operation
- Interrupts are handled using the bus
  - The device controller asserts an interrupt line
  - The CPU detects this, and asserts an acknowledgement line
  - The device that triggered the interrupt identifies itself
  - The CPU ...
    - Saves it's program counter and other status information
    - Jumps to an interrupt handling subroutine (part of the OS kernel), using the device identifier to determine the exact subroutine
  - The interrupt handling subroutine ...
    - Masks interrupts
      - Won't deal with any more interrupts at that moment, only one interrupt at a time
      - Gets hairy with nested interrupts
    - Deals with the interrupt, e.g by transferring data from the disk to memory
      - Don't usually do any computation with the data
      - Otherwise the computer would become unresponsive
    - Restores the state of the current process
    - Jumps back to the saved program counter
- The CPU itself can create interrupts
  - Some instructions can create interrupts potentially for a RISC instruction set

## Networks

- Computer to computer communication
- Networks can be classified by their scale, e.g:
  - Local Area Network (LAN) - at home/company/university
  - Metropolitan Area Network (MAN) - size of a city
  - Wide Area Network (WAN) - up to global scale, e.g the networks that make up the internet
- Networks can also be classified by their topology, e.g
  ![Network topology diagrams](https://i.imgur.com/AgJe8pR.png)
- Connection technologies
  - Copper wire
  - Wireless
  - Optical fibre

### Network Interfaces And Devices

#### Network interface (NI)

- Connects a network node to a network. This may be a computer or a printer for instance
- Connection is via a port - a cable socket or radio signal transmitter/receiver
- Each NI has a unique MAC (Media Access Control) address
- Computers without a built in network interface may have a Network Interface Card (NIC) instead

#### Repeater/hub

- Allows a network to be increased in size when longer wires would cause too many errors
- Regenerates the signals passing through
- Takes each data packet received and distributes it to all connected nodes, no matter which is the actual recipient

#### Bridge

- Efficiently links different segments of a network
- Examines the packets passing through, learns the addresses of nodes in a segment and only forwards the packets to the node it's addressed to
- Can deal with interconnected nodes where there are multiple paths to a single node
- Usually one input/output port

#### Switch

- May look like a hub, but works like a bridge
- Several ports for connecting nodes
- May be used to group segments of a network into virtual LANs in order to control traffic, ease administration, etc.
- Sends packets to the actual recipient, thus using the available network bandwidth more efficiently than a hub

#### Router

- Connects different networks, such as a LAN and a WAN
- Can translate network protocol addresses between the networks, and also filter out packets

### Ethernet

- Most common form of LAN technology today
- The design dates back to 1973
- Physical aspects were covered in this lecture
- In order to transfer info, we need protocols
