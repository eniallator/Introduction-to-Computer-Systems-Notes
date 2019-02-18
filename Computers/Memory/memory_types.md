# Notes

## Main Memory

- Kind of primary storage
- The working memory of the computer:
  - In java, the result of `x = 100;` will be stored in the memory
- Made up of transistors and capacitors on silicon - several million per square millimetre
- In a normal PC, it's on a seperate chip to the CPU
- Info stored in binary, organised into 8-bit bytes
- Each byte has a unique address
- Access to the RAM has 60 nanosecond latency, whereas the CPU is going at 3.6 nanoseconds (in the lab computers)

## Caches

- CPU waits for the main memory quite a lot
- Modern computers have caches
- All modern computers have atleast 1 cache, sometimes 3 levels of caching
  - First level of cache (L1) is stored on the CPU
  - Consecutive levels will each have more and more storage available
  - If it doesn't find in the current level of cache, it will go to the next and see if it's there, until it runs out of levels in which case it will go to the main memory
- Relatively small amount of very fast access memory
- Uses CMOS (just transistors)
- Nearby locations will be accessed quicker than further away locations
- E.g the `x = 100;` writes to memory, however we'll need to read it later on
  - Hopefully it will be stored in cache memory
- If reading from a location in a program, likely will be read again later on
- Cache will automatically keep a set of chunks from memory that have been accessed recently - think of website caching
- Cache will make sure the main memory gets updated every so often

## Virtual Memory

- This is found in the primary storage (e.g HDD or SSD)
- Used when memory runs out
- MUCH SLOWER
  - Since it has to go all the way to the primary storage
- To the programmer, they won't see much difference, just the amount of addresses they can access will be much greater
- To do this, there needs to be hardware support + the operating system must be able to do this
  - Memory is split up into pages which are chunks of memory that is usually 4KB
- Process of moving main memory to storage is called paging
- As a user/programmer, if the program is taking a while to access virtual memory, there'll be a lot of paging and so the program will slow down
  - Paging doesn't take CPU time, it's done by another chip
  - Uses a page table that stores the locations of all the pages so far
- If you have a disk drive, you can sometimes hear the disk under stress
- Might be of the order of a million times slower than accessing main memory

![Virtual memory img](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6e/Virtual_memory.svg/375px-Virtual_memory.svg.png)

## Secondary And Tertiary Storage

- Compared to primary storage:
  - non-volatile
    - When power is off, it doesn't lose it's contents
  - Larger capacity
  - Larger access time (latency), lower data rate (bandwidth)

| Prefix | power of 10 |
| ------ | ----------- |
| kilo   | 3           |
| mega   | 6           |
| giga   | 9           |
| tera   | 12          |
| peta   | 15          |
| exa    | 18          |
| zetta  | 21          |

- Google earth database is estimated between 3 and 20 petabytes of data
- IDC the 'global datasphere' has 33 zettabytes (the entire sum of the world's data) in 2018

| ?            | Primary  | Secondary | Tertiary |
| ------------ | -------- | --------- | -------- |
| Non-volatile | No       | Middle    | Most     |
| Availability | Yes      | Yes       | No       |
| Capacity     | Smallest | Middle    | Biggest  |
| Latency      | Fastest  | Middle    | Slowest  |
| Bandwidth    | Best     | Middle    | Middle   |
| Cost         | Most     | Middle    | Least    |
