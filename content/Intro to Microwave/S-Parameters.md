---
title: S-Parameters 
---
### General S-Matrix (two-port, relates outgoing waves to incoming waves
$$\begin{pmatrix} b_1 \\ b_2 \end{pmatrix} = \begin{pmatrix} s_{11} & s_{12} \\ s_{21} & s_{22} \end{pmatrix}\begin{pmatrix} a_1 \\ a_2 \end{pmatrix}$$

$$b_1 = s_{11}\,a_1 + s_{12}\,a_2 \\b_2 = s_{21}\,a_1 + s_{22}\,a_2$$

entries: $s_{11}$ = input reflection, $s_{22}$= output reflection, $s_{21}$ = forward transmission (port 1 to port 2), $s_{12}$ = reverse transmission (port 2 to port 1).

### Determinant
$$\det(S) = s_{11}\,s_{22} - s_{12}\,s_{21}$$

### Unitarity Condition (holds for lossless networks, energy conservation)
$$S^{*T} \cdot S = E$$

$S∗^T$ = conjugate transpose of $S$; $E$ = identity matrix.

### Power Balance from Unitarity (per-column power conservation, two-port)
$$|s_{11}|^2 + |s_{21}|^2 = 1 \qquad |s_{12}|^2 + |s_{22}|^2 = 1$$

### Reflected Power Fraction at a Port (fraction of input power reflected)
$$\frac{P_1^-}{P_1^+} = |s_{11}|^2$$

### Ideal Lossless Line S-Matrix (transmission line as a two-port, phase shift only)
$$S = \begin{pmatrix} 0 & e^{-j\beta \ell} \\ e^{-j\beta \ell} & 0 \end{pmatrix}$$

### Lossy Line S-Matrix (transmission line with attenuation)
$$S = \begin{pmatrix} 0 & e^{-(\alpha + j\beta)\ell} \\ e^{-(\alpha + j\beta)\ell} & 0 \end{pmatrix}$$

### Phase Constant of a Line (used to compute the transmission phase)
$$\beta = \frac{\omega}{c_0}\sqrt{\varepsilon_r \mu_r}$$

Check wethere the U_o and Epsilon_not is used or not for loss less case

### Wave Chain (Cascade) Matrix Definition (relates port-1 waves to port-2 waves)
$$\begin{pmatrix} a_1 \\ b_1 \end{pmatrix} = C \begin{pmatrix} b_2 \\ a_2 \end{pmatrix} = \begin{pmatrix} c_{11} & c_{12} \\ c_{21} & c_{22} \end{pmatrix}\begin{pmatrix} b_2 \\ a_2 \end{pmatrix}$$

### Wave Chain (Cascade) Matrix from S-Matrix (enables cascading of two-ports)
$$C = \frac{1}{s_{21}}\begin{pmatrix} -\det(S) & s_{11} \\ -s_{22} & 1 \end{pmatrix}$$

### Cascading Rule (total network from two cascaded two-ports)
$$C_{\text{total}} = C_1 \cdot C_2$$

### Shortcut for Two Matched Networks (skips the chain-matrix procedure) 
$$s_{21,\text{total}} = s_{21}^{(1)} \cdot s_{21}^{(2)} \quad\text{when}\quad |s_{11}| = |s_{22}| = 0$$

When both cascaded networks are reflection-free at both ports, the total forward transmission is simply the product of the 
individual ones

### Chain Matrix Back to S-Matrix (conversion from C to S)
$$S = \frac{1}{c_{22}}\begin{pmatrix} c_{12} & \det(C) \\ 1 & -c_{21} \end{pmatrix}$$
### S-Parameter in Decibels (magnitude of a wave-amplitude ratio)
$$|s_{ij}|_{\text{dB}} = 20 \log_{10} |s_{ij}|$$

### Reflection Coefficient in Decibels to Linear (converting a given $r_1$ in dB)
$$|r_1| = 10^{\,|r_1|_{\text{dB}} / 20}$$

### Absolute Power in dBm (used for input and reflected power)

$$P|_{\text{dBm}} = 10 \log_{10}\!\left(\frac{P}{1\ \text{mW}}\right)$$

### VSWR 
When a wave travels down a transmission line toward a load that is not perfectly matched, part of it reflects back. The forward
and reflected waves interfere, producing a fixed pattern of voltage maxima and minima along the line, a standing wave. VSWR is the
ratio of the largest voltage amplitude to the smallest:

$$VSWR = \frac{|E_{\max}|}{|E_{\min}|}$$

### VSWR from Reflection Coefficient (standing wave ratio in terms of $|s_{11}|$
$$VSWR = \frac{1 + |s_{11}|}{1 - |s_{11}|}$$

### Reflection Coefficient from VSWR (inverting the relation)

$$|s_{11}| = \frac{VSWR - 1}{VSWR + 1}$$

### Forward Gain (transmission from port 1 to port 2, amplification)

$$10 \log\!\left(\frac{P_2^-}{P_1^+}\right) = 20 \log|s_{21}|$$

### Backward Attenuation (reverse transmission, port 2 to port 1, isolation)

$$-10 \log\!\left(\frac{P_1^-}{P_2^+}\right) = -20 \log|s_{12}|$$

### Input Matching (input reflection $s_{11}$ from input VSWR)
$$VSWR_E = \frac{|E_{\max}|}{|E_{\min}|} \qquad |s_{11}| = \frac{VSWR_E - 1}{VSWR_E + 1}$$

### Output Matching (output reflection $s_{22}$ as reflection attenuation)
$$-10 \log\!\left(\frac{P_2^-}{P_2^+}\right) = -20 \log|s_{22}|$$


### Reciprocity (network behaves the same in both directions)
Signal transmission is identical forward and backward.For a two-port this means 
$$s_{12} = s_{21}$$

### Losslessness / Unitarity (no power dissipated inside the network)
Network is lossless when all incident power leaves through the ports and none is converted to heat. 
$$S^{*T} \cdot S = E$$

$$|s_{11}|^2 + |s_{21}|^2 = 1 \qquad |s_{12}|^2 + |s_{22}|^2 = 1$$

$$P_V = 1 - |s_{11}|^2 - |s_{21}|^2$$

If this is zero the network is lossless (regardless of how big $s_{11} is);
### Reflection Symmetry / Matching (self-reflection-free ports)
For a two-port this means $s_{11} = s_{22} = 0$

### Wave Amplitudes $a$ and $b$
$$a = \frac{1}{2}(u + i) \qquad b = \frac{1}{2}(u - i)$$

a = incident (ingoing) wave, b = reflected (outgoing) wave. 

### Magnitude Relations from Power Balance (abbreviation $\varrho$ for the reflection magnitude)
$$|s_{11}| = \sqrt{1 - |s_{12}|^2} = \varrho \qquad |s_{12}| = \sqrt{1 - |s_{11}|^2} \\[4pt]|s_{22}| = \sqrt{1 - |s_{12}|^2} = \varrho$$

### Impedance Matrix Definition (voltages from currents, Z-matrix)
$$\begin{pmatrix} U_1 \\ U_2 \end{pmatrix} = \begin{pmatrix} Z_{11} & Z_{12} \\ Z_{21} & Z_{22} \end{pmatrix}\begin{pmatrix} I_1 \\ I_2 \end{pmatrix} \qquad U = Z \cdot I$$

### The four parameters written out (two-port)

$$Z_{11} = \left.\frac{U_1}{I_1}\right|_{I_2 = 0} \qquad Z_{12} = \left.\frac{U_1}{I_2}\right|_{I_1 = 0} \\[6pt]Z_{21} = \left.\frac{U_2}{I_1}\right|_{I_2 = 0} \qquad Z_{22} = \left.\frac{U_2}{I_2}\right|_{I_1 = 0}$$

### Admittance Matrix Definition (currents from voltages, Y-matrix)
$$\begin{pmatrix} I_1 \\ I_2 \end{pmatrix} = \begin{pmatrix} Y_{11} & Y_{12} \\ Y_{21} & Y_{22} \end{pmatrix}\begin{pmatrix} U_1 \\ U_2 \end{pmatrix} \qquad I = Y \cdot U$$

### Normalized Impedance Matrix from S-Matrix (conversion S to z)
$$z = (E - S)^{-1}(E + S)$$

### S-Matrix from Normalized Impedance Matrix (conversion z to S)
$$S = (z - E)(z + E)^{-1}$$

### Inverse of a 2×2 Matrix (general formula)
$$M^{-1} = \frac{1}{\det(M)}\begin{pmatrix} d & -b \\ -c & a \end{pmatrix}, \qquad \det(M) = ad - bc$$

### Wave Source Definition
b is the wave coming out of the source (outgoing onto the cable). This is the total wave the source sends down the line toward 
the rest of the circuit.
$b_Q​$ = source wave (what the source launches on its own), $r_Q$ = source reflection coefficient
The outgoing wave b is made of two contributions added together:
$$b = \underbrace{b_Q}_{\text{launched}} + \underbrace{r_Q \cdot a}_{\text{reflected}}$$

### Normalized Source Impedance and Voltage (dimensionless quantities)
$$z_Q = \frac{Z_Q}{Z_\ell} \qquad u_Q = \frac{U_Q}{\sqrt{Z_\ell}}$$
$Z_ℓ​$ = cable characteristic impedance used as the reference for normalization.

### Source Wave from a Voltage Source (launched wave)
$$b_Q = \frac{u_Q}{1 + z_Q}$$

### Source Reflection Coefficient (reflection looking back into the source)
$$r_Q = \frac{z_Q - 1}{z_Q + 1}$$

### Current Source Version (via source transformation)

A current source $I_Q$  with parallel admittance $Y_Q$ is the same source, using $U_Q = I_Q / Y_Q$ and $Z_Q = 1/Y_Q$. In normalized form 
with $y_Q = Y_Q Z_\ell$

$$r_Q = \frac{1 - y_Q}{1 + y_Q} \qquad b_Q = \frac{i_Q}{1 + y_Q}, \qquad i_Q = I_Q \sqrt{Z_\ell}$$

$Z_Q​$ means source impedance. Quelle = source

### Measuring S Parameters
<img src='attachments/measurement_s_matrix.png' alt='measurement_s_matrix' width='400'/>

### phase of wave traveling down a line 

$$ \varphi = \frac{2\pi f \sqrt{\varepsilon_r}}{c_0}\,\ell$$



### Make notes for the case where reflection between the source and teh input port in S port 


### Checking if the S matrix can be realized using the passive componnets

A network described by scattering matrix $S$ is realizable with only passive components if and only if it does not generate power. 

$$P = E - S^{*T} S$$

For a $2×2$, just check $P_{11} \geq 0$ and $det⁡P≥0$
