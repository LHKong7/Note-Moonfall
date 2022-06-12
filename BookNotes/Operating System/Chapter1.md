

## Chapter 1: Process

The OS creates this illusion by virtualizing the CPU. By running one process, then stopping it and running another, and so forth, the OS can promote the illusion that many virtual CPUs exist when in fact there is only one physical CPU.

​	**Time Sharing** of the CPU: allows user to run as many concurrent processes as they would like; the potential cost is performance, as each will run more slowly if the CPU(S) must be shared.

​	**Space Sharing**: a resource is divided (in space) among those who wish to use it.

TO implment virtualization of the CPU, and to implement it well, the OS will need both:

- some low-level machinery mechanisms
- some high-level intelligence



mechanisms (low level machinery) : low-level methods or protocols that implement a needed piece of functionality.

**Context Switch**: gives the OS the ability to stop running one program and start running another on a given CPU





Policies: algorithms for making some kind of decision within the OS.

**Scheduling policy**: which program should run (using historical information? workload knowledge? performance metrics?)



##### Process

Components of machine state that comprises a process:

- memory: instructions lie in memory, the data that the running program reads and writes sits in memory. Thus the memory that the process can address (address space) is part of the process
- Registers: many instructions explicitly read or update registers and thus clearly they are important to the execution of the process
  - program counter (PC): which instruction of the program will execute next
  - Stack pointer and associated frame pointer: manage the stack for function parameters, local variables and return address



##### Process API

**Create**, **Destroy**, **Wait**, **Miscellaneous Control**, **Status**

**Process Creation**: 

Load its code and any static data (eg, intialized variables) into memory, into address space of the process. Programs initially reside on **disk** (flash-based SSDs) in some kind of executable format; thus, the process of loading a program and static data into memory requires the OS to read those bytes from disk and place them in memory.

Modern OSes perform process lazily => by loading pieces of code or data only as they are needed during program execution. (paging and swapping)



Before running the process, The OS also do:

1. some memory must be allocated for the program's **run-time stack** for example, C programs use the stack for local variables, function parameters and return addresses.
2. Allocate some memory for the program's **heap**. For example, C programs, the heap is used to explicitly requested dynamically-allocated data.
3. I/O actions. Three open **file descriptors**: standard input, output, error



##### Process States:

Running: In the running state, a process is running on a processor. This means it is executing instructions.

Ready: In the ready state, a process is ready to run but for some reason the OS has chosen not to run it at this given moment.

Blocked: In the blocked state, a process has performed some kind of operation that makes it not ready to run until some other event takes place. A common example: when a process initiates an I/O request to a disk, it becomes blocked and thus some other process can use the processor.





# Interclude: Process API



the PID is used to name the process if one wants to do something with the process.

The children process is not an exact copy. Specifically, although it now has its own copy of the address space (i.e., its own private memory), its own registers, its own PC and so forth, the value it returns to the caller of **fork()** is different. 









