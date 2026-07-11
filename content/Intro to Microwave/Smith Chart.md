--- 

title: Smith Chart 

---

## Denormalization on the Smith Chart

**Core rule: actual = normalized × reference**

- Impedance reference is $Z_0$; admittance reference is $Y_0 = 1/Z_0$.
- The differing reference is why impedance "multiplies" but admittance "divides".

**Impedance (multiply by $Z_0$)**

$$z = \frac{Z}{Z_0} \quad\Rightarrow\quad Z = z \cdot Z_0$$

Read $z = r + jx$, then $R = r \cdot Z_0$ and $X = x \cdot Z_0$.

**Admittance (divide by $Z_0$)**

$$y = \frac{Y}{Y_0} = Y \cdot Z_0 \quad\Rightarrow\quad Y = \frac{y}{Z_0}$$

Read $y = g + jb$, then $G = \dfrac{g}{Z_0}$ and $B = \dfrac{b}{Z_0}$.

**Component values from parallel admittance $y = g + jb$**

- Parallel resistance: $\displaystyle R = \frac{1}{G} = \frac{Z_0}{g}$
- Sign of $b$: $b > 0 \Rightarrow$ capacitor, $b < 0 \Rightarrow$ inductor
- Capacitor: $B = \omega C \;\Rightarrow\; C = \dfrac{B}{\omega}$
- Inductor: $B = -\dfrac{1}{\omega L} \;\Rightarrow\; L = \dfrac{1}{\omega\ |B|}$

**Worked example** ($y_1 = 0.275 - j0.91,\ Z_0 = 50\ \Omega,\ f = 1\ \text{GHz}$)

$$R_1 = \frac{Z_0}{g} = \frac{50\ \Omega}{0.275} = 182\ \Omega$$

$$b < 0 \;\Rightarrow\; \text{inductor}$$

$$L_1 = \frac{1}{\omega \cdot \dfrac{|b|}{Z_0}} = \frac{1}{2\pi \cdot 10^9 \cdot \dfrac{0.91}{50\ \Omega}} = 8.7\ \text{nH}$$


## Line Length to Smith Chart Rotation

The Smith chart rotates by **electrical length** (fraction of a wavelength $\ell/\lambda$), not physical length. Convert cm into $\lambda$ first.

**Step 1: Wavelength on the line** (the dielectric slows the wave, so include $\varepsilon_r$)

$$\lambda = \frac{c}{f \sqrt{\varepsilon_r}}$$

where $c = 3 \times 10^8\ \text{m/s}$, $f$ = frequency, $\varepsilon_r$ = relative permittivity.

**Step 2: Electrical length** (the value you rotate on the chart)

$$\frac{\ell}{\lambda}$$

**Step 3 (optional): Convert to angle.** One full turn of the chart $= 0.5\lambda = 360°$:

$$\theta = \frac{\ell}{\lambda} \cdot \frac{360°}{0.5} = \frac{\ell}{\lambda} \cdot 720°$$

**Direction of rotation**

- Toward the generator: clockwise
- Toward the load: counterclockwise

**Worked example** ($\ell_1 = 4.45\ \text{cm},\ \varepsilon_r = 2,\ f = 1\ \text{GHz}$)

$$\lambda = \frac{3 \times 10^8}{10^9 \cdot \sqrt{2}} = 0.2121\ \text{m} = 21.21\ \text{cm}$$

$$\frac{\ell_1}{\lambda} = \frac{4.45\ \text{cm}}{21.21\ \text{cm}} = 0.21\ \lambda$$

$$\theta = 0.21 \cdot 720° = 151°$$

So rotate $0.21\lambda$ (about $151°$) clockwise toward the generator.S

### Reflection Coefficient from Smith Chart 
$$|r_1| = \frac{\text{distance from center to } z_1}{\text{radius of chart (center to rim)}}$$

By formula

$$|r| = \left| \frac{z - 1}{z + 1} \right| = \left| \frac{Z - Z_0}{Z + Z_0} \right|$$
### what is a quater wave transformer?

### When to use parallel short circited stub lines vs parallel open circuited stub lines?

### Conversion of the conversion of the wavlength to rotational value for the smith chart?
