---
title: Important Formulas 
---

### Trigonometric Identities (used in RLC / Laplace problems)

**Euler's formula** (turns complex exponential into sin/cos, the reason complex poles give oscillation):

$$
e^{jx} = \cos x + j\sin x
$$

**Sine addition theorem** (used to combine $\cos + \sin$ into a single phase-shifted sine):

$$
\sin(\alpha + \beta) = \sin\alpha\cos\beta + \cos\alpha\sin\beta
$$

**Cosine addition theorem** (used when deriving the current $i_L(t)$):

$$
\cos(\alpha + \beta) = \cos\alpha\cos\beta - \sin\alpha\sin\beta
$$

**Combining cos and sin into one sinusoid** (what the addition theorem achieves in practice):

$$
A\cos\omega t + B\sin\omega t = R\sin(\omega t + \gamma), \qquad R = \sqrt{A^2 + B^2}, \quad \gamma = \arctan\frac{A}{B}
$$

**Periodicity of sine** (used when shifts are multiples of $2\pi$):

$$
\sin(t - 2\pi m) = \sin t \quad(\text{any integer } m)
$$


## Same but shifted
$$
\cos(x) = \sin\left(x + \frac{\pi}{2}\right)
$$
