---

title: Waveguide Theory

---

### The naming rule
For any $H_{mn} (= TE)$ mode:

**m** = half-waves across the **width** a (x-direction)

**n** = half-waves across the **height** b (y-direction)

### General cutoff formula for every mode

$$f_{c,mn} = \frac{c_0}{2\sqrt{\varepsilon_r}}\sqrt{\left(\frac{m}{a}\right)^2+\left(\frac{n}{b}\right)^2}$$

With magnetic material

$$f_{c,mn} = \frac{c_0}{2 \sqrt{\mu_r \epsilon_r}} \sqrt{\left(\frac{m}{a}\right)^2 + \left(\frac{n}{b}\right)^2}$$

Plug in $m,n$ and you get any cutoff.

$a$ = the width (the longer side), measured along the $x$-direction

$b$ = the height (the shorter side), measured along the $y$-direction

$H₁₀$ is fundamental and depends only on width $a$.

### α_D​ is the dielectric attenuation coefficient

$$\alpha_D = \frac{k^2}{2\beta}\tan\delta_\varepsilon$$

### Guide wavelength

$$\lambda_g = \frac{\lambda}{\sqrt{1 - \left(\frac{\lambda}{\lambda_c}\right)^2}}$$

$$\lambda = \frac{c_0}{f \sqrt{\mu_r \varepsilon_r}}$$

where
 
$λ_g​$: guide wavelength (the real spacing between wavefronts inside the pipe)

$λ$: free-space wavelength of the same signal

$λ_c​$: cutoff wavelength of the mode; 

$a$ width

### Cutoff wavelength (general, rectangular waveguide)
$$\lambda_c = \frac{2}{\sqrt{\left(\frac{m}{a}\right)^2 + \left(\frac{n}{b}\right)^2}}$$

### Field wave impedance of a  H(magnetic) mode
$$Z_{F,\text{TE}} = \frac{Z_F}{\sqrt{1 - \left(\frac{\lambda}{\lambda_c}\right)^2}} = Z_F \cdot \frac{\lambda_g}{\lambda}$$

$Z_F$ : field wave impedance of the filling medium alone, $Z_F = 120\pi\ \Omega \cdot \sqrt{\frac{\mu_r}{\varepsilon_r}}$ (equals $\approx 377\ \Omega$ for air)

$\frac{\lambda_g}{\lambda}$ : the guide-wavelength stretch factor; always greater than 1, so it raises the impedance above $Z_F$

$\lambda_g$ : guide wavelength, the wavelength as the wave actually travels down the pipe

$\lambda$ : free-space wavelength of the same signal, $\lambda = \frac{c_0}{f \sqrt{\mu_r \varepsilon_r}}$

$\lambda_c$ : cutoff wavelength of the mode



Field wave impedance of a TM (E) mode:

$$Z_{F,\text{TM}} = Z_F \cdot \sqrt{1 - \left(\frac{\lambda}{\lambda_c}\right)^2} = Z_F \cdot \frac{\lambda}{\lambda_g}$$

Same square-root factor as TE, but multiplying instead of dividing, so the E-mode impedance is lower than $Z_F$ (TE is higher). Use this if a problem switches to 
$E_{11}$ or any E-mode.

#### k is the wavenumber 

Wave cutoff number at any frequency and mode 

$$k_{c,mn} = \sqrt{\left(\frac{m\pi}{a}\right)^2 + \left(\frac{n\pi}{b}\right)^2}$$

It measures the waves total electromagnetic  activity in the medium

$$k = \frac{2\pi}{\lambda} = \frac{2\pi f}{v} = \frac{\omega}{v} = \omega\sqrt{\mu\varepsilon}$$

For all non magnetic material eg plastic, air,glass, most metals eg copper the $u_r =$1 

Connecting to 

$$v = \frac{1}{\sqrt{\mu\varepsilon}} = \frac{1}{\sqrt{\mu_0\varepsilon_0}}\cdot\frac{1}{\sqrt{\mu_r\varepsilon_r}} = \frac{c_0}{\sqrt{\mu_r\varepsilon_r}}$$

#### β — the propagation constant (inside the guide)

This is the wave's actual phase advance per meter as it travels down the waveguide. 

$$\beta = \sqrt{k^2 - k_c^2}$$

where $k$ is the wavenumber at the operating frequency at which we send the wave. 

### Attenuation power relation

$$a = -10\log\left(\frac{P_{out}}{P_{in}}\right), \qquad \frac{P_{out}}{P_{in}} = e^{-2\alpha_{ges}\ell}$$

where $a$ = attenuation in $dB$,
$\alpha$ = attenuation constant

### Dielectric loss $\alpha$ from its formula

$$\alpha_D = \frac{k^2}{2\beta}\tan\delta_\varepsilon$$

where 

$k$ = wavenumber and $\beta$ = propagation constant, $\alpha_D$ dilelctiric filling absorbing energy


### Losses add (superposition of attenuation)

$$\alpha_{ges} = \alpha_D + \alpha_{wand,\text{H10}}$$

Total attenuation of the wave equals the sum of the attenuation from each independent loss mechanism. There are two possible loss mechanism

- the dielectric filling absorbs energy $(\alpha_D)$

- imperfect metal walls absorb energy $(\alpha_{wand})$ 

wall loss depends on which mode you're using eg $H_{10}$

### Wave guide Wall Attenuation formula
$$\alpha_{wand,\text{H10}} = \frac{R_\square}{Z_F}\cdot\frac{\Omega^2 + 2\dfrac{b}{a}}{b\,\Omega\sqrt{\Omega^2 - 1}}$$

$$α_{wand},H_{10​}$$ — wall attenuation coefficient for the $H₁₀$ mode

$R_□​$ — surface resistance (sheet resistance) of the wall metal.


$$R_\square = \frac{1}{\sigma\delta} = \sqrt{\frac{\pi f\mu_0\mu_r}{\sigma}}$$

$Z_F​$ — field wave impedance of the medium filling the guide

$$Z_F = \sqrt{\frac{\mu_0\mu_r}{\varepsilon_0\varepsilon_r}}$$

where $a$ = guide width, $b$ = guide height, $f$ =operationg frequency

### Skin depth 
$$\delta = \frac{1}{\sqrt{\pi f\mu_0\mu_r\sigma}}$$

### Inverted form for the conductivity 

$$\sigma = \left(\frac{\Omega^2 + 2\dfrac{b}{a}}{\alpha_{wand,\text{H10}}\,b\,\Omega\sqrt{\Omega^2 - 1}}\right)^2\cdot \pi f\varepsilon_0\varepsilon_r$$

### What is $\Omega$ 

It's the operating frequency divided by the cutoff frequency

$$\Omega = \frac{f_{\text{H10}}}{f_{c,\text{H10}}}$$

### Electric field magnitude in waveguide
This formula takes a position $(x,y)$ inside the guide's cross-section and gives you back how strong the **electric field** is at that point.

$$E_y(x,y) \sim \cos\left(\frac{m\pi}{a}x\right)\sin\left(\frac{n\pi}{b}y\right)$$

where $a$ = width wave guide, $b$ = wave guide height, $x$ = horizontal position, $y$ =vertical position

### Transported Active Power (for any H_{m0} mode)

$$P = \frac{ab}{4} \cdot \frac{|E_{y,\text{max}}|^2}{Z_{F,\text{H-mode}}}$$

### Phase and group velocity:
$$v_{\text{ph}} = \frac{c_0}{\sqrt{1 - \left(\frac{\lambda}{\lambda_c}\right)^2}}, \qquad v_{\text{gr}} = c_0 \cdot \sqrt{1 - \left(\frac{\lambda}{\lambda_c}\right)^2}$$

Same $\sqrt{1 - (\lambda/\lambda_c)^2}$ factor again. Phase velocity is faster than $c_0$ (divides), group velocity is slower (multiplies). 

Their product is $v_{\text{ph}} \cdot v_{\text{gr}} = c_0^2$.

### Waveguide: Advantages & Trade-offs 

Why waveguide? → low losses

Why coat with gold? → low corrosion

Disadvantage compared to coaxial line? → no DC (direct current) transmission						

### Longitudinal Field Components in Waveguides
The H- and E-field types differ in the occurrence of longitudinal field components. In H-field types, the magnetic field has a z-component. In E-field types, by contrast, 
the electric field has a z-component.

### Cut off Frequency
The cutoff frequency in a waveguide is the lowest frequency at which a given mode can propagate. 


### Conceptual story
At high frequncy the coaxial cables doens't work because they heat up so we use hollow metal tube but the quirk is below a certain frequncy(cutoff frequency) they don't work

### What is a "mode" (H₁₀, H₂₀, etc.)?

Because the wave bounces around inside the tube, the electric field can arrange itself into different standing patterns across the width and height. Each distinct pattern 
is a mode. Each patteren has its own cutoff frequency

$H₁₀$ = the simplest pattern. One "hump" of electric field across the width. This is the fundamental, the one you almost always want to use.
$H₂₀$ = two humps across the width.
$H₀₁$ = one hump across the height instead of the width.


**Impoprtant:** Metal kills electric fields that touch it sideways

 ### Direction the energy travels versus the direction the electric field points. 


**Two separate directions**
In the $H₁₀$ wave traveling down a normal waveguide (no wall yet):

Energy travels in the z  direction (down the tube). Yes. That's the propagation direction. The wave carries power from one end to the other along z.
**The electric field** points in the y direction (vertically, up and down across the height). The field is transverse, meaning it points sideways to the direction of travel, 
not along it.

Left and right side walls of wave guide (vertical sheets at $x=0$  and $x=a_1$): the vertical field runs along these. That's the tangential case. 
Forbidden. So the field must drop to zero at the two side walls.


<image src="attachments/waveguide_1.png" alt="waveguide" width="400" />


In the $H_{10}$ case $E$ field  wave are  perpendicular to the top and bottom walls of the wave guide tube so $E$ field not zero at the top and bottom. 
In the $H_{01}$ case waves are perpendicular to the left and right wall of the wave guide so not zero at the side walls. 

Where $E$ wave is parallel to the wall it will be zero 


### Magnetic Field Lines 
Magnetic field curl the elctric field that are oscilating the y direcion hence the $H$ (Magnetic field) lines fomr a closed loop and in the complete one wavelength they cahnage
 direction at half wavelength 

<image src="attachments/magnetic_field.png" alt="magnetic field"  width="400"/>



For $H_{10}$ specifically (the case you actually use): $|E_y(x)| \sim \sin\left(\frac{\pi}{a}x\right)$, zero at both side walls, maximum at the center $x = a/2$. Trust this over the schematic cos/sin form: the physical rule "E is zero where it runs parallel to a wall" always wins.


