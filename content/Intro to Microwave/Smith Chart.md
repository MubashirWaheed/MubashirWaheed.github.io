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

$$
\lambda = \frac{c}{f \sqrt{\varepsilon_r}}
$$

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

### Reflection Coefficient and Phase  from Smith Chart 
$$|r_1| = \frac{\text{distance from center to } z_1}{\text{radius of chart (center to rim)}}$$

By formula

$$
|r| = \left| \frac{z - 1}{z + 1} \right| = \left| \frac{Z - Z_0}{Z + Z_0} \right|
$$

For the **phase** read the angle at the rim. the phase is given by convection from $+180$ to $-180$. Read Clockwise

### what is a Quater Wave Transformer?
quarter-wave transmission line changes the **real part (resistance)** of the impedance, not the imaginary part.

$Z_1​$ is the characteristic impedance the λ/4 section must have for the match to work. It's the target value you design the physical line to hit,
computed from:

$$
Z_1 = \sqrt{Z_S \cdot R}
$$

$$
\underbrace{Z_S}_{\text{source side}} \longrightarrow \Big[\ \lambda/4,\ Z_1\ \Big] \longrightarrow \underbrace{R}_{\text{load side, real}} \longrightarrow [\ \text{extra line}\ ] \longrightarrow Z_A \text{ (complex)}
$$

$Z_S$ = source side impeadnce you want to match to 

$R$ = the real impedance sitting at the output of the $λ/4$ transformer, on the load side. It is what the complex load $Z_A$ has been turned into
after the extra line rotated it onto the real axis of the Smith chart. It must be purely real for the transformer to work.

### Physical length of the transformer ($\ell$ = length to cut, $\lambda$ = the wavelength from above):
$$
\ell = \frac{\lambda}{4}
$$

### Wave length on line given by 

$\lambda=$ wavelength on the transmission line, $c$ = speed of light, $f$ = frequency, $\varepsilon_r$ = relative permittivity of the dielectric):

$$
\lambda = \frac{c}{f \sqrt{\varepsilon_r}}
$$

### Concept: rotating the load with a line section
A length of line is used to rotate the load impedance around the Smith chart (along a circle of constant $|\Gamma|$) until it lands on either 
the $r=1$ circle or the $g=1$ circle. Once on that circle, the remaining reactive part is cancelled with a lumped element (capacitor or inductor, 
in series or in parallel) to reach the center.Rotation along the constant $|\Gamma|$ circle changes both the real and the reactive 
parts of the impedance. At the two points where this circle crosses the horizontal axis of the Smith chart, the reactance passes through zero, 
so the impedance there is purely real.

### Stub line 
A stub is a piece of line whose only job is to present a pure reactance (or susceptance) at the point where it's connected. A parallel/shunt 
stub adds a pure susceptance $jb$ to the main line, moving you along a constant-g circle, 

## Parallel(shunt) stub 

### When to use parallel short circuited vs parallel open circuited stub lines?
 
Mark the reactance/suseptance value on the smith chart  of the componeent is si being replaced by the stub line then order to figureout which stub to use start from
zero(left real part) and reach the imaginary value present on the rim do same but from the right side (clockwise) which ever has the shortest path we use that. 

**Shorted shunt stub**  starts at $y = \infty$ (short = infinite admittance), right edge.

**Open shunt stub**  starts at $y = 0$ (open = zero admittance), left edge.

When a component eg inductor or capacitor is replaced by stub line we have to deterrmine teh length of the line which produces the same 
suseptance value as component and we always start at the termination of the stub and increase length. Rotation is always clockwise since 
technically we are moving towards the generator. We mark the point on the outer rim(susceptance value) and start clockwise from $y=0$ left edge 
or $y = \infty$ right edge which ever gives shorter path.

If element(inductor or capacitor) is in parallel then convert to admiatnce to  find the normalized value in smith chart 

Shorter legth = more bandwidth, lower loss

A short-circuited or open-circuited lossless stub produces only the imaginary part (reactance in impedance, or susceptance in admittance) and no real part.

### VSWR from reflection coefficient
$s$ = standing wave ratio, $|\Gamma|$ = magnitude of reflection coefficient at the load

$$
s = \frac{1 + |\Gamma|}{1 - |\Gamma|}
$$

- voltage minimum in admitance sits on the right side of smith chart (always on the horizontal line)
- voltage minimum in impedacne sits on the left side of smith chart (always on horizontal line)

### Voltage maximum and current minimum from the VSWR
where s= VSWR
$$
U_{max} = s\cdot U_{min} \qquad I_{min} = \frac{I_{max}}{s}
$$ 

When moving from the element(capacitor, indctor)in stub line of certain length(eg 3.5) that movement is translated as tworads generated hence clockwise on smith chart

You invert (go to admittance) only when you're combining a shunt element with something else in parallel, because parallel admittances add:
$$y_{total​}=y_4​+y_{AP}$$

**broadband as possible** (shortest transformation path)

**Important:** Constant **$g (r)$** cicle changes only the **susceptance b**

On the impedance only printed chart the **$g=1$** is only on the right side of the chart.


### Voltage and current curve on one line

On smith chart Voltage line always from the right side , current always from left side

#### Impedance case (reading $z=r+jx$):

Right crossing, high resistance (r>1): this is the voltage-maximum, current-minimum point. High impedance means for a given current the voltage is large → ∣U∣ max.

Left crossing, low resistance (r<1): this is the voltage-minimum, current-maximum point. Low impedance → ∣U∣ min, ∣I∣ max.

#### Admittance case (reading $y=g+jb$):

Right crossing, high conductance ($g>1$): current-maximum, voltage-minimum (what we used, $y_0$).

Left crossing, low conductance ($g<1$): current-minimum, voltage-maximum.
<img src="volatge-curent.png" alt="volatge-curent" width="400"/>

Current always on left and voltage always on right


Understood constant Conductance(reactacne) circle, constant reactance arcs, constant VSWR circle(cenetr at the center of smith chart).

Also there is no $2 \pi$ used in $v= f\lambda$ while calculating the wavelength


# Cases where r=1 or g=1 circle used and when lambda/4 tranformer used the toplogy of circuit(series element)
