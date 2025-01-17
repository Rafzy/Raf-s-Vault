
# Top Down Parsing

create LL(1) parsing task
First set -> Set of terminal symbol in string
Follow set -> Set of terminal symbol after the variable

E -> TE'
E' -> + TE' | $\epsilon$
T -> FT'
T' -> * FT' | $\epsilon$
F -> (E) | id

1. Free of left recursion and left factoring
2. Find the first
3. Find the follow, alogirthm:
	1. If S is tart variable, then $ is follow S
	2. if A -> $\alpha$ B $\beta$. all non-$\epsilon$ first $\beta$ is follow B
	3.  - if A -> $\alpha$ B, all follow A is follow B 
	    \- if A -> $\alpha$ B $\beta$ and first $\beta$ is $\epsilon$ -> all follow A is follow B
4. Create parsing table

