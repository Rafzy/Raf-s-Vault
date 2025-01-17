

# Lexical Analysis

> Converts RE -> DFA Directly

Example : (a|b) * a

1. Augmented RE -> Add #
	(a | b) * a #
2. Syntax tree
	Create a tree consisting of the syntax

![[Drawing 2024-09-23 13.42.25.excalidraw]]


3. Nullable (Whether the node can return a null or not) , firstpos (Give number for all the leaves from the left to right) , lastpos

![[Drawing 2024-09-23 13.50.03.excalidraw]]

![[firstpost-lastpost.excalidraw]]

4. Follopos
	How many follopos we need is the same as the number of leaves.
	Two algorithms we need to know to determine follopos:
	1. If n is (concatenation)-node with lc ($c_{1}$) and rc ($c_{2}$) and i is a position in lastpos $c_{1}$, then all position in firstpos $c_{2}$ are in follopos(i)
	2. If n is a star node (n) and i is a position in lastpos(n), then all position in firstpos(n) are in follopos(i)

5. Create DFA
	$So$ = firstpos(root) = {1, 2, 3}
	$S_{1}$ = {1, 2, 3, 4}
	If the state contains a leaf that's the hashtag, that means it's the last state

| state | a            | b   |
| ----- | ------------ | --- |
| So    | {1, 2, 3, 4} | So  |
| S1*   | S1           | So  |

![[REtoDFA.excalidraw]]




## Second way

1. Augmented RE
	(a|b) * a#
2. Add concatenation
	(a|b) * . a . #
3. Add numbers
	(a | b) * . a . #
	 1    2       3   4
4. Follopos
	Follopos 1: {1, 2, 3}
	Follopos 2: {1, 2, 3}
	Follopos 3: {4}
	Follopos 4: -
5. Syntax tree

![[Drawing 2024-09-23 13.42.25.excalidraw]]

6. Nullable, firstpos, lastpos
7. DFA



