---

title: Inductance of Toroidal Coil
date: 28-06-2026
---

### Toroid Inductance 

$$L = \mu_0\ \mu_r\ \frac{N^2\ A}{l_m}$$,  area given by $$A = \pi\ r^2$$, circumference length $$l_m = 2\pi r_m$$

$r_m​$ = mean radius (to the middle of the core ring)



### Temperature coefficient ($TK_\mu$)
It's just the relative (fractional) change of quantity $X$ per $°C$.
$X$ can be any property eg permeability, inducatnce, capacitance, resoannce frequency or even conuctivity
general idea: the fractional change of something per degree. 
of permeability tells you the relative (fractional) change in permeability per degree of temperature change.

To find the **temperature coefficient** find gradient(from graph) at the required point and divide by $$u_r$$
 
Temperature coefficient is calculated by: $$TK_\mu = \frac{1}{\mu_r} \cdot \frac{d\mu_r}{dT}$$

$$u_r$$ has direction realtion with inductacne( $$L$$) so higher  the permeability higher the inductance. 

$$TK_X = \frac{1}{X}\cdot\frac{dX}{dT}$$

it can be anything eg  $TK$ of inductane or capactance or reistance 

**General Linear Temperature Model**

$$X(T) = X_N \left(1 + TK_X \cdot (T - T_N)\right)$$

For capacitance 

$$C(T) = C_N \left(1 + TK_C \cdot (T - T_N)\right)$$

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

#### Quality factor($Q$) and Skin depth

$$\delta = \sqrt{\frac{\rho}{\pi\ f\ \mu_0\ \mu_r}} = \frac{1}{\sqrt{\pi\ f\ \mu_0\ \mu_r\ \sigma}}$$

Skin depth can also be written with angular frequncy 

$$\delta = \sqrt{\frac{2\ \rho}{\omega\ \mu}} = \sqrt{\frac{2}{\omega\ \mu\ \sigma}}$$

$$Q_L = \frac{1}{\tan\delta_\mu + \tan\delta_K}$$; $Q$ quality factor, $\tan\delta_\mu$ loss tangent(factor) of core/ferrite material, 
$\tan\delta_K$ wire material loss tangent wrapped around core

So the idea is order to find the quality factor($Q$) of coil(material) we find the quality factor of both coil and wire warpped around it and take
 the inverse.Since a wire is wrapped around  we have to check the skin effect and for that we calculate the skin depth ($\delta$) if the skin 
depth greater than wire radius than current fills the whole cross section hence skin effect neglected. This can also be done using the
 $R_{HF}$ and $R_{DC}$.

if $ R_{HF} \approx R_{DC}$  equivalently $$ \iff (  \delta \gg r ) \;\Rightarrow\; \text{skin effect negligible, use } R_{DC}$$;

where $r$ is radius of wire

Here is the thing at times we quality factor of circuit instead of indiviual elements(capacior or indcutor) so we follow the base formula

$$Q = \frac{X_L}{R} = \frac{\text{the inductor's opposition (stores energy)}}{\text{the resistors' opposition (waste energy)}}$$

Example at resonance frequency a circuit  wih series inductor, load and capacitor so we follow 

Reactance $X_L$ is the part of inductor where energy is stored hence in the numerator for the quality factor formula 

$$X_L = 2\pi f_{res,N} L_N$$

$$Q_L = \frac{2\pi f_{res,N} L_N}{R_c + R_L + R_{Load}}$$ 

At $f_{res}$ energy stored in inductor and capacitor is same hence we only take one reatance(in this case of inductor) 

### Transformer ratio 

Using this formula we can figureout the turns on coil required for system adn load impedance

$$\frac{Z_1}{Z_2} = n^2 = \left(\frac{N_1}{N_2}\right)^2$$


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

inductance directly propaartional to the relative p[ermeability so  use $\mu_{r,eff}$ to find new overall induatce with air and core.

Adding an air gap decreases the inductance.
The reason: the air gap introduces a large reluctance in series with the magnetic path. 

$$L_L = \frac{\mu_{r,eff}}{\mu_r}\,L$$  ; &nbsp; &nbsp; &nbsp; where $L$ inductane without air part cut, $L_L$ new inductance with air part cut




### Magnetic field inside air gap of Core

$$V_m = H \cdot \ell$$ ; &nbsp; &nbsp;  where magnetic voltage = (magnetic field strength ${H}$) × (length) 

Idea: add magnetic voltage of air part and toroid coil part and equate to *electromtive force*

$$H_{Fe}\,\ell_{Fe} + H_S\,\ell_S = N\hat{I}$$ ; &nbsp; where subscript $s$ for $H$ represnet air part

the boundary condition (continuity of $B$)
$$\vec{n}\cdot(\vec{B}_{Fe} - \vec{B}_S) = 0 \quad\Rightarrow\quad B_{Fe} = B_S$$

$$B=μ_0μ_rH$$; &nbsp;where $H$ is magnetic field strength, $B$ is magnetic flux density

$$\mu_0\mu_r H_{Fe} = \mu_0 H_S \quad\Rightarrow\quad H_S = \mu_r H_{Fe}$$

$$\frac{H_S}{\mu_r}\,\ell_{Fe} + H_S\,\ell_S = N\hat{I}$$ ; &nbsp; combined two laws 

$$H_S\left(\frac{\ell_{Fe}}{\mu_r} + \ell_S\right) = N\hat{I}$$ 

$$H_S = \frac{N\hat{I}}{\dfrac{\ell_{Fe}}{\mu_r} + \ell_S}$$ ; &nbsp; where $I$ represnet the current passing through the wire wrapped on coil

**Why use a toroidal coil instead of a solenoid in EMC-sensitive electronics?**

In a toroidal coil the field lines close on themselves inside the core, so the external stray field is very small. This makes it both a 
weaker source of interference and less susceptible to external fields than a solenoid, 
which is why it is preferred in EMC-sensitive electronics.

**Paramagnetic**: weakly attracted to a magnet only while a magnet is nearby.

**Ferromagnetic**: strongly attracted to a magnet and can stay magnetic on its own(real magnet)

**Curie temperature T_C**: heat a magnet past this temperature and it stops being magnetic. $$u_r$$ drops to zero at this temp.

| If the question asks about... | You're working with... |
|---|---|
| Inductance $L$, permeability, flux, air gap effect(part of core removed ) | Reluctance (magnetic) |
| Quality factor $Q$, losses, $\tan\delta$, heating | Resistance (electric) |


**Real coil Concept**

There can be parasitic capacitance in the real Coil at high frequency. Two paths offered between the same two nodes is the definition of a 
parallel connection. That is why $C$  sits in parallel with $L$, not in series for an real coil and resonance can happen in real coil and in
order to model the resistance of wire we put it in series with parallel elements (capacitor and inductor)


**Series resonant circuit vs paralrl resonant circuit **
In parraltrl resonant circuit at rsonacne resiatcen increase (max)
