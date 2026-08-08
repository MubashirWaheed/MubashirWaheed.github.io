---

title: 03 Fourier Analysis of Periodic Signals and Linear Circuit Response
date: 2026-08-02

---

## Fourier Transform

In its simplest form Fourier transform tell us the frequencies present in the signal. Applying Fourier transform technically means multiplying it wth exponential($e^{-jw_0t}$) 
with signal $x(t)$ and then integrating

$$
X(\omega_0) = \int_{-\infty}^{\infty} x(t)\, e^{-j\omega_0 t}\ dt
$$

The result is a single complex number for each frequency $ω0$.Its magnitude $∣X(ω0)∣$ tells you how much of that frequency is present, and its angle tells you the phase. So it's
 not just "which frequencies are present" but also how strong each one is and where its wave sits in time.


The factor $e{^−j2πft}$ is a rotating unit vector in the complex plane


general sinusoidal form

$$
v(t) = A \sin(\omega t + \varphi) + v_0
$$

When working with the Fourier transform we mostly convert the trig ratio signals into exponentials using eulers formula since it is easier to compute 

$$
e^{j\theta} = \cos\theta + j\sin\theta
$$

$$
\sin(\omega_0 t) = \frac{e^{j \omega_0 t} - e^{-j \omega_0 t}}{2j}
$$

$$
\cos(\omega_0 t) = \frac{e^{j \omega_0 t} + e^{-j \omega_0 t}}{2}
$$

### Concept 
So the idea is to convert the trig ratio signal  it to the exponential form using Euler then apply Fourier (multiply with the $e^{-jwt}$) and then mostly simplified form 
is or identity is given for the integrla and we get the signal in frequency domain from time domain where it appears as impulses at its frequency components.

## Fourier Series 

### Fundamental frequncy 
Fundamental frequncy is always the reciprocal of period It sets the repetition rate of the signal. If 
$f_0=100 $Hz, the entire pattern repeats 100 times per second, regardless of how complex the shape within one period is.

$$
f_0 = \frac{1}{T}
$$



### Trigonometric Fourier series of a periodic signal $u(t)$
Basically a periodic signal can be written as a sum of a constant plus sinusoids where $a_0$ is the DC component (the average value over one period), the coefficients 
$a_k$ and $b_k$ say how much cosine and sine of each harmonic you need.

$$
u(t) = a_0 + \sum_{k=1}^{\infty} \left[ a_k \cos(k\omega_0 t) + b_k \sin(k\omega_0 t) \right]
$$


| Symmetry | Condition | Coefficients that vanish |
|---|---|---|
| Even | $u(-t) = u(t)$ | All sine coefficients: $b_k = 0$ |
| Odd | $u(-t) = -u(t)$ | DC and all cosine coefficients: $a_0 = 0$ and $a_k = 0$ |
| Half-wave | $u(t + T/2) = -u(t)$ | DC and all even harmonics: $a_0 = 0$, $a_{2m} = 0$, $b_{2m} = 0$, for $m = 1, 2, 3, \dots$ |

### What is half wave symmetry?

Half-wave symmetry is a property of a periodic signal where the second half of each period is the negative (a flipped copy) of the first half. Formally:

$$
u\left(t + \frac{T}{2}\right) = -u(t)
$$

half-wave symmetry forces all the even harmonics and the DC component to vanish.

$$
a_0 = 0, \qquad a_{2m} = 0, \qquad b_{2m} = 0, \qquad m = 1, 2, 3, \dots
$$


### Identifying Even and Odd Signals by Shape

**Even Signal:** An even signal is a mirror image about the vertical axis. Folding the plot along the $t=0$ line makes the left half land exactly on the right half.
$$
u(-t) = u(t)
$$
**Odd Signal:** An odd signal has point symmetry about the origin: rotating the graph $180°$ around the point $(0,0)$ gives back the original. Equivalently, reflect across 
the vertical axis and then flip upside down.
$$
u(-t) = -u(t)
$$


### Spectral Lines

A spectral line is a single discrete frequency component in a signal. In the frequency domain (amplitude vs frequency), a periodic signal shows not a continuous curve but a set 
of discrete vertical lines, each at one frequency with height equal to that component's amplitude.

For a periodic signal, lines can only appear at integer multiples of the fundamental frequency:

$$
f_k = k f_0, \qquad k = 0, 1, 2, \dots
$$

### Fourier Coefficient Definitions (General Form)
$$
a_k = \frac{2}{T}\int_T u(t)\cos(k\omega_0 t)\ dt, \qquad b_k = \frac{2}{T}\int_T u(t)\sin(k\omega_0 t)\ dt
$$

$$
a_0 = \frac{1}{T}\int_T u(t)\ dt
$$

Where:

- $a_k$ = $k$-th cosine coefficient
- $b_k$ = $k$-th sine coefficient
- $u(t)$ = periodic signal
- $T$ = period
- $\omega_0 = 2\pi/T$ = fundamental angular frequency
- $k$ = harmonic index
- $\int_T$ = integral over one full period
- $a_0$ = DC component

### Checking if a Given Frequency is a Harmonic

If the result is not a whole number, the periodic signal has no spectral line at that frequency

If the result is a whole number, the frequency is on the harmonic grid, but a line is only present if that harmonic's coefficient is also nonzero

$$
k = \frac{f}{f_0}
$$


Where:

- $f$ = target frequency you are testing
- $f_0$ = fundamental frequency of the signal
- $k$ = which harmonic $f$ would be (must be a whole number for a line to be allowed)

### Procedure: Checking if a Harmonic Coefficient is Nonzero

1. **Strip the DC baseline.** Keep only the pulse; the constant offset affects only $a_0$.
2. **Get the coefficient formula** for the pulse shape. For a rectangular pulse: $a_k \propto \sin(k\pi D)$.
3. **Plug in** the harmonic number $k$ and the duty cycle $D$, then check whether $kD$ is a whole number.
4. **Read the result:**
   - $kD$ is a whole number → coefficient $= 0$ → no line
   - $kD$ is not a whole number → coefficient $\neq 0$ → line present

### Pulse Width $(τ)$, Period, and Duty Cycle
**Pulse width** is how long the pulse stays on (at its high level) within one cycle. It measures only the active part of the waveform,

**Period** is how long one full cycle lasts before the whole pattern repeats. It includes both the on-time and the off-time.

**Duty cycle** is the fraction of one period during which the pulse is on. It is simply the ratio of pulse width to period:

$$
D = \frac{\tau}{T}
$$

The DC offset is a constant that's always there; it isn't "on" or "off," it's just the floor the pulse sits on. The pulse is the part that switches: it's **on** when the signal is at $7\ \text{V}$ (the pulse contributes its full $6\ \text{V}$) and **off** when the signal is back at the $1\ \text{V}$ baseline (the pulse contributes $0\ \text{V}$). So
 "off" does not mean zero volts. It means the pulse component is zero and only the offset remains.

$$
u_B(t) = \underbrace{1\ \text{V}}_{\text{DC offset}} + \underbrace{u_{\text{pulse}}(t)}_{\text{0 or 6 V}}
$$

<img src="/attachments/signal.png" alt="signal image" />

A flat line has no wiggle. Fourier harmonics are all about wiggles, so the flat baseline can't add to any of them.

The baseline only affects one thing: the average height of the signal (the DC term). Everything else in the spectrum comes from the part that jumps up and down, the pulse.
integrating a constant times a cosine over one full period gives zero, because the cosine's area above the axis cancels its area below. A constant doesn't oscillate, so it has no
 frequency content except at DC.

$$
\frac{2}{T}\int_T U_0\cos(k\omega_0 t)\ dt = 0 \qquad (k \geq 1)
$$

so we only integrate only  the pulse(on part of signal). 

### Effective (RMS) voltage

The effective voltage is the RMS value, the equivalent DC voltage that delivers the same average power to a resistor:

$$
U_{\text{eff}} = \sqrt{\frac{1}{T}\int_0^T u^2(t)\ dt}
$$

### Important Concept 
$$
A =u^2 * \Delta t
$$

A rectacngle signal is considered a piecewise constant function so technically we can just apply the fomula $A = u^2 * \Delta t$. note that $u$ is the signal and by signal it 
means the height of the signal. Very important that we square the signal ($u$) and then compute the area under signal. We can't square the ramped lines since they become
quadratic (shape changes) but that is not the case with reactangular(flat) signal/lines

### Splitting into DC plus AC

$$
u(t) = U_0 + u_{\text{ac}}(t)
$$

### DC component (average value)
Note that the $u(t)$ is the whole signal including both the $DC$ and $AC$ part

$$
U_{0} = \frac{1}{T}\int_0^{T} u(t)\ dt
$$

The rectangle formula works on piecewise-constant signals: signals that hold a flat, unchanging value for a stretch of time, then jump instantly to another flat value, and so 
on. Each flat segment is a rectangle (height = the constant value, width = how long it lasts), so the area is just height times width, summed over the segments.

### AC RMS via Pythagoras
The RMS of the AC part relates to the total RMS and the DC component through a Pythagorean relationship:

$$
U_{\text{ac,eff}} = \sqrt{U_{\text{eff}}^2 - U_0^2}
$$


### Ripple factor

$$
w = \frac{U_{\text{ac,eff}}}{U_0}
$$


## Circuit Response Analysis 


### RMS of a single sinusoidal harmonic

$$
I_{k,\text{eff}} = \frac{\hat I_k}{\sqrt{2}}
$$

$\hat I_{ k}$ is the peak (amplitude) of the k-th harmonic.

### Total effective (RMS) value

total RMS of a periodic current splits into the DC part plus the RMS of every harmonic:
$$
I_{\text{eff}} = \sqrt{I_0^2 + \sum_{k=1}^{\infty} I_{k,\text{eff}}^2}
$$

$$
I_{\text{eff}} = \sqrt{I_0^2 + \frac{\hat I_1^2}{2} + \frac{\hat I_2^2}{2} + \frac{\hat I_3^2}{2}}
$$

$I_{eff}$ is the total RMS current, $I_0$ sthe DC component, and $I_{k,eff}$ the RMS value of the k-th harmonic.

### AC RMS value (remove the DC)

$$
I_{\text{ac,eff}} = \sqrt{\sum_{k=1}^{\infty} I_{k,\text{eff}}^2} = \sqrt{I_{\text{eff}}^2 - I_0^2}
$$

$I_{ac,eff}$ is the RMS of everything except DC, i.e. all harmonics from the fundamental upward.

### Harmonic RMS value (exclude the fundamental)

$$
I_{\text{harm,eff}} = \sqrt{\sum_{k=2}^{\infty} I_{k,\text{eff}}^2} = \sqrt{I_{2,\text{eff}}^2 + I_{3,\text{eff}}^2 + \cdots}
$$

Simplied version untile the end of harmonics in the follwing case it is 2 

$$
I_{\text{harm,eff}} = \sqrt{\frac{\hat I_2^2 + \hat I_3^2}{2}}
$$

This is the RMS of only the harmonics above the fundamental, starting the sum at $k=2$

Take note there is no dc part included for this one 

### Distortion factor 
The distortion factor $k$ measures how much of a signal's AC content comes from harmonics above the fundamental

$$
k = \frac{I_{\text{harm,eff}}}{I_{\text{ac,eff}}} = \sqrt{\frac{\sum_{k=2}^{\infty} I_{k,\text{eff}}^2}{\sum_{k=1}^{\infty} I_{k,\text{eff}}^2}}
$$

Simplified version where $\sqrt 2$ cancels out in numerator and denominator and we get 

$$
k = \sqrt{\frac{\hat I_2^2 + \hat I_3^2}{\hat I_1^2 + \hat I_2^2 + \hat I_3^2}}
$$

### Active Power

The follwoing equations for the current and voltage of the non linear circuit are present. The idea is only the harmonics that are present on both the current and voltage 
contribute to the active power


$$
u(t) = 4.5\ \text{V}\cos\left(\omega t - \frac{\pi}{2}\right)
$$


$$
i(t) = \underbrace{1.8\ \text{A}\cos(\omega t)}_{\text{fundamental }(k=1)} + \underbrace{1.2\ \text{A}\cos(2\omega t)}_{\text{2nd harmonic }(k=2)} + \underbrace{0.2\ \text{A}\cos(3\omega t)}_{\text{3rd harmonic }(k=3)}
$$

$$
P_W = U_0 I_0 + \sum_{k=1}^{\infty} U_{k,\text{eff}}\, I_{k,\text{eff}} \cos(\varphi_k)
$$

we ignore the 2nd and 3rd harmonic of the current since corresponding one aren't present in voltage also note there is no Dc current and voltage in the above example so they are
zero

Phase calculation of first harmonic

$$
\varphi_1 = \varphi_{u,1} - \varphi_{i,1} = -\frac{\pi}{2} - 0 = -\frac{\pi}{2}
$$

Example

$$
P_W = U_{1,\text{eff}}\, I_{1,\text{eff}} \cos(\varphi_1)
$$

$$
P_W = 3.182\ \text{V} \cdot 1.273\ \text{A} \cdot \cos\left(-\frac{\pi}{2}\right)
$$

$$
P_W = 0\ \text{W}
$$

### Accepted apparent power

The apparent power does not care whether the current is useful, reactive, or harmonic. It uses the total RMS voltage and total RMS current:

$$
P_s = U_{\text{eff}}\, I_{\text{eff}}
$$

note that for the calculation of effective value we include everything eg all harmonic of each and dc part as well Formula above 

### Accepted reactive power

$$
P_B = \sqrt{P_s^2 - P_W^2}
$$

Where:

- $P_B$ = non-active power (reactive + distortion), often called $Q$ in English texts
- $P_s$ = apparent power ($= U_{\text{eff}}\, I_{\text{eff}}$), often called $S$
- $P_W$ = active (real) power, often called $P$

## Represenations of Fourier series 

### Amplitude-Phase Representation
$$
u(t) = c_0 + \sum_{k=1}^{\infty} c_k\cos(k\omega t - \varphi_k)
$$

**DC** 
$$
c0​=a0​
$$
 
**Amplitude c_k :**
$$
c_k = \sqrt{a_k^2 + b_k^2}
$$


**Phase φ_k**

$$
\varphi_k = \arctan\!\left(\frac{b_k}{a_k}\right)
$$

	
### Complex exponential Representation
$$
u(t) = \sum_{k=-\infty}^{\infty} d_k\, e^{jk\omega t}
$$
