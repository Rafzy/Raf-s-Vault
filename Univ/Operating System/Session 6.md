# Concurrency & Deadlocks

>When multiple processes end up waiting for each other, either for resource, or wait for another to end, and no process continues


Deadlock involves certain resource category:
- Reusable resource -> Resource that we can use again and again (Memory, devices, files, etc)
- Consumable resource -> Resource that after we use will be destroyed (Interrupts, signals, messages)

**Deadlock approaches**
> There is no single effective strategy that can deal with all types of deadlocks

Three approaches are common:
- Deadlock prevention
	Disallow one of the three necessary conditions for deadlock occurrence. 
- Deadlock avoidance
	Do not grant resource request when a deadlock might occur
- Deadlock detection
	Grant resource, but periodically check for deadlocks'


![[deadlock-example.excalidraw]]

One way we can detect deadlocks is by using these graphs


## Conditions for a deadlock to happen

- **Mutual Exclusion**
	When a resource can only be used by one process at a time
	No process may access a resource until it has been allocated to another process
- Hold and wait
	A process may hold allocated resources while waiting for assignment for other resources
- No pre-emption
	No resource can be forcibly removed from a process holding it
- Circular wait
	A closed chain of processes exists, such that each process holds at least one resource needed by the next process in the chain


Two types of approaches
- Indirect
	- Prevent the occurrence of one of the three necessary conditions
- Direct
	- Deal with circular wait

Solve for each problem:
- Mutual exclusion
	- If access to a resource requires mutual exclusion, then mutual exclusion must be supported by the OS
	- Some resources, such as files, may allowmultiple files accesses for reads but exclusive accesss for writes
- Hold and wait
	- Can be prevented by requiring that a process request all of it's resources at one time and blocking all the process until all requests can be granted simultaneously
- No preemption
	- If a process holding a certain resources is denied a further request, that process must release it's original resources and request them again
- Circular wait


## Deadlock avoidance

>The machine will try to "predict" if a deadlock will happen if a certain request is approved

Approaches:
- Resource allocation denial (Don't grant resource if leads to deadlock)
- Process initiation denial (Don't allow a process to initiate if it might lead to deadlock)



### Resource allocation denial

>Also referred to as the *banker's algorithm*

- State -> Reflects the current allocation of resources to processes
- Safe state -> There is at least one sequence of resource allocations to processes that does not result in deadlock
- Unsafe state -> State that is not safe

Deadlock avoidance Advantages:
- Not necessary to pre-empt

Restrictions
- Each process must declare maximum resource requirement
- Processes under consideration must be independent
- There must be a fixed number of resources to allocate
- No process may exit while holding resources


## Recovery strategies

- Abort all deadlocked processes
- Back up each deadlocked process to some checkpoint


# UTS
- Simulation
	- Can be scheduling
	- Can be deadlock, etc
- Essay
	- Theory
- Case
	- Program