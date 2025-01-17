# Naive Bayes

$$
P(A|B) = \frac{P(B|A).P(A)}{P(B)}
$$

| word       | Normal = $\frac{5}{10}$ | Cheat = $\frac{5}{10}$ |
| ---------- | ----------------------- | ---------------------- |
| on         | 3 + 1                   | 6 + 1                  |
| conclusion | 2 + 1                   | 10 + 1                 |
| there      | 8 + 1                   | 2 + 1                  |
| in         | 7 + 1                   | 2 + 1                  |
| good       | 5 + 1                   | 0 + 1                  |
| total      | 30                      | 25                     |

$$
P(N | conc.good.conc)
$$
$$
= P(N).P(cgc|N) = \frac{5}{10}. \frac{3}{30} . \frac{6}{30} . \frac{3}{30} = \frac{2}{3125} = 0.00064
$$


$$
P(C|'cgc') 
$$
$$
= P(C) . P('cgc' | C) = \frac{5}{10}. \frac{11}{25} . \frac{1}{25}. \frac{11}{25} = 0.003872
$$



# Contingency Table

**F1 Score**
$$
F_{1} = \frac{2.P.R}{P+R}
$$
P = Precision
R = Recall

**Precision**
$$
P = \frac{TP}{TP+FP}
$$

**Recall**
$$
R = \frac{TP}{TP+FFN}
$$

## More than two classes

confusion matrix for three-class categorization task

