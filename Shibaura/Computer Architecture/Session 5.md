
# Switch Element

> How are switch elements useful in CPUs?

The total switch element in a cpu is increasing throughout the year (Moore's law)

![[Pasted image 20250512112145.png]]

Depending the voltage of the gate (A), B and C can be electrically connected, or disconnected

"Rules" of a chip:
- Logical value "0" <=> Low voltage 0V
- Logical value "1" <=> High voltage 1.2V (Supply voltage)
- Logical world <=> Physical world


We typically use two types of switch elements

1. Normal switch (nMOS transistor)
	It turns on when A (Gate) = 1
	it turns off when A (Gate) = 0
2. Perverse Switch (Not technical term, pMOS transistor)
	it turns off when A (Gate) = 1
	it turns on when A (Gate) = 0



# Formation of Machine Language

How can we identify individual instructions in machine code?

- For RISC-V Architecture:
	Every instruction is 32 bits (Fixed length)
	We can chop the machine code into 32 bit pieces from the beginning
- For something like x86 intel architecture:
	Instructions can be 8 bits to 120 bits (Variable length)
	The length depends on the instruction itself
	Even if we separate the bits, we cannot tell where the instructions are without decoding (Decoding can be really complex, which can increase the circuit and chip's size)


How can we quickly identify operations and operands by looking at 32-bit instructions? => We see the "field"

RISC-V Instruction (32 Bit)
![[Pasted image 20250512120301.png]]

Field => Segments of an instructions
Instructions and operands can be identified by looking at fields at fixed positions

![[Pasted image 20250512120534.png]]


First, we read the opcode, if it's 0110011 (Magic number), then the combination of funct7 and funct3 denotes the function

![[Pasted image 20250512120658.png]]


![[Pasted image 20250512121136.png]]

Each operand is 5 bits, because 5 bits can represent 32 combinations, and there are total number of 32 registers in RISC-V architecture.


