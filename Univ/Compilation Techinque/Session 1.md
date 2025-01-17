#compilationtechnique
# Compilation Technique


**Compilers**
-> Translates source code into machine code (The only language our machine understands).
-> Detects any errors in our source code whether it contains any fundamental errors (Usually syntax wise)
-> Compilers translates the source code all of them all at once
-> ex: C/C++ , Java

**Interpreters**
-> Translates line by line
-> Ex: Python, Javascript, PHP

<u>Stages of Compilation</u>
Source Program -> [[Lexical analyzer]] -> Syntax Analyzer -> Scematic analyzer -> Intermediate Code generator -> Code optimizers -> Code generator -> <u>Target Program</u>


**RE (Regular Expression)**
-> Expression for language that can be recognized by [[Finite Automata]]
-> Examples:
- $\varepsilon \to \{ \varepsilon \}$
- $a$  $\epsilon$  $\Sigma$, a: RE -> $\{ a \}$
- $(0+1)^{*}$ -> Kleere closure, $a^*=\{ \varepsilon, a, aa, aaa, \dots  \}$
- $(0+1)^+$ -> Positive closure, $a^{+}=\{ a,aa,aaa,\dots \}$a
- $(0+1)^?$ -> Questioni closure, $a^{?}=\{ \varepsilon, a \}$


**Exercise:**
- The set of strings over alphabet $\{ a, b,c \}$, where there is at least one a and one b
	Ans:
	$((a|b|c)^*a(a|b|c)^*b(a|b|c)^{*}|(a|b|c)^*b(a|b|c)^*a(a|b|c)^*)$


