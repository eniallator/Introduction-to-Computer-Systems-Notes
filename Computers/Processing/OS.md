# Notes

- Is a program
- Which:
  - Abstracts many physical details of the machine
  - Has a UI
  - Helps programmers
  - Programming interface which can have system calls
  - Can protect itself from damage _**I SAWED THIS BOAT IN HALF**_
- Examples include windows/linux/macos
- Some computers, especially embedded ones, won't necessarily run a OS
- OS presents a VM to the end user/programmers/programs

## Linux

- Originally mostly used in servers, now in a lot of desktops as well
- Open-source/free
- Comprehensive control with a command line that accepts text input, GUI can also be used though

## Windows

- Dominates the desktop market
- Under commercial control by micro\$oft
- Usually controlled with a GUI, AKA WIMP interface (Window, Icon, Menu, Pointer-device)
- CLI also available, but not often used

## OS Structure

- Contains 2 major subsystems:
  - Kernel
    - Provides central services to all parts of computer and is in overall charge of system resources
    - Controls every other program, ultimately controlled by user, via the shell
  - Shell
    - Provides interface which users can control the kernel
    - For windows, the shell consists of a number of programs including file explorer
    - Linux has CLI, can also be programmed using shell scripts

## OS Kernel

- Kernel provides basic services for computer

### Memory Management

- Allocate memory to programs
- Manage virtual memory
- Protect against malware

### Task Management

- Launch processes (process = program + state of program)
- Maintain process table: list of running processes
- Carry out time slicing + context switching
- Handle interrupts
- Set program privelige levels

### File Management

- Act on program requests for opening/reading/writing/closing files
- Set/check permissions
- Handle buffering/prefetching

### Device Management

- Uses device drivers to respond to program requests to open/read/write/close devices such as printers, cameras, displays and keyboards

## Some Linux Shell Commands

- Some basic file management commands are:
  - `cp`
  - `mv`
  - `rm`
  - `mkdir`
  - `rmdir`
  - `cat`
- Also many utilities which aren't part of the shell, e.g:
  - `find`
  - `grep`
  - `awk`
- Programs/scripts are run by simply entering their filename
