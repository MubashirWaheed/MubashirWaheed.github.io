---
title: 02 Linearity and Time Invariance
---


## Formula 1: Linearity (superposition principle)

$$
\mathrm{S}\{A x_1(t) + B x_2(t)\} = A\ \mathrm{S}\{x_1(t)\} + B\ \mathrm{S}\{x_2(t)\}
$$

## Formula 2: Time-invariance (shift invariance)

$$
\mathrm{S}\{x(t-\tau)\} = y(t-\tau), \qquad \text{where } y(t) = \mathrm{S}\{x(t)\}
$$


## Numeric anchors 

Numbers cannot prove a property, only disprove one. Use these to reconstruct the symbolic proof from memory, then write the symbolic version in the exam.

### Linearity anchor: $x_1(t) = t^2$, $x_2(t) = t^3$, $A = 3$, $B = 5$

Path one, mix first:

$$
\frac{\mathrm{d}}{\mathrm{d}t}\big[3t^2 + 5t^3\big] = 6t + 15t^2
$$

Path two, differentiate first, then mix, using $\dot{x}_1(t) = 2t$ and $\dot{x}_2(t) = 3t^2$:

$$
3\,(2t) + 5\,(3t^2) = 6t + 15t^2
$$

Same result. The constants rode through untouched and the two terms never interfered.

### Time-invariance anchor: $x(t) = t^2$, $\tau = 2$

Path one, delay first, then differentiate:

$$
x(t-2) = (t-2)^2 = t^2 - 4t + 4 \quad\longrightarrow\quad \frac{\mathrm{d}}{\mathrm{d}t}\big[t^2 - 4t + 4\big] = 2t - 4
$$

Path two, differentiate first, then delay, using $y(t) = 2t$:

$$
y(t-2) = 2(t-2) = 2t - 4
$$

Same result. Expanding and differentiating produced $2(t-2)$ by itself, which is the chain rule with inner factor $1$.

### Contrast anchor 1: time-variant system with its own clock

For $y(t) = t \cdot x(t)$ with $x(t) = t^2$ and $\tau = 2$:

$$
\text{delay first: } t\,(t-2)^2 \qquad\text{versus}\qquad \text{system first: } y(t-2) = (t-2)^3
$$

At $t = 3$ these give $3$ and $1$. Different, so time-invariance fails. The leading $t$ was never shifted in path one because it belongs to the system, not the signal.

### Contrast anchor 2: nonlinear system

For $y(t) = x^2(t)$ with $A = 2$ and input value $3$:

$$
\mathrm{S}\{2 \cdot 3\} = 36 \qquad\text{versus}\qquad 2\ \mathrm{S}\{3\} = 18
$$

Doubling the input quadrupled the output. Here the numbers are a valid proof, since one failing case is enough to disprove.


Will come back to this proof latter for better understanding
