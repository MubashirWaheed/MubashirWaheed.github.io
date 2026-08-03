---

title: Fourier Analysis of Periodic Signals and Linear Circuit Response
date: 2026-08-02

---

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
is or identity is given for the integrla and we get the signal in 
