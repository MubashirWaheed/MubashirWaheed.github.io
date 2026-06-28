---

title: Inductance of Toroidal Coil
date: 28-06-2026
---

### Toroid Inductance 

$$L = \mu_0\ \mu_r\ \frac{N^2\ A}{l_m}$$,  area given by $$A = \pi\ r^2$$, circumference length $$l_m = 2\pi r_m$$


**Paramagnetic**: weakly attracted to a magnet only while a magnet is nearby.

**Ferromagnetic**: strongly attracted to a magnet and can stay magnetic on its own(real magnet)

**Curie temperature T_C**: heat a magnet past this temperature and it stops being magnetic. $$u_r$$ drops to zero at this temp.

### Temperature coefficient ($TK_\mu$)

general idea: the fractional change of something per degree. 
of permeability tells you the relative (fractional) change in permeability per degree of temperature change.

To find the **temperature coefficient** find gradient(from graph) at the required point and divide by $$u_r$$
 
Temperature coefficient is calculated by: $$TK_\mu = \frac{1}{\mu_r} \cdot \frac{d\mu_r}{dT}$$

$$u_r$$ has direction realtion with inductacne( $$L$$) so higher  the permeability higher the inductance. 

$$TK_X = \frac{1}{X}\cdot\frac{dX}{dT}$$

it can be anything eg  $TK$ of inductane or capactance or reistance 

### Loss tangent ($$tanδ$$):

Quantifies how much a dielectric material dissipates electromagnetic energy as heat versus storing it.
$$\varepsilon = \varepsilon' - j\varepsilon''$$

In simple terms we need to figre out how much energy stored vs loss for real capacitor(parallel or series) and real inductor

Loss tangent is the ratio of energystored ($$\varepsilon'$$) vs energy lost($$ j\varepsilon''$$); &nbsp; $$\tan\delta = \frac{\varepsilon''}{\varepsilon'} = \frac{\text{power dissipated}}{\text{power stored}}$$

$$\tan\delta = \frac{\text{real (loss) part}}{\text{reactive (storage) part}} = \frac{1}{Q}$$; where $Q$ is the **quality factor**

##### Loss tangent for Real inductor 
Modeled as an ideal L with either a series winding resistance $R_s$  or a parallel loss resistance $R_p$. The reactance $\omega L$ stores energy, while $R_s$
(series) or $R_p(parallel)$ dissipates it. Use $R_{DC}$ value when no skin effect and $R_{HF}$ value when high skin effect present

$$\tan\delta = \frac{R_s}{\omega L}$$; &nbsp;  $$\tan\delta = \frac{\omega L}{R_p}$$, where $R$ is the resistance value of material eg wire 

##### Loss Tangent for Real Capacitor

Modeled as ideal $$C$$ with a series resistance $$R_s$$ (ESR), or equivalently a parallel resistance $$R_p$$:

$$\tan\delta = \omega R_s C = \frac{1}{\omega R_p C} = \frac{\epsilon''}{\epsilon'}$$


##### DC and HF Resistance (wire)
$$R_{DC} = \frac{\ell}{r^2\,\pi\,\sigma} = \frac{\rho\,\ell}{r^2\,\pi} $$; where $\sigma$ is the conductivity of the material, $\rho$ resistivity of material

$$R_{HF} \approx \frac{\ell}{\sigma\,2\pi r \delta}$$; where $r$ is the radius of wire, $\sigma$ is conductivity of meterial

#### Skin depth

$$\delta = \frac{1}{\sqrt{f\pi\mu_0\sigma_K}} $$

$$Q_L = \frac{1}{\tan\delta_\mu + \tan\delta_K}$$; $Q$ quality factor, $\tan\delta_\mu$ loss tangent(factor) of core/ferrite material, 
$\tan\delta_K$ wire material loss tangent wrapped around core

So the idea is order to find the quality factor($Q$) of coil(material) we find the quality factor of both coil and wire warpped around it and take
 the inverse.Since a wire is wrapped around  we have to check the skin effect and for that we calculate the skin depth ($\delta$) if the skin 
depth greater than wire radius than current fills the whole cross section hence skin effect neglected. This can also be done using the
 $R_{HF}$ and $R_{DC}$. If $R_{HF}$ resistance very small compared to the $R_{DC}$ we can neglect the skin effect and $R_{DC}$ to calculate the 
loss tangent of wire.

| If the question asks about... | You're working with... |
|---|---|
| Inductance $L$, permeability, flux, air gap effect(part of core removed ) | Reluctance (magnetic) |
| Quality factor $Q$, losses, $\tan\delta$, heating | Resistance (electric) |

### Magnetic Reluctane 

Magnetic reluctance is the opposition a magnetic circuit offers to the establishment of magnetic flux

$$R_m = \frac{\ell}{\mu_0 \mu_r A}$$


A magnetic circuit is formed when you wind a current-carrying wire (coil) around a ferromagnetic core, creating a closed loop path that guides 
magnetic flux, much like a wire guides current in an electric circuit.

### Conceptual Story 
we remove part of coil and it has different permeability(air). We assume a new value of relative permeability(called effective relative 
permeability) and the find it and relate to inductacne. 

### Effective permeability of a toroid with an air gap and air gap inductance

$$R_{m,total} = \frac{\ell_{Fe}}{\mu_0 \mu_r A} + \frac{\ell_S}{\mu_0 A}$$, &nbsp; &nbsp; &nbsp; &nbsp; where $Fe$ is iron core, $\ell_s$ is
 air gap cut in coil length

$$R_{m,total} = \frac{\ell_{Fe} + \ell_S}{\mu_0\,\mu_{r,eff}\,A}$$, &nbsp;&nbsp; &nbsp; &nbsp; &nbsp;  where $R_m$ is magnetic reluctance

$$\frac{\ell_{Fe} + \ell_S}{\mu_0\,\mu_{r,eff}\,A} = \frac{\ell_{Fe}}{\mu_0 \mu_r A} + \frac{\ell_S}{\mu_0 A}$$; &nbsp; where $A$ is correctional area 
of core

$$\mu_{r,eff} = \frac{\mu_r\,(\ell_{Fe} + \ell_S)}{\ell_{Fe} + \mu_r \ell_S}$$; &nbsp; &nbsp; made $\mu_{r,eff}$ the subject;

$$ \ell_{Fe} = 2\pi r_m - \ell_S$$

inductance directly propaartional to the relative p[ermeability so  use $\mu_{r,eff}$ to find new overall induatce with air and core 

$$L_L = \frac{\mu_{r,eff}}{\mu_r}\,L$$  ; &nbsp; &nbsp; &nbsp; where $L$ inductane without air part cut, $L_L$ new inductance with air part cut




### Magnetic field inside air gap of Core

$$V_m = H \cdot \ell$$ ; &nbsp; &nbsp;  where magnetic voltage = (magnetic field strength ${H}$) × (length) 

Idea: add magnetic voltage of air part and toroid coil part and equate to *electromtive force*

$$H_{Fe}\,\ell_{Fe} + H_S\,\ell_S = N\hat{I}$$

the boundary condition (continuity of $B$)
$$\vec{n}\cdot(\vec{B}_{Fe} - \vec{B}_S) = 0 \quad\Rightarrow\quad B_{Fe} = B_S$$

$$B=μ_0μ_rH$$; &nbsp;where $H$ is magnetic field strength, $B$ is magnetic flux density

$$\mu_0\mu_r H_{Fe} = \mu_0 H_S \quad\Rightarrow\quad H_S = \mu_r H_{Fe}$$

$$\frac{H_S}{\mu_r}\,\ell_{Fe} + H_S\,\ell_S = N\hat{I}$$ ; &nbsp; combined two laws 

$$H_S\left(\frac{\ell_{Fe}}{\mu_r} + \ell_S\right) = N\hat{I}$$ ;where subscript $s$ for $H$ represent air part 

$$H_S = \frac{N\hat{I}}{\dfrac{\ell_{Fe}}{\mu_r} + \ell_S}$$ ; &nbsp; where $I$ represnet the current passing through the wire wrapped on coil
