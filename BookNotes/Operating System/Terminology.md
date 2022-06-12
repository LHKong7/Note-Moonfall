# Terminologies



##### Time Sharing



##### Space Sharing



##### Process

##### user mode: 
code that runs in user mode is restricted in what it can do. For example, when running in user mode, a process cannot issue I/O requests; doing so would result in the processor raising an exception; the OS would then likely kill the process.

##### kernel Mode
code thats runs can do what it likes, including priviledged operations such as issuing I/O requests and executing all types of restricted instructions.

##### system call
allow the kernel to carefullt expose certain key pieces of functionality to user programs, sucha s accessing the file system, creating and destorying processes, communicating with other processes, and allocating more memory.

##### Context Switch
All the OS has to do is save a few register values for the currently-executing process (onto its kernel stack) and restore a few for the soon-to-be-executing process (from its kernel stack). By doing that, the OS thus ensures that when the return-from-trap instruction is finally executed, instead of returning to the process that was running, the system resumes execution of another process.

##### Scheduler
Making a decision whether to continue running the currently-running process or switch to a different one.

##### scheduling metric
A metric is just something that we use to measure something and there are a number of different metrics that make sense in scheduling.

##### turnaround time
The turnaround time of a job is defined as the time at which the job completes minus the time at which the job arrived in the system.

##### FIFO
First in First out, 


##### Blocking and Nonblocking I/O
Most I/O requests are considered **blocking** requests, meaning that control does not return to the application until the I/O is complete. The delayed from system calls such *read()* and *write()* can be quite long. Using system calls that block is sometimes called **synchronous** programming.
In most cases, the wait is not really a program because the program cannot do anything else until the I/O is finished. However,  in cases such as networking programming with multiple clients or with graphical user interface prorgamming. the program may wish to perform other activity as it continues to wait for more data or input from users.

One solution is to use multiple threads so that one part of the program is not waiting for unrelated I/O to complete. 

