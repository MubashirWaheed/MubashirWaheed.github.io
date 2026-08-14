--- 
title: 05 Network Analysis 
---
**Balancing process(Ausgleichen) = transient behaviour**

Mainly in Network Analysis I am learning the transient behaviour of the circuits (z.B. RL, damped RLC, damped series resonant circuit).

Drawing the circuit from the time domain to Laplace domain: since the coil and capacitor have a derivative in the time domain, which when converted to the Laplace domain results in initial conditions. Each element can be represented as either a series 
voltage source (Thévenin) or a parallel current source (Norton), as shown in the table below.

 
| Component | Impedance | Series source (Thévenin) | Parallel source (Norton) |
|---|---|---|---|
| Inductor | $sL$ | voltage $L\;i_L(0)$ | current $\dfrac{i_L(0)}{s}$ |
| Capacitor | $\dfrac{1}{sC}$ | voltage $\dfrac{u_C(0)}{s}$ | current $C\;u_C(0)$ |


<img src="/attachments/lcircuit.png" alt="laplace circuit" />


## Writing Transfer Function $G(s)$

- Write the circuit equations (mesh or node method).
- Figure out which variables to eliminate. For $G(s)$ we only want input and output voltage, so the currents get removed.

$$
G(s) = \frac{U_2(s)}{U_1(s)}
$$

- The element equations link current and voltage, so they are what let us swap a current for a voltage:

$$
u_L(t) = L\,\frac{di(t)}{dt} \qquad i_C(t) = C\,\frac{du(t)}{dt}
$$

- Steps to eliminate the currents:
    - Take one loop equation, make the first current the subject, substitute it into the second loop equation (removes current 1).
    - Use the element equation to replace the remaining current with a voltage (removes current 2).
- What's left is a relation between $U_1$ and $U_2$ only. Take the ratio to get $G(s)$.

- In the Laplace domain the derivatives become multiplication by $s$, so the element equations turn into plain algebra:

$$
U_L(s) = sL\,I(s) \qquad I_C(s) = sC\,U(s)
$$

### Worked example (the RLC circuit)

**Start: two mesh equations + one element equation.**

$$
\text{I}: \quad -U_1 + 2R I_1 - R I_2 = 0
$$

$$
\text{II}: \quad \left(2R + sL + \tfrac{1}{sC}\right) I_2 - R I_1 = 0
$$

$$
\text{element}: \quad I_2 = sC\,U_2
$$

**Remove current 1:** solve I for $I_1$, substitute into II:

$$
I_1 = \frac{U_1 + R I_2}{2R} \;\Rightarrow\; \left(2R + sL + \tfrac{1}{sC}\right) I_2 - \frac{U_1 + R I_2}{2} = 0
$$

**Remove current 2:** replace every $I_2$ with $sC\,U_2$, expand, collect $U_2$ vs $U_1$, multiply by 2:

$$
\left(s^2\,2LC + s\,3RC + 2\right) U_2 = U_1
$$

**Take the ratio:**

$$
G(s) = \frac{U_2}{U_1} = \frac{1}{s^2\,2LC + s\,3RC + 2}
$$


### DC source switched on at $t=0$ → transform to $\frac{U_0}{s}$

- A DC source that closes a switch at $t=0$ is not constant for all time, it is $0$ before and $U_0$ after. That "on at $t=0$" behaviour is a **step**, so we write it with the unit step $\varepsilon(t)$:

$$
u_1(t) = \varepsilon(t)\,U_0
$$

- The $\varepsilon(t)$ is what makes the voltage exist only for $t > 0$. Its Laplace transform is the standard step pair $\varepsilon(t) \leftrightarrow 1/s$, so a constant times a step gives:

$$
U_1(s) = \frac{U_0}{s}
$$

- **Takeaway:** any DC value switched on at $t=0$ transforms to (that value)$/s$. The $1/s$ is the fingerprint of the step.


### Putting a denominator into standard pole form (worked on $U_2(s)$)

**Start:**

$$
U_2(s) = \frac{U_0}{s^3\,2LC + s^2\,3RC + 2s}
$$

**Step 1: factor $s$ out of the denominator** (gives pole $s_1 = 0$):

$$
U_2(s) = \frac{U_0}{s\left(s^2\,2LC + s\,3RC + 2\right)}
$$

**Step 2: pull out the $s^2$ coefficient $2LC$** so $s^2$ has coefficient 1:

$$
U_2(s) = \frac{U_0}{2CL}\cdot\frac{1}{s\left(s^2 + s\,\frac{3R}{2L} + \frac{1}{LC}\right)}
$$

**Step 3: substitute** $\frac{1}{LC} = \omega_0^2$ and the given middle-term relation $\frac{3R}{2L} = \frac{6}{\sqrt5}\omega_0$. The front $\frac{1}{2CL}$ becomes $\frac{\omega_0^2}{2}$:

$$
U_2(s) = \frac{U_0\,\omega_0^2}{2}\cdot\frac{1}{s\left(s^2 + s\,\frac{6}{\sqrt5}\omega_0 + \omega_0^2\right)}
$$

**Poles:** $s_1 = 0$ from the factored $s$; $s_{2,3}$ from solving

$$
s^2 + s\,\frac{6}{\sqrt5}\omega_0 + \omega_0^2 = 0
$$


Every entry in the standard Laplace table implicitly carries an $ε(t)$, whether or not it's written. So:

$$
e^{-at} \text{ in the table always means } \varepsilon(t)\,e^{-at}
$$


## Physical Meaning of the Capacitor Voltage

The step response describes how the capacitor voltage evolves after the switch closes at $t=0$. Its S-shape comes directly from the circuit physics: each feature of the curve maps to one circuit element.

### Start: zero voltage, zero slope

At switch-on both the voltage and its rate of rise are zero:

$$
u_2(t=0) = 0 \qquad u_2'(t=0^+) = 0
$$

- **Voltage can't jump** (from $i = C\frac{du}{dt}$): a jump means $\frac{du}{dt}=\infty$, so $i=\infty$, impossible. The voltage is pinned to its pre-switch value $0$ and can only rise gradually.
- **Slope starts flat** because of the inductor: it resists a sudden current change, so at $t=0$ almost no current reaches the capacitor yet. No current means no charge arriving, so the voltage barely moves. This is the flat "foot". (A plain RC circuit, no inductor, would rise fastest at $t=0$.)

### Fastest rise: the inflection point

As current builds, charge flows in faster and the voltage climbs more steeply, reaching its steepest point at the inflection time $t_{WP}$ (Wendepunkt). After this, the rise slows down.

### Final value: half the source

For $t \to \infty$ the voltage settles at:

$$
u_2(t \to \infty) = \frac{1}{2}U_0
$$

It stops at **half** $U_0$, not the full source. At steady state the capacitor stops drawing current and acts as an open branch, so $U_0$ is divided across the two left-hand resistors; the capacitor sees only the divided-down half.

### Summary of the shape

$$
\text{zero start} + \text{zero start-slope} + \text{finite asymptote} \Rightarrow \text{S-curve}
$$

- Starts at $0$: uncharged capacitor
- Rises slowly at first: inductor delays the current
- Steepest at $t_{WP}$: inflection point
- Flattens toward $\frac{1}{2}U_0$: resistor divider sets the final value

<img src="attachments/u2-graph.png" width="600" />


## Goal when asked to "write the differential equation" for a variable X

**TARGET:** one equation containing only X and its derivatives, every other variable eliminated. (Here X $= u_C$.)

**Step 1: Write the loop (mesh) equation.** It contains several variables:

$$
i_L R + u_L - u_C = 0
$$

Unknowns here: $i_L$, $u_L$, $u_C$. Three variables, need to kill two.

**Step 2: Write each unwanted variable in terms of X using element laws.**

Capacitor (note the $-i_L$ from the arrow directions):

$$
i_C = C\,\frac{du_C}{dt} = -i_L \quad\Rightarrow\quad i_L = -C\,\frac{du_C}{dt}
$$

Inductor (substitute the $i_L$ just found):

$$
u_L = L\,\frac{di_L}{dt} = -LC\,\frac{d^2 u_C}{dt^2}
$$

**Step 3: Substitute both into the loop equation.**

$$
\underbrace{-RC\,\frac{du_C}{dt}}_{i_L R} \;\underbrace{-\,LC\,\frac{d^2 u_C}{dt^2}}_{u_L} \;-\; u_C = 0
$$

**Step 4: Only X remains.** Every term is now in $u_C$, no $i_L$ or $u_L$ left.

**Step 5: Tidy up** (multiply by $-1$, divide by $LC$, order by derivative):

$$
\frac{d^2 u_C}{dt^2} + \frac{R}{L}\,\frac{du_C}{dt} + \frac{1}{LC}\,u_C = 0
$$

**Order check:** 2 energy elements ($L$ and $C$) → highest derivative is 2nd → second-order equation. Falls out automatically.


## Initial Conditions (IC) — cheat sheet

### Core rule: "can't jump"
Each energy element pins one starting value, because it can't change instantly:
- **Capacitor voltage can't jump:** $u_C(0^+) = u_C(0^-)$
- **Inductor current can't jump:** $i_L(0^+) = i_L(0^-)$
- Why: $i_C = C\frac{du_C}{dt}$, $u_L = L\frac{di_L}{dt}$ → a jump means infinite slope → infinite current/voltage → impossible.

### How many ICs
Number of ICs = number of energy elements = order of the differential equation.
(2nd-order needs 2: a starting **value** and a starting **slope**.)

### Getting the two ICs (value + slope)
- **1st IC (value):** read the capacitor voltage (or inductor current) directly at $t=0$.
- **2nd IC (slope):** get it from the element law, using the "can't jump" current/voltage.

$$\frac{du_C}{dt}\bigg|_0 = \frac{i_C(0)}{C} \qquad \frac{di_L}{dt}\bigg|_0 = \frac{u_L(0)}{L}$$

$|$ means evaluated at and zero next to it means at $t=0$

### One-line hook
*No current at the start ⟹ capacitor voltage isn't moving ⟹ slope = 0.*
(Switch was open → $i(0)=0$ → $\frac{du_C}{dt}\big|_0 = 0$.)

The differential equation gives the shape of possible solutions; the two ICs select the one that's physically happening.

The slope initial condition tells you how fast the voltage (or current) is changing at the very moment the circuit turns on $(t=0)$.

$$
\frac{du_C}{dt}\bigg|_0 = \text{how fast the voltage is CHANGING at } t=0
$$


## Solving a 2nd-Order Homogeneous ODE (Characteristic Equation Method)

Use this whenever the differential equation is homogeneous (right-hand side = 0), like the pre-charged RLC circuit.

### Starting point

$$
\frac{d^2 u_C}{dt^2} + \frac{R}{L}\frac{du_C}{dt} + \frac{1}{LC}u_C = 0
$$

### Step 1: Exponential ansatz (the guess)

Guess the solution is an exponential, because differentiating it just multiplies by $s$:

$$
u_C(t) = e^{st} \quad\Rightarrow\quad \frac{du_C}{dt} = s\,e^{st}, \quad \frac{d^2 u_C}{dt^2} = s^2\,e^{st}
$$

### Step 2: Substitute → characteristic equation

Insert the guess, every term carries $e^{st}$, divide it out (it's never zero):

$$
s^2 + \frac{R}{L}s + \frac{1}{LC} = 0
$$

This is the **characteristic equation**. Its roots are the **poles** (textbook calls them eigenvalues).

### Step 3: Solve for the poles (quadratic formula)

$$
s_{1,2} = -\underbrace{\frac{R}{2L}}_{\sigma} \pm \sqrt{\underbrace{\left(\frac{R}{2L}\right)^2}_{\sigma^2} - \underbrace{\frac{1}{LC}}_{\omega_0^2}}
$$

Name the pieces: $\sigma = \frac{R}{2L}$ (decay rate), $\omega_0^2 = \frac{1}{LC}$ (undamped frequency squared).

### Step 4: Check the case (sign under the root)

The sign under the root decides whether the circuit **oscillates or not**, which changes the whole shape of the answer:

$$
\left(\frac{R}{2L}\right)^2 > \frac{1}{LC} \;\Rightarrow\; \text{two real poles} \;\Rightarrow\; \text{smooth decay (no oscillation)}
$$

$$
\left(\frac{R}{2L}\right)^2 < \frac{1}{LC} \;\Rightarrow\; \text{complex conjugate poles} \;\Rightarrow\; \text{decaying oscillation (ringing)}
$$

**Point of the "complex conjugate" case:** it's the ringing case. Small $R$ means weak damping, so energy sloshes between $L$ and $C$ before dying out. This problem tells us to use it, so the answer will have sin/cos.

**How $\frac{1}{LC}$ becomes positive under the root.** In the complex case the root holds a negative number ($\frac{1}{LC}$ is bigger). A negative under a root is the problem, so factor out $-1$. **This flips the order of the two terms** (small − big becomes −(big − small)), which is why $\frac{1}{LC}$ ends up in front and positive:

$$
\left(\frac{R}{2L}\right)^2 - \frac{1}{LC} = -\left(\frac{1}{LC} - \left(\frac{R}{2L}\right)^2\right)
$$

Then $\sqrt{-1} = j$ splits off, and the now-positive bracket is named $\omega_d$:

$$
s_{1,2} = -\sigma \pm j\omega_d, \qquad \sigma = \frac{R}{2L}, \qquad \omega_d = \sqrt{\frac{1}{LC} - \left(\frac{R}{2L}\right)^2}
$$

- $\sigma$ = real part = **decay rate**
- $\omega_d$ = imaginary part = **damped oscillation frequency**

### Step 5: Write the general solution

**Where sin and cos come from.** Put a complex pole into the guess $e^{st}$ and split the exponent ($e^{a+b}=e^a e^b$):

$$
e^{st} = e^{(-\sigma + j\omega_d)t} = e^{-\sigma t}\cdot e^{j\omega_d t}
$$

The first factor $e^{-\sigma t}$ is the real decaying envelope. The second factor $e^{j\omega_d t}$ (imaginary exponent) becomes sin/cos through **Euler's formula**:

$$
e^{j\omega_d t} = \cos\omega_d t + j\sin\omega_d t
$$

**Why the final answer is real (the $j$ disappears).** The two poles are a conjugate pair, so their solutions differ only in the sign of the sin. Adding the pair collects cos and sin; the imaginary parts are equal and opposite, so they cancel and leave real coefficients:

$$
s_{1,2} \text{ conjugate pair} \;\xrightarrow{\text{add}}\; \text{imaginary parts cancel} \;\Rightarrow\; \text{real solution}
$$

The two basis solutions and the general solution:

$$
u_{C,1} = e^{-\sigma t}\cos\omega_d t \qquad u_{C,2} = e^{-\sigma t}\sin\omega_d t
$$

$$
u_C(t) = e^{-\sigma t}\left(k_1\cos\omega_d t + k_2\sin\omega_d t\right)
$$

$k_1, k_2$ are real unknown constants, found next from the two initial conditions.

### Step 6: Apply the two initial conditions

**First IC** (value), $u_C(0) = U$. Set $t=0$ ($e^0=1$, $\cos 0=1$, $\sin 0=0$):

$$
u_C(0) = k_1 = U
$$

**Second IC** (slope), $\left.\frac{du_C}{dt}\right|_0 = 0$. Differentiate, then set $t=0$:

Differentiate the follwoing equation using the product rule and equate to zero since slope 
zero at the start  $(t=0)$ and find the $k_2$

$$
u_C(t) = e^{-\sigma t}\left(k_1\cos\omega_d t + k_2\sin\omega_d t\right)
$$ 

$$
\left.\frac{du_C}{dt}\right|_0 = -k_1\sigma + k_2\omega_d = 0 \quad\Rightarrow\quad k_2 = \frac{k_1\sigma}{\omega_d} = \frac{U\sigma}{\omega_d}
$$

Need to understand how the derivative was applied

### Step 7: Final result

Substitute $k_1 = U$ and $k_2 = \frac{U\sigma}{\omega_d}$ back in:

$$
u_C(t) = U\,e^{-\sigma t}\left(\cos\omega_d t + \frac{\sigma}{\omega_d}\sin\omega_d t\right)
$$

### Optional: single-sinusoid form (easier to sketch)

Using $\sin(\alpha+\beta) = \sin\alpha\cos\beta + \sin\beta\cos\alpha$:

$$
u_C(t) = \frac{U}{\sin\gamma}\,e^{-\sigma t}\sin(\omega_d t + \gamma), \qquad \gamma = \arctan\frac{\omega_d}{\sigma}
$$

A decaying sine: amplitude shrinks as $e^{-\sigma t}$, oscillates at $\omega_d$, phase-shifted by $\gamma$.

### Current through the inductor (for part f)

From $i_L = -C\frac{du_C}{dt}$:

$$
i_L(t) = \frac{CU\omega_d}{\sin^2\gamma}\,e^{-\sigma t}\sin\omega_d t
$$

Also a decaying oscillation, as expected.

### Vocabulary (textbook synonyms, don't get thrown)
- pole = root = **eigenvalue** (textbook uses $\lambda$; I use $s$)
- decay rate $\sigma$ = **damping** (textbook uses $d = \frac{R}{2L}$)
- $u_{C,1}, u_{C,2}$ = **solution basis** (independent solutions)
- $\omega_0 = \frac{1}{\sqrt{LC}}$ undamped frequency; $\omega_d$ = damped (actual) frequency

### The method in one line
Guess $e^{st}$ → characteristic quadratic → solve for poles → if complex, write $e^{-\sigma t}(k_1\cos\omega_d t + k_2\sin\omega_d t)$ → fix $k_1,k_2$ from the two ICs.


## Idea  of differential equation 

A linear ODE of order 𝑛 has exactly n independent solutions, and the general solution is a weighted sum of them.

Second-order means $𝑛=2$, so you need two independent solutions. Call them $𝑢_1$ and $𝑢_2$
	
$$
u(t) = k_1 u_1 + k_2 u_2
$$

The two weights $𝑘_1$,$𝑘_2$ are unknowns you'll pin down at the very end using two initial conditions

$$
e^{j\omega_d t} = \cos\omega_d t + j\sin\omega_d t
e^{-j\omega_d t} = \cos\omega_d t - j\sin\omega_d t
$$

$$
e^{j\omega_d t} + e^{-j\omega_d t} = 2\cos\omega_d t + \underbrace{(j\sin - j\sin)}_{= 0} = 2\cos\omega_d t
$$

$$
u_1 = e^{-\sigma t}e^{j\omega_d t}, \quad u_2 = e^{-\sigma t}e^{-j\omega_d t}
$$

These are correct solutions, but they contain $$, the imaginary unit. That's a problem: the voltage across your capacitor is a real,
 measurable number. You can't hand an engineer an answer with $j$ in it. You need real functions.

The superposition theorem says any combination 
$𝐴𝑢_1 + 𝐵𝑢_2$  is also a valid solution, for any numbers 
𝐴 and 𝐵 you like. So you have total freedom to pick A and B.

$$
u_C(t) = A\,u_1 + B\,u_2
$$

$$
u_1 + u_2 = e^{-\sigma t}\big[(\cos + j\sin) + (\cos - j\sin)\big] = e^{-\sigma t}\cdot 2\cos\omega_d t
$$
