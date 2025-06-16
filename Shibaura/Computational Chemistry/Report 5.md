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

4. Do the compu