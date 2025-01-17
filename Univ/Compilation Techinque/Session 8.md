
# Bottom Up Parser

Starts with string input

Example:
$$
E \to E + T|T
$$
$$
T \to T*F | F
$$
$$
T \to (E)|id
$$

step by step (Pre-processing):
1. Make sure in one grammar only produces one result
2. Add the augmented grammar
3. Give numbers to all grammars
4. Add . (dot) to each beginning of the production result

==Kernel: Productions with dot at the start of the production result==
==Non-kernel: Productions with dot at the end of the production result==
==So we want to convert from kernel to non-kernel==
Next: <u>Go to operation</u>
1. For each production, if the dot is followed by a non-terminal, we have to check the productions (Start with the starting production):
	1. Take the productions whose producer is the non-terminal that followed the dot
	2. Do the same until you can't take the other ones anymore
2. Now for each of the productions you have put down, give inputs for each production possible to move the dot
3. If the resulting input has a dot that is followed by a non-terminal, do the same thing for step number 1
4. Do it again

<u>SLR () Table</u>

For the row -> We take the number of input groups in Go To operation
Column -> Terminal, Non-terminal

yeah bruh gl future me