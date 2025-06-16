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




