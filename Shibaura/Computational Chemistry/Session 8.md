
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
