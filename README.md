# PeachOS
A light weight Multithreaded Kernel based on x86_64 Architecture

Written in C, Assembly 

This is a step by step implementation Done by me of the course Developing a Multithreaded Kernel from Scratch by Daniel McCarthy 

Please Install all the necessary packages before running the kernel

First go to the PeachOS directory and run the following

```
make clean
./build.sh
```

Then go to the bin directory to check the simulation
```
cd bin
qemu-system-x86_64 -hda ./os.bin
```
## Instructions for debugging

After building the project 
```
cd bin
gdb
```
And in gdb, attach the kernelfull.o symbol file and start debugging
```
add-symbol-file ../build/kernelfull.o 0x100000
```
```y``` for yes
```
target remote | qemu-system-i386 -hda ./os.bin -S -gdb stdio
```
Add break point if any  
```c``` to continue, ```next``` for stepping instructions, ```print <var>``` for printing variables


**Boot-Loader Screen**
![WhatsApp Image 2024-05-07 at 08 31 36](https://github.com/satvikviriyala/PeachOS/assets/94317660/8bdf140b-d093-4d30-bebd-d9465ff4f144)



Technical Details:
**Bootloader:** The project starts with a custom bootloader written in assembly language. This bootloader's primary function is to switch the processor from real mode to protected mode, enabling access to the full 4GB address space and facilitating 32-bit operations.

**Memory Management:** The kernel implements paging and virtual memory mechanisms. Paging allows for efficient memory allocation and protection between processes, while virtual memory provides each process with its own isolated address space.

**Process Management:** The kernel supports multitasking, allowing multiple processes to run concurrently. This includes mechanisms for process creation, scheduling, context switching, and handling process termination, including crashes and malicious behavior.

**ELF Loading:** The kernel incorporates an ELF loader, enabling it to load and execute programs in the ELF format, which is commonly used for Linux executables.
System Calls and Userland: User processes can interact with the kernel through system calls, which are invoked via software interrupts. This allows user programs to request services from the kernel, such as file system access, memory allocation, and process management.

**File System:** A basic virtual file system (VFS) layer provides an abstraction for file system operations. Currently, the kernel implements support for the FAT16 file system, enabling read and navigation functionalities.

**Shell and User Interface:** The project includes a simple command-line shell that allows users to interact with the kernel, execute commands, and run user programs.

**Standard Library:** A subset of standard C library functions (e.g., printf, putchar) is implemented for use within userland programs.

**Keyboard Driver:** The kernel incorporates a keyboard driver to handle keyboard input in protected mode and provide access to userland programs.

**Project Status and Future Plans:**
The project is currently in active development and has reached a stage where it supports basic multitasking, user programs, and file system operations.

**Future plans include:**

**Expanding File System Support:** Implementing support for additional file systems, such as ext2 or ext4.

**Networking:** Adding networking capabilities to the kernel, allowing communication with other systems.

**Device Drivers:** Developing drivers for additional hardware devices.

**GUI Development:** Exploring the implementation of a graphical user interface.

**Getting Involved:**
This project is open-source and welcomes contributions from anyone interested in operating system development. Feel free to explore the code, submit issues, or propose improvements.
This project represents my ongoing exploration of the fascinating world of operating systems and kernel development. It's a journey filled with challenges and learning experiences, and Iam excited to see where it leads.

