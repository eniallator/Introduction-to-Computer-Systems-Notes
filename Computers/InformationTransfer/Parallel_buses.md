# Notes

## Information Transfer

- Physical level:
  - Voltage on wires
  - Light pulses in optical fibres
  - Modulation of a wireless signal
- Inside the computer and to nearby peripheral devices: buses
- To other computers: networks such as ethernet

## Buses

- Named busbars in electrical equipment
- Nearly always use copper conductors, either:
  - Insulated flexible wires
  - Lines of copper printed onto a circuit board
- A bus is a collection of conductors, each transmitting a signal
- A bus has a physical and logical specification. Example buses:
  - Peripheral Component Interconnect (PCI) bus: old but still common
  - Universal Serial Bus (USB)
  - SATA
  - Thunderbolt

## Parallel Buses

- Nowadays, only used internally (inside the computer case)
- Simplified visualisation:
  ![Parallel bus](https://i.imgur.com/V3ZJOvd.png)
  - 16 address lines, this bus can address 2<sup>16</sup> or 65536 different locations
  - 8 data lines, 1 byte can be transferred each **bus cycle**
  - 4 control lines signal clock pulses, memory read/write, data parity, etc.
- On each cycle, the CPU asserts if a read or write is to take place, and sets the appropriate lines on the bus
  - Many devices share a single bus: in principle any of them can set/read the address or data lines
  - At any one time, a single device is the bus master (could be the CPU or another device)
    - Asserts a signal on the control lines to ask the other devices to be slaves
    - Bus arbitation resolves conflicts
    - The bus master controls data transfers until it gives up control
  - Correctly timing the signals on a bus can be complex
  - A bus can use the same lines for addresses and data by first setting the address and then the data: called multi-plexing

## Example: The PCI Bus

- Bus width: 124 or 188 lines
  - Has atleast 32 address lines to access 4 GB of memory, but optionally, 64 lines
- Address and data lines are multiplexed
- 1 clock line at 33 or 66 MHz, so if transferring 64 bits per cycle, then can transfer 528MB/sec (66,000,000 \* 64 / 1000 / 1000 / 8)
- The bus is synchronous: everything depends on the clock signal
  - Transfers have to be geared to the slowest device
  - Opposite is an asynchronous bus
- 16 control lines (for 32 bit mode) for things such as:
  - Read or write
  - Bus arbitration: request/acknowledge control of bus
  - Data ready
  - Parity error detected
  - Reset the system
  - Etc.
- Typically used with a bridge
  ![A bridge 😮](https://i.imgur.com/Nhkjs24.png)

### Example Read Cycle

- Master sets the address/data lines and puts read command in control lines
- Master asserts signal to start transaction
- Slave read address and asserts signal to say it has done so
- Master floats address/data lines - i.e it stops putting any specific voltage on them
- Slave puts data on address/data lines and asserts signal to say it has done so
- Master reads data from address/data lines
- Key is to minimize the number of unused cycles when slave/master is waiting for signal

## PCI Express

- Bandwidth of the PCI bus is exhausted by applications like 3D graphics
  - This let to specialized buses to connect to graphics
  - PCIe is commonly used nowadays
- Devices still send the same PCI requests, PCIe is a serial bus that works more like a network, with central communication hub instead of devices attached to a single set of lines, and packets of data carrying their own addresses
- Communcation is facilitated through lanes with each lane able to send/receive data simulatneously
  - PCIe allows connections up to 16 lanes
