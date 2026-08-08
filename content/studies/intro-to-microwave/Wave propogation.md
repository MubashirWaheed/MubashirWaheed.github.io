--- 

title: Wave Propogation

---

### Complex surface impedance

Because the wave penetrating the material is strongly attenuated it see characteristic impedance $$Z_F$$

$$Z_F = \frac{E_g}{H_g} = (1+\mathrm{j})R_\square = (1+\mathrm{j})\sqrt{\frac{\pi f \mu_0}{\sigma}}$$  ;  &nbsp; $R□​$ is the real part of surface resistance 

 $$ Z_F = |Z_F| \cdot e^{\mathrm{j}\Delta\varphi}$$

The magnitude $$∣Z_F∣$$ scales the field ratio; the angle $$Δφ$$ is the phase difference between the $$E$$ and $$H$$ fields at the surface.

Computing the phase 
$$\Delta\varphi = \arctan\frac{\mathrm{Im}\{Z_F\}}{\mathrm{Re}\{Z_F\}} = \arctan 1 = 45^\circ$$;  &nbsp; for good conductor

### Skin effect

$$\delta = \frac{1}{\sqrt{\pi f \mu_0 \sigma}}$$ 

$$R_\square = \frac{1}{\sigma \delta}$$, real part of the surface resisatnce can be caclulated using sken effect and conductivity. 


$$Z_F$$ and $$Z_0$$  are material/medium impedances, known in advance. The boundary (Fresnel) formulas use both impedances to split the incident wave into reflected and transmitted parts. 

### Transmitted / reflected E-field 
$$E_g = \frac{2Z_F}{Z_F + Z_0}E_e \qquad E_r = \frac{Z_F - Z_0}{Z_F + Z_0}E_e$$

### Transmitted / reflected H-field

$$H_g = \frac{E_g}{Z_F} \qquad H_e = \frac{E_e}{Z_0} \qquad H_r = \frac{E_r}{Z_0}$$





| Subscript symbol | German | Meaning |
|--------|--------|---------|
| $e$ | einfallend | incident wave (arriving at boundary) |
| $r$ | reflektiert | reflected wave (bounced back) |
| $g$ | durchgehend | transmitted wave (into 2nd medium) |

So $E_e, E_r, E_g$ and $H_e, H_r, H_g$ are the incident, reflected, and transmitted E and H fields.


$$g = \frac{E_g}{E_e} = \frac{2Z_F}{Z_F + Z_0} \qquad r = \frac{E_r}{E_e} = \frac{Z_F - Z_0}{Z_F + Z_0}$$

(g = transmission coefficient, 
r = reflection coefficient.) These are the formulas that produce the transmitted and reflected fields.

### Brewster angle

$$\text{incident: } E_\parallel + E_\perp \;(\text{circular}) \quad\xrightarrow{\;\alpha_B\;}\quad \text{reflected: only } E_\perp \;(\text{linear})$$

$$\tan\alpha_B = \frac{n_2}{n_1} = \sqrt{\frac{\varepsilon_{r2}}{\varepsilon_{r1}}}$$

wave comes from air ($$\varepsilon_{r1} = 1$$ 
) into the dielectric ($$\varepsilon_{r2} = \varepsilon_r = 3{,}75$$)

$$n = \frac{c_0}{c_{\text{medium}}} = \sqrt{\mu_r \varepsilon_r}$$; &nbsp; For non-magnetic dielectrics ($$\mu_r = 1$$)
 
n is the refractive index of medium

### Reflectvivity 
**Power reflectivity** is the square of the field reflection coefficient:

$$
\frac{P_{r\perp}}{P_{e\perp}} = \frac{|E_{r\perp}|^2}{|E_{e\perp}|^2} = |r_\perp|^2
$$

The subscripts: $$P_{r\perp}$$  = reflected power of the perpendicular component, $$P_{e\perp}$$  = incident power of the perpendicular component, $$r_\perp$$
 = field reflection coefficient for perpendicular (s) polarization.

at Brewster angle, so $$r_\parallel = 0$$ (the parallel component does not reflect at all). The entire reflected wave is perpendicular-polarized.

### Reflection cofficient for perpendicular polarization 

$$
r_\perp = \frac{\cos\alpha_B - \sqrt{\varepsilon_r - \sin^2\alpha_B}}{\cos\alpha_B + \sqrt{\varepsilon_r - \sin^2\alpha_B}}
$$

we doing only perpendicular because at brewster angle only perfendicular component reflected and if we square the r we get the power.

$$
\frac{P_{r\perp}}{P_{e\perp}} = \left[\frac{\cos\alpha_B - \sqrt{\varepsilon_r - \sin^2\alpha_B}}{\cos\alpha_B + \sqrt{\varepsilon_r - \sin^2\alpha_B}}\right]^2 = 0{,}335
$$




### Conceptual story
In wave propagation there are two types of polarization. **Linear** and **Circular polarization**.Polarization describes the shape traced by the tip of the electric 
field vector $$\vec{E}$$.Circular wave has two components. Parallel and perpendicular.At the **Brewster angle**, the $$\parallel$$
component reflects with coefficient zero so only perpendicular component is reflected.Refractive index index tells us how much slower light travels in the medium 
Parallel component is not reflected at all, it is fully transmitted into the dielectric. Only the perpendicular component reflects.At the Brewster angle, the reflected ray
 and the transmitted (refracted) ray are exactly 90° apart:
$$ \alpha_B + \beta = 90^\circ$$
When an Em wave hits a material there is surface impedance $$Z_F$$. Some of the wave is reflected,some passed through the medium.
When a wave hits a dielectric boundary, it generally splits into two polarization components:

1. **parallel polarization** ($$\parallel$$): E-field in the plane of incidence

2. **perpendicular polarization** ($$\perp$$): E-field perpendicular to the plane of incidence.

Reflectivity (Reflexionsgrad) is the ratio of reflected power to incident power.
