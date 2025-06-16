# Mechanism of Addition and Subtraction

- Signed and unsigned numbers (Two's complement)
- How is "addition" conducted in CPU

## Signed numbers

> How does binary handle positive and negative integers?

1 is expressed as:
`0000 0001`

How about -1?
We can't just write it as
`-0000 0001` -> This is wrong

==Determining the sign requires an extra step== -> Using Two's Complement


## Two's Complement

Definition: 
$$
x_{e} = 2^{n} - x
$$

In negative numbers
- MSB = 1
- Decreases by 1 binary

An easier way to find two's complement:
- Flip all bits
- Add 1

Two's complement -> Finding numbers that have the same "absolute value" but different signs

But, if that's the case:
`1111 1111`
can be calculated as both -1, and 255.
So, the CPU needs to differentiate between when we want to define an unsigned and signed numbers.
And it does that, by **instruction**.

An event called overflow can occur if positive + positive = negative, and negative + negative = positive

Some CPU have a special hardware to detect an overflow (Overflow flag)
however, RISC-V CPUs do not provide this, because the software can detect overflow using existing instructions


## Addition: How is it caluclated in CPU?

Full adder -> Takes three inputs (1 bit from A, 1 bit from B, Carry from immediate below bit), outputs 2 (1 bit sum, carry immediate above bit)

