# Apriori

**Some buzzwords**
- K-itemset = Item sets containing K items
- Support(x) = Number of Frequency of x / $\frac{Freq}{All_{Transaction}}$
- Confidence(x, y) = probability of itemset x happens given itemset y
- Frequent Itemset = Itemset where supp > min supp
- Association Rules = Rule for association for each itemset
	Example:
	Freq itemset(A, B)
	Association Rules: A -> B (the possibility of item B given A) | B -> A
		Formula: $A \to B = \frac{Supp(A, B)}{Supp(A)}$


**Apriori**

>If an itemset is frequent, then all subsets are also frequent

Steps:
0. K = 1, min Supp
1. Count I-itemset support
2. Create $L_{k}$ (Frequent itemset)
3. Create $C_{k+1}$ (Candidate Itemset) from $L_{k}$

Example:

| Transaction ID | Items Purchased |
| -------------- | --------------- |
| T1             | I1, I2, I3      |
| T2             | I2, I5          |
| T3             | I4, I5          |
| T4             | I1, I2, I5      |
| T5             | I2, I3, I5      |


| Transaction ID | Min Supp |
| -------------- | -------- |
| I1             | 2        |
| I2             | 4        |
| I3             | 2        |
| I4             | 1        |
| I5             | 4        |
C1
Count the support for each Items, then discard the one that doesn't meet our minimum support (2)

| Transaction ID | Min Supp |
| -------------- | -------- |
| I1             | 2        |
| I2             | 4        |
| I3             | 2        |
| I5             | 4        |
L1

| Transaction ID | Min supp |
| -------------- | -------- |
| (I1, I2)       | 2        |
| (I1, I3)       | 1        |
| (I1, I5)       | 1        |
| (I2, I3)       | 2        |
| (I2, I5)       | 3        |
| (I3, I5)       | 1        |
C2
Then, we remove the ones that doesn't meet our minimum Support


| Transaction ID | Min supp |
| -------------- | -------- |
| (I1, I2)       | 2        |
| (I2, I3)       | 2        |
| (I2, I5)       | 3        |
L2

Note: To get (I1, I2, I3), we need (I1, I2), (I1, I3), and (I2, I3), because we can't create any more from there, we stop



# FP-Growth

**Steps**
1. Count I-itemset support
2. Sort item list in each transaction
3. Make FP-Tree
4. Make Conditional pattern base
5. Make Conditional Frequent Pattern

Example:
$L = {I_{2}, I_{5}, I_{1}, I_{3}, I_{4}}$ -> Sorted supports

| Transaction ID | items      |
| -------------- | ---------- |
| T1             | I2, I1, I3 |
| T2             | I2, I5     |
| T3             | I5, I4     |
| T4             | I2, I5, I1 |
| T5             | I2, I5, I3 |


# MID EXAM TOPICS

Every topic from session 1 - 7 basically

- Intro to data mining
- Data & Measurement (Data Type, Statistics)
- Data warehousing (OLTP vs OLAP, Schema)
- Data Preparation (All)
- Pattern Mining (Basically this session)