Rafael Zefanya Jaya Surya
Z125075

1. Geometry Optimization of $CH_2O$

Molecular Formula: $CH_{2}O$
Charge: 0
Multiplicity: 1

Method: Hartree Fock
Basis: 6-31G*

Bond Length (Angstroms):

|      | C      |
| ---- | ------ |
| O    | 1.1844 |
| H(1) | 1.0916 |
| H(1) | 1.0916 |

Angles:
- C - O - H2: 122.15$\degree$
- C - O - H1: 122.15$\degree$
- C - H1 - H2: 115.69$\degree$

Nuclear repulsion energy: 31.312404 Hartree

How many $\alpha$ and $\beta$ electrons:
8 $\alpha$ and 8 $\beta$ electrons.

Since we have a closed shell system, the charge would be zero, all orbitals are doubly occupied, also meaning that the multiplicity is always 1.

Experimental:
- C = O: 1.23 Arngstrom
- C - O: 1.43 Arngstrom
    Reference: https://chem.libretexts.org/Bookshelves/Physical_and_Theoretical_Chemistry_Textbook_Maps/Supplemental_Modules_(Physical_and_Theoretical_Chemistry)/Chemical_Bonding/Fundamentals_of_Chemical_Bonding/Bond_Order_and_Lengths#:~:text=Referring%20to%20the%20table%20above,60%20+%2053%20=113%20pm.

- Formaldehyde C = O: 1.21 Arngstrom
	Reference: https://en.wikipedia.org/wiki/Formaldehyde

The difference between Single and Double experimental bond length: 0.20 Arngstrom
Difference between computed and experimental Formaldehyde C = O bond length: 0.0256 Arngstrom

**Can we tell if the optimized geometry corresponds to the true energy minimum?**
Finding the lowest energy minimum requires us to find the most optimized geometry, This is because from the last lecture, we know that the bond lengths and angles directly impacts the energy, with this graph roughly describing the change in energy

![[image.png|555x204]] 

This is because of the interaction between atoms, some atoms tend to repel each other, and some tends to attract each other. So finding the true energy minimum requires us to find the optimized geometry as well. But, optimizing the geometry doesn't always correspond to true energy minimum, since with isomers, we can have molecules with the same formula, but different structures, leading it to possess different chemical and structural properties, optimizing those geometries will lead it to have the lowest minimum energy **for that** structural form, but not the true energy minimum.
We also have to take into consideration the local minimum, if we're trying to optimize the geometry, it's possible to roll down to a local minimum energy.


2. Isomers of Formaldehyde

HCOH (cis)

![[image-1.png]]

Molecular formula: HCOH
Charge: 0
Multiplicity: 1

Method: Hartree Fock
Basis: 6-31G*

Bond length:

|      | C      | O      |
| ---- | ------ | ------ |
| C    | -      | 1.2997 |
| O    | 1.2997 | -      |
| H(1) | -      | 0.9507 |
| H(2) | 1.099  | -<br>  |

Angles:
C - O - H(2): 103.04$\degree$
C - O - H(1): 109.49$\degree$

Nuclear repulsion energy: 29.0809

**Bond length Formaldehyde vs Bond Length in hydroxycarbenes**

In formaldehyde: 1.1844 Arngstroms
In Hydroxycarbenes: 1.2997 Arngstroms

This matches the bonding pattern from the experimental, since in hydroxycarbenes, the CO bond is a single bond, it has less length with a difference of around 0.11 arngstroms. The double bond should be shorter than the single bonds.


**Does the optimized structure correspond to a minimum?**

No, the optimized structure of the isomer doesn't correlate to the true minimum, because of the arguments i gave earlier, we have to consider the isomer of the molecule, as well as the local minimums.


**Difference between isomer and formaldehyde**

My optimization found trans isomers. 
Difference in energy:
Formaldehyde: -113.86525
Trans-Hydroxycarbenes: -113.77125 

**Hydroxycarbenes cis**
Energy: -113.76014

Between cis and trans, the lowest is trans hydroxycarbenes.


4. Transition state of HCOH

The molecule has 1 imaginary frequency, which confirms that this is a transition state, local minimas should have zero frequency

![[image-2.png]]

This is what the transition state looks like, one hydrogen atom is out of plane, not having any symmetry.

I think with this transition, the product formed would be cis-HCOH from trans-HCOH. 

For the barrier of Energy, we can calculate by subtracting the energy of transition with the energy of trans HCOH

Transition energy: -113.7335
Trans HCOH energy: -113.7713

Energy barrier: -113.7713 - (-113.7335)
Total: -0.0378