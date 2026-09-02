---
title: 07 Nonlinear Networks
---
### Main Skills to be learned 

1. **Operating points:** Finding where a nonlinear component sits in a circuit (Key idea: a nonlinear element can have multiple operating points.)
2. **Transient behavior with an inductor (T4.2, H4.1)** (Diode curve is non-monotonic, you get the jump phenomenon: the operating point slides along a branch, hits a fold, and jumps 
discontinuously)
3. **Time-variant capacitor / energy harvesting (H4.2, H4.3):** An LC resonant circuit where the capacitance is deliberately switched $(C_0→C_0−ΔC)$ at each charge extremum 
and back at each zero crossing.

## Core components involved

- **Nonlinear resistor / tunnel diode (Esaki diode):** described by a current-voltage cubic $i_n(u_n) = u_n^3 - 6u_n^2 + 9u_n$. Its non-monotonic (N-shaped) curve is the source of all the interesting behavior.
- **Linear resistors** ($R_1, R_2, R$) and **DC voltage sources** ($U$, $U_Q$).
- **Inductor** $L$ (energy storage, gives first-order ODEs in time).
- **Time-variant capacitor** $C(t)$ (the energy-harvesting idea).


## Thévenin Equivalent for Circuits with a Nonlinear Component

### Why do it
- A circuit with one **nonlinear** element (rest linear) can't be solved with linear tools alone, because a relation like $i = f(u)$ (e.g. a cubic) breaks superposition and matrix methods.
- **Thévenin's theorem:** any linear network seen from two terminals behaves like one voltage source $U_Q$ in series with one resistor $R_Q$. All internal sources and resistors collapse into two numbers.
- The circuit reduces to: source + resistor + nonlinear element → two unknowns ($u, i$), two equations:
  - Load line (linear side): $u = U_Q - R_Q\, i$
  - Characteristic curve (nonlinear side): $i = f(u)$
- **Operating point** = intersection of the load line and the characteristic curve.

<img src="attachments/nolinear-network.png" width="380" />
<img src="attachments/converted-nonlinear-circuit.png" width="380" height="205"/>

### Getting the two Thévenin parameters
- $R_Q$ (internal resistance): set all independent sources to zero (short voltage sources, open current sources), find the resistance looking into the terminals → sets the slope of the load line.
- $U_Q$ (open-circuit voltage): find the terminal voltage with the load removed ($i = 0$, so $R_Q$ drops nothing) → sets where the load line meets the voltage axis.

### Worked example
Linear part: source $U$ feeding $R_1$ in series, with $R_2$ across the terminals; nonlinear element connects at the terminals.

**Internal resistance** (short the source, so $R_1 \parallel R_2$ seen at terminals):
$$R_Q = R_1 \parallel R_2 = \frac{R_1 R_2}{R_1 + R_2}$$

**Open-circuit voltage** (terminals open, $i = 0$, no current in $R_1$, so $R_2$ forms a divider):
$$U_Q = U \cdot \frac{R_2}{R_1 + R_2}$$

**Plug in numbers** ($U = 12\,\text{V}, R_1 = 2\,\Omega, R_2 = 4\,\Omega$):
$$R_Q = \frac{2 \cdot 4}{2 + 4} = \frac{8}{6} = 1.33\ \Omega$$
$$U_Q = 12 \cdot \frac{4}{2 + 4} = 12 \cdot \frac{2}{3} = 8\ \text{V}$$

Load line becomes $u = 8 - 1.33\, i$; intersect with $i = f(u)$ to find the operating point(s).

## Operating Point
An operating point is just the actual voltage and current the circuit settles at when you turn it on. That's it. It's one specific pair of numbers, $(u,i)$, that describes the 
real state of the circuit sitting there in equilibrium.

### Sketching a cubic characteristic by hand

Four pieces of info fully fix the shape:

1. **Turning points** (from $di/du = 0$): the max and min corners.
   - e.g. max $(1, 4)$, min $(3, 0)$
2. **Zeros** (factor the cubic): where the curve meets the $u$-axis.
   - e.g. $i = u(u-3)^2 \Rightarrow$ zeros at $u = 0$ and $u = 3$
3. **Slope pattern** (sign of $di/du$ between turning points):
   - rising → max(point reached) → falling (neg-resistance branch) → min(point) → rising

Then connect the points smoothly following the slope pattern. Optional: plug in one extra $u$ (e.g. $u=2 \Rightarrow i=2$) for a point on the middle branch.

$$
i = u^3 - 6u^2 + 9u
$$

$$
i = u\,(u^2 - 6u + 9)
$$

$$
u^2 - 6u + 9 = (u-3)(u-3) = (u-3)^2
$$

$$
i = u\,(u-3)^2
$$

## Solving the cubic equation for operating points

Cubic has no easy root formula → strategy: knock it down to a quadratic.

1. Set curves equal (linear and linear element equations) → :
   $$u^3 - 6u^2 + 10u - 4 = 0$$
2. Find ONE root by trial (test divisors of the constant term $-4$: $\pm1, \pm2, \pm4$;). Here $u = 2$ gives $8 - 24 + 20 - 4 = 0$ 
3. Divide the cubic by $(u - \text{root})$ → leaves a quadratic:
   $$(u^3 - 6u^2 + 10u - 4) \div (u - 2) = u^2 - 4u + 2$$
4. Solve the quadratic with the formula:
   $$u = \frac{4 \pm \sqrt{16 - 8}}{2} = 2 \pm \sqrt{2}$$
5. Three roots: $u = 2,\ 2+\sqrt{2},\ 2-\sqrt{2}$. Get each current from $i = 4 - u$.

## Finding operating points graphically

Instead of solving algebraically, plot both characteristics on one $i$–$u$ graph and read off the crossings.

1. Draw the nonlinear curve $i = u^3 - 6u^2 + 9u$ (the N-shape).
   - Turning points (using first derivative) : max $(1, 4)$, min $(3, 0)$; zeros at $u = 0, 3$.
2. Draw the load line $i = 4 - u$ (straight line).
   - Two points are enough: $u = 0 \Rightarrow i = 4$; $i = 0 \Rightarrow u = 4$.
3. **Operating points = where the line crosses the curve.**
   - Here it crosses 3 times → three operating points.
   - Read off approximate $(u, i)$ at each crossing.

Why 3 crossings: a straight line can cut the N-shape in up to three places. A linear component (straight-line characteristic) would give only one.

<img src="attachments/characteristic-curve-non-linear.png" width="450" />

## Characteristic Curve
A characteristic curve is a graph that shows the relationship between the voltage across a component and the current through it.Each component has its own characteristic curve. 
In a series loop they share the same $u$ and $i$, so the actual state must lie on both curves at once, hence the intersection. The load line is literally the characteristic curve
 of the whole linear part (source + resistor) reduced via Thévenin.

### Diode 
A diode is a special type of resistor, specifically a nonlinear resistor. It sits inside the resistor family (instantaneous $i - u$ relationship, no memory), but its curve is 
bent instead of straight. Every diode is a nonlinear resistor, and every nonlinear resistor is a resistor (in the general sense), but not the other way around, a plain linear 
resistor is not a diode.

## Finding current from the differential Equation

$$
\frac{di_n}{dt_n} = -i_n^2 + 8i_n + 9
$$

$$
\underbrace{\frac{di_n}{dt_n}}_{\text{rate (what the ODE gives)}} \quad\xrightarrow{\ \text{integrate}\ }\quad \underbrace{i_n(t_n)}_{\text{the current itself (what we want)}}
$$
Seperate varaibles:
$$
\frac{di_n}{-i_n^2 + 8i_n + 9} = dt_n
$$
integrate both sides 
$$
\int_{0}^{t_n} d\tilde t_n \;=\; \int_{i_n(0)}^{i_n(t_n)} \frac{-1}{\tilde i_n^2 - 8\tilde i_n - 9}\, d\tilde i_n
$$
in order to integrate the right side it is easier to decompose using partial fraction



$$
\begin{aligned}
t_n &= -\int_0^{i_n(t_n)} \frac{1}{(\tilde{i}_n + 1)(\tilde{i}_n - 9)}\ d\tilde{i}_n \\[2ex]
&= \frac{1}{10} \int_0^{i_n(t_n)} \left( \frac{1}{\tilde{i}_n + 1} - \frac{1}{\tilde{i}_n - 9} \right) d\tilde{i}_n \\[2ex]
&= \frac{1}{10} \left[ \ln|\tilde{i}_n + 1| - \ln|\tilde{i}_n - 9| \right]_0^{i_n(t_n)}
\end{aligned}
$$


$$
t_n = \frac{1}{10}\ln\left(\frac{i_n + 1}{9 - i_n}\cdot\frac{9}{1}\right) = \frac{1}{10}\ln\frac{9 + 9i_n}{9 - i_n}
$$

$$
\text{Applying } e^{(\cdot)} \text{ to both sides and using } e^{\ln x} = x:
$$

$$
e^{10 t_n} = \frac{9 + 9i_n}{9 - i_n}
$$

$$
e^{10 t_n}(9 - i_n) = 9 + 9i_n \;\Rightarrow\; 9e^{10 t_n} - i_n e^{10 t_n} = 9 + 9i_n
$$

$$
9e^{10 t_n} - 9 = 9i_n + i_n e^{10 t_n} = i_n\left(e^{10 t_n} + 9\right)
$$

$$
i_n(t_n) = \frac{9e^{10 t_n} - 9}{e^{10 t_n} + 9}
$$

### Inflection Point

An inflection point is where a curve changes concavity, switching from bending one way to the other.

Condition

$$
\frac{d^2 i_n}{dt_n^2} = 0 \quad \text{and changes sign at that point}
$$


## Change of Variables Inside a Derivative

### The Rule (memorize this)

If you scale both variables by constants, the constants factor out:

$$
\frac{d(a\,x_n)}{d(b\,t_n)} = \frac{a}{b}\cdot\frac{dx_n}{dt_n}
$$


Numerator constant multiplies, denominator constant divides. That's it.

### Example

Given $i = I_0 i_n$ and $t = \frac{3LI_0}{2U_0}t_n$, so $a = I_0$ and $b = \frac{3LI_0}{2U_0}$:

$$
\frac{di}{dt} = \frac{I_0}{\frac{3LI_0}{2U_0}}\cdot\frac{di_n}{dt_n} = \frac{2U_0}{3L}\cdot\frac{di_n}{dt_n}
$$

While writing the differential equation of a system containing non linear component and inductor/capacitor when using eg $L\frac{di}{dt}$ and 
we have to normalize based on the given factor we can directly substitute in the derivative. Example shown above


## Chain rule: converting a current-rate into a voltage-rate

### The identity
$$
\frac{di_n}{dt_n} = \frac{di_n}{du_n}\cdot\frac{du_n}{dt_n}
$$

Read as: (rate of current in time) = (slope of the i-u curve) × (rate of voltage in time).
The $du_n$ formally cancels top-and-bottom, which is the intuition for why it holds.

### When to use it
- The circuit's ODE (from KVL) comes out with $\frac{di_n}{dt_n}$, but the problem
  wants the equation in $u_n$ only (e.g. to solve for $t_n(u_n)$).
- The equation then has TWO unknowns (current term AND voltage term) → unsolvable.
- Use the identity to trade the current-rate for a voltage-rate → one variable left.

### Why it's valid
- Current isn't independent: the diode curve $i_n = f(u_n)$ locks it to the voltage.
- So current changes over time ONLY because voltage changes over time.
- The chain rule expresses exactly that dependency.


###  EXAMPLE (H4.1)


### **Solving a nonlinear circuit ODE: using the chain rule and the diode's characteristic curve to rewrite $di_n/dt_n$ as $du_n/dt_n$**
$$
2 = \frac{2}{3}\frac{di_n}{dt_n} + u_n
$$
Problem: contains $\frac{di_n}{dt_n}$ (current) AND $u_n$ (voltage) → two unknowns.
Want: everything in $u_n$.

**Step 1 — slope of the characteristic curve** (differentiate the diode cubic):
$$i_n = u_n^3 - 6u_n^2 + 9u_n \;\Rightarrow\; \frac{di_n}{du_n} = 3u_n^2 - 12u_n + 9$$

**Step 2 — apply the chain rule** (replace the current-rate):
$$\frac{di_n}{dt_n} = \underbrace{(3u_n^2 - 12u_n + 9)}_{di_n/du_n}\cdot\frac{du_n}{dt_n}$$

**Step 3 — substitute back into the ODE:**
$$2 = \frac{2}{3}(3u_n^2 - 12u_n + 9)\frac{du_n}{dt_n} + u_n$$
Now only $u_n$ and $\frac{du_n}{dt_n}$ remain. 

**Step 4 — tidy constants** (factor 3, then $\tfrac{2}{3}\times 3 = 2$):
$$2 = 2(u_n^2 - 4u_n + 3)\frac{du_n}{dt_n} + u_n$$
Finished ODE in voltage form.


### The reverse direction works too
If you had a voltage ODE and wanted current, flip it:
$$\frac{du_n}{dt_n} = \frac{du_n}{di_n}\cdot\frac{di_n}{dt_n}$$
with $\frac{du_n}{di_n}$ = slope of the u-i characteristic.


### One-line takeaway
$$\frac{d(\text{one variable})}{dt} = \big(\text{slope of characteristic curve}\big)\times\frac{d(\text{other variable})}{dt}$$
The characteristic curve is the bridge that lets you swap which variable the ODE is written in.


## Substitution formulas — capacitor present
When asked to write the differential equation (ODE) for  capacitor charge $q(t)$ after writing the KCL or KVL around the  circuit we do 
subsitition for the charge using the below equation so that current and volatge is remvoed and the equaiton only contains charge 
eg 
$$
L\frac{d^2q}{dt^2} + R\frac{dq}{dt} + \frac{1}{C(t)}q(t) = 0
$$

Current as rate of change of charge:
$$
i(t) = \frac{dq}{dt}
$$

Charge–voltage–capacitance relation (time-varying C):
$$
q(t) = C(t)\,u_c(t) \;\Rightarrow\; u_c(t) = \frac{q(t)}{C(t)}
$$


## Key property: sine and cosine are their own negative second derivative

Differentiating sin or cos TWICE returns the same function with a minus sign:

$$\frac{d^2}{dt^2}\sin(\omega t) = -\omega^2 \sin(\omega t)$$
$$\frac{d^2}{dt^2}\cos(\omega t) = -\omega^2 \cos(\omega t)$$

They are the ONLY basic functions with this "curves back toward zero in
proportion to their own height" behavior.


### Why it matters
- Any system obeying  d²x/dt² = -(const)·x  MUST oscillate as sin/cos.
- That equation = "acceleration points back toward zero, proportional to
  displacement" = the definition of simple harmonic motion.
- Appears everywhere: LC circuits, masses on springs, pendulums (small angle),
  vibrations, waves.
- The constant sets the frequency: $d²x/dt² = -ω²x$ → oscillates at ω.

### The one-line takeaway
"Second derivative = minus a copy of itself" is the mathematical fingerprint
of oscillation, and sine/cosine are the functions that carry it.


## Solving differential equation full working: LC oscillator via $q = e^{st}$ (H4.2b)

ODE:
$$
L\frac{d^2q}{dt^2} + \frac{1}{C_0}q = 0
$$

1. Trial $q = e^{st}$: derivatives bring down $s$ each time.
2. Substitute:
$$Ls^2 e^{st} + \frac{1}{C_0}e^{st} = 0$$
3. Cancel $e^{st}$ (never zero) → characteristic equation:
$$Ls^2 + \frac{1}{C_0} = 0$$
4. Solve:
$$s^2 = -\frac{1}{LC_0} \;\Rightarrow\; s = \pm j\frac{1}{\sqrt{LC_0}} = \pm j\omega_0, \qquad \omega_0 = \frac{1}{\sqrt{LC_0}}$$
   (imaginary roots → oscillation)
5. General solution:
$$q = K_1 e^{j\omega_0 t} + K_2 e^{-j\omega_0 t} \;\xrightarrow{\text{Euler}}\; q = A\cos(\omega_0 t) + B\sin(\omega_0 t)$$
6. Initial conditions:
$$q(0) = 0 \;\Rightarrow\; A = 0 \;\Rightarrow\; q = B\sin(\omega_0 t)$$
$$\frac{dq}{dt}\bigg|_0 = i_0 \;\Rightarrow\; B\omega_0 = i_0 \;\Rightarrow\; B = \frac{i_0}{\omega_0}$$

Result:
$$
q(t) = \frac{i_0}{\omega_0}\sin(\omega_0 t) = i_0\sqrt{LC_0}\,\sin\frac{t}{\sqrt{LC_0}}
$$

### Finding harmonmic Solution

A harmonic solution is one that's a pure sinusoid, a clean sine or cosine wave at a single frequency, oscillating forever with constant amplitude.
 "Harmonic" literally means "sinusoidal / wave-like." Example above


## Energy harvesting, simple version (H4.2c)
Big idea: pump the oscillation by changing the capacitor at the right moments,
like pushing a swing in time.

- Charge oscillates (sine wave), full ↔ empty.
- At FULL charge (peak): shrink C. Costs effort → ADDS energy. (the "push")
- At EMPTY charge (zero): reset C to normal. Costs nothing → FREE reset.
- Repeat each half-cycle → energy accumulates = harvesting.

Why these moments: changing C is expensive when charged (so you gain energy)
and free when empty (so you reset for nothing).

The formulas just track:
- T₁ = first peak (shrink C), T₂ = next zero (reset C).
- Between them the wave is a COSINE (it starts at a peak).
- Smaller C → faster oscillation (ω₀ → ω₁).


## Where does the oscillation frequency come from?

Two cases:

**1. Driven (forced) oscillation** — frequency set by the INPUT.
- An external AC source at frequency $\omega_{\text{drive}}$ forces the circuit to
  oscillate at that driving frequency.
- The input signal dictates the frequency.
- True for most powered/signal-fed circuits (radio fed a signal, amplifier, mains devices).

**2. Free (natural) oscillation** — frequency set by the COMPONENTS.
- Give the circuit one kick, then let it go with no ongoing input.
- It oscillates at its natural frequency, set purely by $L$ and $C$:
$$\omega_0 = \frac{1}{\sqrt{LC}}$$
- Like a struck bell ringing at its own pitch. Smaller $C$ → higher frequency.


**Link — resonance:** a driven circuit responds strongest when the drive frequency
matches $1/\sqrt{LC}$. Tuning a radio = adjusting $C$ so the natural frequency
matches the station. So $1/\sqrt{LC}$ is the circuit's "preferred" frequency in both cases.


## Max charge on capacitor ↔ zero current

### The basic concept
Current is the rate of change of stored charge:
$$i = \frac{dq}{dt}$$
So the current depends on how fast the charge is CHANGING, not on how much charge
is stored. At a maximum, the charge is momentarily not changing (its slope is zero),
so the current is zero there.

### The two cases

**Case 1 — charge maximum → current zero**
- The capacitor is fully charged, $q$ is at its peak.
- At a peak the charge is momentarily flat: $\frac{dq}{dt} = 0$.
- Therefore $i = 0$.
- Energy: all of it is stored in the CAPACITOR (full), none in the inductor.

**Case 2 — charge zero → current maximum**
- The capacitor is empty, $q = 0$ (a zero crossing).
- At the crossing the charge is changing fastest (steepest slope).
- Therefore $i$ is at its MAXIMUM.
- Energy: all of it is in the INDUCTOR (max current), none in the capacitor.


$q$ and $i$ are 90° out of step: when one is at an extreme, the other is zero.

## Circuit stores energy in two places
$$
W_{\text{capacitor}} = \frac{q^2}{2C}, \qquad W_{\text{inductor}} = \frac{1}{2}L i^2
$$

total energy at any moment is the sum of both:
$$
W_{\text{total}} = \frac{q^2}{2C} + \frac{1}{2}L i^2
$$

Write $ΔW$ as the difference of energies at the two times.
$$
\Delta W = W(T_2) - W(T_0)
$$

## Fidning R for undampped oscilation 
The idea of "undamped oscillation" is a balance:

The capacitor-switching adds energy each half-wave: $ΔW$ (from part d).
The resistor removes energy each half-wave: $ΔWR$ (burned as heat).

For the oscillation to sustain itself (neither grow nor die), these must be equal:
$$
\Delta W_R = \Delta W
$$

### The formula for energy lost in the resistor

A resistor dissipates power $P_R=Ri^2$ , and energy is power integrated over time:
$$
\Delta W_R = \int_0^{T_2} R\,i^2(t)\,dt
$$

in simple terms when resistor power is integrated we get energy dissipated by the resistor 


## The whole story (H4.2) in plain English
SETUP: coil + capacitor + switch in a loop. NO battery. Just an initial current
kick i₀, then left alone.

WHAT HAPPENS: it oscillates by itself — energy sloshes coil ↔ capacitor, charge
goes up and down like a wave, at its own natural frequency. No resistance = never
dies down on its own.

THE TRICK (harvesting): change the capacitor at the right moments:
- at full charge (peak): SHRINK it → takes effort → ADDS energy.
- at empty charge (zero): RESET it → free (no charge to fight).
Repeat → energy builds up. That's the harvesting.

"TWO CURRENTS" = same current, two different times:
- i₀ = current at the start.
- i₂ = current half a swing later, after shrinking the capacitor.
- i₂ is BIGGER than i₀ → proof energy was added.

WHAT EACH PART FOUND:
a) the equation describing the circuit (2nd-order ODE for charge).

b) solved it (no switching yet) → charge is a pure sine wave.

c) added the switching → found the new wave shape (cosine) between peak and zero,
   and the times T₁ (peak) and T₂ (next zero); current grew to i₂.

d) calculated HOW MUCH energy was gained per half-swing: ΔW = ½Li₀²(ΔC/C₁) > 0.
   Positive = energy really was harvested.

e) real circuits lose energy to resistance R. Found the biggest R the harvesting
   can afford before the oscillation dies — by balancing energy gained vs energy
   burned as heat.


## Tunnel Diode Jump effect
The tunnel diode's current-voltage curve is N-shaped: current rises, falls, then rises again. The circuit's operating point can only sit on 
the two rising parts, not the falling middle. As conditions change, it climbs a rising branch until it hits the top of the hump, then, unable 
to continue, it suddenly jumps sideways across to the other rising branch. That sudden leap (instead of a smooth slide) is the jump phenomenon.

### Stable vs unstable resting spots

A stable operating point is like a ball in a valley: nudge it, and it rolls back. An unstable one is like a ball balanced on top of a hill: the
 slightest nudge and it rolls away, never to return.

The two rising branches of the N-curve are valleys (stable). The falling middle branch is the hilltop (unstable). So the circuit can physically 
rest on the rising parts, but it can never actually sit on the falling part, even if it's mathematically an operating point, the moment it tries, 
a tiny fluctuation knocks it off.

## The habit to build

For any $t → ∞$ question, redraw the circuit with capacitors replaced by open circuits and inductors replaced by short circuits, then solve the 
resulting resistive network.


### Rule for simplification
$$
a^{-x} = \frac{1}{a^{x}}
$$

$$
e^{-t/\tau} = \frac{1}{e^{t/\tau}}
$$
