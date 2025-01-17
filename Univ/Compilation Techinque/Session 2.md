#compilationtechnique 
# Lexical Analyzer

**Finite Automata**
-> <u>state</u> machine that takes a string of symbols as input, and it changes it's state according to the input
-> Types:
	- DFA = Deterministic
		- In DFA, each of the state given an input only leads to one other state
	- NFA = Non-deterministic
		- In NFA, given one input, a state can lead to two other states

Ex:
Define Regular Expression for tokens i, then convert them into DFA to get lexycal analyzers for our tokens
1. RE -> NFA -> DFA
2. RE -> DFA

**NFA/DFA**
M = $(Q, \Sigma, \sigma, q_{o}, F)$
$Q$ = Set of states
$\Sigma$ = set of input symbols
$\sigma$ = transition functions
$q_{o}$ = initial state
$F$ = final states 