---
title: 04 Convolution
---

An operation that combines two signals into a third, written $h(t) * x(t)$, defined by the integral

$$
y(t) = h(t) * x(t) = \int_{-\infty}^{\infty} x(\tau)\ h(t - \tau)\ d\tau
$$

**What we do:** flip one signal $(h(t) → h(−τ))$, slide it across the other by amount *t*, and at each position integrate the product of the 
overlap; the resulting area as a function of *t* is the output.


### What ε means, concretely

step function ε(something) looks at the value inside the parentheses and gives:

$$
\varepsilon(\text{input}) = \begin{cases} 1 & \text{if input} \geq 0 \\ 0 & \text{if input} < 0 \end{cases}
$$

## Convolution computation 

$$
x(t) = \frac{1}{t}\,\varepsilon(t-1)
$$

$$
h(t) = t^2\,\varepsilon(t) - t^2\,\varepsilon(t-1)
$$
Substituting $\tau$ and $t - \tau$
$$
x(\tau) = \frac{1}{\tau}\,\varepsilon(\tau - 1)
$$

$$
h(t-\tau) = (t-\tau)^2\,\varepsilon(t-\tau) - (t-\tau)^2\,\varepsilon(t-\tau-1)
$$

Multiply them

$$
x(\tau)\,h(t-\tau) = \frac{(t-\tau)^2}{\tau}\,\varepsilon(\tau-1)\Big[\varepsilon(t-\tau) - \varepsilon(t-\tau-1)\Big]
$$

Now here is the important detail for multiplication to be non zero and in term the integral to be no zero the value of unit step function such 
that the integrla multiplication doesn't turn zero. 

Unit step function can either be 1 or 0 we take each step function 

### Step 1: $ε(τ − 1)$
it has to be 1(on) otherwise the whole function turns zero so we set the inequality as 
$$ 
ε(τ − 1) > 0 
$$

$$
τ − 1 > 0 
$$

This is the first case meaning tau has to be greater than 1 

$$
τ > 1
$$

### Step 2: $ε(t − τ)$ is 1 when:

$$
t − τ > 0 
$$

$$
t > τ 
$$

### Step 3: $(t − τ − 1)$ is 1 when:
This is the tricky part in order for the riginla function (refer above) to be non zero this unit step function has to be zero (off) which means 
$$
ε(t − τ − 1) < 0 
$$

$$
t − 1 <  τ 
$$

note important in all the above cases we make the tau $(τ)$ the subject and assume that $t$ is fixed technically at some unknown point

now combine the cases 

$$
\underbrace{\tau \ge 1}_{\text{from } x} \quad\text{AND}\quad \underbrace{t-1 < \tau \le t}_{\text{from } h}
$$
now we simplify the equation 

$$
\varepsilon(\tau-1) = 1, \qquad \varepsilon(t-\tau) = 1, \qquad \varepsilon(t-\tau-1) = 0
$$

$$
\frac{(t-\tau)^2}{\tau}\cdot 1 \cdot [1 - 0] = \frac{(t-\tau)^2}{\tau}
$$

### Writing it out per case
### Case II (1 ≤ t ≤ 2), region 1 < τ ≤ t:

$$
y_{II}(t) = \int_{1}^{t} \frac{(t-\tau)^2}{\tau}\,\mathrm{d}\tau
$$

### Case III (t > 2), region $t − 1 < τ ≤ t$:

$$
y_{III}(t) = \int_{t-1}^{t} \frac{(t-\tau)^2}{\tau}\,\mathrm{d}\tau
$$

expanding the square 

$$
(t-\tau)^2 = t^2 - 2t\tau + \tau^2
$$

$$
\frac{(t-\tau)^2}{\tau} = \frac{t^2}{\tau} - 2t + \tau
$$

$$
\int \frac{t^2}{\tau}\,\mathrm{d}\tau = t^2\ln\tau, \qquad \int (-2t)\,\mathrm{d}\tau = -2t\tau, \qquad \int \tau\,\mathrm{d}\tau = \frac{\tau^2}{2}
$$


$$
F(\tau) = t^2\ln\tau - 2t\tau + \frac{\tau^2}{2}
$$

now do limit substituion

$$
\left[t^2\ln(\tau) - 2t\tau + \frac{\tau^2}{2}\right]_1^t
$$



## Finding the "special place" in x

The window edges (integration limits) come from **h**. The **special place** is a separate landmark that lives in **x**: it's wherever x stops being one single smooth formula. Look at x alone, ignore h, and find where x changes behavior.

### Type 1: absolute value → kink where the inside = 0 (expect a split)

An absolute value bends into a V at the point where its inside is zero. On each side of that point x has a different formula, so if the sliding window straddles it, the integral must split there.

**Example:** x(τ) = e^(−|τ − 2|)

Set the inside to zero: τ − 2 = 0, so the special place is τ = 2.

$$e^{-|\tau - 2|} = \begin{cases} e^{(\tau - 2)} & \tau < 2 \\[4pt] e^{-(\tau - 2)} & \tau \ge 2 \end{cases}$$

Two flavors meeting at τ = 2. If the window covers τ = 2, cut the integral into a piece up to 2 and a piece after 2.

### Type 2: step function ε(τ − a) → switch-on wall at τ = a (expect a clip)

A step is 0 before its inside hits zero and 1 after. So x is completely off (zero) on one side and on (a single formula) on the other. Only one flavor exists, so there's no split, just a wall that clips the window: integration can't start before the wall.

**Example:** x(τ) = (1/τ)·ε(τ − 1)

Set the inside to zero: τ − 1 = 0, so the special place (wall) is τ = 1.

$$x(\tau) = \begin{cases} 0 & \tau < 1 \\[4pt] \dfrac{1}{\tau} & \tau \ge 1 \end{cases}$$

Left of 1 there's nothing to add up. So the lower limit can never go below 1: the real lower limit is max(1, window's left edge).

### Type 3: piecewise definition → a special place at each break point

If x is defined in labeled pieces, every break point between pieces is a special place. Treat each one like a wall or kink: if the window covers a break, split there.

**Example:**

$$x(\tau) = \begin{cases} 0 & \tau < 0 \\[4pt] \tau & 0 \le \tau < 2 \\[4pt] 1 & \tau \ge 2 \end{cases}$$

Break points at τ = 0 and τ = 2, so there are two special places. If the window covers both, the integral splits into up-to-0, 0-to-2, and after-2 pieces (using the right formula in each).

### Type 4: any other spot where the formula for x changes

Anything that makes x switch formula counts: a rectangle pulse (two switch edges), a shifted step, a product of steps, etc. Find every value of τ where the description of x changes, and mark it.

**Example:** x(τ) = ε(τ + 1) − ε(τ − 1)  (a rectangle that is 1 only on −1 < τ < 1)

Two special places, at τ = −1 (switches on) and τ = 1 (switches off). Outside that band x = 0.

### The one-line rule

Window edges come from h; special places come from x. To find them, ask only of x: "where does this function switch on, switch off, or bend?" Each such τ value is a special place, and whenever the sliding window covers one, the integral either gets clipped (a wall) or split (a kink or a between-pieces boundary) at that value.



## definition of Absolute 
Dealing with abolsute in a function 
$$
|\tau| = \begin{cases} \tau & \text{if } \tau \ge 0 \\[4pt] -\tau & \text{if } \tau < 0 \end{cases}
$$


### Right side, τ ≥ 0: here |τ| = τ. Substitute:

$$
e^{-|\tau|} = e^{-(\tau)} = e^{-\tau}
$$

### Left side, τ < 0: here |τ| = −τ. Substitute:
$$
e^{-|\tau|} = e^{-(-\tau)} = e^{+\tau} = e^{\tau}
$$


### connect to the integral limits
Now you know: to the left of 0 use e^τ, to the right of 0 use e^−τ. So when the sliding window (from t−5 to t−3) contains the point 0, you must
 break the integral at 0 and use the correct flavor on each side:

$$
y_{II}(t) = \int_{t-5}^{0} 2e^{\tau}\,\mathrm{d}\tau + \int_{0}^{t-3} 2e^{-\tau}\,\mathrm{d}\tau
$$


# Convolution exam recipe, taught by example

Every step is shown on two real problems so the lingo is concrete.

- **Problem A:** $x(t) = e^{-|t|}$, $\quad h(t) = 2\big(\varepsilon(t-3) - \varepsilon(t-5)\big)$
- **Problem B:** $x(t) = \dfrac{1}{t}\,\varepsilon(t-1)$, $\quad h(t) = t^2\varepsilon(t) - t^2\varepsilon(t-1)$

---

## Step 0: Write the integral

$$
y(t) = \int_{-\infty}^{\infty} x(\tau)\,h(t-\tau)\,\mathrm{d}\tau
$$

Flip the FUNCTION THAT IS A PULSE (has a switch-on AND a switch-off), because
a flipped pulse gives you a clean finite window. In BOTH problems $h$ is the
pulse, so we flip $h$. That means: the sliding "window" comes from $h$, and the
fixed "landmarks" come from $x$.

- **A:** $h$ is a pulse (on at $3$, off at $5$) $\rightarrow$ flip $h$.
- **B:** $h$ is a pulse (on at $0$, off at $1$) $\rightarrow$ flip $h$.

---

## Step 1: WINDOW edges (from $h$)

The "window" is the stretch of $\tau$ where $h(t-\tau)$ is nonzero. Find it by
taking each step in $h$, replacing its argument with $(t-\tau)$, and solving
$\ge 0$ for $\tau$. If $h$ turns on at $a$ and off at $b$ (with $a<b$), the
window is always:

$$t - b < \tau \le t - a$$

**"Window edges"** = these two $\tau$-values, $t-b$ (left) and $t-a$ (right).
The window has fixed width $b-a$ and slides right as $t$ grows.

- **A:** on at $a=3$, off at $b=5$. Window: $\;t-5 < \tau \le t-3\;$ (width $2$).
- **B:** on at $a=0$, off at $b=1$. Window: $\;t-1 < \tau \le t\;$ (width $1$).

---

## Step 2: LANDMARKS (from $x$)

A **"landmark"** is a fixed $\tau$-value where $x(\tau)$ changes its formula.
Look only at $x$, and check for:

- **KINK** = an absolute value $|\tau - c|$. The graph bends at $\tau = c$. Both
  sides are nonzero but use DIFFERENT formulas. A kink inside the window forces
  a SPLIT (two integrals).
- **WALL** = a step $\varepsilon(\tau - c)$. $x$ is zero on one side of $\tau=c$
  and nonzero on the other. A wall never splits; it just blocks the window
  (nothing to add up on the zero side).

Examples:

- **A:** $x = e^{-|\tau|}$. The $|\tau|$ is a KINK at $\tau = 0$. (Set inside
  $=0$: $\tau=0$.) Both sides nonzero, so expect a split.
- **B:** $x = \dfrac{1}{\tau}\varepsilon(\tau-1)$. The $\varepsilon(\tau-1)$ is a
  WALL at $\tau = 1$. $x=0$ left of $1$, $x=\frac{1}{\tau}$ right of $1$. No split,
  just a block.

---

## Step 3: CASE BOUNDARIES (where the window meets a landmark)

The **"case boundaries"** are the special values of $t$ where the sliding window
just touches a landmark. Find them by setting each window edge equal to each
landmark and solving for $t$.

- **A:** landmark $0$, edges $t-5$ and $t-3$.
  - $t - 3 = 0 \Rightarrow t = 3$
  - $t - 5 = 0 \Rightarrow t = 5$
  - Cases: $\;t < 3,\quad 3 \le t \le 5,\quad t > 5.$
- **B:** landmark $1$, edges $t-1$ and $t$.
  - $t = 1 \Rightarrow t = 1$
  - $t - 1 = 1 \Rightarrow t = 2$
  - Cases: $\;t < 1,\quad 1 \le t \le 2,\quad t > 2.$

---

## Step 4: LIMITS for each case (lower and upper)

Now pin the actual integral limits in each case. Two things constrain $\tau$:
the window (from $h$) and the requirement that $x$ is nonzero (from $x$'s walls).

- **Lower limit** $= \max(\text{window left edge},\ \text{any wall } \tau \text{ must exceed})$
- **Upper limit** $= \min(\text{window right edge},\ \text{any wall } \tau \text{ must stay under})$

"Wall wins" $\rightarrow$ limit is the fixed number. "Edge wins" $\rightarrow$
limit is the $t$-expression. If lower $\ge$ upper, the case is $y = 0$.

**Problem A** (no wall, kink handled in Step 5). Limits are just the window
edges $t-5$ to $t-3$ in every nonzero case:

- $t < 3$: limits $\;t-5\;$ to $\;t-3.$
- $3 \le t \le 5$: limits $\;t-5\;$ to $\;t-3\;$ (but will split at $0$, Step 5).
- $t > 5$: limits $\;t-5\;$ to $\;t-3.$

**Problem B** (wall at $1$). Lower limit $= \max(t-1,\ 1)$, upper $= t$:

- $t < 1$: upper $t < 1$ but need $\tau \ge 1$ $\Rightarrow$ empty $\Rightarrow y=0.$
- $1 \le t \le 2$: here $t-1 \le 1$, so $\max(t-1,1)=1$. Limits $\;1\;$ to $\;t.$
- $t > 2$: here $t-1 > 1$, so $\max(t-1,1)=t-1$. Limits $\;t-1\;$ to $\;t.$

---

## Step 5: Pick $x$'s FLAVOR, and SPLIT if a kink is inside

A **"flavor"** of $x$ is which formula $x$ uses on a given side of a kink.
An absolute value has two flavors; substitute each piece:

$$e^{-|\tau|} = \begin{cases} e^{\tau} & \tau < 0 \ (\text{left flavor}) \\[4pt] e^{-\tau} & \tau \ge 0 \ (\text{right flavor}) \end{cases}$$

(Left flavor: $|\tau| = -\tau$, so $e^{-(-\tau)} = e^{\tau}$. Right flavor:
$|\tau| = \tau$, so $e^{-\tau}$.)

**"Split"** = if a KINK sits inside the window, cut the integral at the kink;
use the left flavor below it and the right flavor above it. The kink value is
the upper limit of piece 1 AND the lower limit of piece 2.

- **A, $t < 3$:** window entirely left of kink $0$ $\rightarrow$ left flavor
  $e^{\tau}$, one integral.
- **A, $3 \le t \le 5$:** kink $0$ is INSIDE the window $\rightarrow$ SPLIT at $0$:
  left piece $t-5$ to $0$ uses $e^{\tau}$, right piece $0$ to $t-3$ uses $e^{-\tau}$.
- **A, $t > 5$:** window entirely right of kink $0$ $\rightarrow$ right flavor
  $e^{-\tau}$, one integral.
- **B:** the landmark is a WALL, not a kink, so $x$ has only ONE flavor
  ($\frac{1}{\tau}$) wherever it's alive. Never split.

---

## Step 6: Integrate and substitute

Put the flavor of $x$ times the $h$-value into each integral, integrate in
$\tau$ (treat $t$ as constant), then plug in the Step 4 limits.

Useful antiderivatives:

$$\int \frac{1}{\tau}\,\mathrm{d}\tau = \ln\tau, \qquad \int e^{a\tau}\,\mathrm{d}\tau = \frac{1}{a}\,e^{a\tau}$$

**Problem A, case $t<3$** (here $h$-value is the constant $2$, flavor $e^{\tau}$):

$$y_I(t) = \int_{t-5}^{t-3} 2e^{\tau}\,\mathrm{d}\tau = 2\big[e^{\tau}\big]_{t-5}^{t-3} = 2\big(e^{t-3} - e^{t-5}\big)$$

**Problem A, case $3\le t\le 5$** (split at $0$):

$$y_{II}(t) = \int_{t-5}^{0} 2e^{\tau}\,\mathrm{d}\tau + \int_{0}^{t-3} 2e^{-\tau}\,\mathrm{d}\tau = 2\big(2 - e^{t-5} - e^{-t+3}\big)$$

**Problem B, case $1\le t\le 2$** (flavor $\frac{1}{\tau}$, $h$-value $(t-\tau)^2$).
Expand first, then integrate:

$$\frac{(t-\tau)^2}{\tau} = \frac{t^2}{\tau} - 2t + \tau \;\Rightarrow\; \Big[t^2\ln\tau - 2t\tau + \tfrac{\tau^2}{2}\Big]_{1}^{t}$$

$$y_{II}(t) = t^2\ln t - \tfrac{3}{2}t^2 + 2t - \tfrac{1}{2}$$

**Problem B, case $t>2$** (same integrand, limits $t-1$ to $t$):

$$y_{III}(t) = \Big[t^2\ln\tau - 2t\tau + \tfrac{\tau^2}{2}\Big]_{t-1}^{t} = t^2\ln\!\Big(\tfrac{t}{t-1}\Big) - t - \tfrac{1}{2}$$

---

## Step 7: Assemble with step functions (the "gate")

A **"gate"** is a step-function switch that turns each case's formula on only
over its own $t$-range, so you can add all cases into one $y(t)$:

- active on $a < t < b$ $\rightarrow$ multiply by $\big(\varepsilon(t-a) - \varepsilon(t-b)\big)$
- active on $t > c$ $\rightarrow$ multiply by $\varepsilon(t-c)$
- active on $t < c$ $\rightarrow$ multiply by $\varepsilon(c-t)$

**Problem A:**

$$y(t) = y_I(t)\,\varepsilon(3-t) + y_{II}(t)\big(\varepsilon(t-3) - \varepsilon(t-5)\big) + y_{III}(t)\,\varepsilon(t-5)$$

**Problem B:**

$$y(t) = y_{II}(t)\big(\varepsilon(t-1) - \varepsilon(t-2)\big) + y_{III}(t)\,\varepsilon(t-2)$$


### Infinite support 
While choosing which signal to fix (changing $t$ to $\tau$) and choosing the function to flip(changing the $t$ to $t- \tau$) so it become sliding 
window. the flip function usually has two $\epsilon$ so signal is turned on and off and hence it is not infnite and easier to compute integral 
with limits

the signal gets turned on but never off. One epsilon switches it on and it just runs forever

$$
x(t) = \frac{1}{t}\,\varepsilon(t-1)
$$

### Forming cases for the Convolution integral
while figuring it the cases make sure to take into consideration the window width. Take for example the signal is turned on at $\tau > 1$ and 
the moving signal is the window $t-1 < \tau < t$. If you look closely the window has width of $1$ so I write the cases then for t < 0 integral 
is 0

Case II 

from $1$ to $t$ (not complete till 2 ) since  there is apossiblility window being half left of 1 and half right of 1 

Case III 

$t < 2$ window completely right side  of 1 and since the window width is 1 so max it can reach it 2 so we take limits as $t-1$ to $t$ 

## Solving convolution integral 
- replace $t$ with $\tau$ in infinte signal and in a finte signal (where two $\epsilon$ present) with $t - \tau$
- find limts of the window form the finte signal by forming ineqaulities where signal will be on and overall integrall won't beocme zero
- find the break point (point where signal gets turned on) from infinte signal. notes abosule signal forms two cases around break point 
- form cases based on the break point and the position of the sliding window
- solve integral for the cases based on the limits and function 

## Convolution: Quick Rules for Matching / Sketching (no integration needed)

### Rule 0 — The three universal facts (use these first, always)
- **Support adds (widths add):** if $x$ lives on width $\Delta t_1$ and $h$ on width $\Delta t_2$, then $y = x * h$ lives on width $\Delta t_1 + \Delta t_2$.
- **Start points add:** left edge of $y$ = (left edge of $x$) + (left edge of $h$). Likewise right edge of $y$ = (right edge of $x$) + (right edge of $h$).
- **Areas multiply:** total area of $y$ = (area of $x$) $\times$ (area of $h$). Handy sanity check on peak height.

### Rule 1 — Rectangle $*$ Rectangle
- Result is a **triangle** (trapezoid if widths differ).
- **Equal widths $\to$ symmetric triangle.** Unequal widths $\to$ trapezoid (flat top).
- Peak height = (overlap area) = $\text{height}_1 \times \text{height}_2 \times (\text{shorter width})$.
- Start of triangle = $t_1 + t_2$ (sum of the two rectangles' start points).

### Rule 2 — Triangle $*$ Rectangle
- Result is made of **parabolic (quadratic) sections** — smooth curved rises/falls, not straight lines.
- Width still = sum of widths (Rule 0).
- Spotting tip: if a candidate $y$ has **curved** rising/falling edges $\to$ one input was a triangle. If edges are **straight lines** $\to$ both inputs were rectangles.

### Rule 3 — Anything $*$ $\delta(t - t_0)$ (delta / impulse)
- Convolving with a delta = **copy the signal, shifted to $t_0$** (and scaled by the delta's weight).
- **Sum of deltas $\to$ sum of shifted copies.** Three deltas at $-1$, $0$, $+1$ $\to$ three copies of the signal overlaid, each shifted accordingly, then added.
- Effect on support: each delta shifts the edges by its position. Multiple deltas widen the total support by the spread of the delta positions.
- If shifted copies of a triangle overlap, the overlapping middle often **adds up to a flat constant** (rising edge of one copy + falling edge of the next cancel their slopes).

### Fast exam decision tree (matching problems)
1. **Count widths** $\to$ width of $y$ must equal $\Delta t_1 + \Delta t_2$. Kills most wrong options immediately.
2. **Check left edge** = sum of left edges. Kills more.
3. **Straight vs curved edges?** straight = rect $*$ rect (triangle/trapezoid); curved = something $*$ triangle (parabolic).
4. **Any deltas?** $\to$ it's just shift-and-add copies; look for flat-topped or stepped results.
5. **Peak height** = $\text{area}_1 \times \text{area}_2$ (or overlap area) as a final tie-breaker.

### Worked mapping (this exercise)
- **$1 \to D$ and $2 \to A$:** rect $*$ rect $\to$ triangle. Start point = sum of starts. Pair 1: left edges $-2$ and $-1$, so triangle starts at $-3$. Pair 2: $-1$ and $0$, so starts at $-1$. (Rules 0 + 1.)
- **$3 \to F$ and $4 \to B$:** triangle $*$ rect $\to$ parabolic sections, width = sum of widths ($2 + 2 = 4$ for pair 3, $2 + 4 = 6$ for pair 4). Curved edges are the giveaway. (Rules 0 + 2.)
- **$5 \to C$ and $6 \to E$:** convolving with deltas $\to$ shift-and-add copies. Two deltas at $\pm 1$ spread the edges outward by $1$ each side; the triangle copies overlap into a **flat middle**. Three deltas $\to$ three copies added. (Rule 3.)

### The single most powerful exam move
If you memorize one thing: **width of $y$ = width of $x$ + width of $h$, and left edge of $y$ = left edge of $x$ + left edge of $h$.** Those two facts alone eliminate $4$ of the $6$ options in a matching question in about ten seconds, with no integration. Then use "straight vs curved edges" and peak height to settle the last pair.


### Rule 4 — Convolving with a single scaled/shifted delta (signed)
$x(t) * A\,\delta(t - t_0) = A\, x(t - t_0)$
- Shift the signal to $t_0$ AND scale its height by $A$.
- If $A$ is negative, the copy is **flipped upside down** (multiplied by $-1$).

### Rule 5 — Delta DOUBLET / pair with opposite signs → gives a DIFFERENCE
Two deltas of opposite sign, e.g. $x_2(t) = \delta(t-1) - \delta(t-2)$ (weight $+1$ at $t=1$, $-1$ at $t=2$):
$g(t) * x_2(t) = g(t-1) - g(t-2)$
- Stamp a **positive** copy at the first delta, a **negative** (flipped) copy at the second, then add.
- Net effect looks like the signal, immediately followed by an inverted, shifted echo of itself.

### Rule 6 — Convolving with a sinusoid → sinusoid of the SAME frequency (eigenfunction rule)
$\cos(\omega t) * g(t) = |G(\omega)|\cos(\omega t + \angle G(\omega))$, and same for $\sin$.
- A pure sine/cosine convolved with anything stays a sine/cosine of the **same frequency**.
- Only two things can change: the **amplitude** (scaled) and the **phase** (shifted).
- The shape never becomes a triangle/parabola: sinusoid in → sinusoid out. This alone identifies the answer in a matching question.
- If the other signal is a delta pair, you don't even need the transform: just shift-and-add copies of the sine (Rules 4–5), which automatically gives back a scaled/shifted sine.
