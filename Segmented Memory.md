> Segmented memory is a memory management technique in computers where memory is separated into logical segments, these segments can then be used for different processes for different purposes.

# Application

in x86 architecture, segmented memory depends on the [[Operating Modes]] of the Operating System.

**Real Mode**
in real mode, the segmented memory has no memory protection, meaning segments can overlap one another. This brings a security risk where programs can either intentionally or accidentally access data of other segments from other programs. 

In real mode, Memory is segmented, and they are stored like so:

```
[Segment:offset] -> Physical = (Segment << 4) + Offset
```

This essentially means that segments can only be placed in 16 bits separated from one another, relative to the physical address. 
The physical address also has a 20 bit size => 1MB maximum of address.

**Protected Mode**
In protected mode, not only the Registers are different, the way memory is implemented is also different, in this mode, we use [[Virtual Addresses]]. The address space is 32-bit long => 4GB per process

[[4 Privilege Rings]] is utilized for security

**Long Mode**
In long mode, they don't use segmented memory at all, [[Flat linear addressing]] is utilized for memory management.
The address space is 48-bit virtual => 256TB per process

A combination of enhanced rings protection as well as additional security features are utilized. 