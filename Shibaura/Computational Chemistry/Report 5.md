Rafael Zefanya Jaya Surya
Z125075

1. Proof

- $\mu=-\int dr \rho(r)r+\sum_{A}Z_{A}R_{A}$

First of all, we know that 
$\rho(r) = \sum_{\mu v}^{M}P_{\mu v}\chi_{\mu}(r)\chi^{*}_{v}(r)$

We got this from substituting the LCAO approximation into the total charge density formula., where $P_{\mu v}$ is the density matrix

We can substitute the electron density into the initial equation

- $\mu=-\int dr \left[ \sum_{\mu v}P_{\mu v}\chi_{\mu}(r)\chi_{v}^{*}(r) \right]r +\sum_{A}Z_{A}R_{A}$

since $P_{\mu v}$ doesn't depend on r, we can pull it out of the integral

- $\mu = -\sum_{\mu v}P_{\mu v}\int dr \chi_{\mu}(r)\chi_{v}^{*}(r)r + \sum_{A}Z_{A}R_{A}$

And, we know that $\bra{v}r\ket{\mu} = \int dr \chi^{*}_{v}(r)r \chi_{\mu}(r)$, so we can substitute that in

- $\mu = - \sum_{\mu v}P_{\mu v}\bra{v}x\ket{\mu}+\sum_{A}Z_{A}R_{A}$

Q.E.D


2. Express spin density

We can define the electron densities for both $\alpha$ and $\beta$ spin electrons as:

$$
\rho^{\alpha}(r) = \sum_{i=1}^{N_{a}}|\varphi_{i}^{\alpha}(r)|^{2}
$$
$$
\rho^{\beta}(r) = \sum_{i=1}^{N_{\beta}}|\varphi_{i}^{\beta}(r)|^{2}
$$
Now, since $N_{\alpha} > N_{\beta}$, we know that all the $\beta$ spin orbitals are all doubly occupied, up until it reaches the orbital with only $\alpha$ spin electrons, we also know that spin density is expressed as $\rho^{s}(r) = \rho^{\alpha}(r) - \rho^{\beta}(r)$. So, we can express them as this:

$$
\rho^{s}(r) = \left[ \sum_{i=1}^{N_{\beta}} |\varphi_{i}^{\alpha}(r)|^{2}+ \sum_{i=N_{\beta}+1}^{N_{\alpha}}|\varphi_{i}^{\alpha}(r)|^{2} \right] - \sum_{i=1}^{N_{\beta}}|\varphi_{i}^{\beta}(r)|^{2}
$$

for the alpha orbitals, i split them out, one part we sum up from 1 up to $\beta$ spin electron's number, and the other continues from there up until $\alpha$ spin electron's number. This way, since $\varphi^{\alpha}$ and $\varphi^{\beta}$ are the same according to ROHF, we can cancel two terms out, so we end up with this expression

$$
\rho^{s}(r) = \sum_{i=N_{\beta}+1}^{N_{\alpha}}|\varphi_{i}^{\alpha}(r)|^{2}
$$

The fact that we can cancel out the two terms solidify that doubly occupied orbitals don't contribute to spin density, we only need to calculate the density for the singly occupied $\alpha$ spin orbitals, which starts from $N_{\beta}+1$ up until $N_{\alpha}$ (in this case since $N_{\alpha}$ > $N_{\beta}$)

3. Summarize each atomic charges

These are the natural Charges of each atom accross the board with NBO and Mulliken and two different basis sets

| Atom | NBO (6-31G*) | NBO (6-31+G*) | Mulliken (6-31G*) | Mulliken(6-31+G*) |
| ---- | ------------ | ------------- | ----------------- | ----------------- |
| C    | 0.33193      | 0.33547       | 0.134642          | 0.078075          |
| O    | -0.57767     | -0.59315      | -0.415739         | -0.389353         |
| H1   | 0.12287      | 0.12884       | 0.140549          | 0.155639          |
| H2   | 0.12287      | 0.12884       | 0.140549          | 0.155639          |

Accross NBO and Mulliken, and all the basis sets, these all agree to the relative electronegativeness.
We see accross the board Oxygen is the most electrically rich. According to the pauling scale, oxygen has electronegativity value of 3.44, Hydrogen is 2.20, and Carbon is 2.55
So Oxygen should attract the most electrons in the chemical bond of Formaldehyde, which is exactly what we're seeing, Oxygen has negative charge across the board.
But wait a second, in pauli's scale, carbon has electronegativity of 2.55, more than hydrogen which is 2.20, how come C is more positively charged than the two Hydrogens?
This is because, both hydrogens are connected to C and C alone is double bonded to O,

![[image-27.png|289x251]]

The fact that C is connected to O (with high electronegativity), and it's double bonded, causes C to lose alot of electrons, making it positively charged. Meanwhile for both Hydrogen, they're singly bonded to C with smaller electronegativity than O, causing them to lose not as much electrons.

4. Do the computed charges change with the basis set

Yes, they do, if we compare the results of both NBO and Mullikens based on the two basis sets, they yield different results. I'll make a table that summarize the output difference between two base sets for NBO and Mulliken

| Atom | NBO     | Mulliken |
| ---- | ------- | -------- |
| C    | 0.00354 | 0.056567 |
| O    | 0.01548 | 0.026386 |
| H1   | 0.00597 | 0.01509  |
| H2   | 0.00597 | 0.01509  |

With this table, we can see that NBO's output is more stable accross 6-31G* and 6-31+G* basis sets compared to Mulliken. NBO's difference on average is < 0.01, while Mulliken's difference on average is > 0.02
This may be tied to the fact that Mulliken's population analysis utilizes a non-orthogonal basis function and it doesn't satisfy Pauli's exclusion principle. In short, with Mulliken, electrons are delocalized. While NBO represents atomic orbitals that are localized to each atom.


5. Natural Population

| Atom | Core    | Valence | Rydberg | Total   |
| ---- | ------- | ------- | ------- | ------- |
| C    | 1.99972 | 3.63146 | 0.03689 | 5.66807 |
| O    | 1.99972 | 6.55185 | 0.02601 | 8.57767 |
| H1   | 0       | 0.87489 | 0.00224 | 0.87713 |
| H2   | 0       | 0.87489 | 0.00224 | 0.87713 |

Let's analyze from the core, we can see that only C and O atom that contains electrons in the core atom. it should be the ($1s^{2}$) orbitals from both C and O. These electrons don't contribute the chemical bonding of the overall molecule, meanwhile both H doesn't have electron belonging in the core, meaning H contributes all of it's electron to the chemical bonding (well yeah since H only has 1 electron)

For valence, C is 3.6 which in theory should be 4, so it is according to lewis structure, C should have 4 valence electrons (2 electrons each bond to H, and the other 2 forms a double bond with O).
O has 6.5, in theory O has 6 valence electrons, and this is still according to lewis structure, O contributes 2 electrons to double bond with C, and has 2 lone pairs.
Same goes with H which has 0.87 electrons, in theory, H only has one electron that contributes to bonding. 
What's interesting is that, O has around 0.55 extra electrons which assumingly is gained from C and H, and this corresponds to the negative charge we saw above, with the case of C and H, C lost around 0.4 electrons, and H lost around 0.2 electrons, both also correspond to the positive charge we saw the table above. 
The rydberg orbital is typically unoccupied, only there to accomodate things like hypervalence, excited state etc, which explains why the values are so small in rydberg's orbital for all atoms.
If we total up all the electrons from the table, it sums up to 16, so it sums up perfectly to the total amount of electrons in formaldehyde.


6. Bond type, order, and hybridization of each bond

These are the results for bonding orbitals based on NBO

![[image-28.png|523x411]]

Let's look at the double bond between C = O first.
Because it is a double bond, we have two BD orbitals between C = O.
For BD(1), we can see that from both C and O, the bond is formed from almost purely p orbital (> 99%). while BD(2), we can see it's a bond from $sp^{2}$ hybrid for C atom, and more or less $sp$ hybrid for O atom.
We know that $sp_{2}$ hybridization orbitals will make $\sigma$ bonding, so BD(2) results in $\sigma$ bonding.
For BD(2), since it is a pure p orbital, and we know there is already a sigma bonding formed, and we can imagine the p orbitals are perpendicular to the formed $\sigma$ bond, so the perpendicular p orbitals will form $\pi$ bonding.
So in summary, C = O bonding consists of $\sigma$ + $\pi$ bond.
Since we can see for both bonds of C=O, they're basically fully occupied, assuming no electrons in antibonding orbital, we can immediately tell the bonding order by the number of bonds.
(C = O)Bond order = (Num of electrons) / 2 = 2

For both C-H bonds, we can see that that it's formed by an overlap of C's $sp^{2}$ hybrid orbital (we can tell because s contributes around 30 percent, and p contributes around 60 percent, around 1:2 ratio), and H's only s orbital contribution.
since we can tell it's a head on overlap between $sp^{2}$ and $s$ orbitals, and only one bond between C and H, we know that both C-H bond is of $\sigma$ bond.
Same case with C=O, since we can see both C-H bonds are basically fully occupied, we can assume there's no antibonding electrons, thus we can immediately tell that bond order of C-H is
(C - H)Bond order = (Num of electrons in bond) / 2 = 1

I can say that yes, the NBO matches our chemical intuition. Based on our theory, and from looking at the lewis structure of formaldehyde. We expect things like C = O forms a double bond of $\sigma$ and $\pi$ bonding, and C hybridization should be of $sp^{2}$, and the result of the NBO matches those intuitions. We should also see two lone pairs that belongs to O, and NBO also shows this result.

![[image-29.png]]

to find out whether they are basis set dependent, let's compare it to 6-31+G*'s result.

6-31+G* NBO analysis result

![[image-30.png|549x487]]

The output of the 6-31+G* is more or less the same, C = O still forms a double bond of $\sigma$ and $\pi$ bond, C-H is formed from $sp^{2}$ hybridization. So this shouldn't be basis set dependent.


7. NBO and Canonical Molecular orbitals

I'll show the orbitals from NBO that's drastically different from HF's Canonical orbitals (which usually is the bonding orbitals since the difference between NBO and HF is more apparent in the valence region)

**NBO's Orbitals**
![[image-31.png|313x292]]

![[image-32.png|317x316]]

![[image-33.png|322x348]]

![[image-34.png|326x310]]

These three visualizations from NBO's orbital highlight the difference between NBO and HF's orbitals. The first two images show the bonding orbital between C and H atoms, with the small red region i'm assuming is the antibonding orbital.
The third region seems to be showing the Lone Pair electrons that's surrounding O.
The fourth orbital seems to be the showing the bonding orbital between O and C atoms.
Let's compare these with HF's canonical orbitals

**HF Canonical MO visualization**

![[image-35.png|333x373]]

![[image-36.png|335x362]]

![[image-37.png|334x429]]

![[image-38.png|343x356]]

These are the visualization from HF's canonical orbitals. The main difference we can see between them is that some of the HF's orbital appear to be **delocalized**, the orbitals don't belong to one or two atoms. For example if we see the second image, we can see that it appears to visualize the bonding orbital of two of the H atoms with C simultaneously. Another point of difference is that HF's orbitals **energy ordered**. which is why the order of which we find the core orbital in HF and NBO is different, even though the core orbitals between HF and NBO shouldn't change.



**NBO**
Advantages:
As we know, NBO directly solves one of HF's disadvantages which is that HF doesn't represent lewis structures, because electron density is localized to 1 or two atoms unlike HF canonical orbitals which is delocalized. 
So in several orbitals, we can directly see the visualization of bonding formed, like bonding between C=O and C-H, so it's a better visualization when it comes to bonding between atoms. 
Disadvantages:
However, because NBO forces localization, it can obscure delocalization effects when it's important. And NBO is also more computationally heavy compared to HF, because of the fact that NBO introduces non-orthogonality. NBO is also great for visualization for students, because it respects the lewis structure, it should be more familiar for students since students most likely learn lewis structures for molecule bond structures.


**Hartree Fock Canonical Molecular Orbitals**
Advantages:
HF gives a direct solution within HF approximation, so HF canonical orbitals show the actual quantum mechanical energy. Compared to NBO, HF is not as computationally heavy to perform, and turns out HF canonical orbitals is the standard output of most programs including IqMol. HF also reflects the true symmetry of the molecule orbitals, as we have learnt in the previous session of symmetrical operations on MO, we used HF canonical orbitals instead of NBO.
Disadvantages:
However, as discussed before, HF doesn't correspond to bonds, lone pairs, or lewis structure, and because HF is delocalized, it can be harder for larger molecules, the orbitals can be hard to tell since it can spread everywhere. And compared to NBO, HF Canonical orbital isn't familiar, since most students would have learnt about lewis structures when it comes to bonding in molecules.