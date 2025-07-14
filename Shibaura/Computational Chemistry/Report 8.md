Rafael Zefanya Jaya Surya
Z125075

Note:
When i wanted to calculate \[Br...C(CH3)3...CN]- Transition state, my IQmol couldnt compute the result due to server timeout issues, and because my calculation exceeded the time limit from Q-Chem's public server. 
This is because the transition state is rather bulky, and despite this i will try to answer my best using the calculations that work.

1. Transition & Intermediate states

Reaction:
$$
CH_{3}Br + CN^{-} \to CH_{3}CN+Br^{-}
$$

Intermediate state:
$CH_{3}^{+}$
![[image-83.png|311x258]]

Transition state:
$[Br\dots CH_{3}\dots CN]^{-}$
![[image-84.png|383x185]]

Reaction:
$$
C(CH_{3})_{3}Br + CN^{-} \to C(CH_{3})_{3}CN + Br^{-}
$$

Intermediate state:
$C(CH_{3})_{3}^{+}$
![[image-85.png|399x397]]

Transition state:
$[Br\dots C(CH_{3})_{3}\dots CN]^{+}$

![[image-86.png|414x312]]


2. Reaction Barrier
$$
CH_{3}Br + CN^{-} \to CH_{3}CN + Br^{-}
$$
**SN1 Barriers**
$CH_{3}Br + CN^{-}\to CH_{3}^{+}+ Br^{-}$

$$
\Delta E = E(CH_{3}^{+}) + E(Br^{-}) - E(CH_{3}Br) - E(CN^{-})
$$
$$
\Delta E = -39.17863413 + (-2572.1796463) - (-2611.71562506) - (-92.28572880)
$$
$$
\Delta E = 92.64307343 Ha = 58,134.408686 \frac{kcal}{mol}
$$

$$
\Delta H = H(CH_{3}^{+}) + H(Br^{-}) - H(CH_{3}Br) - H(CN^{-})
$$
$$
\Delta H = 22.083 + 1.481 - 26.787 - 5.485
$$
$$
\Delta H = -8.708 \frac{kcal}{mol}
$$

$$
\Delta S = S(CH_{3}^{+}) + S(Br^{-}) - S(CH_{3}Br) - S(CN^{-})
$$
$$
\Delta S = 48.250 + 39.012 - 60.675 - 46.965
$$
$$
\Delta S = -20.378 \frac{cal}{mol.K}
$$

$$
\Delta G_{sol} = dG_{ILD}(CH_{3}^{+}) + dG_{ILD} (Br^{-}) - dG_{ILD}(CH_{3}Br) - dG_{ILD}(CN^{-})
$$
$$
\Delta G_{sol} = -86.83 + (-73.61) - (-2.23) - (-88.29)
$$
$$
\Delta G_{sol} = -69.92 \frac{kcal}{mol}
$$

$$
\Delta G_{gas} = \Delta E + \Delta H - T \Delta S
$$
$$
\Delta G_{gas} = 58,134.409 \frac{kcal}{mol} + \left( -8.708 \frac{kcal}{mol} \right) - \left( 0.298 * - 20.378 \frac{cal}{mol K} \right)
$$
$$
\Delta G_{gas}= 58,131.773644 \frac{kcal}{mol}
$$
$$
\Delta G = \Delta G_{gas} + \Delta G_{sol}
$$
$$
\Delta G = 58,131.773644 + (-69.92) \frac{kcal}{mol}
$$
$$
\Delta G = 58,061.853644 \frac{kcal}{mol}
$$

**SN2 Barriers**
$CH_{3}Br  + CN^{-} \to [Br\dots CH_{3}\dots CN]^{-}$

$$
\Delta E = E([Br\dots CH_{3}\dots CN]^{-}) - E(CH_{3}Br) - E(CN^{-})
$$
$$
\Delta E = -2703.97225383 - (-2611.71562506) - (-92.28572880)
$$
$$
\Delta E = 0.02910003 Ha = 18.260545 \frac{kcal}{mol}
$$

$$
\Delta H = H([Br\dots CH_{3}\dots CN]^{-}) - H(CH_{3}Br) - H(CN^{-})
$$
$$
\Delta H = (30.494 - 26.787 - 5.485) \frac{kcal}{mol}
$$
$$
\Delta H = -1.778 \frac{kcal}{mol}
$$

$$
\Delta S = S([Br\dots CH_{3}\dots CN]^{-}) - S(CH_{3}Br) - S(CN^{-})
$$
$$
\Delta S = (73.244 - 60.675 - 46.965) \frac{cal}{mol.K}
$$
$$
\Delta S = -34.396 \frac{cal}{mol.K}
$$

$$
\Delta G_{sol} = dG_{ILD}([Br\dots CH_{3}\dots CN]^{-}) - dG_{ILD}(CH_{3}Br) - dG_{ILD}(CN^{-})
$$
$$
\Delta G_{sol} = -69.02 - (-2.23) - (-88.29)
$$
$$
\Delta G_{sol} = 21.5 \frac{kcal}{mol}
$$

$$
\Delta G_{gas} = \Delta E + \Delta H - T \Delta S
$$
$$
\Delta G_{gas} = 18.269545 \frac{kcal}{mol} + \left( -1.778 \frac{kcal}{mol} \right) - \left( 0.298 K * -34.396 \frac{cal}{mol.K} \right)
$$
$$
\Delta G_{gas} = 26.741553 \frac{kcal}{mol}
$$

$$
\Delta G = \Delta G_{gas} + \Delta G_{sol}
$$
$$
\Delta G = (26.741553 + 21.5) \frac{kcal}{mol}
$$
$$
\Delta G = 48.241553 \frac{kcal}{mol}
$$

Discussion:
SN 1 Barrier: $\Delta G = 58,061.853644 \frac{kcal}{mol}$
SN 2 Barrier: $\Delta G = 48.241553 \frac{kcal}{mol}$

As we can see, for this primary reaction, SN1 barrier shows an almost impossibly large value. If we analyze the cause, the large number stems from $\Delta E$'s result. Because the intermediate and the reactant's energy values aren't balanced. 
This implies that $CH_{3}^{+}$, the intermediate structure, is unstable, and in reality, this reaction would never go through SN1.


$$
C(CH_{3})_{3}Br + CN^{-} \to C(CH_{3})_{3}CN + Br^{-}
$$
**SN1 Barriers**
$C(CH_{3})_{3}Br + CN^{-} \to C(CH_{3})_{3}^{+} + Br^{-} + CN^{-}$

$$
\Delta E = E(C(CH_{3})_{3}^{+}) + E(Br^{-}) - E(C(CH_{3})_{3}Br)
$$
$$
\Delta E = -156.373605 + (- 2562.170965) - (-2728.822236)
$$
$$
\Delta E = 10.277666 Ha = 6,449.333053 \frac{kcal}{mol}
$$

$$
\Delta H = H(C(CH_{3})_{3}^{+}) + H(Br^{-}) - H(C(CH_{3})_{3}Br)
$$
$$
\Delta H = (81.506 + 1.481 - 85.278) \frac{kcal}{mol}
$$
$$
\Delta H = -2.291 \frac{kcal}{mol}
$$

$$
\Delta S = S(C(CH_{3})_{3}^{+}) + S(Br^{-}) - S(C(CH_{3})_{3}Br)
$$
$$
\Delta S = (67.752 + 39.012 - 75.667) \frac{cal}{mol.K}
$$
$$
\Delta S = 31.097 \frac{cal}{mol.K}
$$

$$
\Delta G_{sol} = dG_{ILD}(C(CH_{3})_{3}^{+}) + dG_{ILD}(Br^{-}) - dG_{ILD}(C(CH_{3})_{3}Br)
$$
$$
\Delta G_{sol} = -67.91 + (-73.61) - (-2.49)
$$
$$
\Delta G_{sol} = -139.03 \frac{kcal}{mol}
$$

$$
G_{gas} = \Delta E + \Delta H - T \Delta S 
$$
$$
\Delta G_{gas} = 6,449.333053 \frac{kcal}{mol} + \left( -2.291 \frac{kcal}{mol} \right) - \left( 0.298 K * 31.097 \frac{cal}{mol.K} \right)
$$
$$
\Delta G_{gas} =  6,437.775147 \frac{kcal}{mol}
$$

$$
\Delta G = \Delta G_{gas} + \Delta G_{sol}
$$
$$
\Delta G = 6,437.775147 \frac{kcal}{mol} + \left( -139.03 \frac{kcal}{mol} \right)
$$
$$
\Delta G = 6,298.745147 \frac{kcal}{mol}
$$

**SN2 Barrier**
$C(CH_{3})_{3}^{+} + CN^{-} \to [Br\dots C(CH_{3})_{3}\dots CN]^{-}$

Since my IQMol couldn't compute the transition state, i am unable to calculate the SN Barrier, but i will try to explain which method is best for this reaction based on the SN1 calculation.

3. Which mechanism is favored for each reaction?

For the first reaction, we can see that SN2 is more favorable since the SN1 Barrier energy value is impossibly high, while SN2 is more reasonable.
We know that the first reaction is a primary reaction (Molecule is connected with one carbon), while the second molecule is a tertiary reaction (Connected to three other carbons). Tertiary carbonations should be more stable than primary ones, so for the second reaction, SN1 should be more favorable compared to SN2.

4. Free energies

**First reaction**
$$
CH_{3}Br + CN^{-} \to CH_{3}CN + Br^{-}
$$

$$
\Delta E = E(CH_{3}CN) + E(Br^{-}) - E(CH_{3}Br) - E(CN^{-})
$$
$$
\Delta E = -131.924684 + (-2572.170865) - (-2611.71562506) - (-92.285729)
$$
$$
\Delta E = -0.094195 Ha = -59.108257 \frac{kcal}{mol}
$$

$$
\Delta H = H(CH_{3}CN) + H(Br^{-}) - H(CH_{3}Br) - H(CN^{-})
$$
$$
\Delta H = (32.675 + 1.481 - 26.787 - 5.485) \frac{kcal}{mol}
$$
$$
\Delta H = 1.884 \frac{kcal}{mol}
$$

$$
\Delta S = S(CH_{3}CN) + S(Br^{-}) - S(CH_{3}Br) - S(CN^{-})
$$
$$
\Delta S = (59.139 + 39.012 - 60.675 - 46.965) \frac{cal}{mol.K}
$$
$$
\Delta S = -9.489 \frac{cal}{mol.K}
$$

$$
\Delta G_{sol} = dG_{ILD}(CH_{3}CN) + dG_{ILD}(Br^{-}) - dG_{ILD}(CH_{3}Br) - dG_{ILD}(CN^{-})
$$
$$
\Delta G_{sol} = -9.19 + (-73.61) - (-2.23) - (-88.29)
$$
$$
\Delta G_{sol} = 7.72 \frac{kcal}{mol}
$$

$$
\Delta G_{gas} = \Delta E + \Delta H - T \Delta S
$$
$$
\Delta G_{gas} = -59.108257 \frac{kcal}{mol} + 1.884 \frac{kcal}{mol} - \left( 0.298 K * -9.489 \frac{cal}{mol.K} \right)
$$
$$
\Delta G_{gas} = -54.396535
$$

$$
\Delta G = \Delta G_{gas} + \Delta G_{sol}
$$
$$
\Delta G = -54.396535 + 7.72
$$
$$
\Delta G = -46.676535
$$

**Second reaction**

$$
C(CH_{3})_{3}Br + CN^{-} \to C(CH_{3})_{3}CN + Br^{-}
$$

$$
\Delta E = E(C(CH_{3})_{3}CN) + E(Br^{-}) - E(C(CH_{3})_{3}Br) - E(CN^{-})
$$
$$
\Delta E = -249.00307612 + (-2572.170965) - (-2728.822236) - (-92.285729)
$$
$$
\Delta E = -0.066076 Ha = -41.463393 \frac{kcal}{mol}
$$

$$
\Delta H = H(C(CH_{3})_{3}CN) + H(Br^{-})-H(C(CH_{3})_{3}Br) - H(CN^{-})
$$
$$
\Delta H = (90.852 + 1.481 - 85.278 - 5.485) \frac{kcal}{mol}
$$
$$
\Delta H = 1.57 \frac{kcal}{mol}
$$

$$
\Delta S = S(C(CH_{3})_{3}CN) + S(Br^{-}) - S(C(CH_{3})_{3}Br) - S(CN^{-})
$$
$$
\Delta S = (75.662 + 39.012 - 75.667 - 46.965) \frac{cal}{mol.K}
$$
$$
\Delta S = -7.958 \frac{cal}{mol.K}
$$

$$
\Delta G_{sol} = dG_{ILD}(C(CH_{3})_{3}CN) + dG_{ILD}(Br^{-}) - dG_{ILD}(C(CH_{3})_{3}Br) - dG_{ILD}(CN^{-})
$$
$$
\Delta G_{sol} = -8.76 + (-73.61) - (-2.49) - (-88.29) \frac{kcal}{mol}
$$
$$
\Delta G_{sol} = 8.41 \frac{kcal}{mol}
$$

$$
\Delta G_{gas} = \Delta E + \Delta H - T \Delta S
$$
$$
\Delta G_{gas} = -41.463393 \frac{kcal}{mol} + 1.57 \frac{kcal}{mol} - \left( 0.298 K * -7.958 \frac{cal}{mol.K} \right)
$$
$$
\Delta G_{gas} = -37.521909 \frac{kcal}{mol}
$$

$$
\Delta G = \Delta G_{gas} + \Delta G_{sol}
$$
$$
\Delta G = -37.521909 + 8.41 \frac{kcal}{mol}
$$
$$
\Delta G = -29.111909 \frac{kcal}{mol}
$$

5. Why is it important to consider solvation effects for these reactions?

There are several reasons why it's important especially for these reactions to include solvation effect. These reactions involved charged molecules/atoms, And charged structures are stabilized by polar solvents. Solvation also stabilizes carbocations (which is important since it's what makes SN1 possible), so without solvation in our equation, SN1 would most likely always appear impossible.

Aside from that, real chemistry reactions are usually performed in solvents (like water, or alcohol), and so solvation effects are part of the actual reaction environment. 

6. How can we improve upon the calculations?

Instead of HF, we can use DFT methods, with HF, we know that HF ignores electron correlations, and each electron are assumed to be independent, meanwhile carbocation depends on electron movement. Using DFT would allow electron correlation to be considered in the calculations, so using something like B3LYP with 6-311+G basis would be good.

Other than that, we can use other solvation model aside from ChemSol. ChemSol is a simple model relative to other models, and it may not accurately capture specific solvent interactions. So we can try using other solvation models like SMD (Solvation Model Density) or PCM (Polarizable Continuum Model)

