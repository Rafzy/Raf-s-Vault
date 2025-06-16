Rafael Zefanya Jaya Surya
Z125075

1. What is the point group of CH2O?
	
	![[image-4.png|304x324]]
	
	If we analyze the Structure of $CH_{2}O$, we can see the structure has a trigonal planar structure. If we want to evaluate the point group, we need to examine the symmetrical operations applicable to this structure.
	
	First of all, we can immediately tell that this structure has two reflection operations, ($\sigma_{v}$ and $\sigma'_{v}$), we can imagine the first reflection cutting through the oxygen and carbon atom, making a symmetrical reflection from left and right. And the other reflection cuts laterally, going through all the atoms.
	
	Next, we can also tell that the molecule possesses a rotation symmetry, imagine the axis going through the oxygen and carbon atom right in the middle. And if we spin the molecule $180 \degree$, the shape is the same (symmetrical), so now we know it  also possesses $\hat{C}_{2}$ rotation, and $n = 2$ since we rotate it by $180 \degree$, and $360 \degree / n$.f
	
	And i think that's all for $CH_{2}O$'s symmetry operation, and referencing last lecture's ppt,
	![[image-1.png|394x137]]
	
	$CH_{2}O$ belongs in $C_{2v}$ point group

2. $CH_{2}O$ MO
	Manual Input File:
	![[image-3.png|317x246]]
	
	MO 1
	![[image-5.png|274x295]]
	
	The first orbital surrounds the Oxygen atom, the energy of this level is -20.585, and the symmetry for this orbital from the .out file is labelled $1A_{1}$, we can analyze the character table for $C_{2v}$ Point group to analyze the character  irreducible representation for $A_{1}$.
	
	![[C2v-character-table.png|496x147]]
	
	We can see that for $A_{1}$, The characters for all symmetry operation is 1, so it stays symmetrical under $E$, $C_{2}$, $\sigma_{v}$, and $\sigma_{v}'$ symmetry operations. We can also imagine this, since if we have an axis that goes through the orbital (The axis must go through the oxygen and carbon atom), it will stay the same, and mirroring the orbital will also cause it to still stay symmetrical (For both $\sigma_{v}$ and $\sigma'_{v}$)
	
	MO 2
	![[image-6.png|308x295]]
	
	The second orbital surrounds the C atom, The energy for this orbital is -11.344, the symmetry is also $A_{1}$, labelled as $2A_{1}$ in the output file, meaning this is also has the same orbital symmetry as the first orbital
	
	MO 3
	![[image-7.png|301x324]]
	
	For the third orbital, we can see it's a negative sign this time, surrounding the whole molecule. Same with the previous orbitals, this is also $A_{1}$ symmetry. Which we can also prove by just looking at the orbital itself, it stays negative when we do $C_{2}$ operation, as well as both reflection operations.
	
	MO 4
	![[image-8.png|308x321]]
	
	For MO 4, we can see it has positive sign orbital on top, and a bigger negative sign orbital in the bottom. The energy for this orbital is -0.866, and the symmetry is also $A_{1}$. If we have an axis that goes directly through the molecule vertically, we can see that $C_{2}$ operation retains the shape and sign of the orbitals. This is also true for both reflection operations.
	
	MO 5
	![[image-9.png|320x291]]
	
	For MO 5, we can see it has both positive and negative sign on the left and right side of the molecule. The energy of this molecule is -0.689, and the symmetry for this orbital is B1. B1 means we have anti-symmetry result for $\hat{C_{2}}$ and $\sigma_{v}'$ operations. We can visualize this by having a vertical axis right in the middle, and if we imagine turning it 180 degrees, the shape retains but the sign of the orbitals will swap. This also applies to the reflection operation, which can be easily visualized by flipping the image.
	
	Flipped image:
	![[image-12.png|333x301]]
	
	
	MO 6
	![[image-13.png|313x379]]
	
	For the 6th MO, we can see three orbitals, two negative and one positive in the middle, the energy for this orbital is -0.684, and the symmetry is $A_{1}$, retaining symmetry for all symmetrical operation. If we imagine rotating the orbitals by the y axis, it stays symmetrical, and goes for reflection operations as well.
	
	
	MO 7
	![[image-14.png|341x361]]
	
	For the 7th orbital, we can see there are two orbitals, one positive and one negative, located in the "Frontside" and "Backside" of the molecule, kind of surrounding it laterally. The energy for this orbital is -0.533, and the symmetry is $B_{2}$, which means the orbital results in anti-symmetry for $\hat{C_{2}}$ operation, and $\hat{\sigma_{v}}$ operation. This is a similar case with MO 5 where if we rotate the molecule by 180 degrees, the signs of the orbital will flip, as well as the reflection operator, just differing in the type of the reflection, because of the different positions of the orbital.
	
	
	MO 8 (HOMO)
	![[image-15.png|353x302]]
	
	For the last occupied orbital (HOMO), we can see it is an antibonding $\pi$ orbital, resulting in four orbitals, two positive and two negative. This orbital's energy level is -0.437, and has a symmetry of $B_{1}$, yielding antisymmetry for both $\hat{C_{2}}$ and ${\sigma_{v}'}$. We can visualize this by flipping the image/molecule.
	
	Flipped image:
	![[image-16.png|353x346]]
	
	When we rotate the molecule by 180 degree, we can see that the shape is the same, but the sign of the two orbitals on either side is flipped, resulting in antisymmetry. This is also true for the reflection operator as well.

3. Electronic configuration of $CH_{2}O$
	Configuration:
	$\ket{\Phi_{HF}} = \ket{[core] \phi_{3A_{1}}^{\alpha}\phi_{3A_{1}}^{\beta} \phi_{4A_{1}}^{\alpha} \phi_{4A_{1}} ^{\beta}\phi_{1B_{1}}^{\alpha}\phi_{1B_{1}}^{\beta} \phi_{5A_{1}}^{\alpha}\phi_{5A_{1}}^{\beta}\phi_{1B_{2}}^{\alpha}\phi_{1B_{2}}^{\beta}\phi_{2B_{1}}^{\alpha}\phi_{2B_{1}}^{\beta}}$ 
	
	The first two Molecular orbitals are considered core because it is formed by non-valence electrons (1s2 from Oxygen and 1s2 from carbon). And all orbitals are doubly occupied (we know since this is a singlet), so alpha and beta spins exist for all orbitals.
	
	Since we know that all orbitals are doubly occupied, and $CH_{2}O$ is closed shell, then we know all orbitals contribute $A_{1}$, since same irrep x same irrep = $A_{1}$. So, the overall symmetry of this molecule is $A_{1}$
	
4. Electronic configuration of $CH_{2}O^+$.
	Configuration:
	$\ket{\Phi_{HF}} = \ket{[core] \phi_{3A_{1}}^{\alpha}\phi_{3A_{1}}^{\beta} \phi_{4A_{1}}^{\alpha} \phi_{4A_{1}} ^{\beta}\phi_{1B_{1}}^{\alpha}\phi_{1B_{1}}^{\beta} \phi_{5A_{1}}^{\alpha}\phi_{5A_{1}}^{\beta}\phi_{1B_{2}}^{\alpha}\phi_{1B_{2}}^{\beta}\phi_{2B_{1}}^{\alpha}}$ 
	
	For $CH_{2}O^+$, we check the orbital for the HOMO first, since the HOMO is $2B_{1}$ orbital, we can remove 1 electron from that orbital for positively charged $CH_{2}O$.
	
	Now, for the HOMO since it is a singly occupied orbital, it will contribute $B_{1}$ to the overall symmetry, while the others still contribute $A_{1}$. If we multiply all of the contributing orbitals, we get an overall of $A_{1}$ ⊗ $B_{1}$, and consulting this table from the last lecture:
	
	![[image-17.png|350x183]]
	
	Then we get $B_{1}$ as the overall symmetry of the $CH_{2}O^+$ molecule.
	
	Koopman's theorem states that the potential energy of ionization is equal to the negative of the orbital energy being removed.
	$IP = -\epsilon$.
	The electron being ionized is from the HOMO, so if we check the orbital energy of HOMO which is -0.437, we can get the Ionization potential:
	$IP = - (-0.437) = 0.437$.

5. I'm not too sure, but since ionizing $CH_{2}O$ into $CH_{2}O^+$ involves removing the electron from the HOMO, and we know that the HOMO is antibonding, from the shape of the orbitals, then removing one electron should make the bond stronger. We know this because, antibonding is caused by Atomic Orbitals that form with differing signs, meaning a destructive interference, hence a weaker bond. So, the more electrons exist in this antibonding orbital, the weaker the bonding will be. If we were to remove one electron from ionization, we then **should** get a stronger bond, since we remove one electron from an orbital that causes the destructive interference. 
   So, from ionization of $CH_{2}O$, we should see the HOMO orbital's bond becoming stronger and shorter in length.

6. $IP[\Delta SCF] =E[CH_{2}O^{+}] - E[CH_{2}O]$
	Total energy of $CH_{2}O$: -113.86525396
	Total energy of $CH_{2}O^{+}$: -113.51898763
	
	$IP[\Delta SCF] = -113.51898763 - (-113.86525396)$
	$IP[\Delta SCF] = 0.34626633$

7. Koopman's theorem is derived from removing an orbital term from $\ket{\Phi}$, which then is stated as $\bra{\Phi_{i}}\hat{H}\ket{\Phi_{i}} = \bra{\Phi_{i}}\hat{H}\ket{\Phi_{i}} - \epsilon_{i}$.
   But, koopman's theorem assumes that all the orbitals **stay the same** after ionization, it doesn't take into consideration factors like orbital relaxation, and of course the very complicated one-to-one electron interactions. And variational principle states that Approximated wave function will always have greater than or equals to the true wavefunction's energy.
   But wait, doesn't HF also involve a lot of approximations?
   Yes, HF does involve a lot of approximation as well, but in terms of calculating the IP, it can still be more accurate than koopman's theorem, because when subtracting the approximated SCF of the neutral molecule and the cation molecule, they cancel each other's error out assuming the approximation error for each is the same. So the difference between the two should be really close to the true Ionization potential. So, overall, i think that koopman's theorem will generally be higher when compared to calculating $\Delta SCF$