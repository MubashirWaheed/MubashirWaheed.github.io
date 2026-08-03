---
title: 02  Complex Frequency
date: 2026-07-30
---

## Partial fraction rules 

**Rule 1:** Simple partial fractions: distinct linear factors

$$
\frac{5\underline{s}_n + 1}{(\underline{s}_n + 1)(\underline{s}_n + 2)} = \frac{A}{\underline{s}_n + 1} + \frac{B}{\underline{s}_n + 2}
$$


**Rule 2:** Numerator degree = denominator degree minus one.

Irreducible quadratic factor $(x^2+bx+c)$ gets a linear numerator $(Ax+B)$.
$$
\frac{6\underline{s}_n^2+9}{\underline{s}_n(\underline{s}_n^2+4)} = \frac{A}{\underline{s}_n} + \frac{B\underline{s}_n+D}{\underline{s}_n^2+4}
$$

**Rule 3:** Repeated factors get one term per power.

$$
\frac{P(x)}{(x^2 + 1)^2} = \frac{Ax + B}{x^2 + 1} + \frac{Cx + D}{(x^2 + 1)^2}
$$


## Circuit element values from Pole Zero Graph

Possible equivalient circuits
- First Foster Impedance realization 
- Second Foster Admittance realization
- Cauer form from decreasing powers
- Cauer form from increasing powers

Foster separates the function into resonant subblocks, while Cauer synthesis constructs a ladder network one element at a time



## Foster form I (impedance of one finite pole pair)
After having done the partial fraction of the pole zero fraction we get the fractrions in this form which means we can compare it with the **impedance of a parallel LC** resonantor 
and extract the componnet values

In this form parallel LC forms 

$$
\underline{Z}_{\parallel LC} = \frac{\frac{1}{C}\,\underline{s}}{\underline{s}^2 + \frac{1}{LC}}
$$

$$
\underline{Z}_k = \frac{K\,\underline{s}}{\underline{s}^2 + \omega_0^2}
$$

$$
K = \frac{1}{C}, \qquad \omega_0^2 = \frac{1}{LC}
$$

$$
\underline{Z}_L = \underline{s}_n\,L \qquad\qquad \underline{Z}_C = \frac{1}{\underline{s}_n\,C}
$$


##  Foster From II realization
is obtained from the admittance 

$$
\underline{Y}_C = \underline{s}_n\,C \qquad\qquad \underline{Y}_L = \frac{1}{\underline{s}_n\,L}
$$

### Admittance of a series LC resonator

$$
\underline{Y}_{\text{series }LC} = \frac{\frac{1}{L}\,\underline{s}}{\underline{s}^2 + \frac{1}{LC}}
$$


## Cauer Form I (decreasing power)

In this one we start from the highest power of $s_n$ and work down => decreasing power

For large s, the dominant behavior is obtained by dividing the highest powers:

$$
\underline{Y}(\underline{s}) = \frac{\underline{s}^4 + 10\underline{s}^2 + 9}{\underline{s}^3 + 4\underline{s}}
$$

$$
\underline{Y}(\underline{s}) \sim \frac{\underline{s}^4}{\underline{s}^3} = \underline{s} \qquad\Longrightarrow\qquad \text{capacitor: } \underline{Y}_C = \underline{s}C
$$

- Extract the leading term (divide highest power by highest power) → that's your element.
- Subtract the element off the current function → leftover fraction (remainder).
- Invert the remainder → switches you between Y and Z (shunt ↔ series).
- Repeat on the inverted remainder.


## Cauer form II (increasing power)
In this one we start from the lowest power of $s_n$ and work up => increasing power

For small s, the lowest powers dominate. The numerator behaves like

$$
\underline{Y}(\underline{s}) = \frac{\underline{s}^4 + 10\underline{s}^2 + 9}{\underline{s}^3 + 4\underline{s}}
$$

$$
\underline{Y}(\underline{s}) \sim \frac{9}{4\underline{s}} \qquad\Longrightarrow\qquad \text{inductor: } \underline{Y}_L = \frac{1}{\underline{s}L}
$$

- Extract the trailing term (divide lowest power by lowest power) → that's your element.
- Subtract the element off the current function → leftover fraction (remainder).
- Invert the remainder → switches you between Y and Z (shunt ↔ series).
- Repeat on the inverted remainder.


The one sentence to hold onto: 
$e^{st}$ is the one signal shape that differentiation can't change, it can only multiply it by $s$
, so choosing that shape lets you replace every derivative in a circuit with the single number $s$  and turn calculus into algebra.


$$
e^{\underline{s}t} = e^{(\sigma + j\omega)t} = e^{\sigma t}\, e^{j\omega t}
$$


$$
\frac{d}{dt}\, e^{\underline{s}t} = \underline{s}\, e^{\underline{s}t}
$$

$$
e^{j\omega t} = \cos(\omega t) + j\sin(\omega t)
$$


$$
r(t) = e^{\sigma t}, \qquad \varphi(t) = \omega t
$$


- $e^{\sigma t}$ is a **real positive number**, so it sets the **radius**: $r(t) = e^{\sigma t}$.
- $e^{j\omega t}$ is a **unit-magnitude rotation** (by Euler's formula it's $\cos \omega t + j \sin \omega t$), so it sets the **angle**: $\varphi(t) = \omega t$.


$$
e^{\underline{s}t} = \underbrace{e^{\sigma t}}_{\text{radius}} \cdot \underbrace{e^{j\omega t}}_{\text{rotation}}
$$

- **$\omega$ (imaginary part) → rotation.** The factor $e^{j\omega t}$ spins the point around the origin. If $\omega > 0$, it rotates **counter-clockwise (CCW)**. Bigger $\omega$ = faster spin. If $\omega = 0$, no spin at all.
- **$\sigma$ (real part) → radius.** The factor $e^{\sigma t}$ scales the distance from the origin. $\sigma < 0$ shrinks it (spirals **inward**), $\sigma > 0$ grows it (spirals **outward**), $\sigma = 0$ keeps it fixed (a perfect **circle** of radius 1).


### Impedance Normalizing 
You pick reference values, a reference resistance $R_0$(or impedance $Z_0$) and a reference frequency ω0, and divide your real quantities by them. That strips out the units and the specific scale of your particular circuit:

$$
\underline{Z}_n = \frac{\underline{Z}}{R_0}, \qquad \underline{s}_n = \frac{\underline{s}}{\omega_0}
$$


### Resonance signatures in the impedance
So zeros = series resonance (short), poles = parallel resonance (open).


| Position | $\sigma$ | Time behavior | For a pole, this means |
|---|---|---|---|
| Left half-plane | $< 0$ | decays | stable (rings down) |
| Imaginary axis | $= 0$ | constant oscillation | lossless / marginally stable |
| Right half-plane | $> 0$ | grows | unstable (runs away) |

### What does stable means for a circuit?
Stable means the circuit settles down on its own; unstable means it runs away. Decay is settling; growth is running away.


## Concept
Poles are the circuit's natural-response modes; zeros are not. The "natural response" is what the circuit does on its own after you disturb it and remove the source, how it 
rings, decays, or blows up with no input driving it. Those self-sustained modes are determined entirely by the poles of the impedance. A pole is a frequency where the response 
can be nonzero even with no input,So each pole is one of the circuit's natural modes, and its position $(σ<0, =0=0, or >0)$ directly tells you whether that mode decays, 
holds steady, or grows.

A zero is a frequency where the output vanishes, where the impedance goes to zero (a short) or a transfer function blocks the signal. it describes where the circuit suppresses or
 transmits a driven signal


$$
\text{poles} \;\Rightarrow\; \text{natural modes (how the circuit rings on its own)}
$$
$$
\text{zeros} \;\Rightarrow\; \text{where the response vanishes (blocking / short, driven behavior)}
$$


Not any zero produces zero impedance for a real sinusoid. Only zeros that sit on the imaginary axis do


### Sinusoidal signal
To analyze the circuit with algebra instead of calculus, engineers represent that real cosine using a complex exponential (the trick you learned earlier, 
$e^{st}$)

For a steady real sinusoid, the complex frequency $s$ has:

- no decay or growth → real part $σ=0$
- oscillation at frequency $ω$ → imaginary part $=ω$

So for a real sine wave, the complex frequency is purely imaginary:

$$
\underline{s} = \sigma + j\omega = 0 + j\omega = j\omega
$$


$$
\underline{Z}(\underline{s}) \;\xrightarrow{\;\underline{s} = j\omega\;}\; \underline{Z}(j\omega)
$$


The complex plane has two directions: horizontal ($σ$, decay/growth) and vertical ($ω$, oscillation). A real sine wave never decays or grows, it just oscillates forever at 
constant amplitude, so its $σ$ is always 0

So "sweeping frequency" = sliding the point $jω$  along the imaginary axis:


### On-axis vs off-axis zeros: real short vs shallow dip
- If that spot is **on the imaginary axis** (at some $j\omega_0$), then when you dial your generator to $\omega = \omega_0$, your point $j\omega$ lands right on it, and you 
measure $\underline{Z} = 0$ (a real short circuit you can actually observe).
- If that spot is **off the axis** (like $s_{2,1}$, which has a nonzero $\sigma$), then no matter what frequency you dial, your point $j\omega$ stays on the axis and never 
reaches that off-axis spot. You get *close* (impedance dips low) but never exactly zero.


### Rotation direction of complex-frequency point

"Rotation direction" refers to the direction in which the complex-frequency point rotates in the polar (complex) plane as time $t$ increases

The rotation direction is set entirely by the sign of $ω$ (the imaginary part of the point).

$$
\omega > 0 \;\Rightarrow\; \text{counter-clockwise (CCW)} \qquad \omega < 0 \;\Rightarrow\; \text{clockwise (CW)}
$$

### Lossless LC: the reactance function conditions
A passive lossless LC network always has all its poles and zeros on the imaginary axis."Lossless" means no resistors, so there's nothing in the circuit that dissipates energy.


## Reactance Diagram
a graph of the reactance $X(ω_n)$ versus frequency $ω_n$. It shows how inductive or capacitive a lossless LC network looks at each frequency.

Direction of the curve 
$$
\text{left of pole} \to +\infty \qquad\text{jump}\qquad -\infty \to \text{right of pole}
$$

the curve is ALWAYS rising.

<img src="/attachments/reactacne-chart.png" width="800" alt="reactacne-chart.png" />


## Realizability check: is it a lossless LC driving-point impedance?

For an impedance to be realizable using only passive inductors and capacitors, all four conditions below must hold. The pole-zero check is the fastest visual test: if any one
 condition fails, the function is not realizable as a passive lossless LC one-port.

- **Imaginary-axis location.** All finite poles and zeros must lie on the imaginary axis. The origin $s = 0$ may occur by itself, and every nonzero pole or zero must appear with 
its complex conjugate, i.e. as a pair $s = \pm j\omega_0$.
- **Poles and zeros are simple.** No repeated resonances at exactly the same frequency (no double poles or double zeros).
- **Poles and zeros alternate.** As frequency increases, the network alternates between resonance and anti-resonance, so poles and zeros must interlace along the axis.
- **Residues are positive.** Each residue becomes a positive $L$ or $C$ value in the synthesized circuit; a negative residue would require a negative (non-passive) element.


### Rule for behavior at infinity.
compare the degrees of the numerator and denominator polynomials

- **Numerator degree > denominator degree** → $\underline{Z} \to \infty$ as $\underline{s} \to \infty$ → **pole at infinity**.
- **Numerator degree < denominator degree** → $\underline{Z} \to 0$ as $\underline{s} \to \infty$ → **zero at infinity**.
- **Degrees equal** → $\underline{Z} \to$ a finite constant → **neither** (no pole or zero at infinity).

## Finding a pole or zero at infinity

A pole is where $Z \to \infty$; a zero is where $Z \to 0$. To check what happens at infinity, look at the leading (highest) powers of $\underline{s}$ on top and bottom, since only those matter as $\underline{s} \to \infty$:

$$
Z(\underline{s}) \sim \underline{s}^{\,\deg(\text{num}) - \deg(\text{den})}
$$

- **Numerator degree > denominator degree** → top outruns bottom → $Z \to \infty$ → **pole at infinity**.
- **Numerator degree < denominator degree** → bottom wins → $Z \to 0$ → **zero at infinity**.
- **Equal degrees** → $Z \to$ constant → neither.

Example: $Z_b \sim \dfrac{\underline{s}^4}{\underline{s}^3} = \underline{s} \to \infty$, so pole at infinity.

Keep two things separate: "at infinity" is *where* (very high frequency, far end of the $j\omega$ axis); "pole/zero" is *what* the impedance does there (blows up / vanishes).

Shortcut for LC functions: whichever polynomial has one extra root has its leftover critical point at infinity. Physically, a pole at infinity means the network looks like a series inductor at high frequency ($\underline{Z}_L = \underline{s}L \to \infty$). Always mark the infinity point at the top of the axis so the pole-zero alternation check runs all the way up.
