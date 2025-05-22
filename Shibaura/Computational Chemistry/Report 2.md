
1. $H_{2}O$
	**MO #1**
	![[Pasted image 20250521195800.png]]
	
	For the first Molecular orbital, it seems to follow only the O's atomic orbital, this makes sense since in the IQMol, we can see that for MO#1, 1s of O has the highest MO coefficient (-0.99468), meaning, that orbital is the highest contributor for forming the Molecular Orbital.
	![[Pasted image 20250521203636.png]]
	
	**MO #2**
	![[Pasted image 20250521200111.png]]
	
	For the second MO, we can see that the orbital surrounds the three atoms, and from this we can infer that this is a bonding orbital, since we don't see any nodes between atoms. This is also supported when we analyze the MO coefficients for MO#2, we see that the Coefficients that contribute to forming the MO all has negative sign, (-0.47705 for 1s orbital of O, and -0.12372 for 1s orbital of H, and some other orbitals),
	![[Pasted image 20250521204351.png]]
	 this means it means the wavefunction from the AO forms an "in-phase" Molecular orbital, forming a bonding orbital. We also know that bonding orbitals release energy since it should be lower energy.
	
	**MO #3**
	![[Pasted image 20250521204545.png]]
	
	For MO #3, we can see what appears to be an antibond orbital, since a node is visible. But it's interesting that the node splits right in the middle of the O atom, dividing the two H atoms. This may be explained when we analyze the MO coefficients from the result.
	![[Pasted image 20250521213848.png]]
	
	(The final four rows are for H orbitals)
	We can see that for the H orbital, there are two negative, and two positive coefficients. These two would together form antibonding orbital, which would explain why the node separates between the two Hydrogen. Other than that, if we also look at the Oxygen atom's coefficient, we can see that there are two major positive coefficients (0.50196 and 0.31249), as well as two somewhat major negative coefficients (-0.22739 and -0.11940), and the two AO with positive coefficients may have formed a bonding orbital with one Hydrogen atom, and the two AO with negative coefficients forms a bonding orbital with the other.
	This may explain why it looks like a bonding orbital for each H with half of the O atom.
	
	**MO #4**
	![[Pasted image 20250521214351.png]]
	
	For the fourth orbital, we can see that it is an antibonding orbital between the two Hydrogen atoms, and the Oxygen atom. So the node, splits between the Oxygen and the two hydrogens. Let's analyze the output again :D
	![[Pasted image 20250522140659.png]]
	If we pay attention, all the MO coefficient for both Hydrogen atoms are negative, which may explain why between the two H atoms, it looks like a bonding orbital, but if we look at the Oxygen MO coefficients, the three major coefficients (0.55143, 0.31825, and 0.40365) are all positives, which may explain why it forms an antibonding orbital between the Oxygen atom and the two Hydrogen atoms.
	
	**MO #5**
	![[Pasted image 20250522141029.png]]
	
	For the 5th molecular orbital, it's also the HOMO (Highest occupied molecular orbital), which we can see from the IQmol's canonical orbital, and we can also infer from the Eigenvalues, the 5th orbital is the last orbital with negative eigenvalue which denotes the energy, and negative eigenvalues usually tell us that the orbital is occupied.
	
	For the orbital itself, we can see that it forms an antibonding orbital, but interestingly, the node splits all three atoms right in the middle (Laterally), which i think is interesting because usually nodes exist in the middle of two atoms, but this kindof exists right in the middle of the three atoms.
	
	Maybe this would be explained in the output file.
	![[Pasted image 20250522141839.png]]
	
	If we see, the MO coefficient for the two Hydrogen atoms are zero, so their AO doesn't contribute for this MO, but we can see the MO coefficient for the Oxygen AO has positive and negative values (0.03221, -0.64052, etc). And so maybe this is an antibonding effect from the Oxygen atom itself (I'm not sure if antibonding is possible with only one atom's AO), which may explain why the node "*passes through*" the two hydrogen atoms.
	
	**MO#6**
	![[Pasted image 20250522142251.png]]
	
	For the 6th orbital, it is LUMO (Lowest Unoccupied Molecular Orbital), so from this orbital forward, it will be unoccupied. If we see, the orbital is pretty big, covering the whole molecule, but we can see a cavity in the middle, the cavity wraps around the Oxygen atom, and barely touching the two hydrogen atoms.
	So what's interesting is that, i think that there is a node between the outer orbital and the orbital inside the cavity, so the node kindof wraps around the Oxygen atom. 
	
	Because if we zoom in, we can see the orbital inside of the cavity is red, the opposite wave sign of the blue orbital we can see outside.
	
	**MO #7**
	![[Pasted image 20250522144008.png]]
	
	For the 7th MO, we can see that it forms several antibonding orbitals, and three nodes are visible. We can analyze the output file to try to explain this behavior.
	
	![[Pasted image 20250522144600.png]]
	
	We can see that the two Hydrogen atoms, have different signs which explain the antibonding between the two hydrogen atoms. For the Oxygen atom, the MO coefficient has mostly negative signs and one positive sign, the different sign may cause the antibonding orbital we see in the middle, as well as the antibonding orbital formed between the two hydrogen atoms.
	
	**MO #8**
	![[Pasted image 20250522144834.png]]
	
	For the 8th molecular orbital, we can see a really interesting visualization, we can see the two big orbitals on the left and right, but for the hydrogen atoms, it creates a smaller orbital that's tucked inside the bigger orbital, and technically forming two nodes (Between the two bigger orbital and between the two smaller orbital inside).
	
	![[Pasted image 20250522145417.png]]
	
	If we look at the output file, we can see that for the two hyrogen atoms, each atom contains both negative and positive signs, which may explain the antibonding orbital formed between the two hydrogen atoms, as for the Oxygen atom, we can see the MO coefficients are all negative. (Unfortunately i cannot explain the behavior for the antibonding of the two bigger orbitals, since all the MO coefficients of Oxygen atom is all negative, i don't rlly get why it forms a big antibonding orbital like that, but my guess is due to the different MO coefficient sign in each of the hydrogen atoms, it causes the orbitals to be like that.)
	
	**MO #9**
	![[Pasted image 20250522151913.png]]
	
	For the 9th MO, we get this really interesting antibonding orbital shape, we can see the big blue orbital that wraps around the Oxygen atom, and we can also see the red orbital, that has these two prong shapes that goes inside the blue orbital, and wraps around the two hydrogen atoms, and it warps out of the blue orbital, forming a circular shape outside of the blue orbital. So there exists two node sthat separate between the Two hydrogen atoms and the Oxygen atom. 
	
	![[Pasted image 20250522152235.png]]
	
	We can see from the MO coefficients, that again each of the Hydrogen atoms have different signs for the two AOs, and for the oxygen atom has various coefficients with differing signs, these different signs between the oxygen atom and hydrogen atom may cause this unique antibonding orbital to form between them.
	
	**MO #10**
	![[Pasted image 20250522152422.png]]
	
	For the 10th and final virtual orbital, we can see an antibonding orbital being formed, between the Hydrogen and Oxygen atom. If we look at it from another angle, 
	
	![[Pasted image 20250522153024.png]]
	
	We can see that the blue orbital kindof "goes through" the red orbital, and the node exists in between the two orbitals, cutting between the oxygen with the two hydrogens.
	
	**H2O Orbital Diagram:**
	![[Pasted image 20250522154021.png]]


2. $N_{2}$
	**MO #1**
	![[Pasted image 20250522155853.png]]
	
	For the N2's first MO orbital, it looks like the two orbitals have the same phase, yet is separate from one another. 
	It looks lke this because in IQmol, it takes all molecular orbitals, including the non-valence electrons (Core electrons). Usually, the core electrons are tightly bound to their nucleus, and don't really participate much to the bonding, which is why we see two red orbitals surrounding both N atoms and are separate. Technically, this is a non-bonding orbital, $\sigma$* orbital.
	If we see the output file, we can see that there is one major contributing MO coefficient for each N atoms (-0.7038), which is basically saying that each 1s orbital from each N contributes to forming the MO, but doesn't contribute much to bonding (Why we don't see them overlap)
	
	**MO #2**
	![[Pasted image 20250522162803.png]]
	
	For the second MO, it's a similar case to the first MO, it is the result of the two Nitrogen's core electrons, which also forms the higher energy "antibonding" orbital, but since these are core electrons, they both don't "overlap". This is also supported in the output file, where the MO coefficient of one Nitrogen's 1s orbital is negative (-0.7041), and positive (0.7041), which forms the differing sign color of the orbital.
	
	**MO #3** $\sigma$
	![[Pasted image 20250522163102.png]]
	
	For the third MO, it involves valence electrons (2s orbitals from each N atom), which is why we can see actual bond forming, and we see it's a bonding orbital. If we analyze the output file, we can see altering signs of positive and negative coefficients, but the major coefficients are all positive for both Nitrogen atoms (0.34250, 0.25895, etc). These positive coefficients form an in-phase (constructive) wave bonding. And since this is a head-on electron overlap, this is considered to be $\sigma$ bonding.
	
	**MO #4** $\sigma$*
	![[Pasted image 20250522165029.png]]
	
	For the fourth MO, we can see that it forms an antibonding orbital. This is the antibonding equivalent from MO #3, formed from the same two AO (2s). If we analyze the output file, the major MO coefficient for is mostly negative
	![[Pasted image 20250522203301.png]]
	
	And the other one is mostly positive
	![[Pasted image 20250522203334.png]]
	
	The difference in majority of MO coefficient sign causes the two atoms to form an antibonding orbital, $\sigma$*
	
	**MO #5** $\sigma$
	![[Pasted image 20250522203643.png]]
	
	From the 5th molecular orbital, we can see it's actually bonding orbital that's formed by $p_{z}$ orbital. Due to the shape of the $p_{z}$ orbital, it causes the orbitals to look like squished together (like a burger). But this is still considered a $\sigma$ bonding orbital.
	
	**MO #6** $\pi$
	![[Pasted image 20250522204356.png]]
	
	From this molecular orbital, we can clearly see that this is a pi bonding, due to the parallel bonding formed by the p orbitals. This is supported by the fact that this is formed by p Atomic Orbitals that tend to form pi bonding, and the orbitals look in parallel. 
	![[Pasted image 20250522205019.png]]
	This is also supported by the fact that that the MO coefficients are mostly positive, forming a bonding orbital. Making this a $\pi$ bonding.
	
	**MO #7** HOMO $\pi$
	![[Pasted image 20250522211118.png]]
	
	For the 7th MO, we can see that it's also a $\pi$ bonding orbital, same with the previous MO, so the reasons are the same, and the result of the MO coefficients for this orbital layer is also similar
	![[Pasted image 20250522211445.png]]
	
	Since MO coefficients are mostly positive, it supports the creation of bonding pi orbitals
	
	**MO #8** LUMO $\pi$*
	![[Pasted image 20250522211541.png]]
	
	For the 8th MO, we can see that it forms a $\pi$ antibonding orbital, because it forms two nodes that split the orbital into four. This is also supported by the fact that the MO coefficient between the two N atoms differ in sign
	![[Pasted image 20250522212430.png]]
	
	As we can see, the first half (Orbitals of one N atom) is mostly negative and the majority of the second N atom's MO coefficient is positive, forming an antibonding orbital
	
	**MO #9** $\pi$*
	![[Pasted image 20250522215343.png]]
	
	For the 9th molecular, similar to the previous orbital, we can see that it is an antibonding $\pi$* orbital, since it forms two nodes between the two atoms. We can also analyze the output file.
	![[Pasted image 20250522222037.png]]
	
	Similar to the reason above, the two N atoms have different major MO coefficient signs, resulting in an antibonding orbital.
	 
	**MO #10** $\sigma$*
	![[Pasted image 20250522222340.png]]
	
	For the 10th orbital, we can see that it forms a sort of antibonding orbital with three nodes, since it is a head-on overlap, not parallel, we can assume that it is a $\sigma$* antibonding orbital.
	![[Pasted image 20250522222503.png]]
	
	If we analyze the MO coefficient output file, we can see that within one N atom, there are different MO coefficient signs, that may cause this antibonding formation
	
	
3. $N_{2}^+$
	![[Pasted image 20250522224558.png]]
	The \<S^2> shown here is 0.752720080, we can try to solve it theoretically and compare it with IQMol's answer.
	The formula for S^2 should be $(S(S  +  1))$  and $S = ms = \frac{N_{\alpha}-N_{\beta}}{2}$ , given unrestricted open shell Hartree Fock, since UHF may have spin contamination.
	Still we can use that formula to see whether the result is close enough for UHF or not.
	Since we know $N_{2}^+$ definitely has unpaired electron, and it's located at the HOMO, because HOMO is the likely orbital to be a donor electron. So we know either the alpha spin or the beta spin would be one less than the other, so $S = \frac{1}{2}$. Thus,
	$$
	<S^{2}> = \frac{1}{2}\left( \frac{1}{2} + 1\right)= \frac{3}{4} = 0.75
    $$
	Based on our formula, the <S^2> should be 0.75, and thus, the result of the IQmol is reasonable.
	
	**Bond Order**
	For the bond order, we don't have to calculate $N_{2}^+$, We know that $N_{2}$ has 4 bonding orbitals, and one antibonding orbital, and we can calculate using the following formula
	$$
BO = \frac{1}{2}(n_{b} - n_{ab})
$$
	For each total bonding and antibonding orbital, we multiply by two cuz one orbital can contain two alpha and beta elctron.
	$n_{b} = 4 * 2 = 8$ 
	$n_{ab} = 1 * 2 = 2$ 
	Thus,
	
	$$
BO = \frac{1}{2}(8 - 2) = 3
$$
	For $N_{2}$, Bonding Order is 3, now we can calculate $N^{+}_{2}$
	We know that the HOMO of N2 is located on a bonding orbital, so $N_{2}^+$, would lose electron in a Bonding orbital.
	So, we can immediately calculate
	$$
BO = \frac{1}{2}(7-2) = 2.5
$$
	So we can see that $N_{2}^+$ has 2.5 Bonding order, less than $N_{2}$, so we know that $N_{2}^+$ has a weaker bond due to the missing electron in the HOMO bonding orbital.

4. $O^{2}$
	Singlet:
	Energy
	![[Pasted image 20250522233333.png]] 
	This is the total energy when SCF convergence is met
	
	**MO #1**
	![[Pasted image 20250522234854.png]]
	
	For the first molecular orbital, it's quite the same with N2's case where this is actually the non-valence electron or core electron, which is why they don't form any bondings, because they are closely bound to the nucleus.
	
	**MO #2**
	![[Pasted image 20250522235349.png]]
	
	Same case with the first Molecular Orbital, this the "antibonding" equivalent of the first MO, and it still involves 1s or the core electron.
	
	**MO #3** $\sigma$
	![[Pasted image 20250522235836.png]]
	
	The third MO shows the first bonding orbital, it's formed by the 2s AO from O's atom. similar with N2, it's a $\sigma$ bonding orbital. Since it's similar to N2's result i won't be showing the output file for all of them now, (point is, different sign creates antibonding, same sign creates bonding :D, it's just a matter of whether it's sigma or pi bonding).
	
	**MO #4** $\sigma$*
	![[Pasted image 20250523000650.png]]
	
	This seems to be an antibonding $\sigma$* orbital, because it's a product of different signs of MO coefficient between atoms, and it's a head-on overlap between AOs.
	
	**MO #5** $\pi$
	![[Pasted image 20250523000934.png]]
	
	For the fifth MO, we can see that it's a bonding pi orbital.
	
	**MO #6** $\sigma$
	![[Pasted image 20250523001142.png]]
	
	This seems to be a $\sigma$ bonding orbital, similar to $N_{2}$'s case explained before, it's a bonding orbital that's formed by $p_{z}$ AOs
	
	**MO #7** 
	![[Pasted image 20250523001418.png]]
	