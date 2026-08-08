---

title: Overview 
date: 2026-07-17
---

This is a rough overview of the course listing with a brief explanation of everything.

## Defining an Autonomous System

An autonomous system is characterized by:

- **Understanding the environment** through perception
- **Decision-making** under uncertainty
- **Adaptability** to changing conditions

## Why Simulate Autonomous Systems?

| Benefit | Description |
|---|---|
| Cost effectiveness | Avoids expensive physical prototyping |
| Rapid development | Faster iteration cycles |
| Error identification | Catches faults before deployment |
| Extreme scenarios | Safely tests edge cases |

## Modeling of Dynamic Systems

**Dynamic system:** a system whose state changes over time due to internal and external factors.

**Modeling:** creating a mathematical, computational, or physical representation of a system to describe how it behaves.

**Simulation:** executing a model over time to analyze how the system evolves under different conditions.

Physically, the components of a dynamical system fall into different domains, e.g. mechanical, electrical, thermodynamic.

### Component types

| Domain | Example components |
|---|---|
| Mechanical | Rotating shaft, bearing, housing |
| Electromagnetic | Magnets, coils, connectors |

### Dynamic System Types

| Type | Description | Example |
|---|---|---|
| Single Input Single Output (SISO) | One input drives one output | Cruise control: throttle in, speed out |
| Multiple Input Single Output (MISO) | Several inputs affect one output | Room temperature from heater, window, and outside temp |
| Single Input Multiple Output (SIMO) | One input affects several outputs | Engine throttle affecting both speed and fuel consumption |
| Multiple Input Multiple Output (MIMO) | Several inputs affect several outputs | Quadcopter: four motor inputs controlling pitch, roll, yaw, and altitude |

## Classification of Dynamic Systems

Dynamic systems can be classified along five independent axes. A given system sits somewhere on each one (e.g. a system can be linear, deterministic, lumped, continuous, and time-invariant all at once).

| Axis | Type | Definition | Example |
|---|---|---|---|
| **Linearity** | Linear | Governed by linear differential equations | Spring-mass-damper: $m\ddot{x} + c\dot{x} + kx = f$ |
| | Nonlinear | Governed by nonlinear differential equations | Same system with dry friction: $m\ddot{x} + c\dot{x} + kx + \mu N\,\text{sgn}(\dot{x}) = f$ |
| **Predictability** | Deterministic | Same input always produces the same output | Ideal pendulum with no random disturbance |
| | Stochastic | Contains randomness; output described by probabilities | Sensor readings with measurement noise |
| **Spatial dependence** | Distributed | Variables depend on both time and space; behavior can vary in space | Heat conduction in a solid: temperature varies with time and position |
| | Lumped | Variables depend only on time; behavior uniform in space | Electrical circuit with discrete R, L, C components |
| **Time domain** | Continuous-time | State defined at every instant | Analog voltage in a circuit |
| | Discrete-time | State defined only at sampled instants | Digital controller sampling every 10 ms |
| **Time dependence** | Time-invariant | Governing equations have constant coefficients | Fixed pendulum: $mL^2\ddot{\theta} + mgL\sin\theta = 0$ |
| | Time-variant | Coefficients change with time | Varying pendulum: $m(t)L^2\ddot{\theta} + m(t)gL(t)\sin\theta = 0$ |

## Role of Simulation in Autonomous System Development

**Hardware in Loop (HIL) and Digital Twin Testing**
- HIL testing integrates real hardware with simulated environments for realistic validation
- Digital twins replicate real-world systems in simulation for optimization

**Validation and Regulatory Compliance**
- Autonomous systems must meet safety and regulatory standards before deployment
- Simulation demonstrates compliance with industry regulations without physical trials

**Multi-Agent and Human Interaction Testing**
- Simulation enables testing of multi-agent interactions
- Examples: swarming drones, self-driving convoys, human-robot collaboration

## Simulation Methodologies

Three main approaches, often combined into hybrid methods.

### Model-based simulation

Develops **mathematical models** from system dynamics and control principles, usually derived from first principles (differential equations, state-space representations).

| Advantages | Challenges |
|---|---|
| High interpretability and explainability | Requires accurate mathematical modeling |
| Incorporates known system physics and constraints | Computationally expensive for complex nonlinear systems |
| Suitable for control design and verification | May not handle high uncertainty or rapid changes |

### Physics-based simulation

Explicitly applies **physical laws** (Newtonian mechanics, electromagnetism, fluid dynamics) to simulate behavior. Used when direct mathematical models are too complex.

| Advantages | Challenges |
|---|---|
| Accurate when physical interactions are understood | Computationally intensive for real-time applications |
| Captures nonlinear and complex interactions | Requires detailed knowledge of material properties and environmental interactions |
| Essential for virtual prototyping and safety testing | |

### Data-driven simulation

Relies on **historical or real-time data** to learn system behavior, using statistical methods or machine learning models.

| Advantages | Challenges |
|---|---|
| Handles complex and uncertain systems | Requires large, high-quality datasets |
| Does not require precise physical models | Poor generalization outside training data |
| Enables real-time simulation with high adaptability | Often lacks explainability and interpretability |

## Simulation to Reality: The Sim-2-Real Gap

The **sim-to-real gap** is the discrepancy between how a system behaves in simulation versus the real world.

- Simulation offers a controlled, repeatable, cost-effective environment for training and testing
- Real-world deployment introduces unmodeled complexities and uncertainties that can degrade performance

### Sources of the gap

| Source | Problem |
|---|---|
| Physics discrepancies | Simulators use approximations that don't match real physics precisely |
| Sensor and actuator noise | Real devices have noise, latency, and calibration errors |
| Environmental variability | Real-world randomness: lighting changes, wear, tear, disturbances |
| Robot-object interactions | Contact dynamics are hard to model accurately |
| Model biases | Data-driven models trained in sim fail in the real world due to domain shift |


## Understanding a Mechatronic System

Understanding a mechatronic system requires several thought processes, each mapping to a type of process:

| Thought process | Maps to |
|---|---|
| Modeling of components (mechanical, electrical, ...) | Analytical process |
| System design and control | Systematical process |
| Error handling and progression | Statistical process |

Together, these three converge on a full **understanding of the mechatronic system**.


## What Is a Model?

A model is a **simplified representation of a system, concept, or process** that helps us understand, analyze, or predict its behavior.

| Type | Description |
|---|---|
| Mathematical | A set of equations describing relationships between variables |
| Physical | A tangible object or structure that mimics the real thing |
| Computational | A digital simulation of a system |
| Conceptual | A high-level abstraction used for explanation or planning |
| Data-driven | A model trained on data to make predictions or detect patterns |

## Mathematical Fundamentals

Dynamic systems are described through **mathematics**. The key fundamentals used for modeling are:

- Vector algebra
- Matrix algebra
- Complex numbers
- Differential equations
- Laplace

# Fundamentals of Modelling


## How to Create a Model? Types of Modeling

There are two broad approaches to modeling, and this course focuses on the rule-based one.

### Descriptive modeling

Captures **"what the system looks like"**, the actual state of a system at a given time point (or several).

- Specifies the actual state in a descriptive manner
- Methods: taking a picture, creating a miniature
- More quantitative methods: regression analysis, pattern recognition

### Rule-based modeling  ← focus of this lecture

Captures **"how the system will behave"**, finding dynamical rules that explain and predict observed behavior.

- Finds dynamical rules that explain observed system behavior
- Used for predictions
- Methods: dynamical equations, theories

## How to Create a Model? Example: Heater

The **cycle of rule-based modeling**, illustrated with a thermostat-controlled heater:

1. **Observe the system of interest.** The room temperature stays roughly within a comfortable range, between 20°C and 22°C.

2. **Reflect on possible rules** that might cause the observed characteristics. Propose a rule: *if temperature < 20°C, turn the heater ON; if > 22°C, turn it OFF.*

3. **Derive predictions and compare with reality.** If the room cools to 19°C, the heater should activate; once it warms to 23°C, it should stop.

4. **Repeat and refine** until satisfied with the model. Does the heater turn on and off as predicted? Is the temperature staying in range?

basically create the mathemicatical equation for the equation


## Modeling Complex Systems: Computational Modeling

**Computational modeling and simulation:** construct your own model with the full details of *microscopic rules* coded into the computer, then let it run and reveal the 
*macroscopic behavior* that arises from those rules.

## Modeling Complex Systems: Hospital Emergency Department

**Macroscopic behavior** observed after running an agent-based simulation:

| Emergent behavior | Interpretation |
|---|---|
| Bottlenecks in treatment | Long patient queues during peak arrival hours |
| Overloaded staff | Doctors and nurses remain in "busy" states most of the time |
| Idle robots during low demand | When few patients are present, robots stand by |
| Throughput patterns | Number of patients processed per hour stabilizes over time |
| Coordination gains from autonomy | Autonomous robots reduce staff workload by offloading tasks |

You might also observe **non-linear behaviors**, such as:
- A small increase in arrival rate causing a sudden system collapse
- Better robot-human coordination producing nonlinear improvements in efficiency

## A Good Model

A good model is **simple, valid, and robust**.

| Property | Meaning |
|---|---|
| Simplicity | A short, simple description of reality; eliminate any parameter, variable, or assumption you can without losing the model's characteristic behavior |
| Validity | How closely the model's prediction agrees with observed reality; each assumption must be valid given existing knowledge and common sense |
| Robustness | Insensitivity of the model's prediction to minor variations in assumptions or parameter settings |

## System Model Representations

A mathematical model is converted into an equivalent **model representation**. Which one you pick depends on the type of system, the questions being asked, and the level of detail needed.

Common representations:
1. Transfer function formulation
2. State-space representation
3. Block diagram representation (in the s-domain)
4. Block diagram representation (in the time domain)
5. And others

**Purpose:** provide a *standard form* for numerical solutions, understand the *interactions* among components, and obtain information about internal variables 
(*state variables*).

## System Model Representations: Transfer Function Formulation

**Spring-mass-damper system**, worked from equation of motion to transfer function.

- System input: external force $f$
- System output: displacement $x$

The key insight: in the s-domain, the system output is the **product of the transfer function and the input**.


<img src="/attachments/transfer-function.png" width="800" />


## System Model Representations: State-Space Representation

**Spring-mass-damper system**, converted from a second-order equation of motion into a set of first-order state equations.

Key rule: the **number of state variables equals the order of the original differential equation**. Here the equation of motion is second-order, so two state variables are needed.

Output equations depend on which system outputs you select. If velocity and spring force are chosen as outputs, they follow directly from the state variables.


$$
m\ddot{x} + c\dot{x} + kx = f
$$

### Selection of state variables
Position becomes the first state, velocity the second. Two states because the equation is second-order
$$
x_1 = x, \qquad x_2 = \dot{x}
$$

### Converted state equations
The single second-order equation rewritten as two coupled first-order equations, which is the state-space form.
$$
\dot{x}_1 = x_2, \qquad \dot{x}_2 = \frac{1}{m}\left[-kx_1 - cx_2 + f\right]
$$

### Output equations (velocity and spring force as outputs)
Chosen outputs expressed in terms of the state variables.

$$
y_1 = x_2, \qquad y_2 = kx_1
$$

Up untill this point we have gave the governing equation of single mass and double mass spring which is converted to different forms eg State space represenation, 
block diagram time domain and s domain and transfer function
write down the governing equations of the spring mass (double and single) on the formula sheet

## Drawing the free body diagram of Mechnaical system 
1. Every mass(translation) or **moment of inertia $J_m$** (rotational) gets its own box.
This also tells how many equations of motion we will have (one per box) 
2. $\tau_m$(force) applied to the moment of inertia $J$ block. Direction of the arrow into the block since force applied to the block.
3. Spring, drag and shaft resistance opposes the torque applied. direction of the arrow again into the box
4. in rotational systems $\theta$ direction will be in the direction of the $\tau$(force) since force applied is greater than than the  opposing (resistance) forces hence the body 
rotates.
5. In order to derive the equaitons of the system we apply the Newtons 2nd law which says 
$$
\sum \tau = J\ddot{\theta}
$$

In simple terms we put all the $\tau$ acting on the body and equate to the $J\ddot{\theta}$

Slight important detail to remmeber the 
Different elements relate torque to different derivatives of the same angle.

| Element | Constitutive relation | Depends on |
|---|---|---|
| Inertia | $\tau = J\ddot{\theta}$ | Acceleration (2nd derivative) |
| Damper / bearing | $\tau = b\dot{\theta}$ | Velocity (1st derivative) |
| Spring | $\tau = k_T\theta$ | Position (no derivative) |

$$
\underbrace{J_m\ddot{\theta}_m}_{\text{inertia}} + \underbrace{b\dot{\theta}_m}_{\text{damper}} + \underbrace{k_T(\theta_m - \theta_p)}_{\text{spring}} = \tau_m
$$

<img src="/attachments/question-freebody.png" width="400" />
<img src="/attachments/free-body-diagram.png" width="400" />

**Imporatant Note:** If there is only one theta given in the equation you can deduce that every part of the rotating assembly moves together and one one degree of freedom

## Rules for drawing the Schematic diagram
You need to have basic understand of question and usually diferential equaiton given
<img src="/attachments/schematic-diagram.png" width="600" />

## Block diagram from the Transfer function in s Domain 
What you have to do is convert the differential equation to s domain using the lapalce. Remember constant from differential equation has s in denominator in s domain. 
Make the transfer function and then draw the Block digram

Note that transfer function is output/input and we simlify the fraction to get input and output
<img src="/attachments/block-diagram.png" width="800" />

## Block Diagram of equation in Time domain
1. We make the double derivative element subject
2. For each derivative element (double or single) we put one integrator
 
#### Governing Equation
$$
J\ddot{\theta}(t) + d\dot{\theta}(t) + c\theta(t) + \tau_{\text{fric}} = \tau_{\text{ext}}(t)
$$ 

$$
\tau_{\text{fric}} = \text{sgn}(\dot{\theta})\;\tau_{\text{Coul}}
$$

$$
\ddot{\theta}(t) = \frac{1}{J}\left[\tau_{\text{ext}}(t) - d\dot{\theta}(t) - c\theta(t) - \tau_{\text{fric}}\right]
$$

Making $\ddot{\theta}$ the subject puts it at the start of that chain. Everything else in the diagram is produced downstream by integrating.

In the question it says to use **$tan$** instead of the **$sgn$** for the **$\tau_{fric}$** which depends on 1st derivative hence feedback taken from middle

<img src="/attachments/block-diagram-timedomain.png" width="800" />

## State Space Representaion of Differentrial Equation 
you can trade one high-order equation for several first-order ones.
criteria for choosing the state variable: state variables are the quantities that store energy
so the idea is you need to figureout the states for each system(Spring mass damper, Electrial, Thermal, Fluid )


Once you understand which states we need to use to write the differenrtial equation we take derivatives and seperate and subsistue and teh whole thing becomes very mechaniocal 
in nature 

| System | Storage elements | States | Order |
|---|---|---|---|
| Spring-mass-damper | Mass + spring | $x$, $\dot{x}$ | 2 |
| Series RLC | Inductor + capacitor | $i_L$, $v_C$ | 2 |
| Heater / room | Thermal mass only | $T$ | 1 |
| RC circuit | Capacitor only | $v_C$ | 1 |
| Single tank | Tank only | $h$ | 1 |
| Two coupled tanks | Two tanks | $h_1$, $h_2$ | 2 |

| System | Storage elements | State 1 | State 2 |
|---|---|---|---|
| Spring-mass-damper | Mass + spring | $x_1 = x$ (displacement) | $x_2 = \dot{x}$ (velocity) |
| Rotating shaft (torsional) | Inertia + torsional spring | $x_1 = \theta$ (angle) | $x_2 = \dot{\theta}$ (angular velocity) |
| Series RLC circuit | Inductor + capacitor | $x_1 = v_C$ (capacitor voltage) | $x_2 = i_L$ (inductor current) |
| Two-capacitance thermal | Two thermal masses | $x_1 = T_1$ (first temperature) | $x_2 = T_2$ (second temperature) |
| Two coupled tanks | Two fluid capacitances | $x_1 = h_1$ (first tank level) | $x_2 = h_2$ (second tank level) |

## The governing equation per domain

The reason for writing these governing eqautions is to be able to draw the free body diagram in each system and in turn be able to write differential equations of a system

| Domain | "Body" is | Governing law | Equation |
|---|---|---|---|
| Mechanical (translational) | Each mass | Newton's 2nd law | $\sum F = m\ddot{x}$ |
| Mechanical (rotational) | Each inertia | Newton's 2nd law (rotational) | $\sum \tau = J\ddot{\theta}$ |
| Electrical | Each loop or node | Kirchhoff's voltage / current law | $\sum v = 0$ around a loop |
| Thermal | Each thermal mass | Conservation of energy | $C\frac{dT}{dt} = \sum q_{\text{in}} - \sum q_{\text{out}}$ |
| Fluid | Each tank | Conservation of mass | $C_v\frac{dh}{dt} = \sum q_{\text{in}} - \sum q_{\text{out}}$ |

All five are the same statement: rate of change of what's stored equals net flow in. Newton's law is momentum accumulation, thermal is energy accumulation, fluid is mass 
accumulation, Kirchhoff is charge and energy accounting.

## Thermal Systems

$$
q_{out} = \frac{T - T_f}{R_{eq}}
$$
Where $q_{out}$ = heat flow rate escaping

$R_{eq}$ the total series thermal resistance

$$
C\frac{dT}{dt} = q_{in} - \frac{T - T_f}{R_{eq}}
$$

$C$ is thermal capacitance , $T$ the body temperature 

## Fluid Dynamics Recipe for differential equation

### Conversion between mass flow rate and volume flow rate
$$
q_m = \rho\;q \qquad \left[\; q_m:\ \text{mass flow rate},\quad \rho:\ \text{liquid  density},\quad q:\ \text{volume flow rate} \;\right]
$$

When we write the pipe equaion we are finding the flow rate through it 

$$
\underbrace{\rho q_1 = \frac{\rho g (h_1 - h_2)}{R_1}}_{\substack{\text{MASS flow [kg/s]} \\ \text{this is the raw output of } \Delta p = R q_m}} \qquad\qquad \underbrace{q_1 = \frac{g (h_1 - h_2)}{R_1}}_{\substack{\text{VOLUME flow [m³/s]} \\ \text{after dividing by } \rho}}
$$


every resistance equation finds a flow. Every tank equation finds a rate of level change. The pump finds nothing, it just tells the valve what pressure to work against.

### Base formula for each element

$$
\underbrace{q_m}_{\substack{\text{mass flow through} \\ \text{the element [kg/s]}}} = \frac{\overbrace{p_{\text{upstream}} - p_{\text{downstream}}}^{\substack{\text{pressures at the two ENDS} \\ \text{of that element [Pa]}}}}{\underbrace{R}_{\substack{\text{resistance of} \\ \text{that element}}}}
$$

#### Pump

The valve has two ends, and one of them is the tank

We are computing the pressure at the valve's right end, and that end happens to be screwed into the bottom of Tank 1. So the pressure there is the tank-bottom pressure.
$$
\underbrace{\text{PUMP}}_{p = P_a + \Delta P} \quad\longrightarrow\quad \underbrace{\big[\ \text{VALVE } R_p\ \big]}_{\substack{\text{the element} \\ \text{you're writing the equation for}}} \quad\longrightarrow\quad \underbrace{\text{TANK 1 BOTTOM}}_{p = P_a + \rho g h_1}
$$

$$
q_m = \frac{\overbrace{(P_a + \Delta P)}^{\text{push from the left}} - \overbrace{(P_a + \rho g h_1)}^{\text{push back from the right}}}{R_p}
$$
#### Pipe 1 
$$
\underbrace{\text{TANK 1 BOTTOM}}_{p = P_a + \rho g h_1} \quad\longrightarrow\quad \underbrace{\big[\ \text{PIPE 1, } R_1\ \big]}_{\substack{\text{the element you're} \\ \text{writing the equation for}}} \quad\longrightarrow\quad \underbrace{\text{TANK 2 BOTTOM}}_{p = P_a + \rho g h_2}
$$

$$
\rho q_1 = \frac{\overbrace{(P_a + \rho g h_1)}^{\text{Tank 1 pushes}} - \overbrace{(P_a + \rho g h_2)}^{\text{Tank 2 pushes back}}}{R_1} = \frac{\rho g (h_1 - h_2)}{R_1}
$$

Divide by $\rho$  for volume flow:
$$
q_1 = \frac{g}{R_1}(h_1 - h_2)
$$

#### Pipe 2

$$
\underbrace{\text{TANK 2 BOTTOM}}_{p = P_a + \rho g h_2} \quad\longrightarrow\quad \underbrace{\big[\ \text{PIPE 2, } R_2\ \big]}_{\substack{\text{the element you're} \\ \text{writing the equation for}}} \quad\longrightarrow\quad \underbrace{\text{OPEN AIR}}_{p = P_a}
$$

$$
\rho q_{out} = \frac{\overbrace{(P_a + \rho g h_2)}^{\text{Tank 2 pushes}} - \overbrace{P_a}^{\text{air pushes back}}}{R_2} = \frac{\rho g h_2}{R_2}
$$
volume flow

$$
q_{out} = \frac{g}{R_2}h_2
$$

#### Tank 1
$$
\underbrace{A_1}_{\substack{\text{cross-sectional} \\ \text{area [m²]}}} \cdot \underbrace{\frac{dh_1}{dt}}_{\substack{\text{how fast the level} \\ \text{rises [m/s]}}} = \underbrace{q_v}_{\substack{\text{IN through} \\ \text{the valve}}} - \underbrace{q_1}_{\substack{\text{OUT through} \\ \text{Pipe 1}}}
$$

$$
A_1\dot h_1 = \underbrace{\left(\frac{\Delta P}{\rho R_p} - \frac{g}{R_p}h_1\right)}_{q_v} - \underbrace{\frac{g}{R_1}(h_1 - h_2)}_{q_1}
$$

$$
A_1\dot h_1 = \underbrace{\frac{\Delta P}{\rho R_p}}_{\substack{\text{input, from} \\ \text{the pump}}} - \underbrace{g\left(\frac{1}{R_p} + \frac{1}{R_1}\right)h_1}_{\substack{\text{everything Tank 1's own level} \\ \text{works against: both resistances}}} + \underbrace{\frac{g}{R_1}h_2}_{\substack{\text{Tank 2 pushing back} \\ \text{through Pipe 1}}}
$$

#### Tank 2
$$
\underbrace{A_2}_{\substack{\text{cross-sectional} \\ \text{area [m²]}}} \cdot \underbrace{\frac{dh_2}{dt}}_{\substack{\text{how fast the level} \\ \text{rises [m/s]}}} = \underbrace{q_1}_{\substack{\text{IN through} \\ \text{Pipe 1}}} + \underbrace{q_{in}}_{\substack{\text{IN from the} \\ \text{external supply}}} - \underbrace{q_{out}}_{\substack{\text{OUT through} \\ \text{Pipe 2}}}
$$

$$
A_2\dot h_2 = \underbrace{\frac{g}{R_1}(h_1 - h_2)}_{q_1} + q_{in} - \underbrace{\frac{g}{R_2}h_2}_{q_{out}}
$$

$$
A_2\dot h_2 = \underbrace{\frac{g}{R_1}h_1}_{\substack{\text{Tank 1 pushing in} \\ \text{through Pipe 1}}} - \underbrace{g\left(\frac{1}{R_1} + \frac{1}{R_2}\right)h_2}_{\substack{\text{everything Tank 2's own level} \\ \text{works against: both resistances}}} + \underbrace{q_{in}}_{\substack{\text{input, external} \\ \text{volume supply}}}
$$

### Volume Capacitance: The Tank Equation

$$
\underbrace{C_v}_{\substack{\text{volume capacitance} \\ \text{[m²]}}} \cdot \underbrace{\frac{dh}{dt}}_{\substack{\text{rate of level change} \\ \text{[m/s]}}} = \underbrace{q_{in}}_{\substack{\text{volume flow in} \\ \text{[m³/s]}}} - \underbrace{q_{out}}_{\substack{\text{volume flow out} \\ \text{[m³/s]}}}
$$

The value of $$C_v$$

$$
\underbrace{C_v}_{\substack{\text{volume capacitance} \\ \text{of the tank}}} = \underbrace{A(h)}_{\substack{\text{cross-sectional area} \\ \text{at height } h \text{ [m²]}}}
$$

#### Procedure is identical in every domain

1. Draw a free body for each storage element (mass, inertia, thermal capacitance, tank; for circuits, a loop or node)
2. Cut every connecting element and name the flow through it (torque $\tau_s$τ, heat flow $q_1$, volume flow $q_1$, current $i$)
3. Write the balance equation per storage element
4. Write the constitutive relation for each connecting element
5. Substitute to eliminate the auxiliary variables

- Electrical circuit state space represenation 
- I need to do thermal system free body diagram, differential equation, transfer function
- Fluid sytem free body diagram, differential equaion, transferion function, block diagram
- write spring mass and spring double mass equations in sheet
- how to write state space represenatation of each system
- Dc motor with load 

#### Basic Concept 
Basically figureout where is the enrgy, capacitance, mass, momentum is being stored and for that we write the differential equation. The general Storage balance is 

$$
\frac{dQ_{stored}}{dt} = \dot{q}_{in} - \dot{q}_{out}
$$

$q˙_{in},q˙{out}$: rates of flow in and out (current, mass flow rate, heat flow rate)

After that write the resisatnce elemnets equation for the system. Resistance elements can be in series or parallel

Example resistanc formula
$$
R = \frac{L}{kA}
$$

Following is most important it is applied to all in some way or form

$$
\text{flow} = \frac{\text{potential difference}}{\text{resistance}};

\hspace{2em}

q_{out} = \frac{1}{R_{eq}}(T - T_f);

\hspace{2em}
i = \frac{1}{R}(v_1 - v_2);
$$



I am learnig about the possible states for different system and hwo to form differential equations for thema and their converion to the State space representaion then differnet 
forms 
I am understadning what is the governing equation for each system. example in case of the shaft rotational we take the net torque on a body given by $\tau= J\theta$ to form the 
differential equaition of each body represented by  $J$

Thought
understand common governing equation for each system then draw block diagram based on the undrstading that which is the storage element in the system hence you will be able to
write the differential equaion as you have identified the number of storage element then comes the part of represenation of differential eqauion in transfer fuhnction, state 
space or block diagram(s domain or time domain)

I am finding the equation derivation for the fluid system rather complex reason being so many components
