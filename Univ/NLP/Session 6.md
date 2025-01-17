
# Concurrency: Mutual Exclusion and Synchronization

## Concurrency control

> Why do we need concurrency control? Because we have multiple processes


**Multiple Process**
- OS design is concerned with the management of processes and threads
	- Multiprogramming -> Multiple processes within uniprocessor system
	- Multiprocessing -> Multiple processes within multiprocessor
	- Distributed processing -> Management of multiple processes executing on multiple computer systems

**Terms in synchronization**
- Atomic operation -> 
- Critical section
	Section of code that requires access to shared resources and must not be executed while another process is in a corresponding section of code
- deadlock
	two or more processes cannot proceed because they are waiting for each other
- livelock
	two or more processes continuously changing their states in response to changes in other processes without doing anything useful
- mutual exclusion
- race condition
- starvation

# Difficulties of Concurrency

- Sharing global resources
- Difficult for OS to manage all allocations optimally
- Difficult to locate programming errors


# Common Concurrency Mechanism

- Semaphone
	Something to give signal (Basically just an integer). Only three oprations may be performed on a semaphone, all of which are atomic.
- **Binary Semaphore**
	Only takes the value 0 and 1
- Mutex
	Similar to semaphone, but the process locks the mutex
- Condition variable
	A data type used to block a process or thread until a particular condition is true




## Semaphore

Three operations:
- Initialization
	initialized to a nonnegative integer value
- Wait
- Signal

A queue is used to hold processes