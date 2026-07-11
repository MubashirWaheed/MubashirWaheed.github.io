---

title: Resonant Circuits

---

### Series vs Parallel Resonant Circuits 

resonant circuit exchanges energy between the inductor's magnetic field and the capacitor's electric field. Resonance is an 
AC phenomenon (needs ω≠0\omega \neq 0ω=0). At resonance, the reactive parts cancel and the impedance becomes purely real.


At DC: inductor = short (Z_L \to 0 ), capacitor = open (Z_C \to \infty).

In series: Capacitor blocks the single path

In Parallel: Inductor shorts the terminals


in series the largest branch impedance dominates; in parallel the smallest dominates.

### Resonant Frequency
$$\omega_0 = \frac{1}{\sqrt{LC}}, \qquad f_0 = \frac{1}{2\pi\sqrt{LC}}$$

### Series Resonant Circuit 
$$Z = R + j\omega L + \frac{1}{j\omega C} = R + j\left(\omega L - \frac{1}{\omega C}\right)$$


At resonance the imaginary part of impedance cancels:

- $Z = R$  (purely real, minimum impedance)
- Behaves like a short-ish path at $f_0$, blocks DC

### Parallel Resonant Circuit 
$$Y = \frac{1}{R} + j\omega C + \frac{1}{j\omega L} = \frac{1}{R} + j\left(\omega C - \frac{1}{\omega L}\right)$$

At resonance the imaginary part of admittance cancels:

- $Y = 1/R \Rightarrow Z = R$ (purely real, maximum impedance)
- Peaks at $f_0$, shorts at DC

### Quality Factor Q
$$Q = \frac{f_0}{\Delta f}$$

$Δf$ = bandwidth, $Q$ = sharper/narrower resonance

### Series $Q$ 
$$Q_{\text{series}} = \frac{\omega_0 L}{R} = \frac{1}{R}\sqrt{\frac{L}{C}}$$


### Parallel $Q$
$$Q_{\text{parallel}} = \frac{R}{\omega_0 L} = R\sqrt{\frac{C}{L}}$$ 


### Characteristic Impedance
$$Z_K = \sqrt{\frac{L}{C}} = \omega_0 L = \frac{1}{\omega_0 C}$$
