
Rafael Zefanya Jaya Surya
Z125075

## Q1

In the case of "taken",  in the original RISC-V pipeline, the instruction that needs to be executed would have been fetched in clock cycle 5.

Let's look at this step by step:

- CC1: 'beq' instruction fetched
- CC2: 'beq' in ID (because we assume no branch is taken, the next instruction is fetched, which is the wrong instruction)
- CC3: 'beq' in EX (another wrong instruction is fetched)
- CC4: 'beq' in MEM (Decision is made) (Another wrong instruction fetched)
- CC5: Branch target then finally fetched

Since the next instruction is first taken at CC2 then the delay would be:
CC5 - CC2 = 3 clock cycles

## Q2

If we use the technique of moving up the branch decision and branch adder to ID, we would significantly decrease the delay. Let's analyze this step by step

- CC1: 'beq' instruction fetched
- CC2: 'beq' in ID (**Branch decision made**, wrong instruction fetched)
- CC3: Branch target is fetched!

When the branch is taken, the fetch would occur on the third clock cycle, and the delay would be:
CC3 - CC2 = 1 Clock cycle
This immediately shows a significant improvement compared to the previous technique. However this approach has some difficulties, like having to add new forwarding logic since forwarding the operand of branches was initially handled by the ALU forwarding logic.
Also, the value we need to compare in ID may be dependent on previous instructions, which hasn't been produced yet, causing data hazard, which means we would need to stall, because we can't do forwarding, since we need the value very early on in the ID stage, the value wouldn't have been finished producing from the previous instruction.


## Q3

The best case is to be able to fetch the instruction needed after beq at CC2, regardless of whether the branch is taken or not.

There are many researches and many approaches that have tried to solve this dilemma.
Including:

### Dynamic Branch Prediction
With this approach, the hardware will try to predict the branch's outcome before it's computed. It makes the decision based on the **runtime behavior**, it will learn from what the branch did in the past, and tries to predict what it will do in the future.
If the prediction is correct, then there will be no penalty and the next instruction will be able to be fetched at CC2, but if the prediction is wrong, we will need to flush the registers. 

We use two bits that represent the decision making of the model. 
(11 = strongly taken, 10 = weakly taken, 01 = weakly not taken, 00 = strongly not taken), with the hierarchy sorted as how i listed them out.
We will start at a certain state of the counter, and based on the result of the prediction, will go up (towards strongly taken), or go down (towards strongly not taken).

This is extremely effective for loops in programs, since loops are usually done in multiple concurrent times, the program would be encouraged to predict the "taken" state in loops, which would be true up until the end of the loop when it ends.
This technique would essentially make loops have over 90% accuracy in predicting the branch decisions.

Source:
Smith, J.E. (1981). "A Study of Branch Prediction Strategies"  
Proceedings of the 8th Annual International Symposium on Computer Architecture (ISCA), pp. 135-148

### Branch Target Buffer 

Branch target buffer aims to solve a problem even when we have perfect branch prediction. Imagine we can perfectly predict whether the next branch will be taken or not, the problem with this, is we still need to decode where the branch would go (Calculating the branch address), this problem was previously fixed by moving it up to the ID stage, this means we still cannot guarantee to fetch the next instruction in CC2.

BTB aims to solve this, by utilizing a sort of table that stores entries. Each entry has five attributes: PC (Tag), Target address, prediction (Can be taken from dynamic branch prediction which i explained before), Valid, Type.

PC is the address of the branch instruction itself, Target address is the branch goes if taken, prediction is a 2 bit counter similar to the dynamic branch prediction method i said before, Valid is a bool value that explains whether this entry is valid or not, and type is the branch type (BEQ, JAL, BNE, etc). 


How it works:
- Send PC to IF (Instruction Fetch), and BTB (To check if it's a branch or not, if it is, save in entry with the attributes explained above)
- Since it is the first time seeing this branch and it is just put in the entry, so we most likely have to flush if branch is taken (BTB miss essentially). The branch is executed normally, and the branch address is also saved in the entry
- Next time another branch instruction is found, we look up the BTB and compare the PC with all tags, if found => Hit (We read the target address as well as the prediction), if miss => we have to flush


This approach is akin to caching, but contains PC, branch prediction, and target, allowing the possibility to instruction fetch at CC2 for both taken and not taken situation, since both the prediction and the branch target address is stored in the BTB.

Source:
Lee, J.K.F. and Smith, A.J. (1984). "Branch Prediction Strategies and Branch Target Buffer Design"
IEEE Computer, vol. 17, no. 1, pp. 6-22