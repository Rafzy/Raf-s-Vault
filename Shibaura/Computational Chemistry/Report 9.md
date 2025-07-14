Rafael Zefanya Jaya Surya
Z125075


## Biphenyl

![[image-87.png|596x330]]

Transition with strength > 0.1:
**From .out file**
Excited state 8
excitation energy: 5.7823
Oscillator strength: 0.5881856949
Dominant orbitals: D(41) -> V(1) Amplitude: 0.9564
Multiplicity: Singlet

Main orbitals involved in the lowest triplet energy
![[image-88.png|499x139]]

Most dominant: D(41) --> V(1) amplitude = 0.8474
Plot:
Alpha 41 (HOMO) orbital:
![[image-89.png|491x266]]

Seems to be a bonding $\pi$ orbital, there are several C-C bonds with the same signs.

Alpha 42 (LUMO) orbital:
![[image-90.png|496x280]]
 
This seems to be an antibonding $\pi^{*}$ orbital, there are nodes between carbon atoms.

Since for the tripled excited state, the electron jumps from Alpha 41 to Alpha 42, the Alpha will lose some electrons, and since there there are carbon atoms that are in phase with each other, creating a bonding orbital, carbons with the same phase will weaken the bond, thus lengthening.
Looking at the other side, Alpha 42 will gain electron, and since this is an antibonding orbital observed by differing signs between carbon bonds, will cause it to further weaken the bond, thus further lengthening the bonds between carbon atoms with different signs.

**Geometry optimization for triplet**
First thing we noticed is that the structure became planar, instead of a non planar structure. 
![[image-91.png]]

We can also observe that our guess before was correct, the bonding between atoms became longer than that of the optimized singlet structure. This can be explained by observing the singlet structure's HOMO orbital, each phase of the orbital kind of spirals around the structure, which would explain why this molecule would have a non-planar structure to it. Meanwhile, the LUMO orbital doesn't exhibit that property.

Triplet:
![[image-92.png|458x261]]

Singlet:
![[image-93.png|458x273]]

For example, the bond between these two atom bonds became longer by around 0.07 Angstrom

Singlet energy at optimized triplet energy: -463.01296690

## Naphthelene

![[image-94.png|479x312]]

Transition with strength > 0.1:
**From a.out file**
Excited state 7
Excitation energy: 5.1907
Oscillation strength: 0.1052894505
Dominant orbitals: D(34) -> V(1) amplitude: 0.9286
Multiplicity: singlet

Excited state 9
Excitation energy: 6.9303
Oscillation strength: 2.0213810885
Dominant orbitals: D(34) -> V(2) amplitude: 0.6919
Multiplicity: singlet

Excited state 10
Excitation energy: 7.1270
Oscillation strength: 0.3857387817
Dominant orbitals: D(33) -> V(2) amplitude 0.8961
Multiplicity: singlet

Main orbitals involved in the lowest triple energy:
![[image-95.png|569x130]]

Most dominant: D(34) -> V(1) amplitude = 0.9420
Plot:
Alpha 34 (HOMO)
![[image-96.png|460x350]]

Here, we can see that this is a bonding$\pi$ orbital, adjacent C bonding create bonding orbitals, dibided into several orbitals of the structure.

Alpha 35 (LUMO)
![[image-97.png|463x344]]

For LUMO, we can see that this is bonding forms an antibonding $\pi^{*}$ orbital, we can see nodes between C bondings, except for the two leftmost and rightmost C pair.

So, from what we can see, my prediction is that the general bonding length will lengthen when transitioning into an excited triplet state, same case with biphenyl, however we might see mixed effects for the peripheral C-C bond in the middle, because there's no apparent change that might happen between HOMO and LUMO as of now.


**Geometry optimization for triplet**
![[image-98.png|402x272]]

By the naked eye, there doesn't seem to be much change, but if we analyze the length of the C bonds, we can see that the triplet structure has longer bonds

Triplet:
![[image-100.png|510x360]]

Singlet:
![[image-101.png|503x403]]

As we can see, for the C bonds it's longer for the triplet state compared to the singlet state by around 0.07 angstrom. proving the previous prediction. Now, let's examine the C bond in the middle to see the effect, since i couldn't make a clear prediction before

Triplet:
![[image-102.png|506x368]]

Singlet:
![[image-103.png|509x381]]

So it seems that the C-C bond in the middle also increases in length, but not as drastic as the other C-C bonds

Single point energy for triplet structure: -385.64927511

## Pyrene

![[image-104.png|479x365]]

Transitions with strength > 0.1
**From a.out**
Excited state 7
excitation energy: 4.4176
Oscillator strength: 0.4188466109
Dominant orbital: D(53) -> V(1) amplitude = 0.9096
Multiplicity: singlet

Excited state 10
excitation energy: 5.6549
Oscillator strength: 0.6067996962
Dominant orbital: D(52) -> V(1) amplitude = 0.6751
Multiplicity: singlet

Main orbitals involved in the lowest triple energy:
![[image-105.png|586x116]]

Most dominant: D(53) -> V(1) amplitude: 0.9427
Plot:
Alpha 53 (HOMO)
![[image-106.png|515x463]]

This seems to be also a bonding $\pi$ orbital, we can see that there the Molecular orbital is comprised of in phase orbitals that surrounds most of the bond between C atoms.

Alpha 54 (LUMO)
![[image-107.png|519x394]]

For the LUMO orbital, we can see that it's a antibonding $\pi^{*}$ orbital, since we can see a lot more nodes in between most of the C bondings.

So my prediction is the same as before, because the electrons move from HOMO, a bonding MO, to LUMO, an antibonding MO, the length of the bonds would generally lengthen.

**Geometry optimization for triplet**
![[image-108.png|532x422]]

Same with naphthelene, the geometry optimization for the triplet structure doesn't seem to change to the naked eye. But we can observe the exact change in length between triplet structure and singlet structure

Triplet:
![[image-109.png|423x304]]

Singlet
![[image-111.png|425x315]]

As we can see, for the two C atom bond, it grows longer for the triplet structure compared to the singlet.

Singlet energy at optimized triplet energy: -615.39879622


## Answers for questions

1. Result tables

Optimized energies

| Energies                  | Biphenyl      | Naphthalene   | Pyrene        |
| ------------------------- | ------------- | ------------- | ------------- |
| Singlet                   | -463.04049661 | -385.66834379 | -615.41644366 |
| Triplet                   | -462.91834876 | -385.56177608 | -615.33410840 |
| Singlet energy at triplet | -463.01296690 | -385.64927511 | -615.39879622 |

Nuclear repulsion

| Energies                  | Biphenyl     | Naphthalene  | Pyrene       |
| ------------------------- | ------------ | ------------ | ------------ |
| Singlet                   | 599.17351703 | 457.42431267 | 966.04381800 |
| Triplet                   | 595.34834823 | 453.93939959 | 962.75448116 |
| Singlet energy at triplet | 595.34834043 | 453.93940286 | 962.75447983 |

eV table

| Molecule    | Energy (eV) | Oscillator strength | Configuration |
| ----------- | ----------- | ------------------- | ------------- |
| Biphenyl    | 5.7823      | 0.5881856949        | D(41) -> V(1) |
| Naphthalene | 5.1907      | 0.1052894505        | D(34) -> V(1) |
| Naphthalene | 6.9303      | 2.0213810885        | D(34) -> V(2) |
| Naphthalene | 7.1270      | 0.3857387817        | D(33) -> V(2) |
| Pyrene      | 4.4176      | 0.4188466109        | D(53) -> V(1) |
| Pyrene      | 5.6549      | 0.6067996962        | D(52) ->V(1)  |

2. Why are all the bright transitions singlets?

Because of selection rules for transitions, for electric dipole transitions, total spin quantum numbers cannot change. Since we calculated TDA from an optimized singlet structure of the three molecules, the transitions would be (singlet -> singlet).
For example, it's not allowed for transitions to change from zero spin quantum to one spin quantum (singlet -> triplet)

3. phosphorescence from the lowest triplet to the ground state

To predict the phosphorescence from lowest triplet to ground state, i'll subtract the energy at the triplet geometry with the single point energy at triplet geometry.
The reason we get this is because the prediction is:
$T_{1} \to S_{0}^{T} + photon$
What i mean is, the energy for the optimized triplet geometry, is the product of the single point energy at that geometry + photon

with that, we'll get this result

| Molecule    | Phosphorescence energy |
| ----------- | ---------------------- |
| Biphenyl    | 2.57 eV                |
| Naphthalene | 2.38 eV                |
| Pyrene      | 1.76 eV                |

4. Geometric effects from singlet to triplet
I've answered this in the lab report above, but to summarize, all three molecules result in the bond length increasing, going from singlet to triplet structures. Pictures are also included above.

5. What is the magnitude of Stokes shift
We can calculate the stokes shift by subtracting the absorption energy with the emission energy (Phosphorescence energy). Stoke shift represents the energy loss between absorption and emission. So we can immediately calculate stoke shift with what we have

Biphenyl: 5.7823 - 2.57 = 3.21 eV
Naphthalene: 5.1907 - 2.38 = 2.81 eV
Pyrene: 4.4176 - 1.76 = 2.66 eV