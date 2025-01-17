# Virtual Machines

> Virtual machines are hypervisors (Basically software) that emulates the functionality of a separate physical computer inside of your computer. Which essentially allows a computer to live inside of your computer


A virtual machine works by "Virtualization" of resources. so what is virtualization?

## Concept of Virtualization

Virtualization is a process of creating a virtual version of computing resources, including processors, memory, storage devices, and basically any resource you need for a basic computer to run. 
So a virtual machine uses this concept of virtualization to create a software-defined environment that emulates a physical computer with all it's resources, allowing it to run Operating Systems as if it is it's own standalone computer.
There are multiple benefits to running an Operating System (or even multiple) on virtual machines, which we will get into further on in the analysis.


## Hypervisors

A hypervisor (Sometimes called as Virtual Machine Monitor or VMM) is the actual piece of software that enables the virtualization explained above, it's the layer between the host's physical hardware, and the VM's virtualized hardware. The hypervisor has several key responsibilities:
- Resource allocation
	As we discussed before, Virtual Machines emulate a virtual computer by "borrowing" it's host's own resources to the VM to be virtualized, so hypervisors manage the allocations of CPU time, memory, and storage among various VMs (if multiple VMs are used at the same time)
- Hardware Emulation
	After allocating the resources needed by the VM (usually the amount of resources allocated is determined by the user or automatically by the hypervisor), the hypervisor then presents the VM or "emulates" it with the virtualized  hardware components
- Isolation
	One of the key characteristics of Virtual Machines is that they are completely isolated from other VMs and even isolated from the host Operating System, which is why VMs have been used as a "sandbox" for testing software, hacking, etc, because whatever happens to one VM doesn't affect other VMs or the host OS. The hypervisor is responsible in isolating these VMs.
- Security & Control
	Because VM is an actual computer running, despite being virtualized, security protocols are needed to ensure the safety and integrity of the system, as well as the host OS's safety. Hypervisor provides the security policies needed, as well as management interfaces and controls for administrators.


Hypervisors are divided into two main categories:

1. Type 1 (Bare metal hypervisors)
	Hypervisors under Type 1 mean they run directly on top of the host's hardware without any OS underneath. Hypervisor under this category has more control over the resources it allocates, because it has full access to the whole hardware components. Examples of hypervisor of this cateogry are: VMware ESXi, Microsoft Hyper-V, Citrix Hypervisor. These types of hypervisors are very efficient, and are commonly used in data centers or big servers.
	![[type1hypervisor.excalidraw]]

2. Type 2 (Hosted Hypervisor)
	VMs under this category runs on top of a conventional Operating System that runs on the actual PC. This means the Hypervisor needs to "borrow" the resources from the hosting OS first before being able to virtualize them. Examples: VMware workstation, VMware Fusion, Virtualbox. These types of hypervisors are convenient for desktop use or general users use.
	![[type2hypervisor.excalidraw]]


## Virtualization Techniques

Other than using the compatible hypervisor, we also need to ensure that the hardware itself supports virtualization. Most modern CPUs already support virtualization by including virtualization extensions like Intel VT-x for intel chips or AMD-V for amd chips. These extensions assist hypervisors in virtualizing resources by handling certain virtualization tasks directly at the hardware level.
Processors without these extensions can still run virtualization, however they need to rely on the slower software-based technique of virtualization like binary translation, as they cannot execute tasks directly in the hardware level.

## Benefits

As mentioned before, within a VM, the virtualized operating system doesn't know that they are running on a "virtualized environment". From their perspective, they're running regularly on the available hardware and resources to them, like a regular computer. this is useful because then using VM provides:

- Portability
	VMs can be duplicated, moved, or copied between host machines, and run exactly the same between the hosts
- Scalability
	Multiple VMs can share a single powerful physical server, allowing them to be able to run a lot of applications, or instructions or tasks at once.
- Flexibility
	VMs are extremely easy to use, and we have a lot of control over the virtualized OS environment, like we can easily create, start, pause, or rollback entire OS environment states.



# VirtualBox by Oracle

>VirtualBox is a Virtual Machine by oracle, it is a type 2 hosted hypervisor. 