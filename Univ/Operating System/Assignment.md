
1. Explain in detail what happens when a process gets interrupted. You should explain the relationship between interrupts and the process counter.
	
	Interrupting a program means that the CPU stops processing the current process, and turns to handle a higher priority process. 
	Interrupting a program can occur because of system calls requesting for higher priority processes to be processed first, or it can be due to the current process failing, creating exceptions or hardware signals
	
	Breakdown of interrupt:
	- Start of interrupt
		An interrupt is initiated by a signal that notifies the CPU to immediately stop the current process temporarily. This signal can come from several sources like I/O or a request from another software
	- Save current process
		Before interrupting the current process, the CPU needs to save the state so that the process can be continued later on. The CPU uses what's called a Process Counter, the Process Counter saves the address of the next instruction for the current process. the CPU then holds the value of this PC in a designated area called the Process Control Block (PCB)
	- Switch to Interrupt Service Routine
		the CPU switches execution context to an Interrupt Service Routine which is designed to handle specific types of interruptions. The CPU then does the interrupt handling code and performs necessary tasks like managing data, or responding to events that requested the interrupt.
	- Resume Interrupted Process
		After handling the interruption code, the CPU then resumes the initial execution it was doing when it was interrupted. The CPU then does the initial process's normal sequence 


2. What is a Process Control Block?

	Process Control Block (PCB) is a data structure that exists to store important information of a specific process. it kind of acts like a process's identity card, containing details needed by the CPU to identify and manage the process through it's life cycle. For example, the CPU uses the PCB when it's requested an interruption, to save the process's instructions to be able to resume the process after the interruption.


3. In threading, in which case and why should we use pthread_join()?

	pthread_join is a function that's used when we want a thread to wait for the completion in another thread. It can be used to synchronize threads, or if we want a thread has finished executing before allowing a program to proceed.
	
	There are several reasons why we want to use pthread_join:
	- When we want to synchronize threads
		If we want to ensure that a thread completes it's task before proceeding with the program, we can use pthread_join() 
	- To prevent premature exit of main thread
		In a single process environment, if the main thread finished prematurely, it can cause the entire process to terminate, including unfinished threads. In order to prevent this, we can use pthread_join() so that the main thread has to wait for other threads to finish first.
	- remove zombie states
		Sometimes, a thread can get into a "zombie state", which is a thread that has finished executing, but the resources aren't reclaimed by the system. to solve this, the parent thread (or also other threads) can call pthread_join() to ensure resources are properly released after a thread finishes it's life cycle


4. Scheduling algorithms
	a. Shortest Job First
	![[WhatsApp Image 2024-10-17 at 10.27.29_b20e8fd0.jpg]]
	
	b. shortest job remaining time next
	![[WhatsApp Image 2024-10-17 at 10.40.45_843677eb.jpg]]
	
	c. Round Robin
	![[WhatsApp Image 2024-10-17 at 11.04.06_bac63962.jpg]]
	
	
	d. Highest Response Ratio Next
	![[WhatsApp Image 2024-10-17 at 11.12.58_79e73984.jpg]]

5. What are the issues involving process scheduling in a multiprocessor environment?
	
	- Load balancing
		load balancing ensures all processors have an equal amount of work, but in a multiprocessor environment, it can be difficult to achieve dynamic load balancing, because it requires real time monitoring and transfer between the multiple processors
	- Processor affinity
		Processor affinity means binding processes to specific processors, in a multiprocessor environment, incorrect processor affinity can lead to load imbalancing if some processors become underutilized while others are overloaded
	- Process migration
		Process migration involves moving processes from one processor to another to balance load, but this can become time consuming because memory and contents must be transferred, and also may affect performance.

6. what is the difference between embedded system and deeply embedded system
	Embedded systems is a term for computing devices that are dedicated to performing specific tasks within a larger system, usually includes a processor, memory and I/O interfaces. They can also run general purpose operating system like Linus.
	
	Meanwhile, a deeply embedded system is a subset of embedded systems that is more specialized and constrained in terms of resource and accessibility. These deeply embedded systems have less processing power, memory and storage, and they usually can't run a complex operating systems
	
	Examples:
	- Embedded systems:
		- Smart thermostat
		  Runs an operating system (Typically android), I/O interfacaes, etc
		- Digital camera
		  Includes a processor to handle image capture, processing, and storage
		- Smart TV
		  Contains processor to run apps, stream contents, and manage user interface 
	- Deeply embedded systems:
		- Pacemaker
		  Contains a microcontroller to regulate heartbeats with very tight resources
		- Industrial sensors
		  contains microcontroller to read data and send signals
		- Smoke signal
		  Contains a microcontroller that detects smoke particles and trigger an alarm


## Code

![[Pasted image 20241017115921.png]]

## Output

![[Pasted image 20241017115940.png]]