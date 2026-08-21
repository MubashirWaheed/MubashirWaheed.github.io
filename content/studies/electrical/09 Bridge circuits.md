---
title: 09 Bridge circuits
---
<img src="attachments/bridge-circuit.png" width=400/>

## The general rule for AC bridge balance
Balance (null) condition for any four-arm bridge

At balance the detector voltage is zero, so opposite-arm impedance products are equal.

$$
\underline{Z_1}\,\underline{Z_4} = \underline{Z_2}\,\underline{Z_3}
$$


## Applied to this Maxwell-Wien bridge

Unknown arm $\underline{Z_x}=R_x+j\omega L_x$, opposite arm is the parallel combo $R_4\parallel C_4$:

$$R_2 R_3 = (R_x + j\omega L_x)\,\frac{R_4\,\frac{1}{j\omega C_4}}{R_4 + \frac{1}{j\omega C_4}}$$

Clear the fraction (multiply both sides by $R_4+\frac{1}{j\omega C_4}$, then by $j\omega C_4$):

$$R_2 R_3\,(1 + j\omega R_4 C_4) = (R_x + j\omega L_x)\,R_4$$

**Real part** gives the unknown resistance:

$$R_x = \frac{R_2 R_3}{R_4}$$

**Imaginary part** gives the unknown inductance:

$$L_x = R_2 R_3 C_4$$

## Loss Factor (tan δ) — Inductors and Capacitors

| Component | Series model | Parallel model |
|-----------|-------------|----------------|
| Inductor | $\tan\delta_L = \dfrac{R_s}{\omega L}$ | $\tan\delta_L = \dfrac{\omega L}{R_p}$ |
| Capacitor | $\tan\delta_C = \omega R_s C$ | $\tan\delta_C = \dfrac{1}{\omega R_p C}$ |

## Symbol key

- $R_s$: series loss resistance (in series with the reactive element).
- $R_p$: parallel loss/leakage resistance (across the reactive element).
- $\omega L$: ideal inductive reactance; $\dfrac{1}{\omega C}$: ideal capacitive reactance.
- $\omega = 2\pi f$: angular frequency.

## General rule to memorize

For any AC bridge "can it run at another frequency?" question:

1. Write the balance results for the unknowns.
2. If $\omega$ **cancels out**, the balance is frequency-independent, so the answer is yes.
3. Then check whether any **given quantity** ($\tan\delta$, a reactance value, a component tolerance) was specified at a particular frequency; that part must be re-evaluated at the new frequency.

$$
R_x = \frac{R_2 R_3}{R_4} \qquad L_x = R_2 R_3 C_4
$$

$$
R_x = \underbrace{\omega}_{\text{depends on } f}\, L_x\, \underbrace{\tan\delta_x}_{\text{also depends on } f}
$$
