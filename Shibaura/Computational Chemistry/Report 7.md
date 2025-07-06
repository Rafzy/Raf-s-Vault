Rafael Zefanya Jaya Surya
Z125075

1. Single point calculations

Table summary:

|       | HF          | MP2         | CCSD        | LDA         | PBE         |
| ----- | ----------- | ----------- | ----------- | ----------- | ----------- |
| $F_2$ | -198.754097 | -198.754097 | -198.754097 | -198.327490 | -199.408855 |
| FH    | -100.058083 | -100.058083 | -100.058083 | -99.833831  | -100.383593 |
| FFH   | -199.268853 | -199.268853 | -199.268854 | -198.828677 | -199.921739 |
| F     | -99.405525  | -99.405525  | -99.405525  | -99.100793  | -99.661351  |
| H     | -0.499810   | -0.499810   | -0.499810   | -0.478348   | -0.499588   |

|       | B3LYP       | $\omega$B97X-D |
| ----- | ----------- | -------------- |
| $F_2$ | -199.586338 | -199.523873    |
| FH    | -100.483522 | -100.453995    |
| FFH   | -200.098553 | -200.025301    |
| F     | -99.762868  | -99.732926     |
| H     | -0.502156   | -0.502669      |

For some reason, in my calculations for the wave function methods (HF, MP2, and CCSD), resulted in the same exact energy levels for all molecules & atoms. I doubled checked the input file, the setup and everything, but this still yielded the same result. This may be because the effects of the electron correlation is small, because this is a small system, and the different wave function methods ends up yielding the same amount of energy.

Between CCSD and the DFT methods, we can see that there is a general order when it comes to energy output between them, accross the board, B3LYP yields the most negative energy, while LDA yields the least negative.
The overall order sorting from the most negative to least negative is like this
B3LYP > $\omega$B97-D > PBE > CCSD > LDA

The reason why this is, for LDA, in the handout it's mentioned that LDA is purely a function of $\rho(r)$ or electron density. It only uses local electron density, and has no information regarding the gradients of the electron density $\nabla \rho(r)$, so this method isn't really suitable for molecules where the electron density and the potential change rapidly.

CCSD utilizes the CC theory (Coupled Cluster). Coupled clusters include how pairs of electron avoid each other, it also especially treats bonds forming and breaking fairly well, making it suitable for this reaction.

PBE is a variant of GGA, which unlike LDA, is a function of both $\rho(r)$ as well as $\nabla \rho(r)$. This allows GGA and it's variants to be able to handle rapid changes in electron density and potential, making it perform better for molecules compared to LDA.

$\omega$B97X-D is a hybrid between pure DFT and HF, it is parametrized empirically in order to replicate experimental results.

B3LYP like $\omega$B97X-D is also a hybrid, it mixes 20% HF exchange with DFT exchange, and B3LYP tends to overbind molecules which results in it having the most negative energy result


2. Reaction energy $\Delta E_{r}$ and barrier height $\Delta E^{‡}$

These are the formula for both reaction energy and barrier height
$$
\Delta E_{r} = E(p) - E(r)
$$
$p$ -> Products
$r$ -> Reactants

$$
\Delta E^{‡} = E(t) - E(r)
$$
t -> Transition state

$$
F_{2} + H \to(F\dots F\dots H)^{‡} \to F+FH
$$
 

|                | Reaction Energy     | Barrier Height |
| -------------- | ------------------- | -------------- |
| HF             | -131.5 kcal/mol     | -9.4 kcal/mol  |
| MP2            | -131.5 kcal/mol     | -9.4 kcal/mol  |
| CCSD           | -131.5 kcal/mol<br> | -9.4 kcal/mol  |
| LDA            | -80.8 kcal/mol      | -14.3 kcal/mol |
| PBE            | -85.7 kcal/mol      | -8.3 kcal/mol  |
| B3LYP          | -99.1 kcal/mol      | -6.3 kcal/mol  |
| $\omega$B97X-D | -100.6 kcal/mol     | +0.8 kcal/mol  |

**HF**
Reactant: -198.754097 + (-0.499810) = -199.253907
Products: -99.405525 + (-100.058083) = -199.463608
Transition: -199.268853

Reaction energy = -199.463608 - (-199.253907) = -0.209701 Hartree \* 627.509 = -131.5 kcal/mol
Barrier Height = -199.268853 - (-199.253907) = -0.014947 Hartree \* 627.509 = -9.4 kcal/mol

**LDA**
Reactant: -198.327490 + (-0.478348) = -198.805838
Products: -99.100793 + (-99.833831) =  -198.934624
Transition: -198.828677

Reaction energy = -198.934624 - (-198.805838) = -0.128786 Hartree \* 627.509 = -80.8 kcal/mol
Barrier height = -198.828677 - (-198.805838) = -0.022839 Hartree \* 627.509 = -14.3 kcal/mol

**PBE**
Reactant: -199.408855 + (-0.499588) = -199.908443
Products: -99.661351 + (-100.383593) = -200.044944
Transition = -199.921739

Reaction energy = -200.044944 - (-199.908443) = -0.136501 Hartree \* 627.509 = -85.7 kcal/mol
Barrier height = -199.921739 - (-199.908443) = -0.013296 Hartree \*627.509 = -8.3 kcal/mol

**B3LYP**
Reactant: -199.586338 + (-0.502156) = -200.088494
Products: -99.762868 + (-100.483522) = -200.24639
Transition: -200.098553

Reaction energy: -200.24639 - (-200.088494) = -0.157896 Hartree \* 627.509 = -99.1 kcal/mol
Barrier height: -200.098553 - (-200.088494) = -0.010059 Hartree \* 627.509 = -6.3 kcal/mol

**$\omega$B97X-D**
Reactant: -199.523873 + (-0.502669) = -200.026542
Products: -99.732926 + (-100.453995) = -200.186921
Transition: -200.025301

Reaction energy: -200.186921 - (-200.026542) = -0.160379 Hartree \* 627.509 = -100.6 kcal/mol
Barrier height: -200.025301 - (-200.026542) = 0.001241 Hartree \* 627.509 = -0.8 kcal/mol

3. Discuss the accuracy

To evaluate the accuracy of each method, we will need a reference to compare all the results to. There are several approaches, like finding results from experiments from online, or using CCSD as the reference because CCSD out of all of the used method should be the "most accurate"

for this purpose, i will be comparing the DFT methods with CCSD, because CCSD is the "most accurate" method out of the ones used

Error summary table:

| Methods        | Reaction Energy Error | Barrier Height error |
| -------------- | --------------------- | -------------------- |
| CCSD           | 0                     | 0                    |
| HF             | 0                     | 0                    |
| MP2            | 0                     | 0                    |
| LDA            | 50.7                  | -4.9                 |
| PBE            | 45.8                  | 1.1                  |
| B3LYP          | 32.4                  | 3.1                  |
| $\omega$B97X-D | 39.9                  | 10.2                 |
Aside from the fact that CCSD, HF, and MP2 yields the same energy output, we can compare the errors from DFT methods relative to CCSD.
One thing we can analyze is that accross the board, most of the error is positive, meaning that for the DFT methods, it shows a less exothermic energy output compared to CCSD, this can be interpreted as DFT methods underestimating the bonds between molecules compared to CCSD
We can also see that LDA has the biggest error.

4. Wall time summary

| Method         | F2 (s) | FH (s) | FFH (s) | F (s) | H (s) |
| -------------- | ------ | ------ | ------- | ----- | ----- |
| HF             | 1.32   | 0.77   | 3.16    | 0.60  | 0.29  |
| MP2            | 1.74   | 0.98   | 4.54    | 0.76  | 0.33  |
| CCSD           | 26.80  | 6.81   | 19.64   | 3.05  | 2.18  |
| LDA            | 1.16   | 0.88   | 2.44    | 0.67  | 0.35  |
| PBE            | 1.22   | 0.91   | 2.72    | 0.61  | 0.34  |
| B3LYP          | 1.82   | 0.84   | 3.46    | 0.62  | 0.31  |
| $\omega$B97X-D | 3.20   | 2.00   | 7.10    | 1.29  | 0.59  |

looking at the overall summary, we can see that the LDA method is the quickest to compute, accross the board, and CCSD is dramatically slower compared to all of the other methods.

by order, these are the methods from fastest to slowest
LDA -> PBE -> HF -> B3LYP -> MP2 -> $\omega$B97X-D -> CCSD

we can see that there is a tradeoff between accuracy and compute time. CCSD should be the most accurate method out of all but trades off computational efficiency, being the slowest, while LDA is the quickest one, being the method with the simplest calculations, but having the least accuracy out of all.

I would say the best sweet spot is B3LYP method, because it yields the least amount of error compared to the DFT methods, but while also being relatively quick compared to the others.
