Welcome to my spaghetti code

# Introduction

This is a documentation for my code of Minix's X86 instruction set interpreter. For disclaimer, i am an undergraduate that's taking this class my knowledge was very limited for this class, but did my best to implement the interpreter, although my interpreter worked for 1.c - 6.c, i recognize that my code is a mess and that there are a lot of things that can be improved.

Github for my code:
https://github.com/Rafzy/Minix

# How to compile the interpreter

I don't use cmake or anything complicated, to compile, any cpp compiler would do, for example:

- Using gcc
```
g++ -o minix *.cpp
```

"\*.cpp" is basically a wildcard that says, compile all code with the cpp extension

# How to execute

To execute is also as simple as executing the compiled code, the .out files are compiled from the lecturer's m2cc executable

```
./minix 1.out
./minix 2.out
./minix 5.out 1 2 3
```

# Documentation

![[image-161.png]]

In general, this is how my code works, a parser takes in the machine language, in which inside there are many specified parsers that's designed to handle specific machine code patterns, and it spits out the "Result Info", which is all strings, for the opcode as well as the operands.

The reason why it pops out strings is because initially, we were told to make a disassembler, and i thought it would be easier to print out the result if the parser just returns a string. But i mistakenly also used this parser for the interpreter, since then the interpreter has to work with operands in string data type, but somehow in the end it all worked out :D

## CPU Struct

Before going into the core components of the code, i will explain regarding a struct i created called cpu_state_t

![[image-163.png]]

This is created in order to mimic the behavior of CPU, the registers i use a simple array to store the values, and for the memory, i create a pointer that points to another struct that contains data array. 
This seems very redundant and complicated for no reason, but i decided to do this because i want to "mimic" how real cpu works, cpu itself of course doesn't contain the memory's data, but it has a reference to the memory.

Then i initialized this cpu struct using cpu_init() function, as you can tell, for this cpu, i use a functional approach rather than a class based approach, this is because i didn't start with OOP approach for the project, and i didn't want to start halfway

![[image-164.png]]

As you can see, init_cpu() takes in a pointer for a cpu_state_t struct, and initializes all the arrays with it's initial values, for the segments, i kind of gave them a random segment address, but i was sure to give gaps of 1000 hex values in between the segments.
The interpreter will be primarily working with this cpu_state_t struct to change the register values, flags, Instruction Pointer, etc.

## Initialize Stack

We also have to initialize the stack before starting to execute the machine code, since the stack information must already be known before execution.
The stack will be stored in the stack segment of the cpu, denoted by "SS" of the cpu's register values.
The stack itself contains argv and env values, and the stack starts at virtual address 0xFFFF (This part is initialized in the init_cpu, for the SP initial value).

![[image-168.png]]

## Parser

Now going back a bit, to the parser themselves that takes in the machine code and pops out the opcode, and operands.
The parser itself is made out of a lot of switch cases, it's used to filter out the known machine code hex values and what opcode they're correlated to.
To do this, i used the documentation for opcode patterns


![[image-165.png]]


This goes on for pretty long.
I also created specific parser functions, for specific opcode patterns, because there are several machine code patterns that are reused for several opcodes (Same w, mods, reg bits position, same operand length, etc)
And the output of this function is the result info containing all the opcodes and operands required, this also carries the info of how much byte this instruction uses, taking into account the dynamic nature of operands. The length then is used to be added to the IP to grab the next appropriate opcode.


## Interpreter

For the interpreter, i it will take in the result_info given by the parser, and it executes exec_parsed, which identifies the opcode, then passes the operands to the according functions for that specific operation.

![[image-166.png]]

(I know, this is so messy, and probably breaks 10 different programming standards)

Basically, after recognizing the opcode from the result_info, we pass the operands to the corresponding functions to handle the logic. Something else to note, since there are different types of operands (Immediate, register, register high, register low, memory), i also created a function that detects the operand type based on the string given, and depending on the type, the operator function's logic can handle the operand accordingly

![[image-167.png]]


## Syscalls

The syscalls are for the `int` operations, since for this project, there are only several syscalls implemented, i only implemented the syscalls required for 1.c - 6.c

