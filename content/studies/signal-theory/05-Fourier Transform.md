---
title: 05 Fourier Transform
---

### Rect Definiton 

$$
\text{rect}\!\left(\frac{t}{2}\right) = \begin{cases} 1 & |t| \le 1 \\ 0 & \text{otherwise} \end{cases} = \begin{cases} 1 & -1 \le t \le 1 \\ 0 & \text{otherwise} \end{cases}
$$

$rect(t)$ is the plain box with $T = 1$: total width $1$, centered at $0$, so it runs from $-1/2$ to $+1/2$.

$$
\text{rect}(t) = \begin{cases} 1 & |t| \le \dfrac{1}{2} \\ 0 & \text{otherwise} \end{cases} = \begin{cases} 1 & -\dfrac{1}{2} \le t \le \dfrac{1}{2} \\ 0 & \text{otherwise} \end{cases}
$$

### Rect as a limits-setter

$$
\int_{-\infty}^{\infty} f(t)\,\text{rect}\!\left(\frac{t}{2}\right)e^{-\mathrm{j}\omega t}\,dt = \int_{-1}^{1} f(t)\,e^{-\mathrm{j}\omega t}\,dt
$$

### Euler's formulas

$$
e^{\mathrm{j}\theta} = \cos\theta + \mathrm{j}\sin\theta, \qquad e^{-\mathrm{j}\theta} = \cos\theta - \mathrm{j}\sin\theta
$$


### Sin and cos from exponentials

$$
e^{\mathrm{j}\theta} - e^{-\mathrm{j}\theta} = 2\mathrm{j}\sin\theta, \qquad e^{\mathrm{j}\theta} + e^{-\mathrm{j}\theta} = 2\cos\theta
$$

$$
e^{\mathrm{j}t} - e^{-\mathrm{j}t} = 2\mathrm{j}\sin(t), \qquad e^{10\mathrm{j}t} - e^{-10\mathrm{j}t} = 2\mathrm{j}\sin(10t)
$$

### Box transform and sinc definition

$$
\int_{-a}^{a} e^{-\mathrm{j}\omega t}\,dt = \frac{2\sin(\omega a)}{\omega}, \qquad \text{sinc}(\omega) = \frac{\sin\omega}{\omega}
$$

### Integration by parts (general rule)

$$
\int u\,dv = uv - \int v\,du
$$

example 

$$
u = t, \quad du = dt, \qquad dv = e^{-\mathrm{j}\omega t}\,dt, \quad v = \frac{e^{-\mathrm{j}\omega t}}{-\mathrm{j}\omega}
$$

substituting
$$
\int_{-1}^{1} t\,e^{-\mathrm{j}\omega t}\,dt = \left[t \cdot \frac{e^{-\mathrm{j}\omega t}}{-\mathrm{j}\omega}\right]_{-1}^{1} - \int_{-1}^{1} \frac{e^{-\mathrm{j}\omega t}}{-\mathrm{j}\omega}\,dt
$$

### sinc definition

$$
\text{sinc}(\omega) = \frac{\sin(\omega)}{\omega}
$$

### sinc value at zero

$$
\text{sinc}(0) = 1
$$

### sinc is even (odd ÷ odd = even)
$$
\text{sinc}(-\omega) = \frac{\sin(-\omega)}{-\omega} = \frac{-\sin(\omega)}{-\omega} = \frac{\sin(\omega)}{\omega} = \text{sinc}(\omega)
$$

### The key transform pair (box in time ↔ sinc in frequency)

$$
\text{rect}\!\left(\frac{t}{T}\right) \;\bullet\!\!-\!\!\circ\; T\,\text{sinc}\!\left(\frac{\omega T}{2}\right)
$$

### Parity Test (Checking if a Function is Even or Odd)
pass in the opposite sign of ω and see whether the function stays the same (even), flips to its negative (odd), or does neither.


## Forward transform (time → frequency)
$$
X(\mathrm{j}\omega) = \int_{-\infty}^{\infty} x(t)\,e^{-\mathrm{j}\omega t}\,dt
$$

## Inverse transform (frequency → time)
$$
x(t) = \frac{1}{2\pi}\int_{-\infty}^{\infty} X(\mathrm{j}\omega)\,e^{+\mathrm{j}\omega t}\,d\omega
$$
note we are integrating wrt $w$

### Antiderivative rule for an exponential (integrating over ω)

$$
\int e^{a\omega}\,d\omega = \frac{1}{a}e^{a\omega}
$$

$$
\int e^{\mathrm{j}\omega t}\,d\omega = \frac{1}{\mathrm{j}t}e^{\mathrm{j}\omega t}
$$


## Fourier Transform Pairs (ω convention, inverse carries 1/2π)

Read each as x(t) ●─○ X(jω): left is time, right is frequency.

**Impulse → constant**
Transforms a single spike at t = 0 into a flat spectrum (all frequencies equally).

$$
\delta(t) \;\bullet\!\!-\!\!\circ\; 1
$$

**Constant → impulse**
A constant (DC) signal has all its energy at ω = 0, so it becomes a spike there.

$$
1 \;\bullet\!\!-\!\!\circ\; 2\pi\,\delta(\omega)
$$

**Box → sinc** (the key pair)
A rectangular pulse of width T in time gives a sinc in frequency.

$$
\text{rect}\!\left(\frac{t}{T}\right) \;\bullet\!\!-\!\!\circ\; T\,\text{sinc}\!\left(\frac{\omega T}{2}\right)
$$

**sinc → box** (the reverse, used in this exercise)
A sinc in time gives a rectangular box in frequency.

$$
\frac{1}{\pi}\text{sinc}(t) \;\circ\!\!-\!\!\bullet\; \text{rect}\!\left(\frac{\omega}{2}\right)
$$

**Cosine → two positive impulses**
A cosine at frequency ω₀ shows up as two spikes at ±ω₀ (both positive).

$$
\cos(\omega_0 t) \;\bullet\!\!-\!\!\circ\; \pi\big(\delta(\omega - \omega_0) + \delta(\omega + \omega_0)\big)
$$

**Sine → two opposite impulses**
A sine at ω₀ gives two spikes at ±ω₀ with opposite signs (imaginary, odd).

$$
\sin(\omega_0 t) \;\bullet\!\!-\!\!\circ\; \mathrm{j}\pi\big(\delta(\omega + \omega_0) - \delta(\omega - \omega_0)\big)
$$

**Complex exponential → single impulse**
A single rotating exponential at ω₀ is one spike at ω₀ (no negative-frequency twin).

$$
e^{\mathrm{j}\omega_0 t} \;\bullet\!\!-\!\!\circ\; 2\pi\,\delta(\omega - \omega_0)
$$

# Multiplication Theorem (Fourier Transform)

## The idea in one line

Multiplying two signals in the **time domain** corresponds to **convolving** their spectra in the frequency domain, with an extra factor of 1/(2π).

So whenever a spectrum is given as a *convolution*, you can read it backwards and get a simple *product* in time.

---

## Formula: Multiplication theorem (time-domain product)

$$
x_1(t)\cdot x_2(t) \;\; \circ\!\!-\!\!\!-\!\!\bullet \;\; \frac{1}{2\pi}\,X_1(\mathrm{j}\omega) * X_2(\mathrm{j}\omega)
$$

Symbols:
- $x_1(t), x_2(t)$: two time signals
- $X_1(\mathrm{j}\omega), X_2(\mathrm{j}\omega)$: their Fourier transforms
- $*$: convolution, here performed over the variable $\omega$
- $\frac{1}{2\pi}$: normalisation factor that appears because we use the angular frequency $\omega$ convention

## Formula: Multiplication theorem (the form you actually use)

Read the same statement from right to left. If a spectrum is handed to you as a convolution, the time signal is a plain product times $2\pi$:

$$
X(\mathrm{j}\omega) = X_1(\mathrm{j}\omega) * X_2(\mathrm{j}\omega)
\quad\Longrightarrow\quad
x(t) = 2\pi\, x_1(t)\, x_2(t)
$$

This $2\pi$ is the single most commonly forgotten factor in this whole topic.

## Formula: Convolution theorem (the dual, for contrast)

$$
x_1(t) * x_2(t) \;\; \circ\!\!-\!\!\!-\!\!\bullet \;\; X_1(\mathrm{j}\omega)\cdot X_2(\mathrm{j}\omega)
$$

Note the asymmetry: convolution in **time** gives a clean product with **no** prefactor. Convolution in **frequency** carries the $\frac{1}{2\pi}$.

---

## Recipe

1. Look at the given spectrum and **split it into a convolution** of two spectra you recognise. Typically one factor is a pair of Dirac impulses (a shift) and the other is a simple shape such as a rect.
2. Transform each factor back separately using a table.
3. Multiply the two time signals and **multiply by $2\pi$**.

Why impulses show up so often: convolution with a shifted Dirac is just a shift.

$$
f(\omega) * \delta(\omega - \omega_0) = f(\omega - \omega_0)
$$

---

## Building blocks used below

### Pair: shifted impulse pair and the sine

$$
\sin(\omega_0 t) \;\; \circ\!\!-\!\!\!-\!\!\bullet \;\; \mathrm{j}\pi\big(\delta(\omega+\omega_0) - \delta(\omega-\omega_0)\big)
$$

- $\omega_0$: the angular frequency of the sine, in rad/s
- The purely imaginary, odd spectrum is the signature of a sine (a cosine gives a real, even one)

### Pair: rect in frequency and the sinc in time

$$
\frac{1}{\pi}\operatorname{sinc}(t) \;\; \circ\!\!-\!\!\!-\!\!\bullet \;\; \operatorname{rect}\!\left(\frac{\omega}{2}\right)
$$

- $\operatorname{rect}(u) = 1$ for $|u| < \tfrac{1}{2}$ and $0$ otherwise, so $\operatorname{rect}\!\left(\frac{\omega}{2}\right)$ is a box of **height 1** spanning $-1 < \omega < 1$, i.e. total width 2
- $\operatorname{sinc}(t) = \dfrac{\sin(t)}{t}$ (unnormalised definition)
- This pair follows from the duality property applied to the standard rect/sinc pair

---

## Worked example

**Given spectrum.** Two boxes of width 2, one of height $+2\pi\mathrm{j}$ centred at $\omega = +10$, one of height $-2\pi\mathrm{j}$ centred at $\omega = -10$.

### Step 1: write it as a convolution

$$
X(\mathrm{j}\omega) = 2\pi\mathrm{j}\operatorname{rect}\!\left(\frac{\omega}{2}\right) * \big(\delta(\omega-10) - \delta(\omega+10)\big)
$$

Each impulse copies the box to its position; the minus sign flips the left copy. Now pull the constants out so that both factors match table entries exactly:

$$
X(\mathrm{j}\omega) = -2 \cdot \underbrace{\pi\mathrm{j}\big(\delta(\omega+10) - \delta(\omega-10)\big)}_{\displaystyle \bullet\!\!-\!\!\!-\!\!\circ \; \sin(10t)} \; * \; \underbrace{\operatorname{rect}\!\left(\frac{\omega}{2}\right)}_{\displaystyle \bullet\!\!-\!\!\!-\!\!\circ \; \frac{1}{\pi}\operatorname{sinc}(t)}
$$

The factor $-2$ comes from swapping the impulse signs, since

$$
\delta(\omega-10)-\delta(\omega+10) = -\big[\delta(\omega+10)-\delta(\omega-10)\big]
$$

together with $2\pi\mathrm{j} = 2\cdot\pi\mathrm{j}$.

### Step 2: apply the multiplication theorem

$$
x(t) = -2 \cdot 2\pi \cdot \sin(10t)\cdot \frac{1}{\pi}\operatorname{sinc}(t)
$$

### Step 3: simplify

$$
\boxed{\,x(t) = -4\,\sin(10t)\,\operatorname{sinc}(t)\,}
$$

### Sanity check on the result

$\operatorname{sinc}(t)$ is a slow envelope (its spectrum is the narrow box of width 2), and $\sin(10t)$ is a fast carrier that shifts that box to $\pm 10$. A slow envelope times a fast carrier is exactly the picture the spectrum shows: one narrow box parked at each carrier frequency.

---

## Common mistakes

- Dropping the $2\pi$. Frequency-domain convolution always drags it along.
- Mixing up the two theorems. Ask yourself which domain the convolution lives in, then apply the matching rule.
- Misreading the rect width. $\operatorname{rect}\!\left(\frac{\omega}{a}\right)$ has total width $a$, not $\frac{a}{2}$.
- Losing a sign on the impulse pair. Sine has $\delta(\omega+\omega_0)$ positive, cosine has both positive.
