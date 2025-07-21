
# The need for Gibbs free energy

Quantum chemical calculations (Schrodinger's equation, DFT) only provide electronic energy at absolute zero, which doesn't represent real chemical reactions that occur within finite temperatures, where molecules exhibit motion, rotation, and vibration

So, we need what's called as **Gibbs free energy (G)** which accounts for temperature effects

$$
G = H-TS = U+PV-TS
$$

$H$ -> Enthalpy
$S$ -> entropy
$U$ -> Initial energy
$P$ -> Pressure
$V$ -> Volume
$T$ -> Temperature

# Partition Functions

At finite temperature, molecules distribute across energy levels according to the **Boltzmann distribution**

$$
P(\epsilon) \propto e^\left( -\frac{\epsilon}{k_{B}T} \right)
$$

- Higher energy states have lower probability
- Temperature controls the spread of this distribution


The **Partition Function (Q)** is to statistical mechanics what the wave function is to quantum mechanics (Contains all thermodynamic information)

**Molecular partition function**

$$
q = \sum e^\left( -\frac{e_{i}}{k_{B}T} \right)
$$
Basically: sum over all possible molecular energy states
Acts as normalization factor for probability distribution

**System partition function** (For N independent, indistinguishable molecules):

$$
Q = \frac{q^{N}}{N!}
$$

**Thermodynamics properties from partition functions**
Internal energy:
$$
U = k_{B}T^{2} \left( \frac{\partial \ln Q}{\partial T} \right)_{V}
$$
Entropy:
$$
S = KBT\left( \frac{\partial \ln Q}{\partial T} \right)+KB \ln Q
$$


# Separating the contribution

For most molecules, we can separate the energy into separate parts

$$
q(total) = qe.qt.qr.qv
$$

$qe$ = Electronic partition function
$qt$ = Translational partition function
$qr$ = Rotational partition function
$qv$ = Vibrational partition function


## Electronic Contribution

Electronic excitation energies (10 - 100 kcal/mol) >> kBT(0.6 kcal/mol at 298K)

So:
- $qe = ge,0$ (ground state degeneracy)
- $Ue = E$ (The electronic energy from quantum calculation)
- $Se = R\ln(ge, 0)$ (very small for singlets)


## Translational Contribution

For ideal gas molecules moving freely:

- $Ut = \left( \frac{3}{2} \right) RT$
- $St = R \left[ \ln qt + \frac{5}{2} \right]$

## Rotational Contribution

Depends on molecular shape

| Molecule Type | Ur                             | Sr                                     |
| ------------- | ------------------------------ | -------------------------------------- |
| Atom          | 0                              | 0                                      |
| Linear        | RT                             | $R(\ln qr+1)$                          |
| Non-Linear    | $\left( \frac{3}{2} \right)RT$ | $R\left( \ln qr + \frac{3}{2} \right)$ |

## Vibrational Contribution

This is the most complex part, requires frequency calculation

$$
U_{v} = R \sum_{j} \theta_{v,j} \left( \frac{1}{2} + \frac{1}{(e^{\theta_{v,j}/T}-1)}\right)
$$
$$
S_{v} = R \sum_{j} \left( \frac{\left( \frac{\theta_{v,j}}{T} \right)}{\frac{e^{\theta_{v,j}}}{T-}} - \ln\left( 1 - e ^{\left( -\frac{\theta_{v,j}}{T} \right)} \right) \right)
$$

# Practical Assembly

1. Get electronic energy E from geometry optimization
2. Run frequency calculation for vibrational frequencies
3. Calculate thermal corrections
	- Ucorr = $Ut + Ur + Uv$
	- Hcorr = Ucorr + RT (Adds PV work)
	- Gcorr = Hcorr - TS
4. Final result: G = E + Gcorr


# Reaction Energetics and Free energies

For any reaction:

ΔrH° = Σ H°(products) - Σ H°(reactants)
ΔrG° = Σ G°(products) - Σ G°(reactants)

The absolute energy cancels out, we only need energy differences

### Transition State theory

The rate constant:

krate = (kBT/h) × e^(-ΔG‡/RT)

- ΔG‡ = G°(transition state) - G°(reactants)

# Entropy Effects in Different reaction types 

## Unimolecular reactions (A -> B)

- $\Delta S = 0$ (one molecule -> one molecule)
- Small entropy changes from geometry differences

## Biomolecular reactions (A + B -> C)

- Large negative $\Delta S$ (-30 to -50 J/mol-K)
- Because two separate molecules -> one transition state
- Effect: Increases ΔG‡ by 40-60 kJ/mol (Makes reaction slower)

## Number preserving vs number changing

- **A + B -> C + D**: Small entropy effect
- **A + B -> C**: Large negative entropy effect (unfavorable)
- **A -> B + C**: Large positive entropy effect (favorable)

So, 