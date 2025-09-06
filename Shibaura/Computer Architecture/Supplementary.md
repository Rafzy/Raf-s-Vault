
# Control Hazards

Control hazards happen in branches. 
When there's a possible branch is about to happen, we can't know until the decision whether to branch is decided in the MEM pipeline stage.
This messes up the continuous instruction fetch that happens in pipelining, since we don't really know whether the branch will happen or not.

There's currently no solution for control hazard that's as effective as forwarding is against data hazards. So we use simpler schemes.

## Assume branch not taken

One approach we can do to handle control hazard is to **predict** that the conditional branch will not be taken, thus just to continue the execution down the instruction stream.
If the branch turns out to be taken, the instruction that is being fetched and decoded must be discarded, and execution starts at the branch target.
To discard functions, we merely change the original control values to 0.
This means we must be able to **flush** instructions in the IF, ID, and EX stages of the pipeline


## Reducing delay of branches

Another way to improve conditional branch performance is to reduce the cost of the taken branch. 
So far we assumed the next PC for a branch is selected in the MEM stage, but if we move the conditional branch execution earlier in the pipeline, fewer instructions need to be flushed. 
We require two actions to occur earlier: computing the branch target address, and evaluating the branch decision.

Easy part of this change is to move up the branch address calculation.
We already have the PC value and the immediate field in the IF/ID pipeline register, so we just move the branch adder (which is a separate physical circuit from the other circuits) from the EX stage to the ID stage.
We can do this because the ID stage has the necessary values in order to execute the branch addition (PC value from IF/ID and the immediate value which we get after decoding the instruction).

The hard part is the branch decision itself.
For branch if equal, we would have to compare two register reads during the ID stage. Equality can be tested by XORing the individual bit position of two registers and ORing the XORed result (Zero output means two registers are equal).
Moving the branch test to the ID stage implies additional forwarding and hazard detection software.
This is possible because register reading happens in the ID stage as well.

There are two complicating factors:
1. During ID we must decode the instruction, decide whether a bypass to the equality test is needed, and complete the equality test.
2. Because the value in a branch comparison is needed during ID but may be produced later in time, it's possible that a data hazard can occur, and a stall will be needed.

