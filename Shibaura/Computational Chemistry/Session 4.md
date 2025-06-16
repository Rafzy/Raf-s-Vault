
# Symmetry of Molecules

Many molecules have symmetrical structure,
For example H20 have the same bond length, and Benzene which we can intuitively say it's symmetrical after looking at the structure

![[Pasted image 20250528151339.png]]

![[Pasted image 20250528151529.png]]

In quantum chemistry, we need a mathematical definition for Symmetrical structures.
So how can we formally define symmetry operations.

## Symmetry operations

Operations after which the molecular structure becomes identical
Let's say we perform a rotation of 180 degree in an axis, this is called C2 operation
![[Pasted image 20250528151846.png]]

If we take a mirror image of the molecule, from different angles, we get the exact same shape which makes sense since it is symmetrical ($\sigma$ stands for reflection, v stands for vertical. $\sigma'$ stands for reflection that cuts all the atoms.)

![[Pasted image 20250528151911.png]]

If we do nothing, it's called E operation
![[Pasted image 20250528152122.png]]


Five types of symmetry operation

$\hat{E}$ -> Does nothing
$\hat{C_{n}}$ -> Rotation about the axis by $360 \degree/n$
$\hat{\sigma}$ -> Reflection through the plane
$\hat{i}$ -> Reflection through the center (inversion center)
$\hat{S_{n}}$ -> Rotation about the axis by $360 \degree/ n$ followed by reflection through a plane perpendicular to the axis

(Computationally relevant operations are Cn and $\sigma$) in most operations

**i and center of inversion**
![[Pasted image 20250528152831.png]]

What kind of symmetry does this molecule have ?
- $C_{2}$
- Mirror reflection ($\sigma_{v}'$).
- $\hat{i}$ center of inversion

**Sn**
 ![[Pasted image 20250528153216.png]]

$S_{n}$ = $C_{n}$ then $\sigma$

## Point Groups

We can categorize any molecule to a certain **group**, **point group**, that has the same symmetry operations. 
![[Pasted image 20250528154122.png]]

since $H_{2}O$ only contains these operations, then falls into the category of $C_{2v}$.

Point groups:
![[Pasted image 20250528154717.png]]


# Symmetry of orbitals

Molecular structure
-> Any symmetry operation in it's point group result in <u>the same structure</u>

Orbital $\varphi(r)$ can be positive or negative sign depending on r
(Remember that wave functions have phase/sign)

## Orbital (a)

![[Pasted image 20250528155847.png]]
We can assume the symmetry operations as actual operators.

$\hat{E}\varphi_{a}(r) = \varphi_{a}(r)$ -> Means that the sign remains unchanged under this symmetry operation
![[Pasted image 20250528155959.png]]

"Irreducible representation (irrep) of $A_{1}$"

## Orbital (b)

![[Pasted image 20250528160340.png]]

Some symmetrical operation causes the wave function's sign to change.

![[Pasted image 20250528160418.png]]
"$B_{1}$ irrep"


## Character tables
![[Pasted image 20250528160639.png]]


# Reduction of computational cost by symmetry

Often we need to compute elements like
$O_{ij} = \bra{\phi_{i}}\hat{O}\ket{\phi_{j}} = \int dr\phi^*_{i}(r)\hat{O}\phi_{j}(r)$

$S_{ij}=\bra{\phi_{i}}\ket{\phi_{j}} = \bra{\hat{R}\phi_{i}}\ket{\hat{R}\phi_{j}} = \bra{\chi_{\sigma_{i}}(\hat{R}\phi_{i})}\ket{\chi_{\sigma_{j}}(\hat{R})\phi_{j}}$

if $\chi_{\sigma_{i}} \neq \chi_{\sigma_{j}}$, $S_{ij}$ = 0

## Symmetry of wave function

We can also check the symmetry of a wave function

Remember we can think of the wave function as the possible positions of all the electrons of position $x = (r, \omega)$. So we can also check the symmetry of wave function

$\hat{R}\ket{\Psi}=\chi_{\psi}(\hat{R})\ket{\Psi}$

Basically:
$\chi_{\Phi_{HF}}(\hat{R})\ket{\Phi_{HF}}$

Where $\chi_{\Phi_{HF}}$ = -1/1

Example:
![[Pasted image 20250528162523.png]]

