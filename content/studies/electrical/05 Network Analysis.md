--- 
title: 05 Network Analysis 
---
Mainly in Network Analysis I am learning the transient behaviour of the circuits (zb. RL, damped RLC, damped series resonant circuit).

Drawing the circuit from the time domain to Laplace domain: since the coil and capacitor have a derivative in the time domain, which when converted to the Laplace domain results in initial conditions. Each element can be represented as either a series 
voltage source (Thévenin) or a parallel current source (Norton), as shown in the table below.

 
| Component | Impedance | Series source (Thévenin) | Parallel source (Norton) |
|---|---|---|---|
| Inductor | $sL$ | voltage $L\;i_L(0)$ | current $\dfrac{i_L(0)}{s}$ |
| Capacitor | $\dfrac{1}{sC}$ | voltage $\dfrac{u_C(0)}{s}$ | current $C\;u_C(0)$ |


<img src="/attachments/lcircuit.png" alt="laplace circuit" />

