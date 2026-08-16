---
title: 06 Bode Plot
---

A transfer function $G(sn)$ is a general mathematical object. But a Bode plot specifically shows how the system responds to sinusoidal (harmonic) 
inputs at different frequencies.

### Rule from signals theory: 
when your input is a pure sine wave of frequency $ω$, you evaluate the transfer function at $s=jω$.  You just substitute $s_n→jω_n$  everywhere.


$$
G(s_n) = \frac{s_n + 1}{(s_n + 100)^2} \quad\Rightarrow\quad G(j\omega_n) = \frac{j\omega_n + 1}{(j\omega_n + 100)^2}
$$

When $\omega_n \ll a$: $\sqrt{\omega_n^2 + a^2} \approx a$ (constant, flat line)

When $\omega_n \gg a$: $\sqrt{\omega_n^2 + a^2} \approx \omega_n$ (rises, sloped line)

The changeover happens at $\omega_n = a$. That is the corner.

### Magnitude of one factor:
$$
|j\omega_n + a| = \sqrt{\omega_n^2 + a^2}
$$
Taking the magniude of the numerator and denominator 
