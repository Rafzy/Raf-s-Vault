**Spectroscopy** ->  interaction between electromagnetic radiation and atoms/molecules.

In this class, we focus on Infrared (IR) absorption

# Molecular Vibrations

Atoms in a molecule can vibrate as if the chemical bonds between them is a spring.
A molecule initially lies at an initial state, with it's wave function $\ket{\Psi_{i}}$ with energy $E_{i}$.
There are different states with differing energy levels (discrete, not continuous). Quantum mechanics indicate that molecules can absorb light as energy, causing them to jump to a higher energy state ($\ket{\Psi_{f}}$ with $E_{f}$).
This happens when the energy of light $hv$ matches the energy difference between the states $\Delta E = E_{f} - E_{i}$.
If it doesn't match, then the light is reflected or transmitted.
Alternatively as well, a higher energy state molecule can emit light with energy $hv$ to relax to the lower energy state.

To specify a molecule with N atom's configuration in space, we need $3N$ coordinates (x, y, z) coordinates for each atom which corresponds to 3N degrees of freedom, attributed to **translational motion**.
Same with **rotation** of a molecule demands three degrees of freedom, except for linear molecules
So, total degrees of freedom corresponding to **vibrational motion**:
- $3N-6$
- $3N-5$ for linear molecules

In the absence of an external field, the energy of a molecule does not depend on the translation or rotation.
Potential energy $V$ of a polyatomic molecule becomes a function of $3N-5$ or $3N-6$ **vibrational coordinates** -> $q_{1},q_{2},\dots,q_{N_{vib}}$
$N_{vib}$ = $3N-5$ or $3N-6$

$$
V = V(q_{1},q_{2},\dots,q_{N_{vib}})
$$

Expanding the function around the equilibrium geometry q=0

$$
V(q_{1},q_{2},\dots, q_{N_{vib}})=V(0,0,\dots,0)+ \sum_{i=1}^{N_{vib}}\left( \frac{{\partial V}}{\partial q_{i}} \right)_{q=o_{9}}q_{i}+\frac{1}{2}\sum_{i=1}^{N_{vib}}\sum_{j=1}^{N_{vib}}\left( \frac{{\partial^{2}V}}{\partial q_{i}\partial q_{j}} \right)_{q=0}q_{i}q_{j}+\dots
$$

This is the [[Taylor Series]] expansion of the potential energy function around the equilibrium.
Basically -> Expands the V as a function of small displacements from the equilibrium.

**First term**
$V(0,0,\dots,0)$
This describes the potential energy at the equilibrium, by definition we set this to 0.

**Second term**
$\sum \left( \frac{{\partial v}}{\partial q_{i}} \right)_{q=0}q_{i}$
These are the first derivatives -> Forces on each atom, at equilibrium geometry, all forces are zero, so this term disappears

**Third term**
$\frac{1}{2}\sum \sum\left( \frac{{\partial^{2}v}}{\partial q_{i}\partial q_{j}} \right)_{q=0}q_{i}q_{j}$
These are second derivatives, how steeply the energy changes with displacement. This term is used to determine vibrational frequencies

So the taylor expansion is basically saying
>If i'm at dequilibrium, and i displace the atoms by small amoung qi, how does the energy change?

