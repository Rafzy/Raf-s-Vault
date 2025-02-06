>GG We comeback UAS OS

![[absolute-cinema-cinema.png]]

# File Management 

> Windows File Explorer sucks

Most apps need file (They either take files as inputs or outputs file for long term storage) so it is necessary to be able to keep the integrity of files. All Operating System will need to provide file management systems, and the FMS will provide means for users and applications to keep, store, and manipulate files.


## Overview

### **Files & File system**
File system permits users to create files with these properties:
- Long term existence
	Files should exist even when the computer is shut down
- Shareable between processes
	Files can have associated access permissions
- Structure
	Files can have different structures that support specific application's needs

File systems should include these operations that can be performed on files:
- Create
	Define a file, put it within the structure of other files
- Delete
	A file is removed from the structure and destroyed
- Open
	An existing files is declared "opened" by a process, and can perform functions on the file
- Close
	The file is closed with respect to a process, usually needs to be closed after opening the file
- Read
	A process reads all or a portion of the data in a file
- Write
	A process updates a file by modifying it (Either add new data or change existing ones)


### **File Structure**
There are four terms when discussing file structures:
1. **Field**
	Basic element of a data. One field contains one value, and it's characterized by length and data type (ASCII STRIUNG, decimal, etc). Fields may be of fixed or variable length. For the case of variable length, the field consists of two or three subfields (The value, the name, and the length)
2. **Record**
	Group of related fields that can be treated as a unit by some program (An employee would have fields like first name, last name, age, social security number, date of hire, etc). Records may be of fixed or variable length either when the fields are of variable length, or when the number of fields vary.
3. **File**
	Collection of similar records, however one file is treated as a single entity by users or applications. Access control restrictions usually apply at the file level. A shared system are usually granted or denied access to entire fields
4. **Database**
	Collection of related data, and there is a clear relationship between elements of data (Customer table might have customerID, name, etc), and databases are meant to be multipurpose (It is a shared resource). The database itself consists of one or more type of files.

Typical operations that is used to make use of files:
- Retrieve_All
	Retrieve all records of a file, typically equated with the term *sequential processing*, because all the records are processed in sequence
- Retrieve_One
	Retrieve a single record
- Retrieve_Next
	Retrieves the "next" record in some logical sequence to the most recently retrieved record
- Retrieve_Previous
	The opposite of Retrieve_Next
- Insert_One
	Inserts a new record into the file. It may be necessary to insert the record in a particular position to preserve the sequencing of the file
- Delete_One
	Delete an existing record, certain data structures may need to be updated to preserve the integrity of the file
- Update_One
	Retrieves one record, update it's field, rewrite the updated record back to the file.
- Retrieve_Few
	Retrieve a number of records (Not all)

==Not all file systems exhibit the sort of structure discussed above==:
- UNIX-like systems have stream of bytes as the basic file structure
- C program is stored as a file, but doesn't have physical fields, records, etc


### **File Management Systems**
Set of system software that provides services in use of files, and typically the only method users and applications can access files, and provides a consistent way for users and programs to controlling files. 
Objectives of a File Management System:
- meet the management needs of the user
- Guarantee, to the extent possible, that the data in the file are valid
- Optimize performance, both from the POV of the system and the user
- To provide I/O Support for different device types
- Minimize or eliminate the potential lost or destroyed data
- Provide a standardized set of I/O interface routines to user processes
- Provide I/O support for multiple users

These are the minimal set of requirements a FMS should meet in respect to the first point above:
1. Users must be able to create, delete, read, write, and modify files
2. Each user may have controlled access to other user's files
3. Each user may control what type of accesses are allowed to their file
4. Each user should be able to move data between files
5. Each user should be able to back up and recover files
6. Each user must be able to access files by name rather than numeric identifier

#### **File System Architecture**

![[Pasted image 20250110172921.png]]


- Device Drivers
	Sits at the lowest level, it communicates directly with peripheral devices or their controllers. It's responsible for starting I/O operations and processing the completion of an I/O request. (For file operation, the typical device controller are disk and tape drives) Basically: deals with physical devices
- Basic File system | Physical I/O
	This part maps logical blocks onto physical blocks on actual storage devices (Deals with placements of data blocks on secondary storage device and on the buffering in main memory). Basically: Deals with blocks of data
- Basic I/O supervisor
	Supervises and controls the I/O requests going to the hardware. Responsible for file I/O initiation and termination. Control structures are maintained that deal with device I/O, scheduling, and file status. I/O buffers are assigned and secondary memory is allocated at this level. Basically: deals with I/O requests
- Logical I/O
	Enables users and applications to access records, it allows the file organizations to see files in terms of high-level records, instead of raw bytes on disks. It abstracts away details like byte positions or sectors. Basically: deals with file records, provides a way to abstract records for users and applications
- Access Methods
	Provides a standard interface between applications and the file systems. Different access methods reflect different file structures, ways of accessing and processing data.
	Most common access methods are:
	- Pile
	- Sequential
	- Indexed Sequential
	- Indexed
	- Hashed


#### **File management functions**
![[Pasted image 20250110190440.png]]

- Before User or applications can do any operations on a file using commands, the file system must identify and locate the selected file
- This uses some sort of directory that describe the location of all files and their attributes, and typically this also needs user access control
- The operations users or applications may perform on a file are performed at the record level.
- The user views the file as having some structure that organizes the records (A file), so to translate a certain user's command in the record level, the access method appropriate to the file structure must be employed
- Users and apps are concerned with records/fields, while I/O is done on a block basis, so the records of a file must be organized into a sequence of blocks for output, and unblocked for input.
- The secondary storage must be managed, by allocating files to free blocks on secondary storage, and managing free storage so as to know what blocks are available for new files and growth for existing files
- Individual I/O Block requests must be scheduled.
- Disk scheduling and file allocation concerns optimization, so both must be considered together
- Optimization depends on structure of files and access patterns


## File Organization and Access

File organization refers to the logical structuring of records, determined by how they are accessed. The physical organization of the file depends on the blocking strategy and file allocation strategy.

Several criteria are important when choosing a file organization:
- Short access time
- Ease of update
- Economy of storage
- Simple maintenance
- Reliability

Fundamental file organizations:
1. The pile
2. The sequential file
3. The indexed sequential file
4. The indexed file
5. The direct, or hashed file

### **The Pile**
![[Pasted image 20250110195738.png]]

- Data are collected in the order of which they arrive
- Each record consists of one burst of data
- Records may have different fields or similar fields in diff order. Thus, each field should be self-describing (Field name as well as value)
- Length of each field must be indicated by delimiters
- Record access is by exhaustive search (Examine each record until the desired record is found/not found)

### **The Sequential File**
==Most common form of file structure==
![[Pasted image 20250110200740.png]]

- Records are fixed lengths
- Records contains the same number of fixed-length fields in a particular order
- Only the values of fields need to be stored, the field name and length are attributes of the file structure
- The first field in each record is referred to as **field key** that uniquely identifies that record.
- Records are stored in key sequence (Alphabetical for text key, and numerical for numerical key)
- Typically used in batch applications, and particularly optimum if they involve the processing of all the records.
- Bad for apps that involve queries or updates for individual records
- Adding files also poses problems, typically new files need to be stored in log files then merged periodically, or a linked list is used to organize the sequential file physically


### The Indexed Sequential File
==one approach to overcoming sequential file's shortcomings==

![[Pasted image 20250110205514.png]]

- Same like sequential file: Records are organized in sequence based on a key field with two added features
- an index to the file to support random access, and an overflow file
- Index provides a  lookup capability to quickly reach the vicinity of a desired record
- The overflow is similar to the log file used with a sequential file, but the pointer to the record in the overflow file is located by a pointer from it's predecessor record
- In the simplest form, a single level of indexing is used, the index file is a simple sequential file, and each record consists of two fields: a key field and a pointer into the main file.
- To find a specific field, the index file is looked up to find the highest key value that is equal to or precedes the desired key value, then the search continues in the main file at the location indicated by the pointer
- Additional to this, each record in the main file contains an additional field not visible to the application which points to the overflow file
- When a new file is inserted it's added to the overflow file, and the record in the main file that precedes that inserted file in logical sequence is updated to contain a pointer that points to that new record.
- The main file is occasionally merged with the overflow file in batch mode
- Accessing this file organization includes processing the entire file sequentially until it finds a pointer to the overflow file, which then processing continues in the overflow file until it finds a null pointer, which will resume the processing in the main file
- Multiple levels of indexing can be used, because the lower level index is treated as a sequential file, the higher level index is essentially an index file for the lower level index


### The Indexed File

![[Pasted image 20250110212636.png]]

- When we want to search for a record based on attributes other than the key field, sequential and indexed sequential file is inadequate
- Thus, indexed file employs multiple indexes, one for each type of field that may be the subject of search.
- The records in the main file can have variable length as well as positions, as long as each record has a pointer leading to it in the index file`
- Exhaustive file is used for every record in the primary file, while partial file is used for field of interest

### Direct or Hashed File

- This file management system hashes the keys of records
- No sequential ordering
- Exploits the capability of disks to directly access a block of a known address


## B-Trees

> This structure is used to organize index files found in indexed sequential file as well as indexed files

Characteristics of a B-Tree:
- The tree consists of a number of nodes and leaves
- Each node contains at least one key which uniquely identifies a file record, and more than one pointer to child nodes and leaves
- Each node is limited to the same number of keys
- The keys of a node is sorted in a non-decreasing order, which each key has a corresponding pointer that points to a subtree which nodes keys are less than the current key, but greater than the preceding key. Also has a pointer on the rightmost that points to a subtree with key values greater than this tree's keys.

A tree is determined by *d degrees*:
- Every node has a maximum of *2d-1* keys and *2d* children/pointers
- Every node except for the root has at least *d-1* keys as well as *d* children
- The root has at least 1 key and 2 children
- All leaves appear on the same level and contains no information, or has null pointers. This is a way to terminate the tree when the interested key is not found
- A non-leaf node with *k* pointers contains *k-1* keys



## File Directories

>Directories are a method to contain files on the higher level, from the user's point of view, directory provides a mapping between file names and the files themselves.

Directories contain information about the files it contains:

![[Pasted image 20250112104637.png]]


Structure of a directory based on a tree shape

![[Pasted image 20250112104814.png]]


## File Sharing

In a multiuser system, the OS must have a way to allow files to be shared among users, with many concerns following this requirement, like rights and the management of simultaneous access

### Access Rights

The owner of a file usually have the highest privilege when it comes to managing that file. But the owner can also give access rights to other users with differing levels of access rights:

- None: The user can't even learn about the existence of the file
- Knowledge: The user can know that the file exists and can petition for the owner to add additional rights
- Execution: Can run the program, cannot copy the file (Proprietary programs, games, etc)
- Reading: The user can read the file for any purpose (Executing and copying)
- Appending: The user can add data to the end of the file, but cannot modify the original file
- Updating: The user can update, delete, and add to the file's data
- Changing the protection: User can change the access rights granted to other users. Typically only given to the owner
- Deletion: The user can delete the file from the system

The owner can give these access rights to different classes of users:
- Specific Users: Individual users
- User groups: A set of users who are not individually defined
- All: All users that have access to this system



## Record Blocking

In a previous note, we have established that the File Management System works with records of a file, while I/O works with blocks as units with secondary storage, thus for I/O to be performed, records must be organized as blocks.

There are three methods of blocking that can be used:
1. Fixed Blocking: Fixed length records are used, and whole numbered records are stored in a block
2. Variable-length spanned blocking: Variable length records are used, some records must span two blocks, with continuation indicated by a pointer to the successor block
3. Variable-length unspanned blocking: Variable length records are used, but spanning is not employed, thus potential wasted space in blocks


![[Pasted image 20250112110512.png]]


## Secondary Storage Management

On secondary storage, a file consists of a collection of blocks. The OS or FMS is responsible for allocating blocks to files. 
These raise two management issues: Space on secondary storage must be allocated to files, and it's necessary to keep track of empty space.

### File Allocation

> A space allocated to file will be referred to as **portions**
> A **File Allocation Table (FAT)** is employed to keep track of the portions assigned to a file

#### Pre-allocation vs Dynamic Allocation

- **Preallocation**
	Pre-allocation policy requires the maximum size of a file to be declared at the time of the file creation request.
	For cases like transfer of a file from another system, or production of summary data files, this is possible, but for most cases, files having to estimate their maximum file size is almost impossible
- Dynamic Allocation
	Allocates space to a file in portion as needed, files don't have to declare their maximum file size

#### Portion Size

The second issue is how much size of the portion must be allocated to a file. Do we allocate the maximum portion to hold the entire file, or we allocate one block at a time in the disk.

Four considerations can be made:
- Contiguity of space increases performance, especially for sequential processing
- Having a large number of small portions increase the tables needed to manage the allocation information
- Having fixed size portions simplifies the reallocation of space
- Having variable size or small fixed size portion minimizes waste of unused storage


Considering these, there are two major alternatives:
- **Variable, large contiguous portions**
- **Blocks**

With variable size-portions, we need to be concerned with fragmentation of free space, So the following are possible strategies:
- First fit: Choose the first unused contiguous group of blocks of sufficient size
- Best fit: Choose the smallest unused group that is of sufficient size
- Nearest fit: Choose the unused group of sufficient size that is closest to the previous allocation (Good to increase locality)

#### File Allocation Methods

After bringing up the points above, we can approach different file allocation methods

![[Pasted image 20250112113529.png]]

- **Contiguous Allocation**
	A single contiguous set of blocks is allocated to a file at the time of file creation (Pre-allocation strategy).
	The file allocation table needs just a single entry for each file, the starting block as well as the length.
	However, with this method, external fragmentation will occur, which means it's necessary to perform a compaction algorithm from time to time to free up additional space
	![[Pasted image 20250112114055.png]]

- **Chained Allocation**
	Allocation of individual block basis, each block contains a pointer that points to the next block.
	File Allocation Table only needs to contain the starting block as well as the length.
	No external fragmentation to worry about because it allocates per block
	However, there is no accommodation of the principle of locality, making it necessary to bring in several blocks of a file at a time, or a solution is to periodically consolidate files
	![[Pasted image 20250112114551.png]]

- **Indexed Allocation**
	File allocation table contains a separate one-level index for each file, Typically the file indexes are stored as a separate block in the secondary storage. Allocation may be of a fixed size blocks of variable-size portions.
	![[Pasted image 20250112120259.png]]
	
	![[Pasted image 20250112120310.png]]


### Free Space Management

Free space must also be managed either by the File Management System or the Operating System. To do this, a Disk Allocation Table is employed in addition to a file allocation table. These are the different techniques of Free Space Management

#### Bit Tables

Uses bits that represent each block (0 means empty, 1 means the block is in use). A bit table is relatively easy to employ, and it's easy to find one or a contiguous group of free blocks. However, this method can still be sizeable, the amount of memory required for a block bitmap is
![[Pasted image 20250112121203.png]]

==And an exhaustive search== of the table can slow down system performance. However an auxiliary data structures can be employed that summarizes the contents of equal sized subranges, where it describes each subrange's number of free blocks, and the biggest free contiguous blocks

#### Chained Free Portions

Free portions are chained together using pointer and length value in each free portion. This method has negligible space overhead because it doesn't need disk allocation table.

However, using this method can cause the disk to become quite fragmented, and many portions will only be single blocks long. And every time we need to allocate a block, we need to read the block first to recover the pointer to the new first free block

#### Indexing

Using a structure similar to index table to store the entry of each free space. And the index should be on the basis of variable-size portions rather than blocks. This approach provides efficient support for all of the file allocation needs


#### Free Block list

This method, each block is assigned a number sequentially, the list of the numbers of free blocks, and the list of numbers of all free blocks is maintained in the disk
Either 24 or 32 bits will be needed to store a single block number. So it's considerably larger than bit map.


### Volumes

Volumes are basically logical representation of the physical disk. A single disk equals one volume, and a disk can be divided into partitions which each partition acting as a separate volume.


# I/O Management

> The messiest aspect of an OS design is input/output

## I/O Devices

External Devices that exchange in I/O is divided into three categories:
1. Human Readable: Suitable for communicating with the computer user (Printers, terminals)
2. Machine Readable: Suitable for communicating with electronic equipment (USB keys, sensors)
3. Communication: Suitable for communicating with remote devices (Modems)


Ky differences within classes of I/O devices:
1. Data Rate
	There may be differences between data transfer rates
2. Application
	The physical device used in a computer can influence the software and policies in the OS
3. Complexity of control
	A printer has a simple control interface where a disk is more complex. So the complexity of the I/O module that controls the device may differ
4. Unit of transfer
	Data may be transferred as a stream of bytes or characters or in larger blocks
5. Data representation
	Different data encoding schemes may be used by different devices. 
6. Error conditions
	The nature of errors, the way they are reported, how they deal with error may differ widely from one device to another.


## Organization of the I/O function

There are three techniques in performing I/O:

1. Programmed I/O
	The processor will issue an I/O command on behalf of a process to an I/O module. The process then busy waits for the operation to be completed before proceeding
2. Interrupt-driven I/O
	The processor issues an I/O command , then there are two possibilities, if the I/O instruction is non-blocking, the processor continues instructions from the process. If the I/O instruction is blocking, then the next instruction will put in a blocked state
3. Direct Memory Access (DMA)
	Processor delegates the task of exchanging data between an I/O module and main memory to the DMA module. It's interrupted only after the entire block has been transferred

### Evolution of the I/O function

Individual components have been increasing in complexity, especially in I/O functions:
1. The processor directly controls a peripheral device (In processor controlled devices)
2. A controller or I/O module is added, the processor uses programmed I/O without interrupts.
   ![[Pasted image 20250112130203.png]]

3. The same configuration as step 2 is used, but interrupts are employed so the processor doesn't need to wait for an I/O operation to be performed
4. The I/O module is given control of memory using DMA. It can move a block of data to or from memory
5. The I/O module is enhanced to become a separate processor, with a specialized instruction set tailored for I/O
6. The I/O module has a local memory of it's own, and it's a computer in it's own right. Thus a large set of I/O devices can be controlled with little to no processor involvement. 

Note: **I/O channel** refers to the I/O channel and I/O processor


### Direct Memory Access

The DMA is capable of mimicking the processor, and it can take control of the system bus like a processor.
When the processor wishes to read or write a block of data, it issues a command to the DMA module by sending it the following information:
1. Read or write control line between the processor and the DMA module
2. The address of the I/O device involved through the data lines
3. The memory location to read from or to write to, stored by the DMA module in it's address register, communicated through the data line
4. The number of words to be read or written, through the data line, stored in the data count register

After delegating the I/O operation to the DMA, the process can continue with other work. The DMA will then interrupt the processor when the I/O operation is complete, thus the processor is only involved at the start and at the end of the I/O request.

![[Pasted image 20250112133143.png]]

Possible configurations of DMA:

![[Pasted image 20250112140831.png]]

## Operating System Design Issues

### Design Objectives

==Objectives of designing I/O facility: Efficiency and Generality==

**Efficiency** is important because most of the time, I/O devices become a bottleneck since they are significantly slower compared to the processor and main memory.
**Generality** means it's best that all devices is handled in a uniform manner. Both in the way of how the processes view I/O devices, and how the OS manage I/O devices and operations.

### Logical Structure of the I/O Function

in the I/O structure of a local peripheral device that communicates in a simple fashion, these layers are involved:
- Logical I/O
	Deals with the device as a logical resource, not concerned with the details of actually controlling the device. It's concerned with managing general I/O functions on behalf of user processes allowing them to deal with the device in terms of a device identifiers
- Device I/O
	The requested operations and data (Buffered characters, records, etc) are converted into appropriate sequences of I/O instructions, channel commands, and controller orders
- Scheduling and control
	Queueing and scheduling of I/O operations occur at this layer. Thus interrupts are handled at this layer and I/O status is collected and reported.


For a communication device, the I/O structure looks similar to the one above, but the logical I/O module is replaced by a communications architecture which itself consists of a number of layers

The structure for managing I/O on a secondary storage device that supports a file system, theses layers are added:
- Directory management
	Symbolic file names are converted into identifiers that either reference the file directly or indirectly using a file descriptor or index table. This layer is also concerned with user operations that affect the directory of files such as add, delete, and organize
- File system
	This layer deals with the logical structure of files and operations that the user has done like open, close, read, and write access rights are also managed at this layer
- Physical organization
	Logical references to files and records are converted into physical secondary storage addresses, allocation of secondary storage space and main storage buffers is generally treated at this layer as well.


## I/O Buffering

Suppose we are requesting to read a block of data of size 512 bytes using `Read_Block[1000, disk]`, then wait until the data becomes available. The problem is that the program is now hung up waiting for the slow I/O to complete. Also, the Virtual location of our target 1000 to 1511 must be kept in main memory during the block transfer. Thus, the process cannot be paged out entirely, at least the page that contains the address must be locked in physical memory

To avoid potential overheads like deadlocks, also inefficiencies, it's convenient to perform input transfers in advance of requests being made, as well as output transfers after the fact. This is known as buffering.

Buffering allows the OS to read data ahead of time into a buffer or hold data after a write request for a while.

First we have to make a distinction of two types of I/O Devices:
- Block oriented device
	Stores information in blocks that are fixed size, and transfers are made on block at a time (Disks, USB)
- Stream oriented device
	Transfers data as a stream of bytes with no block structure (Printers, terminals, mouse, other pointing devices)


### Single Buffer

> The simplest type of buffer.

When a user process issues an I/O request, the OS assigns a buffer in the system portion of main memory to the operation
For block-oriented devices, the buffering scheme will do as follow:
1. Input transfers are made to the system buffer
2. When it's complete, the process moves the block into user space and immediately requests another block (The block it requests may be reading the next sequential block, or it predicts which block it will need)
3. This way, by the time the process asks for the next block, it's already in the OS's buffer in main memory instead of waiting for the disk
4. This method is called reading ahead or anticipated input


For stream oriented devices, a line-at-a-time or a byte-at-a-time system can be employed. 


### Double Buffer

An improvement over single buffer by assigning two system buffers to operations. Called as double buffer or buffer swapping. Same concept as single buffer for both block and stream oriented devices.


### Circular Buffer

However, for rapid bursts if I/O, single and double buffer might be inadequate, then it's better to employ more than two buffers.
When more than two bufers are used, the collection of buffer is called as circular buffer. 


## Disk Scheduling

#important

Processor and main memory speed have far passed that of disks access time, thus it's important to improve the performance of disk storage subsystem.

### Disk Performance Parameters

General timing diagram of disk I/O transfer

![[Pasted image 20250112165908.png]]

To read or write, the head must be positioned at the desired track and at the beginning of the desired sector of that track.

**Seek time** -> The time it takes for the head to take position of the desired track
**Rotational delay** -> The time it takes for the beginning of the sector to reach the head
**Access time** -> Sum of seek time + Rotational delay
**Transfer time** -> The time required for the transfer

### Disk Scheduling Policies

Different policies may be employed in order to decrease the average time spent on seeks. Typically, we use a **random scheduling** as a benchmark to evaluate other techniques. 

#### First In First Out

Basically process items in sequence of their request. This strategy has the advantage of being fair, since every request is honored in the order received.
Very simple to implement, but this method at times will approximate random scheduling in performance which isn't the best.

#### Priority

Using a system based on priority (PRI). The scheduling is handled outside of the disk management software. This approach is usually not used to optimize disk utilization, but too meet other objectives within the OS.

Typically short batch jobs are given higher priority than longer batch jobs, so that a lot of the short jobs can be flushed through the system quickly, however this can cause starvation for the longer bath jobs.


#### Last In First Out

This policy always takes the most recent request, and it has it's merits.
For example in a transaction-processing system, giving the device to the most recent user should result in little or no arm movement for moving through a sequential file. 

#### Shortest Service Time First

This policy is to select the disk I/O request with the least movement of the disk arm from the current position. Thus we always choose to incur the minimum seek time.
Doing this won't guarantee the minimum average seek time, but it's generally better in terms of performance compared to FIFO.


#### SCAN

Except for FIFO, the policies described so far may leave some requests unfulfilled until the entire queue is processed (Starvation to some of the requests).
SCAN or the elevator algorithm is a simple alternative that minimizes starvations for some processes. 
This policy requires the arm to move in one direction only, satisfying all outstanding requests en route until it reaches the last track in that direction or until there are no more requests in that direction. The latter refinement is often referred to as the LOOK policy.
However, limitations to SCAN may arise such as long wait times for requests that just missed by the head, or Potentially wasting time if the head is going to the end of one track while no requests are waiting there.

#### C-SCAN (Circular Scan)

Similar to SCAN, but restricts scanning to one direction only. When the last track has been visited in one direction, the arm is returned to the opposite end of the disk and the scan begins again.
This reduces the maximum delay experienced by new requests, and requests that just missed the head movement, so it's more fair in that point of view, and can reduce the variance in wait times.


#### N-step-SCAN and FSCAN

With SSTF, SCAN, or C-SCAN, it's possible that the arm may not move for a considerable period of time. For example if one or a few processes have very high access rates to one track, they can monopolize the entire device by repeated requests just to that track.

To avoid this "arm stickiness" (Arm stuck in one track), the disk request queue can be segmented, with one segment at a time being processed completely. 

N-step-SCAN segments the disk request queue into subsequences of length N. Subqueues are processed one at a time using SCAN. While a queue is being processed, a new request must be added to some other queue. If fewer than N requests are available at the end of the current queue's scan, then all of them are processed with the next scan. 

FSCAN is a policy where two subqueues are used. When a scan begins in one queue, all new requests are put in one of the queues with the other empty. During the scan, all new requests are put in the other queue, and the scan will proceed to the new queue when it finishes with the current one.


## RAID

One component can only be optimized and pushed so far, to gain additional performance when it comes to disks, parallel components need to be employed. This leads to the development of arrays of disks that can operate independently and in parallel.

RAID is a standardized scheme for multiple disk database design. It consists of seven levels zero to six, not denoting any hierarchical relationship, just designate different design architecture.

All the levels share three common characteristics:
1. RAID is a set of physical disk drives viewed by the OS as a single logical drive
2. Data are distributed across the physical drives of an array in a scheme known as striping
3. Redundant disk capacity is used to store parity information, which guarantees data recoverability



### RAID Level 0

![[Pasted image 20250112200747.png]]

Not really a true member of RAID because it doesn't include redundancy to improve performance or provide data protection.

In this level, the user and system data are distributed across the disks in the array. This is advantageous compared to a single disk structure because if multiple I/O requests are pending for different blocks of data in different disks, then the request can be issued in parallel.

But, data isn't simply distributed across the disk array, it's also *striped* across all the available disks. All user and system data are viewed as being stored on a logical disk. The logical disk is divided into strips, and these strips may be physical blocks, sectors, or some other units.

The strips are then mapped round robin to consecutive physical disks in the RAID array.

### RAID Level 1

![[Pasted image 20250112204217.png]]

RAID 1 differs from the other levels in how the redundancy is achieved.  in RAID 1, redundancy is achieved by just duplicating all the data. It still stripes data into strips, but each logical strip is mapped to two separate physical disks. So every disk in the array has a mirror disk that contains the same data.
These are positive in a number of reasons:
1. A read request can be serviced by either of the two mirrored disks whichever one gives the minimum seek time
2. A write request will need both strips to be updated, but can be done in parallel. There's no "write penalty" in RAID 1
3. Recovery from a failure is simple, when a drive fails, the data can still be accessed from the second drive

However, RAID 1 might be costly because it requires double the amount of disk space for the logical disk it supports.


### RAID Level 2

![[Pasted image 20250112205255.png]] 

Levels 2 and 3 make use of a parallel access technique. In a parallel access array, all member disks participate in the execution of every I/O requests.

RAID 2 strips the data in very small sizes, often as small as a single byte or word. An error-correcting code is calculated across corresponding bits on each data disk. The bits of the code are stored in the corresponding bit positions on multiple parity bits
RAID 2 requires fewer disks than RAID 1 but can still be costly. And because the data are striped into bit level, all disks must operate in lockstep and maintain a very tight synchronization.
RAID level 2 is usually used for environments in which many disk error occurs. Given the high reliability of individual disks and disk drives, RAID 2 is overkill and is not implemented


### RAID Level 3 (Bit interleaved parity)

![[Pasted image 20250112210517.png]]

Organized similar fashion to RAID 2. The difference is that RAID 3 only requires a single redundant disk, no matter how large the disk array. 
Instead of an error correcting code, a simple parity bit is computed for the set of individual bits in the same position of all of the data disks. 
In the event of a drive failure, the parity drive is accessed and the data is reconstructed from the remaining devices.
This is a cheaper alternative to RAID 2 since it doesn't require as many redundant disk drives.


### RAID Level 4 (Block interleaved parity)

![[Pasted image 20250112210804.png]]


RAID level 4 through 6 make use of an independent access technique, where each member disk operates independently, and separate I/O requests can be satisfied in parallel. 
Thus, independent access arrays are more suitable for applications that require high I/O request rates, but less suitable for applications that require high data transfer rates.

Data striping is also used in this scheme, but the strips are relatively large, usually the size of blocks. A bit by bit parity strip is calculated across corresponding strips on each data bit, and the parity bits are stored in the corresponding strip in the parity disk.

It involves a write penalty where an I/O write request is performed, the array management must update the user data as well as the corresponding parity bits.


### RAID Level 5 (Block interleaved distributed parity)

Organized in a similar fashion to RAID 4, but it distributes the parity strip across all disks in a round robin scheme

It avoids the potential I/O bottleneck of the single parity disk in RAID 4![[Pasted image 20250112220127.png]]


### RAID Level 6

![[Pasted image 20250112220306.png]]

In RAID level 6, two parity calculations are carried out and stored in separate blocks in different disks.
In the illustration, P and Q are different data check algorithms, one of the two is the exclusive-OR algorithm found in RAID 4 and 5, the other is an independent data check algorithm
This method provides extremely high data availability, but it incurs a substantial write penalty, because each write affects two parity blocks.

## Disk Cache

The term cache memory is used to apply to a memory that is smaller and faster than main memory. And it's interposed between main memory and the processor
This makes a significant reduce in average memory access time by exploiting the principle of locality.
The same principle can be applied to disk memory, 



# Memory Management

In a uni-programming system, the memory of a computer is divided into two equal parts: one for OS, and the other for the program being executed.
In a multi-programming system, the "user" part of memory must be further accommodated for the multiple processes that may be running. The task of subdivision done dynamically by the OS is called **Memory Management**


## Memory Management Requirements

These are the requirements that memory management must satisfy

- Relocation
- Protection
- Sharing
- Logical organization
- Physical organization

### Relocation

Swapping out a program from main memory will be unavoidable due to the simple fact that the program cannot know which other programs be resident in main memory at the time of execution.

It's also quite limiting to specify that when it's swapped back in that it will be placed in the same region as before, thus we may need to **relocate** the process to a different region in main memory

### Protection

**The processor** also need to protect running processes in main memory as to not get interrupted or interfered by other processes whether accidental or intentional.
So for example, programs shouldn't be able to reference memory location where another program is reading or writing without permission.

Therefore, all memory references generated by a process must be checked at run time to ensure they refer only to the memory space allocated to that specific process.

Note that this protection requirement must be met by the processor instead of the Operating System, because the OS cannot anticipate all of the memory references that a program will make. So the processor hardware must have this capability

### Sharing

Aside from protecting a specific memory region to a process, the protection mechanism must also be able to allow several process to access the same portion of main memory.
For example if a number of processes are executing the same program, it's better to allow each process to access the same copy of the program.


### Logical Organization

Main memory in a computer system is organized as a liner address space, consisting of a sequence of bytes and words, similarly so for secondary memory. While this organization mirrors the actual machine hardware, it doesn't correspond to how programs are constructed. 

Programs are organized into modules, some of which are unmodifiable, and some contain data which can be modified. If the OS can effectively deal with user data in the from of modules, then a number of advantages can be realized.

1. Modules can be written and compiled independently
2. Different degrees of protection can be given to different modules
3. It's possible to introduce mechanisms that modules can share among processes.

**Segmentation** is the tool that most readily satisfy these requirements


### Physical Organization

In the two level scheme of main and secondary memory. the flow between them becomes a system concern. And the task of moving information between the two levels of memory should be a system responsibility which is the essence of memory management.

## Memory Partitioning

Principal of memory management -> Bring processes into main memory for execution by the processor which in modern multiprogramming systems involve a scheme called **virtual memory**

Virtual memory -> The use of one or both techniques (Segmentation and paging)

Discussed in this session are simpler techniques that do not involve virtual memory, one of these techniques called partitioning which is used in variations in some now-obsolete operating systems.

Simple paging and simple segmentation are not used by themselves, but it will clarify the discussion of virtual memory if we analyze these techniques in the absence of virtual memory.


### Fixed Partitioning

> The simplest scheme for managing the available memory not used by the OS is by dividing them into regions with fixed boundaries

#### Partition Sizes

![[Pasted image 20250113121954.png]]

This figure shows two alternatives for fixed partitioning, by using equal sized partitions, where process whose size is equals or less than to the partition size can be loaded into any available partition.

However using equal sized partitions has it's limitations:
- A program may be too big to fit a partition, then the programmer must design the program with the use of overlays.
- Any program no matter how size will occupy the entire partition, which would cause **internal fragmentation**

However, these problems can be minimized by using unequal sized partitions

#### Placement Algorithm

In equal sized partitions, the placements of processes in memory is trivial, since all partitions are equal, it doesn't matter which partition is used.
If all partitions are occupied with processes that are blocked/not ready to run, then they must be swapped out using a scheduling decision

With unequal size partitions, there are two ways to assign processes to partitions, with the simplest way just by assigning each process to the smallest partition within which it will fit. Thus, a scheduling queue is employed for each partition to hold swapped out processes destined for that partition.
This method minimizes internal fragmentation

Although it's not optimum for the whole system, let's say that there are no processes with a size between 12 and 16M, in that case the 16M partition will remain unused, even though smaller processes could have been assigned to it, thus a preferable approach would be to use a single queue for all processes.

However there are a number of disadvantages to fixed partitioning:
- The number of partitions specified limits the nummber of active processes in the system
- Because partition sizes are preset at system generation time, small jobs will not utilize partition space efficiently

Fixed partition is rarely used nowadays


### Dynamic Partitioning

![[Pasted image 20250113132932.png]]

Dynamic partitioning was developed to overcome the limitations of fixed partitioning. With dynamic partitioning, the partitions have variable length and number. When a process is brought into main memory, it's allocated exactly as much memory it needs.

However, as the processes are swapped in and out, it can cause holes in the main memory, and memory can become more and more fragmented, this is referred to as **external fragmentation**. One technique to overcome external fragmentation is by using compaction algorithm, to compact all the used memory.


#### Placement algorithm

Memory compaction is time consuming, the OS must be clever on how to assign processes to a memory.
Three placement algorithms are considered:
- Best Fit: Chooses the block that is closest in size to the request
- First Fit: Begins to scan memory from the beginning, and chooses the first available block 
- Next fit: Begins to scan memory from the location of the last placement and chooses the next available block

#### Replacement Algorithm 

In some cases where all the processes in memory are in a blocked state, the OS will at some point have to swap them out of memory to make room, thus the OS must also choose which process to replace. This will be discussed further in virtual memory schemes


### Buddy System

Buddy system compromises for both fixed and dynamic partitioning. In a buddy system, blocks are available of size $2^{k}$ words, $L \leq K \leq U$, where 

$2^L$ = smallest block that is allocated
$2^U$ = Largest block that is allocated, typically the size of the entire memory available for allocation

if a request of size s such that $2^{U-1} < s \leq 2^U$, then the entire block is allocated, otherwise the block is split into two equal buddies of size $2^{U-1}$, and it continues until the smallest block greater than or equal to s is generated.

The buddy system maintains a list of holes of each size $2^i$. A hole may be removed from the (i+1) list. 


### Relocation

In the case of equal size and unequal size partitions, a process may occupy different partitions during the course of it's life. When the process inevitably gets swapped out, it may be assigned to a different partition than the last time, this also is true for dynamic partitioning.

To solve this, a distinction is made across different types of addresses:
- **Logical address**: which is a reference to a memory location independent of the current assignment data of memory, but a translation must be made to a physical address before the memory access can be achieved (One particular example is **relative address** which is the address as a location relative to some known point)
- **Physical address**: Is the actual location in main memory


When a process is assigned to the Running state, these steps will happen:
- A special **processor register** called the base register is loaded with the starting address in main memory of the program
- There is a "bounds" register that indicates the ending of the program. These values must be set when the program is loaded into memory
- During the course of execution, relative memory will be encountered, and these includes the contents of the instructions register, instruction addresses, and data addresses
- Each relative address goes hrough two steps manipulation by the processor
- The value in the base register is added to the relative address to produce an absolute address
- The resulting address is compared to the value in the bounds register, if it's within bounds, then it may proceed
- If it's outside of the bounds, an interrupt is generated to the Operating System


## Paging

![[Pasted image 20250113152954.png]]

![[Pasted image 20250113153007.png]]

Unequal fixed size and variable size are inefficient in the use of memory. Suppose however, main memory is partitioned into fixed size chunks that are relatively small, and each process is also divided into small fixed size chunks of the same size

The chunks of a process is called **pages**
Chunks of free memory are called **frames** or **page frames**

In order to execute paging, a base address register will no longer suffice, the OS will also maintain a **page table** for each process. The page table shows the frame location of each page of the process.
The processor will then use the page table as well as the logical address in each page to produce a physical address. 
#more


## Segmentation

Segmentation, compared to paging, divides the user's process into segments. Different to paging, segmentation is not required to be of same length, although there is a maximum segment length.

While paging is invisible to the programmer, segmentation is usually visible and provided as a convenience for organizing programs and data.
#more 



# Virtual Memory

## Hardware and Control Structures

After exploring paging and segmentation before, we now know that processes may be split up into pages or segments. We also now know that processes doesn't need to be contiguous in main memory.
*Then, it's not necessary that all of the pages or segments of a process be in main memory during execution*.
The portions of a process that is actually in main memory is called as the **resident set** of a process.
Things proceed smoothly as long as all memory references are to locations that are in the resident set. If the processor encounters a logical address that is not in main memory, it generates an interrupt indicating a **memory access fault**.
With this approach, there are two implications:
1. More processes may be maintained in main memory
2. A process may be larger than all of main memory

Main memory is referred to as **Real memory**
Memory that which is allocated on disk is referred to as **Virtual Memory**


### Locality and Virtual Memory

Virtual memory is essentially used in most operating systems now, because of the simple fact that processes can be divided into subroutines, and only the processes that are essential and can run that is brought to main memory, giving space to other processes.

However, the OS must be smart in bringing in and out pieces of a process, if it swaps out a process in exchange for a new one, and the swapped out process hasn't been executed, then it will need to be brought back in again. Too much of this leads to a condition as **thrashing**, where the processor is too busy swapping pieces rather than executing instructions. So, the OS tries to guess based on recent history, which pieces are likely to be used in the near future

This is based on belief in the **principle of locality**, which states that programs and data references within the same process tend to cluster. 

### Paging

Paging in virtual memory is similar to paging in the previous section, we have equal sized pages of the same length as frames, but not all pages need to be loaded into main memory frames for execution.

In simple paging, when the entire process's page is loaded in, a page table entry containing the frame number for the corresponding page in memory is created. It's also needed for virtual memory scheme based on paging.

However in virtual memory, page tables become more complex, because only some of the pages of a process may be in main memory
A bit is needed to indicate whether the corresponding page is present (P) in main memory or not. If the bit indicates that the page is in memory, then the entry also includes the frame number of that page.

The page table entry includes a modify bit (M) indicating whether the contents of the corresponding page have been altered since the page was last loaded into main memory. If there's no change then it's not necessary to write the page out when it's swapped out.

#### Page Table Structure

Basic mechanism for reading a word from memory involves translating the logical address into physical address consisting of frame/segment number and offset using a page table.

Thus the page table must be in main memory to be accessed. When a process is running, a register holds the starting address of the page table for that process. The page number for a virtual address is used to index the table and look up the corresponding frame number, combined with the offset to find the desired precise address.

Typically the page number would be bigger than the frame number field, because the number of pages in a process may exceed the number of frames in main memory. Making the page table very high, so then most schemes store page tables in virtual memory and they're subject to paging just as other pages.

When a process is running, at least a part of the page table must remain in main memory, including the page table entry of the currently executing page.

Some processors employ a two-level scheme to organize large page tables, with a page directory in which each entry points to a page table. if the number of entries in the page directory is X, and the maximum number of entries in a page table is Y, the process can consist up to X x Y pages. Typically the maximum length of a page table is restricted to be equal to one page

![[Pasted image 20250113182810.png]]

#### Inverted Page Table

![[Pasted image 20250113184605.png]]

A drawback of the page table we have been discussing is that their size is proportional of the virtual address space.

An alternative approach is to use an **inverted page table** structure. In this approach, the page number portion of the virtual address is mapped into a hash value using a simple hash function. Then the hash value is a pointer to the inverted page table, which contains the page table entries. There is one entry in the inverted page table for each real memory page frame, thus a fixed proportion of real memory is required for the table.

Because more than one virtual address may map into the same hash table entry, a chaining technique is used to manage the overflow.

Each entry in the page table includes the following:
- Page number
- Process identifier
- Control bits
- Chain pointer


#### Translation Lookaside Buffer

Having page tables mean that for every virtual memory reference, physical memory access is doubled, one to fetch the page table entry, another to fetch the desired data.
To overcome this, a **translation lookaside buffer (TLB)** is used. This cache functions the same way as a memory cache. 
TLB contains page tables entries that have been most recently used.

![[Pasted image 20250113185132.png]]

When a virtual address is referenced, the processor will first examine the TLB, if the page table entry is present (TLB hit), then the frame number is retrieved, and the real address is formed.

But it's not found (TLB miss), then the processor uses the page number to index the process page, and examine the corresponding page table entry.

If the "present bit" is set, then the page is in main memory, and the processor can just retrieve the frame number from the page table.

If the present bit is not set, then the desired page is not in main memory, and a memory access fault called a **page fault**. When this happens, we invoke the OS which loads the needed page and updates the page table

the entries in TLB must include the page number as well as the complete page table entry. The processor is equipped with hardware that can interrogate simultaneously a number of TLB entries, this is referred to as **associative mapping**. 

Finally, the virtual memory mechanism must also interact with the cache system (The main memory cache, not TLB). 
Once the real address is generated, the cache is consulted to see whether that word is present. If so, it's returned to the CPU, if not the word is retrieved from main memory


#### Page Size

An important design issue now is the size of the page to be used. There are many factors to take into consideration, like internal fragmentation, page table size, etc.

![[Pasted image 20250113192207.png]]

If the page size is very small, then a large number of pages will be available in memory for a process, then the pages in memory will all contain portions of the process near recent references, thus the page fault should be low.

If the size is increased, each individual page will contain locations further and further from any particular recent reference, thus the principle of locality effect is weakened. And nearing the entire size of the process, then page fault would of course go 

Page fault rate is also determined by the number of frames allocated to a process.
#more
### Segmentation

#### Virtual Memory Implications

Segmentations allows programmers to view memory as consisting of multiple address spaces or segments, where segments may be of unequal, dynamic size. Memory references consist of a (segment number, offset) form of address. 

Segmentation has a number of advantages:
1. Simplifies the handling of growing data structures. Growing data structures may be assigned it's own segment that can grow or shrink
2. Allows programs to be altered and recompiled independently
3. Lends itself to sharing among processes
4. Lends itself to protection


#### Organization

Each process has it's own segment table, and when all of it's segments are loaded into main memory, the segmentation table for a process is created and loaded into main memory.

Each segment table entry contains the starting address of the corresponding segment in main memory, as well as the length of the segment.

As with paging in the context of virtual memory, the segmentation table also becomes more complex, because only some of the segments may be in main memory.
Similar to Paging, a present bit as well as a modify bit is used.
Same with paging, translating virtual memory into physical address involves using the segmentation table to fetch the segment number and length, and using the offset to gain the correct address.

![[Pasted image 20250113194645.png]]

### Combined Paging and Segmentation

Paging and segmentation have their strengths and weaknesses. Thus there is a way to combine their strengths

In a combined paging/segmentation system, a user address space is broken up into a number of segments, at the discretion of the programmer, and each segment is then broken up into a number of fixed size pages which is equal to a memory frame.

![[Pasted image 20250113195037.png]]


### Protection and Sharing

Segmentation lends itself to the implementation of protection and sharing policies.

![[Pasted image 20250113195644.png]]


## Operating System Software

The design of memory management portion of an OS depends on three fundamental areas of choice:
1. Whether or not to use virtual memory techniques
2. The use of paging or segmentation or both
3. The algorithms employed for various aspects of memory management

The first two choices depend on the hardware platform available. 
Two comments abt the first two points: most operating systems provide virtual memory, and purely segmentation systems are becoming increasingly rare.
Thus the third element is the general area for discussion

![[Pasted image 20250113195953.png]]

### Fetch Policy

Determines when a page should be brought into main memory. 
Two common alternatives:
- Demand paging
- Prepaging
Demand paging -> brings in a page only when a reference is made to a location on that page

Prepaging -> Pages other than the one demanded are brought in as well. If the pages of a process are stored contiguously in secondary memory, then it's more efficient to bring in a number of contiguous pages at a time.

Shouldn't be confused with swapping, a process is swapped out of memory when it's suspended, and all of it's resident pages are moved out. When it's resumed, all of the pages are returned back to main memory


### Placement Policy

Determines where in real memory a process piece is to reside. In a pure segmentation system, the placement policy is an important design issue: such as best-fit, first-fit, so on. 
However, in a pure paging or paging combined with segmentation, placement is usually irrelevant because the address translation hardware and memory access hardware can perform their functions for any page frame combination with equal efficiency


### Replacement Policy

Deals with the selection of a page in main memory to be replaced when a new page must be brought in, several concepts are involved:

- How many page frames are to be allocated to each active process
- Whether the set of pages to be replaced should be limited to those of the process that caused the page fault, or encompass all the page frames in memory
- Among the set of pages considered, which particular page should be selected for replacement

The first two concepts referred to as *resident set management* The third concept is referred to as *replacement policy*


#### Frame Locking

One important concept is that the frames in main memory may be locked, when a frame is locked, the page currently stored in that frame may not be replaced. 


#### Basic Algorithm

These are basic algorithms for replacement policy:
- Optimal
- Least Recently Used (LRU)
- First-in-first-out (FIFO)
- Clock

**Optimal**
Selects for replacement that page for which the time to the next reference is the longest, This shows the fewest number of page faults. Clearly this is impossible to implement, because the OS would need to be able to see the future.
Although this is a good standard against real-world algorithms

![[Pasted image 20250113203530.png]]

**Least Recently Used**
Replaces the page in memory that has not been referenced for the long time. According to the principle of locality, this should be the page least likely to be referenced in the near future. 
Although this approach would cause a tremendous amount of overhead, since every memory reference would need to be tagged in order to find when it's last requestd.

![[Pasted image 20250113203536.png]]

**First in Fist Out**
Treated as a circular buffer, pages are removed in round robin style. All that's required is for a pointer that circles through the page frames of the process. 

![[Pasted image 20250113203548.png]]

**Clock policy**
Requires an additional bit with each frame, referred to as the use bit. 

![[Pasted image 20250113203555.png]]



#### Page Buffering

LRU and clock policies are superior to FIFO, they involve complexity and overhead not suffered with FIFO.
#more 


# Virtual Machines

Virtualization encompasses a variety of technologies for managing computing resources by providing a software translation layer

## Virtual Machine Concepts

Typically computer runs one OS at at time, thus application vendors would have to rewrite parts of applications for each platform.
**Hardware Virtualization** solves this problem by allowing a single PC server to simultaneously run multiple OSs or multiple sessions of an OS

The host OS can run a number of **Virtual Machines (VM)**

The solution that enables virtualization is the use of **hypervisors**. This software sits between the hardware and the VM acting as a resource broker. 


Each VM includes an OS called the guest OS. 
The number of guests that can exist in a single host is measured on a **consolidation ratio**.


Reasons to use virtualization:
1. Legacy hardware
2. Rapid deployment
3. Versatility
4. Consolidation
5. Aggregating
6. Dynamics
7. Ease of Management
8. Increased availability


## Hypervisors

### Hypervisors

Hypervisor Functions
1. Execution management of VMs
2. Devices emulation and access control
3. Execution of privileged operations by hypervisor for guest VMs
4. Management of VMs
5. Administration of hypervisor platform and hypervisor software

Type 1 Hypervisor -> Sits on top of the hardware directly

Type 2 Hypervisor -> Sits on top of a Host OS



# Security

## Intruders and Malicious Software

A key security issue in the design of OS is to prevent or at the very least detect, attempts by a user or a malicious software from gaining unauthorized privileges on the system

### System Access Threats

Generally fall into two categories: Intruders and malicious software

#### Intruders

Most common threats to security is an intruder (Hacker/cracker) which can be identified into three classes:
- **Masquerader**: An individual who is not authorized to use the computer and who penetrate a system's access controls to exploit a legitimate user's account
- **Misfeasor**: Legitimate user who access data for which such access isn't authorized, or is authorized, but misuses their privileges
- **Clandestine User**: Seizes supervisory control of the system and uses this control to evade auditing

#### Malicious Software

Programs that exploit vulnerabilities in computer systems, referred to as malicious software or **malware**. So in this context, we're concerned with dangerous files and programs.

Can be divided into two classes:
- Malware that needs a host program, referred to as **parasitic**. 
- Malware that are independent

Parasitic malware essentially means that it cannot exist independently outside of an actual program, utility or system program (Viruses, logic bombs, backdoors)

We can also differentiate between software threats that don't replicate and those that do. The former are programs or fragments of programs that are activated by a trigger (Logic bombs, backdoors, bot programs).

### Countermeasures

#### Intrusion Detection

Intrusion detection: Security service that monitors and analyzes system events for the purpose of finding real time attempts of unauthorized access

Intrusion Detection Systems can be classified as:
- **Host Based IDS** Monitors the characteristics of a single host
- **Network based IDS** Monitors network traffics for particular networks segments.


An IDS comprises three logical components:
- **Sensors**: Responsible for collecting data, the input for a sensor can be any part of the system
- **Analyzer**: Receives input from one or more sensors, responsible for determining if an intrusion has occured
- **User Interface**: The user interface to an IDS enables a user to view output from the system or control the behavior of the system


#### Authentication

Fundamental building blocks and the primary line of defence

An authentication consists of two steps:
1. **Identification step**
	Presenting an identifier to the user system. the means which a user provides a claimed identity to the system
2. **Verification step**
	Presenting authentication information that binds the entity and the identifier

There are four means of authenticating a user:
1. Something the individual knows
2. Something the individual possesses 
3. Something the individual is
4. Something the individual does


#### Access Control

Implements a security policy that specifies who or what may have access to each specific system resource

An access control mechanism mediates between a user and system resources. The user must first authenticate a user seeking access.


#### Firewalls

Means of protecting local system or network of systems from network based security threats. 

1. Traffics from inside to outside or vice versa must pass through the firewall
2. Only authorized traffic will be allowed to pass
3. The firewall itself is immune to penetration.


## Buffer Overflow

Main memory and virtual memory are subjects to attacks. We will see another type of threat which involves memory protection


### Buffer Overflow attacks

Also known as buffer overrun, overwrites adjacent memory locations, memory that could hold other program variables or program control flow.
The buffer could be located on the stack, in the heap, or in the data section of the process.
Could lead to corruption of the data, unexpected transfer of control, or memory access violations.

Stack overflow is one of the most common types of buffer overflow. 


### Compile Time Defenses

Finding and exploiting a stack buffer overflow isn't difficult. So there is a need to defend systems against such attacks by preventing them or at least detecting and aborting such attacks
Countermeasures can be classified into two categories:
1. Compile time defenses, which aims to harden programs to resist attacks
2. Runtime defenses which aims to detect and abort attacks in executing programs


#### Choice of Programming Language

Writing programs using a modern high-level programming language is safer since they are not as susceptible to buffer overflows. 


#### Safe Coding Techniques

Programmers should be aware that their ability to manipulate pointer addresses and access memory directly comes at a cost. And they need to be aware of the code they write as to not leave any vulnerabilities.

#### Language Extensions and Use of Safe Libraries

Given problems that can occur in C with unsafe array and pointer references.

#### Stack Protection Mechanisms

Instrument the function entry and exit code to set up and then check it's stack frame for any evidence of corruption.


### Runtime Defences

#### Executable Address Space Protection

Block the execution of code on the stack, assuming that the executable code should only be found elsewhere in the processes address space

#### Address Space Randomization

Change the address at which the stack is located in a random manner to each process. To increase the difficulty for attackers to predict which memory block is used

#### Guard Pages

Places Guard Pages between critical regions of memory.  Basically gaps are placed between the ranges of addresses used for each component. These gaps are then flagged as illegal addresses, where any attempt to access them will result in the process being aborted


## Access Control

Access Control from the POV of file access control

### File System Access Control

Users can be identified to the system, and associated with each users are profiles that specifies permissible operations and file accesses. 
However the database management system or file management system must also control access to specific records or even portions of records.
A general model of access control as exercised by file or database management system is an **access matrix**. The basic elements are:
- Subject -> Entity capable of accessing objects
- Object -> Anything to which access is controlled
- Access rights -> The way in which an object is accessed by a subject (write, execute, and functions in software objects)

![[Pasted image 20250113234746.png]]


The matrix may be decomposed by columns, yielding **access control lists**. Thus for each object, an access control list contains users and their permitted access rights. 
Decomposition by rows yields **capability tickets**. A capability ticket specifies authorized objects and operations for a user. 

### Access Control Policies

Dictates what types of access are permitted, under what circumstances

- **Discretionary Access Control (DAC)**: Controls access based on the identity of the requestor and the access rules stating what the requestor can and cannot do. 
- **Mandatory Access Control (MAC)**:
  Controls access based on comparing security labels with security clearances
- **Role Based Access Control (RBAC)**:
  Controls access based on the roles that users have within the system, and on rules stating what accesses are allowed to users in given roles
- **Attribute-based Access Control (ABAC)**:
  Controls access based on attributes of the user, the resource to be accessed, and the current environmental conditions
#### Discretionary Access Control
