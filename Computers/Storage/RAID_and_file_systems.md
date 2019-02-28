# Notes

## RAID

- Known as Redundant Array of Independant Disks
- Consists of 2 or more physical disks
- Appears to be a single storage device to the computer/user

### Advantages

- Store larger amounts of data
- Provide increased performance
- Increase reliability
- Improve availability (even when a single disk fails)
- After a disk is replaced, the RAID reconstructs the data that should be on it

### Techniques Used

- Mirroring (identical data on two or more disks)
- Striping (each sequential bit, byte or block on a different disk)
- Parity (error checking and correction information stored either with the data or on a dedicated disk)
  - Potentially be able to reconstruct the data from the parity data
- There are several levels of RAID each using different combinations of techniques, e.g RAID 0, 1, 2, 3, 4, 5, 6, 10.

## File Systems

- The physical layout of the hardware is hidden from the programmer and user
- What you see is a file system: a virtual storage device with characteristics determined by the underlying physical storage device, its logic circuitry and the operating system
- Disk file systems are the most familiar kind

### For The User

- A file is a continuous sequence of bytes, which can be interpreted in many ways by programs, e.g as:
  - Formatted text
  - An image
  - Executable machine instructions
- The whole sequence of bytes, or sections in it, can be moved between main memory and disk or other devices
- A file has a name: a string of characters from a small character set
- A file has associated meta data
- Files can be organised into a hierarchy, by placing them in directories or folders
  - Files can then be identified using relative or absolute pathnames
    - E.g `.\example.txt` or `C:\Users\USER\Documents\example.txt`

### For The Operating System

- A file is a continuous sequence of bytes
- That sequence if contained within a collection of blocks which may be physically scattered across the storage medium
- A file does not share a block with any other file, even if there is space left in the block
- Hence, a file might use up more disk space than it's file size would suggest, because it must always occupy whole blocks
- For magnetic disks, a block would normally span 2 or more sectors

#### Why We Need Blocks

- The operating system uses the blocks to efficiently record and assemble the data constituting a file
- The operating system maintains a table, held on disk, recording which blocks make up a file: the file table
- To be able to allocate a new block to a file, the operating system keeps track of which blocks are currently unused (the free list)
- Directories are also files, but hold housekeeping information about the files within them
- There is a trade-off: organising the disk into bigger blocks (allocation units) would
  - Increase speed (as more bytes are read in one go)
  - Reduce capacity (due to more slack space/waste)

### Special-Purpose File Systems

- Other file systems may be appropriate to support special application program requirements and/or different underlying physical storage devices. E.g:
  - Optical disk file system
    - Minimizing non-sequential access, supporting incremental updates on write-once optical media
  - Tape file system
    - Avoiding time-consuming and repeated tape movement when writing new data (e.g LTFS)
  - Transactional file system
    - Ensuring consistency between multiple file system operations, e.g in a database system
    - ACID for DBMS systems
  - Distributed or network file system
    - Access to files that are distributed or processed simultaneously across a network/cluster of computers
