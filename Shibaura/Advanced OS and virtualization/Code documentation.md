Welcome to my spaghetti code

# Introduction

This is a documentation for my code of Minix's X86 instruction set interpreter. For disclaimer, i am an undergraduate that's taking this class, and i did my best to implement the interpreter, although my interpreter worked for 1.c - 6.c, i recognize that my code is a mess and that there are a lot of things that can be improved.

Github for my code:
https://github.com/Rafzy/Minix

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

As you can see, init_cpu()
