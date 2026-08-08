---

title: Miscellaneous
date: 2026-07-27 
---

In this file I will listing information in particualr sequence since I am short on time and I have my exam inn 26 hours 

In electronics, $Ω$ = ohms (unit of resistance). Here it's a unit.

In rotational dynamics / control, $Ω(s)$ = the Laplace transform of **angular velocity**. Here it's a signal.

Capacitor opposes changing voltage and the relaion in terms of integral and the 

Same thing written in derivative and integral for the capacitor
$$
i = C \frac{dv}{dt}; \qquad v(t) = \frac{1}{C} \int_0^t i \; dt
$$


## KVL Sign Rule (Loop Method)

**What it governs:** the sign of each voltage term as you write the loop equation.

**The rule:** Pick a direction to walk around the loop (usually the direction of the loop current). At each element, the sign depends on which terminal you enter first:

- Enter the − terminal first → voltage is a rise → write it positive
- Enter the + terminal first → voltage is a drop → write it negative

Example
entering the source at its − terminal gives 
$+v_{in}$;passing through $R1$ and $C1$ in the current's direction gives drops, so both are negative:

$$
v_{in} - v_{R_1} - v_{C_1} = 0
$$

## KCL Sign Rule (Node Method)

**What it governs:** the sign of each current term as you write the node equation.

**The rule:** Pick a convention (currents into the node positive). At each element, the sign depends on the current arrow's direction relative to the node:

Arrow points into the node → write it positive
Arrow points away from the node → write it negative

**Example**: 
$i_{R1}$ flows into the node (positive); 
$i_{C1}$ and $i_{R2}$
flow away (negative):

$$
i_{R_1} - i_{C_1} - i_{R_2} = 0
$$


## Rule: Flipping Polarity of a Shared Element (Flip Voltage AND Current Together)
You may flip the reference polarity of a shared element in one loop, but only if you flip its current reference in that same loop too. Flip one without the other and you're 
wrong. Flip both and you're fine.


KCL is valid regardless of how many current sources, voltage sources, resistors, capacitors, inductors, or other elements are in the circuit.

KVL can also be applied with multiple current sources and voltage sources present.
