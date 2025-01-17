
# Contact Force Grammar

Type 2 CFG -> Chamsky
Left side => producer
right side => Variables, terminal symbols, closure -> (Called production)

Productions -> Specify the manner in which the terminals and non terminals can be confined to form the string

Possibly contains Ambiguous grammar -> 1 String has more than one string tree


RE to CFG

RE = $\epsilon$ => S -> $\epsilon$
RE = $0$ => S -> $0$
RE = a => S -> a
RE = ab => S -> ab

RE = $a^*$ => S -> aS | $\epsilon$  
RE = $a^+$ => S -> aS | a
RE = $a^?$ => S -> a | $\epsilon$

$RE = (ab|ba)^{*}(abb)^*$
assume:
$(ab|ba)^*$ -> R
$(abb)^*$ -> Q
so:
$S -> RQ$
$R\to XR|\epsilon$
$Q \to YQ | \epsilon$
$X \to ab|ba$
$Y \to abb$
P -> all productions above


## Types of Ambiguous Grammar

1. Left recursive
2. Right Factoring

**Left Recursive**
$A \to A \alpha$  -> Non-terminal that can be denied

- Immediate Left recursive
- Non-immediate left recursive

**How to eliminate left recursive**
$A \to A \alpha | \beta$

turn into:
$A \to \beta A'$
$A' \to \alpha A' | \epsilon$


**Left Factoring**

$A \to \alpha\beta_{1} | \alpha \beta_{2}$

**Eliminate by factoring**
$A \to \alpha A'$
$A' \to \beta_{1} | \beta_{2}$