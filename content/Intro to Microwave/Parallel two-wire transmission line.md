---
title: Parallel two-wire transmission line 
---


### Resonant frequency in Hz
$$f_0 = \frac{1}{2\pi\sqrt{LC}}$$

$$\omega_0 = \frac{1}{\sqrt{L\ C}}$$

### Inductance formula for a parallel two-wire transmission line 

$$L = \mu\,\frac{\ell}{\pi}\ln\!\left(\frac{2a_2}{D_2}\right)$$

$ℓ$: length of one wire, $a_2$: spacing between wire centers, $D_2​$: wire diameter

### Characteristic Impedance of parallel wire

$$Z_\ell = 120\ \Omega \sqrt{\frac{\mu_r}{\varepsilon_r}}\ \ln\!\left(\frac{2a}{D}\right), \quad a: \text{wire spacing}, \ D: \text{wire diameter}, \ a \gg D$$

### Characteristic impedance for a lossless transmission line

$$Z_\ell = \sqrt{\frac{L'}{C'}}$$

### Lossy line characteristic impedance:

$$Z_\ell = \sqrt{\frac{R' + j\omega L'}{G' + j\omega C'}}$$

### Capacitance per unit length of a parallel wire line

$$C' = \frac{\pi \varepsilon_0 \varepsilon_r}{\ln\!\left(\frac{2a}{D}\right)}, \quad \text{2a = center-to-center spacing}$$

### R' Series Resistance per unit length

$$R' = \frac{2}{\pi D \delta \sigma} = \frac{1}{\pi r_0 \delta \sigma} = \frac{2 R_s}{\pi D} = \frac{1}{D}\sqrt{\frac{f \mu_0 \mu_r}{\pi \sigma}} \qquad \left(R' \propto \sqrt{f}\right)$$

### G' (shunt conductance per unit length)

$$G' = 2\pi f\ C' \tan\delta_\varepsilon = \omega C' \tan\delta_\varepsilon = \frac{\pi \sigma_d}{\ln\!\left(\frac{2a}{D}\right)} \qquad \left(\tan\delta_\varepsilon = \frac{\varepsilon''}{\varepsilon'}\right)$$

### Ohmic (conductor) attenuation, caused by R′

$$\alpha_{ohm} = \frac{R'}{2 Z_\ell}$$

### Dielectric attenuation, caused by G′:

$$\alpha_{diel} = \frac{G' Z_\ell}{2}$$

### Total attenuation

$$\alpha = \alpha_{ohm} + \alpha_{diel} = \frac{R'}{2 Z_\ell} + \frac{G' Z_\ell}{2}$$

$α = \text{total attenuation constant, wave decays as  }e^{-\alpha z}$

$ \text{Valid only for low-loss lines}$: $R' \ll \omega L'$, $G' \ll \omega C'$

### Reflection coefficient at the load

When  line meets the load, any impedance mismatch reflects part of the wave:

$$r_A = \frac{Z_A - Z_\ell}{Z_A + Z_\ell} \quad \text{where } Z_A$$

is the load impedance and $Z_\ell$ is line impedance 


### Propagation constant γ

$$\gamma = \alpha + j\beta$$

#### β (phase constant, in rad/m)

$$\beta = \frac{2\pi}{\lambda}$$

For a line with per-length parameters R', L', G', C', γ comes from:

$$\gamma = \sqrt{(R' + j\omega L')(G' + j\omega C')}$$


###  input reflection coefficient of a terminated transmission line

$$r_{input} = r_{load} \cdot e^{-2\gamma\ell}$$


### Power attenuation formula

$$P_{\text{out}} = P_{\text{in}} \cdot e^{-2\alpha\ell}$$

α = attenuation constant (how lossy the line is, Np/m), ℓ = length of the line (m)


### Power carried by a single traveling wave 
$$P^+ = \frac{|\hat{U}^+|^2}{2 Z_0} \qquad P^- = \frac{|\hat{U}^-|^2}{2 Z_0}$$

where $Z_0​$ = characteristic impedance of the line 


### Total voltage at the generator = forward + backward
$$U_G = U_1^+ + U_1^- = U_1^+ \cdot (1 + r_E)$$

where G is generator
