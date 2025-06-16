
# Expectation Value of Property

Properties of molecule can be described by an operator form. Like the Hamiltonian, dipole moment, etc.
Dipole moment is defined as the sum of charges $q_{i}$ with position vectors $r_{i}$

---

**Dipole moment reminder**
Dipole moment -> Measures how separated positive and negative charges are in a molecule.
$\mu = q *d$

---

Based on the above formula, we can refine dipole as

$\hat{\mu} = \sum_{i}q_{i}r_{i}$

($q_{i}=-1$ for electrons, and $q_{i} = +Z_{A}$ for nucleus A)


# Population Analysis

$\rho(r)q$ is viewed as the spatial distribution of electrons at coordinate $r$. We can obtain teh total number of electrons N by integrating it over all space

$$
\int dr \rho(r) = N
$$
We can verify this by normalization of $\varphi_{i}(r)$

$$
\int dr \rho(r) = \sum_{i=1}^{N}\int dr |\varphi_{i}(r)|^{2}=N
$$
since $\int dr|\varphi_{i}(r)|^{2}$ is equal to 1, it directly equals to N

we can substitute in the equation from before

$$
N = \int dx \rho(r)
$$
$$
= \int dr \sum_{\mu v}^{M}P_{\mu v}\chi_{\mu}(r)\chi^{*}_{v}(r)
$$
$$
= \sum_{\mu v}^{M}P_{\mu v}S_{v\mu}
$$
$$
=\sum_{\mu}(PS)_{\mu \mu}
$$
$$
= Tr(PS)
$$

