1. Describe the objectives of File Management
	- Meet data management needs and requirements.
	  Explanation:
		This includes providing a structured and efficient way to store data, and allowing users to manipulate those data
	- Guarantee that the data in the file are valid
	  Explanation:
		so the File Management system needs to ensure that the data is accurate, and isn't corrupted. It should also have an error detection, and have checksums to ensure data consistency
	- To optimize performance, for both from the system's point of view, and from the user's point of view
	  Explanation:
		the system's perspective in terms of performance includes throughput, being able to serve multiple requests simultaneously (Basically performance that isn't exactly apparent for the User directly). Meanwhile, from the User's perspective, optimizing performance includes reducing file access times, faster loads, and anything that directly affects the user's experience with the FMS
	- To provide I/O support for a variety of storage device types
	  Explanation:
		Nowadays, there are various storage devices like hard drives, SSDs, disks, USB devices, and many more. The FMS should be able to support input output operations for all these devices
	- To minimize or eliminate the potential for lost data
	  Explanation:
		Pretty similar to the second point, but the FMS should have features to prevent data loss or corruptions that can be caused by hardware failures. These features include backups, redundancy, journaling file system, etc.
	- To provide a standardized set of I/O interface routines to user processes
	  Explanation:
		the FMS should provide a standardized interface for users despite the complexities of I/O operations with different devices. This abstracts the complexities of hardware operations, allowing users to perform file operations through a consistent API
	- To Provide I/O support for multiple users, for the cases of multiple-user systems.
	  Explanation:
		FMS should be able to support file management in a multi-user environment, it should be able to handle instances of concurrent file access, while ensuring security for each user, and prevents conflict.

2. Describe the 3 file allocation method including it's advantages and disadvantages
	1. Contiguous allocation
		With contiguous allocation, a single set of blocks is allocated to a file at the time of file creation, this is considered as a pre-allocation strategy, using variable-size portions.
		This allocation method only needs a single entry for each file created (The starting block of the file, and the length).
		Pros:
		- Best from the point of view of each of the sequential file
		- Easy to retrieve a single block
		- Multiple blocks can be read in at a time to improve I/O performance
		Cons:
		- External fragmentations will occur, making it difficult to find contiguous blocks of space
		- From time to time, it will be necessary to perform a compaction algorithm to free up additional space on the disk.
		- It's necessary to declare the size of the file at the time of creation
	2. Chained allocation
		The opposite extreme from contiguous allocation. with this method, allocation is on an individual block basis, and each block contains a pointer to the next block in the chain (Similar to a linked list data structure). Similar to contiguous allocation, the file allocation table needs a single entry for each file, showing the starting block and the length of the file.
		It's more common with this method to just allocate blocks as needed dynamically, with this there is no external fragmentation to worry about.
		Pros:
		- best suited for sequential files that are to be processed sequentially
		Cons:
		- No accommodation of the principle of locality (Tendency for a processor to access the same set of memory locations). So it's necessary to bring in several blocks of a file at a time
	3. Indexed allocation
		This method aims to address the problems of contiguous and chained allocation. File allocation table only contains a separate one level index for each file (The index has one entry for each portion allocated to the file). The file indexes aren't stored as part of the file allocation table, but stored in a separate block, and the entry for the file in the file allocation table points to that block.
		Pros:
		- Supports fixed size or variable-size portion allocations (Fixed size allocation eliminates external fragmentation, while variable-size allocation improves locality)
		- Since blocks are allocated dynamically and non-contiguously, files can grow without contiguous free space
		Cons:
		- The index block used to store file indexes consumes extra disk space, which can snowball into needing bigger space for larger files
		- If the index block is corrupted or lost, access to the entire file is compromised.

3. ![[WhatsApp Image 2024-11-30 at 13.54.33_e5e0a084.jpg]]
   
   ![[WhatsApp Image 2024-11-30 at 15.29.52_22462b4c.jpg]]
   
   ![[WhatsApp Image 2024-11-30 at 15.29.57_90027808.jpg]]
   


4. Code:
   ![[Pasted image 20241130164833.png]]
   
   Directory:
   ![[Pasted image 20241130164858.png]]
   
   Results:
   ![[Pasted image 20241130164907.png]]
   
   ![[Pasted image 20241130164912.png]]
   
   
   ==Note that i was using my brother's macbook since some libraries isn't supported in windows, so the owner is my brother's name==

