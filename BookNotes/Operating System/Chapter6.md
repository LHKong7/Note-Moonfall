# Machanism: Limited Direct Execution

### Overview

In order to virtualize the CPU, the OS needs to share the physical CPU among many jobs running seemingly at the same time.

##### Problem Description: 

**Stragety**: run one process for a little while, then run another one.

By time sharing the CPU, virtualization is achieved

**Challenges**:

1. Performance: how can we implement virtualization without adding excessive overhead to the system
2. Control: how can we run processes efficiently while retaining control over the CPU => more important to OS,



### Technique:



##### Limited Direct Execution

The "direct execution" part of the idea is simple: *just run the program directly on the  CPU*. 

- When the OS wishes to start a program running:
  -  it creates a process entry for it in a process list, -
  -  allocates some memory for it, 
  -  loads the program code into memory (from disk), 
  -  locates its entry point, 
  -  jumps to it, 
  -  and starts running the user's code.

There are two problems with this approach: 1. If we just run a program, how can the OS make sure the program does not do anything that we donot want it to do. 2. When we are running a process, how does the OS stop it from running and switch to another process, thus implementing the time sharing we require to virtualize the CPU.

**user mode**: code that runs in user mode is restricted in what it can do. For example, when running in user mode, a process cannot issue I/O requests; doing so would result in the processor raising an exception; the OS would then likely kill the process.

**kernel Mode**: code thats runs can do what it likes, including priviledged operations such as issuing I/O requests and executing all types of restricted instructions.

**system call**: allow the kernel to carefullt expose certain key pieces of functionality to user programs, sucha s accessing the file system, creating and destorying processes, communicating with other processes, and allocating more memory.

Hardware assists the OS by providing different modes of execution. In user mode, applications do not have full access to hardware resources. In kernel mode, the OS has access to the full resources of the machine. Special instructions to trap into the kernel and return from trap back to user-mode programs are also provided.

The hardware needs to be a bit careful when executing a trap, in that it must make sure to save enough of the caller's registers in order to be able to return correctly when the OS issues the **return-from-trap** instruction.

There are two phases in the limited direct execution(LDE) protocol. 
- In the first (at the boot time), the kernel initializes the trap table and the CPU remembers its locations for subsequent use. The kernel does so via a privileged instruction.
- In the second (when running a process), the kernel sets up a few things (e.g. allocatiung a node on the process list, allocating memory) before using a return-from-trap instruction to start the execution of the process; this swicthes the CPU to user mode and begins running the process. When the process wishes to issue a system call, it traps back into the OS, which handles it and once again returns control via a return-from-trap to the process.

### 6.3 Problem #2: Switching Between Processes
there is clearly no way for the OS to take an action if it is not running on the CPU. Thus we arrive at the crux of the problem. How can the OS regain control of the CPU so that it can switch between processes.

#### A Cooperative Approach: Wait For System Calls
The OS trusts the processes of the system to behave reasonably. Processes that run for too long are assumed to periodically give up the CPU so that the OS can decide to run some other task.

Systems like this often include an explicit **yield** system call, which does nothing except to transfer control to the OS so it can run other processes.

A cooperative scheduling system, the OS regains control of the CPU by waiting for a system call or an illegal operation of some kind to take place.

#### A Non-Cooperative Approach: The OS Takes Control
**A time interrupt**. A timer device can be programmed to raise an interrupt every so many millisceonds; when the interrupt is raised, the currently running process is halted, and a pre-configured **interrupt handler** in the OS runs. At this point, the OS has regained control of the CPU, and thus can do what it pleases: stop the current process, and start a different one.

#### Saving and Restoring Context
**Scheduler**: Making a decision whether to continue running the currently-running process or switch to a different one.




