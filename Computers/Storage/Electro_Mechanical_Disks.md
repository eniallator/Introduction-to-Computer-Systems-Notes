# Notes

- Different from primary storage since primary is electronic

## Magnetic Disk

- Has a center rotating platter (Disk) and a read/write head
- Strong relation between electric fields and magnetism
  - By inducing an electric current, you can write information
  - By detecting the electric field -> electric current, you can read the platter
- The read/write head can move on an arc across the platter
- The platter is organized into tracks which run the circumference of the platter, where each track is divided in to sectors which are arcs on the platter
  - 10,000 Tracks/centimeter
  - Sectors are larger towards the outside of the disk
    - Manufacturers now pack more data storage in the outer sectors, which can then be read faster
- Data is stored extremely compactly - 100,000 bits/millimeter around the track
- Has an information density of 250 MB/square millimeter
- Latency using this is very high - in the order of 10s of milliseconds
- Rotation speed: 7200 rpm
- Error rate: 1 in 10<sup>14</sup>
- In theory it can read/write from multiple platters at the same time

### Hard Disks

- Hard disk has a micro-controller chip and about 64 megabit dynamic RAM for disk buffer
  - Disk buffer is kind of like a cache
- Usually has multiple platters and read/write heads

## Optical Disks

- Has a single spiral track along the disk where data is continuous
- Speed of rotation changes to allow for a constant data rate, depending on the location of the data on the disk
- CD
  - Capacity of 650 megabytes
  - Rotates at 200 rpm to 530 rpm
  - 150,000 to 175,000 bytes/second
- DVD
  - Capacity of 4.7 gigabytes
  - Can have multiple layers which can then store up to 17 gigabytes
- Blu-ray
  - Normally store 25 - 50 gigabytes
  - Can be made to store 125 gigabytes
  - Data rate is 4.5 - 72 megabytes/second

### ROM

- Burn data into the disk and then only be able to read it later
- Have a "master" disk to copy the data from on to a new optical disk

### Read/Writable

- Has an alloy beneath the plastic that can be changed using light

### Reader

- Contains:
  - Laser on a head pointed at the disk
  - Photocell at the edge just above the disk to read the laser's output

## Tape

### Paper Tape

- Holes are 25mm
- Reader uses light to read the data
- Durable yet easy to destroy
- Can be decoded by humans
- Immune to electric currents/fields
- Read speed: 10 - 2000 bytes/second

### Magnetic Tape

- Long strip of coated plastic film originally wound on 2 reels in a cartridge
- Pulled the 2 reels across read/write heads
- Patches of the coating are magnetised in parallel tracks that are either slanted or linear. This stores data
- Tape cartridges are removable and portable
- High data transfer speeds, however a lot of latency for random access
- Long life (10+ years)
