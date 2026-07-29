---

title: State Space Representation 

---

## 2nd order differentiaol Equation 

$$
\ddot{y} = u - 7\dot{y} - 12y
$$

## Physical: mass-spring-damper
$$
m\ddot{x} + c\dot{x} + kx = F(t)
$$

## Physical: RLC circuit (single equation in charge)
$$
L\ddot{q} + R\dot{q} + \frac{1}{C}q = v(t)
$$

## Coupled system: two masses

$$
m_1\ddot{x}_1 + c\dot{x}_1 + k_1 x_1 - k_2(x_2 - x_1) = F_1 \\
m_2\ddot{x}_2 + k_2(x_2 - x_1) = F_2
$$


The states are a set you construct using the rule "each variable + its lower derivatives, up to one below the highest
