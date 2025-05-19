
# BrainFuck

> Esoteric programming language, notable for it's extreme minimism, only consists of eight simple commands and an instruction pointer while being **Turing Complete**.

==Implementing Brainfuck is a good practice to know what is an interpreter==


**Turing Machine**
- Operates infinite memory tape which is divided into cells
- Positions it's head over a cell and execute read/write operation
- Stops when the state changes to terminate

**Brainfuck** aims to imitate the turing machine

Instructions in BF machine:
- + -> Increment value
- - -> Decrement value
- > -> Move head to the right
- < -> Move head to the left
- \[ -> Begin of a loop, if value pointed by head equals 0, jump right next to the end of loop (Instruction after the end of loop)
- \] -> End of a loop
- . -> Shows a number pointed by the head as an ascii character
- . -> Read from stdin and store it as a number to the memory pointer by the head
