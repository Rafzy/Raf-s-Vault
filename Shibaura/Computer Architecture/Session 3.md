#SIT

# How are semiconductor chips manufactured

- "Silicon" is a common element from sand
- It's then purified into pure silicon, it's then melted until it becomes molten silicon
- A single silicon crystal is then extracted in the shape of a tube
- The silicon then gets cut into wafer shapes using diamond cutters
- It then gets cleaned to rid of any scratches or contamination, where then they'll get tested before getting manufactured
- Circuits are designed which will be placed on the wafers
- Transistors are built in a microscopic level on the wafers.
- There are millions of transistors in the master blueprint
- The actual manufacturing process requires an ultra clean environment (One source being the human body, like oil, hair, dirt, etc)
- wafers gets rinsed in several liquids to ensure it's absolutely clean
- We use masks or stencils to integrate the circuit on the wafer
- ultraviolet light is passed through the mask to the wafer, and multiple circuits can be made in one wafer
- Regions of silicon dioxide (The outer layer) that gets hit with ultraviolet light is etched
- We add multiple elements to the exposed area to increase it's conductance
- This process can be done multiple times to create complex designs

**Transistors** acts as switches that can turn "on" and "off", or 0 and 1.

![[Pasted image 20250428112000.png]]

- When A is high in voltage, B and C is electrically connected
- When A is low in voltage, B and C in electrically disconnected

==If dust accumulates on a transistor, it won't work properly==




# Deeper story regarding "Yield"

![[Pasted image 20250428113255.png]]

Consider these two wafers, with the same diameter, and the same number and location of dust accumulations, but they have different chip areas.

The wafer with smaller chip area will yield more compared to the wafer with the bigger chip area. Because the smaller the chip area is, the less likely a lot of chips will get stuck with dust.

$$
Y = E^{-DA}
$$



# Instructions and operands, registers

**How do we tell the CPU what to do?**

The computer can't understand source code (Let's say Clang).

The source code needs to be compiled into assembly code first using compilers. The compiler translates source code into assembly code.

Source Code:
```C
Z = X + Y;
```

This simple source code above will be translated into these instructions in assembly below:

1. Transfer data of X from memory into CPU
2. Transfer data of Y from memory into CPU
3. Add them in the CPU
4. Store the addition result in memory at location Z

RISC-V Instructions:
```
lw x18, 4(x22)
lw x19, 8(x22)
add x5, x18, x19
sw x5, 12(x33)
```


Explanation:
- lw -> Load word instruction
- X18, X19, X5, etc -> register
- 4(X22) -> Offset 4 from register x22 (X22+4)


## Instructions set

- Gives CPU "Instructions"
- List of instructions available based on the CPU -> "Instruction set", Slightly differ depending on the CPU
  Ex:
	- Intel core-i7 instruction set -> "x86 instruction set"
	- ARM instruction set
	- MIPS instruction set

- We will be learning the instruction set of RISC-V architecture
	- Arithmetic instructions: Add, subtract
	- Data transfer instructions: load instruction (lw), store instruction (sw)
	- Conditional branch instruction: beq instruction


---

x86 -> Intel's CPU architecture for PC, why is it called that?
Intel manufactured a CPU called 8086, which is installed on the first IBM PC, and since IBM PC used an "open architecture", allowing other companies to create "clones" that's compatible with the open architecture, the 8086 exploded in demand.

Since there is a lot demand for 8086's performance, they created 80186, 80286, and other generations with the same base instruction set

While Intel is growing, AMD saw an opportunity to create an 8086 instruction set compatible chip. 

---

**Arithmetic Instructions**

`add a, b, c`
The instruction above says to add all data in "b" and "c", and store it in "c"

`sub a, b, c`
The instruction above says to subtract "c" from "b" (b-c), and store it in a


**Where is the data to be processed stored?**
The data processed by the CPU is stored in the **Register**. Registers are very high-speed storage circuit inside the CPU itself, it's faster than secondary memory and main memory.

- Read/Write time comparison:
	- Main memory (DRAM) -> 50-70 nanosecond
	- Register -> 0.2 - 1 nanosecond
- Registers need to be extremely fast because the CPU itself is very fast, so it doesn't slow down the CPU's overall processing speed


**Registers**
- For RISC-V Architecture, there are 32 registers, of these, 18 are used for calculations
  x9, x18 - x27 : Stores C program variable data
  x5 - x7, x28 - x31 : Temporary registers (Storing intermediate results of operations)
- The remaining 14 registers are used for special purposes


Example:
```
add x5, x18, x19
```

The data in register x18 and x19 are added and stored in x5

But then, when is the initial data moved from main memory to x18 and x19?
- They are stored from another instruction before the add instruction.


![[Pasted image 20250428122508.png]]


```
add x5, x19, x20
add x18, x5, x21
```

