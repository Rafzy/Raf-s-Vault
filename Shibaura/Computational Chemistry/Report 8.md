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
\Delta E = 10.277666
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

$$