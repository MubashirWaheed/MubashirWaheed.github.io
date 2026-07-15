---

title: Resonant Circuits

---

### Series vs Parallel Resonant Circuits 

resonant circuit exchanges energy between the inductor's magnetic field and the capacitor's electric field. Resonance is an 
AC phenomenon (needs ω≠0\omega \neq 0ω=0). At resonance, the reactive parts cancel and the impedance becomes purely real.


At DC: inductor = short $(Z_L \to 0 )$, capacitor = open $(Z_C \to \infty)$.

In series: Capacitor blocks the single path

In Parallel: Inductor shorts the terminals


in series the largest branch impedance dominates; in parallel the smallest dominates.


### Series RLC at resonance
reactances cancel in a loop, impedance goes to a minimum, current is maximum. Resonance = easy path.

### Parallel RLC at resonance
 currents cancel at a node, impedance goes to a maximum, source current is minimum. Anti-resonance = blocked path.

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

### Capacitor Quality Factor
$Q_C​$ measures how lossless a real capacitor is. It is the ratio of its reactance to its series loss resistance (ESR). Higher
$Q_C$ means lower loss

$$Q_C = \frac{1}{\omega R_s C} = \frac{1}{\tan\delta}$$

### Real Capacitor Modeled
- **Ideal capacitance $C$**: Represents the actual intended capacitance, the charge storage between the two plates separated by 
dielectric.
- **Series inductor**: represents inductance of current path through the component, mainly the leads, terminals, and geometry of 
plates/windings. Basically lead inductance
- **Series resistor**: represents ohmic $(I²R)$ losses in the conducting path: the resistance of  leads, terminals, plates, and 
contacts. Contact + lead resistance
- **Parallel resistor (leakage / dielectric loss)**: sits across the capacitor, in parallel and represents two things
	- DC leakage. No dielectric is a perfect insulator, so a tiny current leaks straight through it from one plate to the other
	- dielectric loss. Under AC, the dielectric material absorbs and dissipates some energy each cycle as its molecules repeatedly polarize. This shows up as an additional loss modeled by the parallel resistance

### Real Inductor Modeled
- **Ideal inductance L**: Represents the actual intended inductance, the magnetic energy storage from current flowing through 
the coil windings.
- **Series resistor** (winding resistance): usually labeled $R_s$. Represents ohmic $(I^2 R)$ losses in the wire forming the coil: DC copper resistance, plus extra resistance at high frequency from skin effect and proximity effect. Current must flow through
 the whole coil, so this sits in series and sets the quality factor Q.
- **Parallel capacitor** (parasitic winding capacitance): usually labeled $C_p$. Sits across the inductor, in parallel. 
Represents capacitance between adjacent turns of the winding (and between winding and core/shield).
- **Optional: core loss resistance**: for a magnetic core, a resistor is sometimes added (often in parallel) to model core losses: hysteresis and eddy currents.

### General Discharge (Self-Discharge) Time Constant of a Capacitor
$$
\tau = R \cdot C
$$

$τ$ = time constant (seconds), $R$  = resistance through which the capacitor discharges (ohms), $C$ = capacitance (farads)

time constant $\tau$ is the characteristic time for a capacitor to charge or discharge through a resistor R. 
A small $\tau$ means fast discharge.
