#operatingsystem 

# Process Control

- Program in execution
- Instance of a program which is running
- Entity that can be assigned to and executed on a processor
## State

**In operating systems, a state refers to the current condition or status of a process.** It defines the process's activity, resource usage, and position in the system's execution queue.

# Process Creation

## Process Spawning

### Spawning a New Process

The act of creating a new process is often referred to as **spawning**. This involves several steps:

1. **Resource Allocation:** The operating system allocates necessary resources for the new process, such as memory, CPU time, and file descriptors.
2. **Program Loading:** The executable code of the new process is loaded into memory.
3. **Process Creation Table Entry:** A new entry is created in the process control block (PCB) table to represent the child process.
4. **Initialization:** The child process's initial state is set, including its program counter, stack pointer, and other registers.

### Examples of Process Creation

- **Forking:** A common method used in UNIX-like systems. The parent process creates a child process that is an exact copy of itself.
- **Exec:** Replaces the current process with a new process, loading a different executable.
- **Creating a new thread:** In some operating systems, creating a new thread is similar to creating a new process, but they share the same address space and other resources.

## Parent Process

### Parent-Child Relationship

- **Parent-Child Link:** The parent process and the child process are linked together.
- **Process ID (PID):** Each process is assigned a unique PID. The child process inherits its PID from the parent.
- **Resource Sharing:** The parent and child processes can share resources like files, memory, and signals.
- **Termination:** The parent process can terminate its child processes, and the child process can also terminate itself.
- **Wait/Join:**

The parent process can wait for its child processes to terminate using the `wait` or `join` system calls.

# Process elements,

While a program is executing, this process can be uniquely characterized by a number of elements:
- Identifier
- State
- Priority
- Program counter
- Memory pointers
- Context data
- I/O Status information
- Accounting information


# Two state process model

## State transition diagram

![[{DA92A616-6C37-481F-B34F-C35E2008CE53}.png]]

## Queueing Diagram

![[{BE91B780-E676-40A7-B98B-D8CEE653CA45}.png]]

# Five State Diagram

![[{1D883B90-17FB-4CE9-B3EC-B5051A91B1BB}.png]]



# Suspended Process

**Swapping**
- Swapping involves moving part of a process from main memory to disk
- When none of the processes in main memory is in the ready state, the OS Swaps one of the blocked processes out on to the disk on a suspended queue
	- This queue exists for programs that has been kicked out of main memory (suspended)
	- the OS then brings in another process from the suspend queue or it honors a new process request
	- Execution then continues


## Characteristics of a suspended process

- The process is not immediately ready to be executed
- The process may or may not be waiting for another event
- The process was placed in a suspended state by an agent
- The process may not be removed from this state until the agent explicitly states for it's removal



# Process Termination

- There must be a means for a process to indicate it's completion
- A batch job should include a HALT instruction, or an explicit OS Service call for termination
- For an interactive application, the action of the user will indicate when a process is to be terminated (Quitting an application)

## Reasons for Process termination

- **Normal completion**: The process executes a service call to indicate it has completed successfully.
- **Time limit exceeded**: The process runs longer than the specified total time limit.
- **Memory use violation**: The process requires more memory than the system can provide.
- **Protection error**: The process attempts to use a resource it is not allowed to use.
- **Arithmetic error**: The process tries a prohibited computation, such as division by zero.
- **Time overrun**: The process waits longer than a specified maximum time for an event.
- **I/O failure**: An error occurs during input or output operations.
- **Out of storage**: The process requires more storage than is available.
- **Invalid instruction**: The process attempts to execute a non-existent instruction.
- **Data misaligned**: A piece of data is of the wrong type or is not initialized.
- **Privilege violation**: The process attempts to use an instruction reserved for the operating system.
- **Parent request**: A parent process requests the termination of its offspring.



# Process control structure

Basically similar to a struct that contains a process's descriptions like:
- Process location
- Process attributes




# Unix SVR4

- Uses a model where most of the OS Executes within the environment of a user process

Unix Process states

![[{E396DAAA-1B3D-437B-B467-FF3259A0E1EB} 1.png]]


