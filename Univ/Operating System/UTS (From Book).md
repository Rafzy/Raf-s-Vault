# Chapter 1. Introduction to Computer System

## 1.1 Basic Elements

>An OS becomes a bridge between a user and a hardware, it exploits resources from processor(s), handle primary & secondary memory, handle I/O, etc.

There needs to be four main structural elements to execute programs:
- Processor
	Controls the operation of the computer, and it performs data processing functions, usually called as the Central Processing Unit if there is only one processor
- Main memory
	Stores data and programs, typically volatile (When computer shuts down, the data is lost). In contrast to the **Contents of disk memory** are retained even when the computer system is shut down.
- I/O Modules
	Move data between computer and external environments. The external environment consists 
- System bus
	Medium between processors, main memory, and I/O Modules, allowing them to communicate with one another


![[Pasted image 20241102103200.png]]


The fugre above depicts these components.

Processor exchanges data with memory. For this purpose, it makes two of the internal registers:
- Memory Address Register (MAR)
	Specifies the address in memory for the next read or write
- Memory Buffer Register (MBR)
	Temporarily contains the data to be written into memory, or receives the data read from memory

Similar to these:
- I/O Address Register (I/OAR)
	Specifies a particular I/O device
- I/O Buffer Register (I/OBR)
	used for exchange of data between an I/O Module and processor

> In summary, a memory module consists of a set of locations, and each location contains either instruction or data. I/O Module transfers data from external devices to processor and memory.



## 1.2 Evolution of the microprocessor

Invention of the microprocessor (Contains a processor on a single chip).
Originally much slower than multiprocessors, but have evolved to the point that they are much faster for most computations.

Microprocessor became the fastest general purpose processors.
They also have evolved to become multiprocessors. Each <u>chip</u> (Called a socket) contains multiple <u>processors</u> (called cores). 
Each with multiple levels of memory caches, and multiple logical processors sharing execution units of each core.

> Some terms:
> - Chips/Sockets: The actual physical CPU
> - Processors/Cores: The entire CPU chip, which may contain one or more cores
> - Logical processors: Virtual representation of a processing unit created by Simultaneous Multithreading
> - Hardware threads: Smallest unit of processing that a core or logical processor can handle at one time, basically means how much threads can one core work at the same time


Processors provide very good performance for most forms of computing.
However, there is an increasing demand for numerical computation.
GPUs provide efficient computation an arrays of data using Single-Instruction Multiple Data technique (SIMD)
GPU are no longer used for just rendering advanced graphics, but also for general numerical processing, such as physics simulation, or computations on large spreadsheets.
Digital Signal Processors (DSPs) are present for dealing with streaming signals such as audio or video.
DSPs used to be embedded in I/O devices, like modems, but they are now becoming first-class computational devices.
System on a Chip is a chip architecture where not just the CPUs and caches are on the same chip, but also many other components such as DSP, GPU, I/O devices, and main memory


## 1.3 Instruction Execution

> A program executed by a processor consists of a set of instructions stored in memory.

<u>In it's simplest form</u>, instruction processing consists of two steps. The processor reads (*Fetches*) instructions from memory one at a time, and executes each instruction.
The cycle repeats the act of fetching, and executing instructions. One instruction execution may involve several operations, it depends on the instruction itself

![[Pasted image 20241103132720.png]]

The processing required for a single instruction is called an *instruction cycle*.
and the program execution halts only if the processor is turned off, an error occurred, or program instruction that halts the processor is encountered.

Steps:
1. Processor fetches an instruction from memory, Typically the <u>Program Counter (PC)</u> holds the address of the next instruction to be fetched
2. Fetched instruction is loaded into the <u>Instruction Register (IR)</u>
3. The instruction contains bits that specify the action the processor is to take
4. The processor interprets the instruction and perform the required actions
   These action fall into four categories:
	   - Processor memory: Data transferred from processor to memory, or from memory to processor
	   - Processor I/O: Data transferred from a peripheral device by transferring between processor and I/O Module
	   - Data processing: Processor performs some arithmetic or logical operation on data
	   - Control: An instruction that specify that the sequence of execution may be <u>altered</u>

Example using a hypothetical processor that includes characteristic below:

![[Pasted image 20241103141431.png]]

The processor contains a single data register called the Accumulator (AC).

The figure below illustrates a partial program execution, showing the relevant portions of memory and processor registers.
The program fragment adds the content of memory word at address 940 to the contents of the memory word at address 941 and stores the result in the latter location.


![[Pasted image 20241103143653.png]]


1. The PC contains 300, the instruction at address 300 (1940 in hexadecimal) is loaded into IR and the PC is incremented. ==Note that this process should involve MAR and MBR, but for simplicity are left out==
2. The first 4 bits in the IR indicates that the AC is to be loaded form memory the remaining 12 bits specify the address, which is 940 (Typically at this point, 940 should be stored in the MAR)
3. The next instruction (5941 in hexadecimal) is fetched from 301 and the PC is incremented
4. 5941 instruction states that the old content of AC and the contents of location 941 is to be added, and the result is stored in the AC
5. The next instruction (2941 in hexadecimal) is fetched from location 302, and the PC is incremented
6. 2941 instruction states that the contents of the AC are to be stored in 941


## 1.4 INTERRUPTS

>Virtually all computers provide a mechanism where other modules (IO, Memory) may interrupt the normal sequencing of the processor

**Classes of interrupts**

| Class            | Description                                                                                                                                                                                    |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Program          | Generated by some instruction execution, such as arithmetic overflow, division by zero, attempt to execute an illegal machine instruction, or reference outside of user's allowed memory space |
| Timer            | Generated by a timer within the processor. This allows the operating system to perform certain functions on a regular basis. Ex: Operating system scheduler, Regular maintenance tasks         |
| I/O              | Generated by an I/O controller, to signal normal completion of an operation or to signal a variety of error conditions Ex: Completion of data transfer, Keyboard input, printer ready          |
| Hardware Failure | Generated by a failure, such as power failure or memory parity error                                                                                                                           |

Interrupts provides an improvement in processor utilization. For example, most I/O devices are much slower than a processor.
Suppose that a processor is transferring data to a printer using the basic instruction cycle scheme. After each write operation, the processor must pause and remain idle until the printer catches up, which is highly ineffective.

The figure below illustrate this state of affairs. The user program executes a series of WRITE calls interleaves with processing. Code segments 1, 2, and 3 refer to sequences of instructions that do not involve I/O. The write calls are to an I/O routine that is a system utility and will perform the actual I/O operation. consists of three sections:
- A sequence of instructions (Labelled 4) to prepare for the actual instruction
- The actual I/O command. Without the use of interrupts, once this command is issued, the program must wait for the I/O device to perform the requested function
- The sequence of instructions (Labelled 5) to complete the operation, like setting up a flag to indicate a success or failure

![[Pasted image 20241103155530.png]]

### Interrupts and the instruction cycle

With interrupts, the processor can execute other instructions while an I/O Operation is in progress.
After executing the preparation code and the I/O command itself, the control return to the user program while the external device is accepting data from computer memory and printing it.
When the external device is ready to be serviced, the I/O module for that external device sends an *interrupt request* to the processor, which the the processor suspends the current program to branch off to a routine to service that I/O Device (Known as interrupt handler)


![[Pasted image 20241103160103.png]]


Note that the user program does not contain any special code to accommodate interrupts, the processor and OS are responsible in suspending user program, then resuming it at the same point

To accommodate interrupts, an *interrupt stage* is added to the instruction cycle.

![[Pasted image 20241103160736.png]]

==Note that usually after the processor does check that there is an interrupt, it will send an acknowledgement to the actor that requested it so that it removes it's interrupt request==


### Interrupt Processing

An interrupt triggers several events, both in the processor hardware and the software. The figure below shows the typical sequence

![[Pasted image 20241103161705.png]]

These sequence occur following an interruption request to the processor:
1. The device issues an interrupt signal
2. The processor finishes the current instruction first before responding to the interrupt
3. The processor checks for any interrupt requests, determine if there is one, and sends an acknowledgment signal
4. The processor prepares to transfer control to the interrupt routine. It first saves information needed to resume the current program at the point of interrupt. The minimum information required is the program status word (PSW) and the location of the next instruction to be executed, which is contained in the PC. (These can be pushed onto a control stack)
5. The processor then loads the PC with the entry location for the interrupt handling routine. there may be a single program or more than one. If more than one, the processor must determine which one to invoke first. This information is either included with the interrupt signal, or the processor may have to issue a request to the device to get a response that contains the information
6. The PSW and PC relating to the interrupted program has been saved on the control stack. However, the contents of the process registers need to be saved, because they may be used by the interrupt handler. Typically the interrupt handler will begin by saving the contents of all registers on the stack.
   ![[Pasted image 20241103164956.png]]
   
   7. The interrupt handler may now proceed to process the interrupt. This includes an examination of status information relating to the I/O Operation or other event that caused an interrupt
   8. When interrupt processing is complete, the saved register values are retrieved back from the control stack and restored to the register
   9. Then the processor restore the PSW and program counter values back from the stack.


### Multiple Interrupts

> What happens when another interrupt request is being handled when one is being processed

Two approaches:
- Disable interrupts while an interrupt is being processed (Sequential interrupt processing)
	*Disabled interrupts* means the processor ignores any new interrupt request signal. If an interrupt occurs during this time, it will remain pending and will be checked after the processor has re-enabled interrupts.
	
	However the drawback of this approach is that it does not take into account the relative priority or time-critical needs. If the new interrupt requires immediate attention from the processor, the processor can't immediately handle the new interrupt.

- Nested interrupt handling
	With this approach, we define priorities for interrupts, and allow an interrupt of higher priority to cause the lower priority interrupt handler to be interrupted. 

![[Pasted image 20241103191931.png]]


## 1.5 The Memory Hierarchy

There are three key characteristics a memory can have:
- Capacity
- Access time (speed)
- Cost

And of course there is a trade off among these three characteristics. The way out of this dilemma is to not rely on a signle memory component, but to employ a **Memory Hierarchy**

![[Pasted image 20241103201743.png]]


As the hierarchy go down, the following occurs:
1. Decreasing cost per bit
2. Increasing capacity
3. increasing access time
4. Decreasing frequency of access to the memory by the processor

So smaller, faster memory is supplemented by bigger, slower memory.

The basis of the validity of condition 4 is a principle known as **Locality of reference**.

<u>Locality of reference</u>
During the course of execution of a program, memory references by the processor, for both instructions and data, tend to cluster. Because programs typically have a number of iterative loops and subroutines, once a loop is entered, there are repeated references to a small set of instructions.
Similarly, a operations on tables and arrays involve access to a clustered set of data bytes.

So, according to this principle, it's possible to organize data accross the hierarchy so such that the lower level has lower percentages of accesses than the level above
Let a level 2 memory contain all the program instructions and data
The current clusters can be temporarily placed on level 1.
From time to time, one of the clusters in level 1 must be swapped back to level 2 to make room for more clusters on level 1
But with this, most references will be to instructions and data contained in level 1.


## 1.6 Cache Memory

> Cache memory is invisible to the OS, but it interacts with other memory management hardware


### Motivation

The processor will access the memory at least one on every instruction cycles, to fetch the instruction, and often one or more times to fetch operands or store results.
That means then that the processor execution rate is limited by the memory cycle time (The time it takes to read one word from or to memory)

Over the years, processor speed has increased rapidly compared to main memory speed. Ideally, main memory should be built with the same technology as the processor registers, giving memory cycles comparable to processor cycle times, but this has been too expensive.

To fix this, we can use the principal of locality by providing a small, fast memory between the processor and main memory, namely the cache

### Cache principles

Cache aims to provide a fast memory access time, and to support the main memory. The concept is illustrated below.

![[Pasted image 20241103211106.png]]


The cache contains a copy of a portion of main memory. When a processor attempts to read a byte or word of memory, the processor will check first if that data is in the cache.
If so, the data will be delivered to the processor.
If not, a chunk of memory will be delivered from the main memory to the cache, and then accessed by the processor.
Because of the principal of reference, that block of data is likely that many of the near future memory references will be to other bytes in that block


## 1.7 Direct Memory Access

> I/O Operations have three possible techniques, Programmed I/O, interrupt-driven I/O, and Direct Memory Access (DMA)


<u>Programmed I/O</u>
When the processor is executing a program and an instruction relating to I/O, it will execute that command relating to the corresponding I/O.
In the case of **Programmed I/O** , the I/O Module performs the action, then sets the appropriate bits in the I/O status register but takes no further action to alert the processor.
So the processor needs to take an active role when the I/O Instruction is completed.
As a result, the processor must wait while repeatedly check the status of the I/O module.


<u>Interrupt driven I/O</u>
As an alternative, in interrupt driven I/O, the processor issues an I/O command to a module then go do some other work.
the I/O module then will interrupt the processor to request service when it's ready to exchange data with the processor.
Even though it's more efficient than programmed I/O, the processor still needs active intervention to transfer data between memory and an I/O Module, and any data transfer must traverse a path through the processor.


When large volumes of data are to be moved, **Direct Memory Access** is more efficient

<u>Direct Memory Access</u>
The DMA function can be performed by a separate module on the system bus, or it can be incorporated into an I/O Module.
When the processor wishes to read or write a block of data, it issues a command to the DMA module by sending these information:
- Whether a read or write is requested
- The address of the I/O Device involved
- The starting location in memory to read data from or write data to
- the number of words to be read or written

The processor will then continue with other work, and <u>delegate</u> the I/O Operation to the DMA module.
The module will then transfer the block of data, one word at a time, directly from or to memory without going through the processor.
When the transfer is complete, the DMA will then send an interrupt signal to the processor, so that the processor is only involved at the start and at the end of the transfer.

## 1.8 Multiprocessor and Multicore organization

> computers have been viewed as a sequential machine, where they execute instructions one at a time and in sequence. But this isn't entirely true, the existence of computers with multiple control signals that are generated at the same time, and overlapping fetch and execute operations have been around for a long time


There are three approaches to providing parallelism in computers:
- Symmetric multiprocessors (SMP)
- Multicore computers
- Clusters

### Symmetric Multiprocessor

SMP can be defined with the following characteristics:
1. Two or more similar processors of comparable capability
2. These processor share the same main memory, and I/O Facilities, and they are interconnected by a bus or other internal connection scheme
3. All processors share access to I/O devices.
4. All processor can perform the same functions
5. The system is controlled by an integrated operating system

SMP has a number of potential advantages over uniprocessors:
- Performance
- Availability
- Incremental Growth
- Scaling

![[Pasted image 20241104104238.png]]


### Multicore Computers

Combines two or more "processors" (Called cores) in a single piece of silicon (called a die)
Each core consists of all the components of an independent processor, such as registers, ALU, pipeline hardware, and control unit.

An example of this is the Intel Core i7-5960X, which includes six x86 processors. Each with a dedicated L2 cache, and a shared L3 cache.

![[Pasted image 20241104104913.png]]






# Chapter 3. Processes

All OS are built around the concept of processes. Most requirements the OS must meet can be expressed to reference to processes:
- The OS must interleave the execution of multiple processes, to maximize processor utilization while providing reasonable response time
- The OS must allocate resources to processes in conformance with a specific policy while at the same time avoiding deadlock
- The OS may be required to support inter-process communication and user creation of processes, both of which may aid in the structuring of applications



## 3.1 What is a process

We will discuss how an OS can manage the execution of applications such that:
- Resources are made available to multiple applications
- The physical processor is switched among multiple applications so all will appear to be progressing
- The processor and I/O devices can be used efficiently

### Processes and process control block

We can think of a process as an entity that consists of a number of elements, these elements are **program code**, and a **set of data** associated to that code.
Let's suppose the processor is executing this program code, and we refer tot his executing entity as a process. At any given time *while the program is executing*, the process can be uniquely characterized by a number of elements:
- Identifier: A unique identifier associated with this process
- State: State of the process (Running, or success, or failed)
- Priority: Priority of this process relative to the other processes
- Program Counter: The address of the next instruction in the program to be executed
- Memory pointers: Include pointers to the program code and data associated with this process
- Context data: Data that are present in registers in the processor while the process is being executed
- I/O Status information: Outstanding I/O Requests, I/O Devices assigned to this process, etc
- Accounting information: The amount of processor time and clock time used, etc

These information is typically stored in a data structure, called **Process Control Block**. The significant point about the Process control block is that the information is sufficient enough so that when a process is interrupted, it can resume at any given time, and the state of the current process can be changed such as *blocked* or *ready*.

![[Pasted image 20241104111745.png]]


## 3.2 Process States

**Trace** -> listing of sequence of instructions that execute for a process
We can characterize the behavior of processor by showing how the traces of various processes are interleaved

**Dispatcher** -> Program that switches the processor from one process to another

![[Pasted image 20241104112747.png]]


Assume there are these three processes each with varying traces.
Assume that the processor will execute them, but with a limited instruction cycles for each processor to avoid one processor monopolizing processor time.

![[Pasted image 20241104113023.png]]


### Two-State Model Process

The first step in designing an OS to control processes is to describe the behavior that we would like the process to exhibit

The simplest form of this is a process with two states: **Running**, or **Not Running**

![[Pasted image 20241104114259.png]]


### The creation and termination of processes

>The life of a process is bounded by it's creation and termination


<u>Process Creation</u>
When a new process is added to those currently being managed, the OS will build a data structure used to manage the process, and allocates address space in main memory to the process.

There are four common events that lead to a process creation:

![[Pasted image 20241104121414.png]]


The 4th point, where the OS creates a process at the explicit request of another process, it's referred to as **process spawning**

When a process spawns another, the former is referred to as the **parent process** and the spawned process is referred to as the **child process**.


<u>Process Termination</u>
There are many typical reasons for a process to be terminated. Any computer system must provide a means for a process to indicate it's completion

![[Pasted image 20241104121944.png]]



### Five State Model Process

Sometimes using the Two state model process is inadequate, some processes in the Not Running state are ready to execute, while others are blocked: like waiting for an I/O Operation to complete. 
Thus if we used a single queue, the dispatcher would have to scan the list looking for the process that is not blocked and that has been in the queue the longest.

A better way would be to split the Not Running state into two states: **Ready** and **Blocked**.

![[Pasted image 20241104122347.png]]


1. Running: The process that is currently being executed.
2. Ready: A process that is prepared to execute when given the opportunity
3. Blocked/Waiting: A process that cannot execute until some event occurs, such as waiting for an I/O operation completion.
4. New: A process that has just been created but not admitted to the pool of executable processes by the OS.
5. Exit: A process that has been released from the pool of executable processes by the OS.

**Transitions**:
- Null -> New: A new process is created to execute a program
- New -> Ready: The OS will move a process from the New state to the Ready state when it's prepared to take on an additional process. ==Most Systems limit the number of existing processes or the amount of virtual memory committed to existing processes==
- Ready -> Running: When it's time to select a process to run, the OS chooses the processes in the Ready state.
- Running -> Exit: The currently running process is terminated by the OS if the process indicates that it has completed or it has aborted
- Running -> Ready: The most common reason for this transition is that the running process has reached the maximum allowable time for uninterrupted execution. or the OS can **preempt** the current process for another, higher priority process.
- Running -> Blocked: A process will be put in the blocked state if it requests something for which it must wait
- Blocked -> Ready: A process in the blocked state is moved to the ready state when the event it has been waiting already occurs
- Ready -> Exit: This transition isn't shown in the diagram, but a parent may terminate a child process at any tame. Or if the parent process is terminated, all child processes may be terminated
- Blocked -> Exit: Same with the comment above

> A blocked queue that has been waiting for an event may be returned to the ready queue when that event happens. This means that the OS must scan the entire blocked queue for the processes waiting for that event.
> So ideally, it's more efficient to have a number of queues, one for each event

![[Pasted image 20241104125717.png]]


### Suspended Processes

Even with the five state model process above, the processor is so much faster than I/O That it will be common that all the processes in memory will end up in block state waiting for I/O. Thus even in multiprogramming, a processor could be idle most of the time.

A solution for this is swapping, which involves moving part or all of a process from main memory to disk. When none of the processes in main memory is in the ready state, the OS swaps one of the blocked processes out on to disk into a suspend queue.

Then the OS either brings another process from the suspend queue, or it honors a new-process request. Execution then continues with the newly arrived process.

We need keep in consideration that the processes in suspended states are previously blocked states, waiting for an event to occur, and when that event occurs, the process is not blocked and potentially available for execution

![[Pasted image 20241104131903.png]]


1. Ready: The process is in main memory available for execution
2. Blocked: The process is in main memory, waiting for an event
3. Blocked/Suspend: The process is in secondary memory waiting for an event
4. Ready/Suspend: The process is in secondary memory but available for execution as soon as it's loaded into memory


**Transitions**:
- Blocked -> Blocked/Suspend: If there are no ready processes, then one blocked process is swapped out to make room for another process that is not blocked, or when the OS needs more main memory to obtain adequate performance
- Blocked/Suspend -> Ready/Suspend: A process in the Blocked/Suspend state is moved to Ready/Suspend when the event it has been waiting occurs. That means that the information regarding the suspended processes must be accessible by the OS
- Ready/Suspend -> Ready: When there are no ready processes in main memory, the OS will bring in one to continue execution. Or it might be the case that a process in Ready/Suspend has a higher priority than any processes in the ready state.
- Ready -> Ready/Suspend: Usually the OS would prefer to suspend a blocked process than a ready one, but it may be necessary to suspend a ready process, if that's the only way to free up a large block of main memory.


<u>Other uses of suspension</u>

General definition of a suspended process:
1. Process is not immediately available for an execution
2. May or may not be waiting on an event, if it is, the blocked condition is independent to the suspended condition
3. The process was placed in a suspended state by an agent: itself, a parent, or the OS
4. The process may not be removed from this state until the agent explicitly orders the removal

Reasons for a process to be suspended:
![[Pasted image 20241104134727.png]]


## 3.3 Process Description

>What information does the OS need to control processes and manage resources from them?

The universal approach to an OS providing information about the current status of each process and resource is straightforward: it creates and maintains tables of information about each entity that it is managing.

The general tables maintained by the OS are: Memory, I/O, File, and Process

![[Pasted image 20241104141205.png]]

<u>Memory tables</u>
Used to keep track of both main and secondary memory. Some of main memory is reserved for use by the OS, the rest is usable by processes. 
Memory tables must include the following information:
- The allocation of main memory to processes
- The allocation of secondary memory to processes
- Any protection attributes of blocks of main or virtual memory.
- Any information needed to manage virtual memory


<u>I/O Tables</u>
Used by the OS to manage I/O devices and channels of the computer system. I/O Devices may be available or assigned to a particular process. If an I/O Operation is in progress, the OS needs to know the status of the I/O Operation and the location in main memory being used as the source or destination of the I/O Transfer.


<u>File Tables</u>
Provide information about the existence of files, their location on secondary memory, status, and other attributes. These information may be maintained and used by a file management system, in which case the OS has little or no knowledge of files.


<u>Process tables</u>
First, consider what the OS must know to manage and control a process, first it must know where the process is located, and it must know the attributes of the process necessary for it's management

- Process Location
	We need to address what the physical manifestation of a process is. A process typically needs a set of programs, set of data locations, sufficient memory to hold the programs and data, and a process typically involves a stack. Finally a process has a collection of attributes called the Process Control Block. 
	
	These collections of data, stack, and attributes are called as the **process image**
	![[Pasted image 20241104142028.png]]
	
	In order for the OS to manage the process, at least a small part of the process image must be in main memory, and to execute the process, the entire image must be loaded into main memory. Thus the OS must know each process on disk and in main memory. And the OS must keep track of which portions of the image of each process are still in main memory.
	

- Process attributes
	An OS will utilize the Process Control Block to identify the process's attributes. We can group the Process Control Block into three general categories:
	1. Process identification
	2. Process state information
	3. Process control information
	![[Pasted image 20241104144333.png]]
	
	Example of process images
	![[Pasted image 20241104144850.png]]

- Roles of the Process Control Block
	the PCB is the most important data structure in an OS. Each PCB contains all of the information about a process that is needed by the OS.
	The blocks are read/modified by virtually every module in the OS.
	However with this design, it brings up an important issue in the matters of protections of the PCB:
	- A bug in a single routine could damage PCBs which would destroy the system's ability to manage the effected processes
	- A design change in the structure or semantics of the PCBs would affect a number of modules in the OS
	We can address these problems by requiring all routines in the OS to go through a handler routine, which is to protect PCBs, and which is the sole arbiter for reading and writing these blocks.

## 3.4 Process Control

### Modes of Execution

Most processors support two types of execution:
- User mode
  Less privileged
  User programs would typically execute in this mode
- Kernel mode
  More privelege
  Refers to the kernel of the OS

![[Pasted image 20241104150249.png]]


Typically, there is a bit in the PSW that indicates the mode of execution, this bit is changed in response to certain events. Like when a user makes a call to an operating system service, the mode is set to the kernel mode, and upon return from the service to the user process, the mode is set to user mode.

### Process Creation

Once the OS decides to create a new process, it proceeds as follows:
- Assign a unique process identifier
- Allocate process for the space
- Initialize the process control block
- Set appropriate linkages
- Create or expand other data structures


### Process switching

<u>When to switch processes</u>
A process switch may occur any time that the OS has gained control from the currently running process

First there are system interrupts, we can distinguish two types of system interrupts:
- Interrupt
- Trap

An **interrupt** is due to some sort of event that is external and independent of the currently running process, such as the completion of an I/O Operation.

A **Trap** relates to an error or exception condition generated within the currently running process. 

![[Pasted image 20241104152002.png]]


<u>Mode switching</u>
Note that in chapter 1, we have discussed that the processor checks to see if any interrupts are pending. If an interrupt is pending, the processor will do the following:
- Sets the program counter to the starting address of the interrupt handler
- It switches from user mode to kernel mode so the interrupt processing code may include privileged instructions

The processor state information portion of the process control block is saved so that the interrupted process may resume after the interrupt handler is finished.


## 3.6 Unix SVR4 Process Management

(To be filled)

# Chapter 4. Threads

## 4.1 Processes and Threads

So far, the concept of a process has two characteristics:
1. Resource ownership
   A process includes a virtual address space to hold the process image. From time to time, a process may be allocated control or ownership of resources such as main memory, I/O Channels, I/O devices, etc
2. Scheduling/execution
   The execution of a process follows a trace through one or more program. This execution may be interleaved with other processes.

These two characteristics are independent and should be treated independently by the OS.
To distinguish the two characteristics, the unit of dispatching is usually referred to as a **thread** or **lightweight process**
While the unit of resource of ownership is usually referred to as a **process** or **task**

### Multithreading

>Refers to the ability of an OS to support multiple paths of execution within a single process.

![[Pasted image 20241104160516.png]]

In a multithreaded environment, a process is defined as the unit of resource allocation and a unit of protection. The following are associated:
- A virtual address space that holds the process image
- Protected access to processors, other processes, files, and I/O Resources

Within a process, there may be one or more threads, each with:
- A thread execution state
- A saved threat context when not running (One way to view thread is as an independent program counter operating within a process)
- Some per-thread static storage
- Access to the memory and resources of it's process, shared with all other threads in that process

![[Pasted image 20241104160851.png]]


As we can see, in a multithreaded environment, there are separate stacks for each thread, as well as a separate control block for each thread containing the register values, priority, and other thread-related state information.
So all the threads of a process share the state and resources of that process. They reside in the same address space and have access to the same data.

Key benefits of thread:
- It takes far less time to create a new thread than to create a new process
- IT takes less time to terminate a thread
- It takes less time to switch between two threads within the same process
- Threads enhance efficiency in communication between different executing programs.


An example of an application that can make use of multithreading is a file server. As new file request comes in, a new thread can be spawned for the file management program, because a server will handle many requests, many threads will be created and destroyed in a short period.

Four examples of the uses of threads in a single-user multiprocessing system:
1. Foreground and background work
	In a spreadsheet program, one thread could display menus and read user input, while another executes user commands and updates in the spreadsheet.
2. Asynchronous processing
	Asynchronous elements in a program can be implemented as threads. For example as a protection against power failure, a word processor can write it's RAM buffer to disk once every minutes.
3. Speed of execution
	A multithreaded process can execute one batch of data while reading the next batch from a device. And threads from the same process may execute simultaneously. So even though one thread may be blocked for an I/O operation, another may be executing
4. Modular program structure
	Programs that involve a variety of activities or a variety of sources and destinations of input and output may be easier to implement using threads

Note that in an OS that supports threads, scheduling and dispatching is done on a thread level, most of the state information dealing with execution is maintained in thread-level data structures. 
But several actions affect all of the threads in a process, like suspending a process.


### Thread functionality

> Like processes, threads may synchronize with one another.

<u>Thread states</u>
Key states for thread are running, ready, and blocked. It doesn't make sense to associate suspend states with threads because they are process level concepts. If a process is suspended, all of it's threads are swapped out because they share the same address space.

Basic thread operations:
1. Spawn
	When a new process is spawned, a thread for that process is also spawned. A thread within a process may spawn another thread within the same process.
2. Block
	When a thread needs to wait an event, it will block. (Same concept as the process)
3. Unblock
	When the event for which a thread is blocked occur, the thread is moved to the ready queue
4. Finish
	When a thread completes, it's register context and stacks are deallocated

<u>Thread synchronization</u>
All of the threads of a process share the same address space and other resources, such as open files.
Any alteration of a resource by one process affects the environment of the other threads in the same process. So it's necessary to synchronize the activities of various threads so that they do not interfere with one another. 


## 4.2 Types of Threads

### User level and kernel-level threads

There are two broad categories of thread implementations:
- User level threads (ULTs)
- Kernel level threads (KLTs)

![[Pasted image 20241104170218.png]]

<u>User-Level threads</u>
In a pure ULT facility, all of the work of thread management is done by the application, and the kernel isn't aware of the existence of those threads
Any application can be programmed to be multithreaded using a threads library, which contains code for creating and destroying threads, passing messages and data between threads, scheduling thread execution, and for saving and restoring thread context

By default, an application will begin with a single thread which then the application can spawn a new thread to run within the same process using the threads library.

This process is not known in the kernel level, the kernel continues to schedule the process as a unit and assigns a single execution state to that process.

**Advantages of ULTs**:
- Thread switching does not require kernel-mode privileges 
- Scheduling can be application specific. One application may benefit most from a simple round-robin scheduling algorithm, while another might benefit from a priority based scheduling algorithm.
- ULTs can run on any OS, no changes are required to the underlying kernel to support ULTs

**Disadvantages of ULTs**:
- In a typical OS, many system calls are blocking, so when ULT executes system calls, all of the threads within the process are blocked
- Multithreading application cannot take full advantage in a pure ULT strategy. A kernel assigns one process to only one processor at a time. So only a single thread can execute at a time.

A way to overcome the problem of blocking threads is to use a technique referred to as **jacketing**. The purpose of jacketing is to convert a blocking system call into a nonblocking system call.

Instead of directly calling a system I/O routine, a thread calls an application level I/O jacket routine. Within this jacket routine is code that checks to determine if the I/O device is busy. If it is, the thread enters the blocked state and passes control (through the threads library) to another thread.



<u>Kernel level threads</u>
All of the work of thread management is done by the kernel. There is no thread management code in the application layer, simply an API to the kernel thread facility.
The kernel maintain context information for the process, and the individual threads within the process. Scheduling by the kernel is done on a thread basis.

**Advantages of KLT**
- Kernel can simultaneously schedule multiple threads from the same process on multiple processors
- If one thread in a process is blocked, the kernel can schedule another thread of the same process
- Kernel routines themselves can be multithreaded

**Disadvantages of KLT**
- The transfer of control from one thread to another requires a mode switch to the kernel
  ![[Pasted image 20241104174242.png]]


<u>Combined Approaches</u>
Some operating system provide a combined ULT/KLT facility
In a combined approach, thread creation is done completely in a user space, as is the bulk of the scheduling and synchronization within an application.
Multiple ULTs are mapped onto some (smaller or equal) number of KLTs.
Multiple threads within the same application can run in a parallel on multiple processors, and a blocking system call doesn't need to block the entire process.


## 4.3 Multicore and Multithreading

A number of classes of applications benefit directly from the ability to scale throughput with the number of cores:
- Multithreaded native applications
	Multithreaded applications are characterized by having a small number of highly threaded processes.
- Multiprocess applications
	Multiprocesses applications are characterized by the presence of many single-threaded processes.
- Java applications
	Java applications embrace threading in a fundamental way.
- Multi-instance applications.
	It's possible to gain from multicore architecture by running multiple instances of the application in parallel

# Chapter 5. Concurrency: Mutual Exclusion and Synchronization

The central themes of operating system are all concerned about managing processes and threads:
- Multiprogramming: Managing multiprocesses within a uniprocessor system
- Multiprocessing: Managing multiple processes within a multiprocessor
- Distributed processing: The management of multiple processes executing on multiple, distributed computer systems. 

Fundamental to these areas is **concurrency**
Concurrency arises in these context:
1. Multiple applications: Multiprogramming was invented to allow processing time to be dynamically shared among a number of active applications
2. Structured applications: As an extension of the principles of modular design and structured programming, some applications can be effectively programmed as a set of concurrent processes
4. Operating system structure: The same structuring advantages apply to system programs, and we have seen that OS themselves are often implemented as a set of processes or threads

==The basic requirement for support of concurrent processes is the ability to enforce mutual exclusion==

Mutual exclusion $\to$ The ability to exclude all other processes from a course of action while one process is granted that ability

![[Pasted image 20241104205811.png]]

## 5.1 Mutual exclusion: Software approaches

We can implement software for concurrent processes that execute on a single processor or multiprocessor machine with main memory.
These approaches usually assume elementary mutual exclusion at the memory access level
- Simultaneous accesses to the same location in main memory are serialized by some memory arbiter
- Beyond this, no support in the hardware, operating system, or programming language is assumed
Djikstra reported an algorithm for mutual exclusion for two processes, designed by Dekker

## 5.2 Principles of Concurrency

in a single-processor multiprogramming system, processes are interleaved in time to yield the appearance of simultaneous execution.
in a multiprocessor system, it's possible not only to interleave the execution of multiple processes, but also to overlap them

Both interleaving and overlapping processes can be viewed as examples of concurrent processing, and both present the same problems. In the case of a uniprocessor, the problem stem from a basic characteristic of multiprogramming systems:
The speed of execution of processes cannot be predicted. It depends on the activities of other processes.
The following problems arise:
1. Sharing global resources is fraught with peril. (Two processes both make use of the same global variable, both perform reads and writes, then the order in which the reads and writes are executed is crucial)
2. It's difficult for the OS to optimally manage the allocation of resources.
3. It becomes very difficult to locate a programming error because results are not deterministic and reproducible

Based on the problems above, we will address one of the issues which is protecting the shared global variable. We can protect the global variable by controlling the code that accesses the variable. If we impose that only one process at a time may access a function that has a global variable, then the error will not occur.

This solution works in both a single processor multiprogramming environment, as well as a multiprocessor environment.

### Race condition

>Occurs when multiple processes or threads read and write data items so that the final result depends on the order of execution of instructions

The "loser" of the ace is the process that updates last and will determine the final value of the variable

### Operating System concerns

Design and management issues raised by the existence of concurrency:
- The OS must be able to keep track of the various processes. This is done with the use of PCB
- The OS must allocate and deallocate various resources for each process, theses resources include:
	- Processor time
	- Memory
	- Files
	- I/O Devices
- The OS must protect the data and physical resources of each process against unintended interference by other processes
- The functioning of a process, and the output it produces must be independent of the speed at which it's execution is carried out relative to the speed of the concurrent processes.


<u>Competition among processes for resources</u>
Concurrent processes come into conflict with each other when they are competing for the use of the same resource. For example, two processes not aware of the existence of the other, and each unaffected by the execution of the other processes.

In the case of competing processes, three control problems must be faced.
First is the need for mutual exclusion. Suppose two or more processes require access to a single non-sharable resource. During the execution, each process will be sending commands to the I/O Device, receiving status information.
We will refer to such a resource as a **critical** resource, and the portion of the program that uses it as a **critical section**.
It's important that only one program at a time can be allowed in this critical section.

The enforcement of mutual exclusion introduces two additional control problems:

**Deadlocks**
For example, two processes P1 and P2, and two resources, R1 and R2. Suppose that each process needs access to both resources, the OS assigns R1 to P2, and R2 to Pw. Each process is waiting for one of two resources, neither one will release the resource until it has acquired the other resource. Both processes are in a deadlock

**Starvation**
Suppose that three processes (P1, P2, P3) each require periodic access to resources R. 
Consider P1 is in possession of R, both P2 and P3 are delayed, waiting for the resource. When P1 exits, either P2 or P3 should be allowed access. Assume OS grants access to P3 and P1 requires access before P3 completes it's critical section, and the OS grants P1 the resource again after P3 finishes.
Then P2 may indefinitely be denied access of the resource, even though there's no deadlock situation.

<u>Cooperation among processes by sharing</u>
This case covers processes that interact with other processes without being explicitly aware of the other process. For example multiple processes have access to a shared variables, and the process know that other processes may have access to the same data, thus they must cooperate to ensure the data they share are properly managed.

Mutual exclusion, deadlock, and starvation is present, the difference is that data may be accessed in two different modes, writing and reading, and only writing operations must be mutually exclusive.

<u>Cooperation among processes by communication</u>
When processes cooperate by communication, various processes participate in a common effect that link all of the processes. Communication provides a way to synchronize, or coordinate the various activities.
Although there is no mutual exclusion in this sort of cooperation, deadlock and starvation still exists.


### Requirements for Mutual Exclusion

1. Mutual exclusion should be enforced: only one process at a time is allowed into it's critical section
2. A process that halts in it's noncritical section must do so without interfering with other processes
3. It must not be possible for a process requiring a critical section to be delayed indefinitely: No deadlock or starvation
4. When no process is in a critical section, any process that requests entry to it's critical section must be permitted to enter without delay
5. No assumptions are made about relative process speeds or number of processors
6. A process remains inside it's critical section for a finite time only

## 5.3 Mutual Exclusion: Hardware Support

### Interrupt disabling

IN a uniprocessor system, a process will continue to run until it invokes an OS service or until it is interrupted. Therefore, to guarantee mutual exclusion, it's sufficient to prevent a process in it's critical section to be interrupted.
The price of this approach is high though, the efficiency of execution could be noticeably degraded because processor is limited in it's ability to interleave processes.
Another problem is that this approach only works in single-processor systems. In a multiprocessor system, disabling interrupt won't guarantee mutual exclusion

### Special Machine Instructions

<u>Compare and swap instruction</u>
Note that CAS is an **atomic** operation, meaning it's executed as a single, indivisible operation that cannot be interrupted.
CAS is used to update a value only if it matches an expected value. This can ensure that changes to shared data are made safely in a concurrent environment.

## 5.4 Semaphores

Common concurrency mechanisms
![[Pasted image 20241105002920.png]]

This is the fundamental principle:
Two or more processes can cooperate by means of simple signals. Such that a process can be forced to stop at a specified place until it has received a specific signal
For signaling, special variables called semaphores are used.
To transmit a signal via semaphore s, a process executes the primitive semSignal(s).
To receive a signal via semaphore s, a process executes the primitive semWait(s), if the corresponding signal has not yet been transmitted, the process is suspended until the transmission takes place.

To achieve the desired effect, we can view the semaphore as a variable that has an integer value upon which only three operations are defined:
1. A semaphore may be initialized to a non-negative integer value
2. The semWait operation decrements the semaphore value. If the value becomes negative, then the process executing the semWait is blocked. Otherwise, the process continues execution
3. The semSignal operation increments the semaphore value. If the resulting value is less than or equal to zero, then a process blocked by a semWait operation, if any, is unblocked.
There is no other way to inspect and manipulate semaphores other than these three operations

semWait is invoked before going into a critical region
semSignal is invoked after exiting a critical region

![[Pasted image 20241105010959.png]]

Another, more restricted version is the binary semaphore, it may only take on values 0 and 1.
1. A binary semaphore may be initialized to 0 or 1
2. The semWaitB operation checks the semaphore value, if the value is zero, then the process executing semWaitB is blocked. If the value is one, then the semaphore value is changed to 0 and the process continues execution
3. The SemSignalB operation checks to see if any processes are blocked on this semaphore. If so, then a process blocked by a semWaitB operation is unblocked. If no processes are blocked, then the value of the semaphore is set to one

![[Pasted image 20241105011409.png]]

Both counting semaphore and binary semaphore uses a queue to hold processes waiting on the semaphore. The fairest removal policy is first-in-first-out, the process that has been blocked the longest is released from the queue first.
A semaphore that includes this policy is called a **strong semaphore.**
A semaphore that does not specify the order in which processes are removed from the queue is a **weak semaphore**


## 5.5 Monitors

The downside of using semaphores is semWait and semSignal operations may be scattered throughout a program, and it's not easy to see the overall effect of these operations on the semaphores they affect.

Monitor is a programming language construct that provides equivalent functionality to that of semaphores, and is easier to control.

Characteristics of a monitor:
1. The local data variables are accessible only by the monitor's procedures and not by any external procedure
2. A process enters the monitor by invoking one of it's procedures
3. Only one process may be executing in the monitor at a time, any other processes that have invoked the monitor are blocked, waiting for the monitor to become available

A monitor supports synchronization by the use of **conditional variables**. that are contained within the monitor, and accessible only within the monitor. Conditional variables are special data types in monitor, operated by two functions:
- cwait (c): suspend execution of the calling process on condition c, the monitor is now available for use by another process
- csignal (c): resume execution of some process blocked after a cwait on the same condition. If there are several such processes, choose one of them, if there is no such process, do nothing

## 5.6 Message Passing

When a process interacts with one another, two fundamental requirements must be satisfied: Synchronization, and communication. Processes need to be synchronized to enforce mutual exclusion, and cooperating processes may need to exchange information.
One approach to providing both of these functions is message passing.

This is the minimum set of operations needed for processes to engage in message passing:
send (destination, message)
receive (source, message)

### Synchronization

The communication of a message between two processes implies some level of synchronization between the two: The receiver cannot receive a message until it has been sent by another process.

When a process issues a receive primitive, there are two possibilities:
1. If a message has previously been sent, the message is received, and execution continues
2. If there is no waiting message, then either (a) the process is blocked until a message arrives, or (b) the process continues to execute, abandoning the attempt to receive

![[Pasted image 20241105015608.png]]


# Chapter 6. Concurrency: Deadlock and starvation

## 6.1 Principles of deadlock

### Resource category

Two general categories can be distinguished: **Reusable** and **Consumable**

Reusable resource means resources that can be safely used by only one process at a time and is not depleted by that use. Processes obtain resources units that they later release for reuse by other processors

Consumable resource is one that can be created and destroyed. Typically there is no limit to the number of consumable resources of a particular type. An unblocked producing process may create any number of such resources.

### Deadlock preventions

There is no single effective strategy that can deal with deadlock. Three approaches are common:
- Deadlock prevention: Disallow one of the three necessary conditions for deadlock occurrence
- Deadlock avoidance: Do not grant a resource request if this allocation might lead to deadlock
- Deadlock detention: Grant resource requests when possible, but periodically check for the presence of deadlock and take action to recover

![[Pasted image 20241105021737.png]]


### Conditions for a deadlock

1. **Mutual Exclusion**
	Only one process may use a resource at a time, no process may access a resource unit that has been allocated to another process
2. Hold and wait
	A process may hold allocated resources while awaiting assignment of other resources
3. No pre-emption
	No resource can be forcibly removed from a process holding it

The first three conditions are necessary, but not sufficient, for a deadlock to exist, and take place, a fourth condition is required:

4. Circular wait
	A closed chain of processes exists, such that each process holds at least one resource needed by the next process chain


## Deadlock Prevention

Deadlock prevention is to design a system in such a way that the possibility of a deadlock is excluded. We can view deadlock prevention into two classes. An indirect method of deadlock prevention is to prevent one of the three necessary conditions to produce a deadlock. These are the four techniques related to each 

- **Mutual exclusion**
	The first one here cannot be disallowed, because mutual exclusion is needed in a synchronized processor environment. If access to a resource requires mutual exclusion, then mutual exclusion must be supported by the OS
- **Hold and Wait**
	Can be prevented that a process requests all of it's required resources at one time and blocking the process until all requests can be granted simultaneously. Although this method can lead to starvation
- **No-preemption**
	can be prevented in several ways. If a process holding certain resources is denied, that process must release it's original resource, and if necessary, request them again together with the additional resource. Or, if a process requests a resource that is currently held by another process, the OS can pre-empt the second process, requiring it to release it's resources.
- **Circular wait**
	Can be prevented by defining a linear ordering of resource types. If a process has been allocated resources of type R, then it may subsequently request only those resources of types following R in the ordering.


## 6.3 Deadlock Avoidance

IN deadlock avoidance, a decision is made dynamically whether the current resource allocation will, if granted, potentially lead to a deadlock.

two approaches:
- Resource allocation denial (Don't grant resource if leads to deadlock)
- Process initiation denial (Don't allow a process to initiate if it might lead to deadlock)

# Chapter 9. Uniprocessor scheduling

in a multiprogramming system, multiple processes exist concurrently in main memory. Each process alternates between using a processor, and waiting for an event to occur, such as the completion of I/O Operation. The processor or processors are kept busy by executing one process while the others wait.

## 9.1 Types of processor scheduling

The aim of scheduling is to assign processes to be executed by the processor, in a way that meets system objectives. 
Scheduling activity is broken down into three separate functions: long, medium, and short term scheduling. 

![[Pasted image 20241104181033.png]]
![[Pasted image 20241104181114.png]]


- Long term (Least frequent) scheduling is performed when a new process is created
- Medium term (more frequent) scheduling is a part of the swapping function, whether to add a process to those that are at least partially in main memory.
- Short term scheduling (also known as the dispatcher and the most frequent) is the actual decision of which ready process to execute next, it's invoked when an event occurs may lead to the blocking of the current process:
	- Clock interrupts
	- I/O Interrupts
	- Operating System calls
	- Signals

## 9.2 Scheduling Algorithms

### Short term scheduling criteria

> The main objective of the dispatcher is to allocate processor time in such a way to optimize one or more aspects of system behavior

The commonly used criteria can be categorized along two dimensions:
- User oriented criteria
	The behavior of the system as perceived by the individual user or process. Example is response time in an interactive system. WE would like a scheduling policy that provides "good" service to various users.
- System oriented criteria
	Focus on effective and efficient utilization of the processor. An example is throughput, which is the rate at which processes are completed. However it focuses on system performance rather than the service provided to the user.

Other dimension which criteria can be classified:
- Performance related
	Quantitative and generally able to be measured. Examples like response time and throughput
- Not performance related
	Qualitative in nature and do not themselves readily to measurement and analysis. Example like predictability (how much the service provided exhibit the same characteristics overtime)

![[Pasted image 20241104193508.png]]


### Decision mode

Specifies the instants in time at which the selection function is exercised

Two categories:
- Non-preemptive
	Once a process is running, it will continue until it terminates or blocks
- Preemptive
	Currently running process may be interrupted and moved to ready state by the OS


### First Come First Serve

- Non-preemptive
- Simplest scheduling policy

Self explanatory, first process to come will get executed, the rest will use a queue system.

![[Pasted image 20241104195636.png]]


### Shortest process next(SPN) /Shortest job first (SJF)

- Non preemptive
- A short process will jump ahead in the queue
- Possible starvation for longer processes

![[Pasted image 20241104195720.png]]

### Shortest remaining time (SRT)

- Preemptive
- Like SPN
- Scheduler always chooses the process that has the shortest expected remaining process time
- Risk of starvation for longer processes

![[Pasted image 20241104195825.png]]


### Round robin

- Pre-emption based on a clock
- Uses time slice, or time quantum

![[Pasted image 20241104200303.png]]

Tutorial:
[https://youtu.be/aWlQYllBZDs?si=SZjOeRKay-gdqNaj]


### Highest response rations next (HRRN)

- Non-preemptive
- Attractive because it accounts for the age of the process

$$
Ratio =  \frac{T+E}{E}
$$

$T \to$ Time spent waiting
$E\to$ Expected service time

### Multilevel queue

Processes may be in the condition such that it can be divided into different classes with different scheduling needs
Process are divided into queues with different priority levels and assign to several queue with different priority levels
Pre-emption is allowed
With feedback mechanism, processes that have been waiting for a long time in low priority level, it's priority level may be increased


### Performance comparison

Any scheduling discipline that chooses the next item to be served independent of service time obeys the relationship:

$$
\frac{T_{T}}{T_{S}} = \frac{1}{1 - p}
$$

$T_{T}$ = Turnaround time or residence time; total time in system (Waiting plus execution)

$T_{S}$ = Average service time; Average time spent in running state
$P$ = processor utilization


### Fair share scheduling

Scheduling decisions that allocate System resources fairly among users or groups. This is only used for systems with multiple users.

- User centric allocation
	Focuses on allocating resources based on users or groups of users
- Resource entitlement
	Users or groups are given a prdetermined share of resources. And the scheduler ensures that the actual usage by each user or group reflects their allocated share over time

