**Little Endian**
Little endian means that the low byte is stored first.

**Big Endian**
Read byte as it is.

**Displacement**
> Information of the address

sign-extended -> -128 ~ 127
unsigned -> 0 ~ 255

what is this value?
11111111 -> unsigned: 255, signed: -1

If first bit is 1 : We have to extend
if first bit is 0: We have top add all zero

Jump operator -> Relative address, not absolute address

f1 -> 11110001
First bit -> Sign information (1)
this number should be minus, to get minus, we use two complement strategy (Invert everything and + 1 at the lowest bit)


