# Threads

> One unit of execution within the processor

- Resource ownership
	Process includes a virtual address space to hold the process image
- Scheduling/Execution
	Follows an execution path that may be interleaved with other processes

- The unit of dispatching is referred to as a thread or lightweight process
- The unit of resource ownership is referred to as a process or task
- Multithreading -> The ability of an OS to support multiple concurrent executions of a process/thread

# One or more threads in a process

Each thread has:
- An execution state
- A saved thread context when not running
- An execution stack
- Some per-thread static storage for local variables
- Access to the memory and resources of it's processes shared with all other threads in that process

# Key benefits of threads

- Takes less time to create a new thread than creating a new process
- Less time to terminate a thread than a process
- Switching between two threads takes less time than switching between processes
- Threads enhance efficiency in communication between programs


# Process switching vs Thread switching

**Process switching**
Process switching is a type of [context switching](https://www.geeksforgeeks.org/context-switch-in-operating-system/) where we switch one process with another process. It involves switching of all the process resources with those needed by a new process. This means switching the memory address space. This includes memory addresses, page tables, and kernel resources, caches in the processor.

**Thread switching**
Thread switching is a type of context switching from one thread to another thread in the same process. Thread switching is very efficient and much cheaper because it involves switching out only identities and resources such as the program counter, registers and stack pointers. The cost of thread-to-thread switching is about the same as the cost of entering and exiting the kernel.


# Thread use in a single-user system

- Foreground and background work
- Asynchronous processing -> Processing in parallel, a process that has asynchronous process will wait until it finishes processing and other processes can go first while waiting


# Thread executing state

- States for a thread:
	- Running
	- Ready
	- Blocked
- Operations:
	- Spawn
	- Block
	- Unblock
	- Finish

# Thread synchronization

- Threads in a single process share the same address (identity) and resources.
- That's why it's important to do a thread synchronization, so that multiple threads don't interfere with each other while accessing shared resources.
- Here are some key synchronization techniques:

1. **Mutex (Mutual Exclusion)**: Ensures only one thread can access a resource at a time. When a thread locks the mutex, no other thread can access the resource until the mutex is unlocked.
    
2. **Semaphores**: A synchronization tool that controls access to a resource by allowing multiple threads to access it, but only up to a specified limit.
    
3. **Locks**: These are mechanisms to control the access of multiple threads to shared resources. Some locks allow multiple readers but only one writer at a time (e.g., reader-writer locks).
    
4. **Monitors**: High-level synchronization constructs that manage access to an object by associating a lock and condition variables with the object.
    
5. **Barriers**: Used to synchronize a group of threads at a specific point. All threads must reach the barrier before any can proceed further.


# Types of Threads

### 1. **User-Level Threads (ULT)**

- **Managed by user-level libraries**: These threads are created and managed by user-space libraries and not by the operating system (OS) directly.
- **Faster context switching**: Switching between user-level threads is faster because it does not require kernel mode privileges.
- **No kernel support needed**: Since the OS is unaware of these threads, it doesn't manage them, which also means system calls can block all threads in a process.
- **Examples**: POSIX threads (Pthreads) in some configurations, Java threads (in a managed runtime).

### 2. **Kernel-Level Threads (KLT)**

- **Managed by the operating system**: These threads are created and controlled by the OS. Each thread has its own entry in the kernel's scheduling table.
- **More control over scheduling**: The OS handles thread scheduling and execution, and it can manage multiple threads across different processors.
- **More overhead**: Context switching between kernel threads is slower compared to user-level threads because it requires system calls.
- **Examples**: Windows threads, Linux native threads (via the `clone` system call), Solaris threads.


# Relationship between threads and processes

