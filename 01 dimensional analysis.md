# Dimensional analysis

$$
\newcommand{\ds}{\displaystyle}

\newcommand{\R}{\mathbb R}

\newcommand{\parens}[1]{\left( #1 \right)}
\newcommand{\curlies}[1]{\left\{ #1 \right\}}
\newcommand{\brackets}[1]{\left[ #1 \right]}
\newcommand{\abs}[1]{\left\lvert #1 \right\rvert}
\newcommand{\inv}[1]{#1^{-1}}

\newcommand{\mbar}{\overline m}
$$

## Dimensional homogeneity

- quantities with like dimension can be added, subtracted, equated
- SI dimension units:
  - mass $M$ - kg
  - length $L$ - m
  - time $T$ - sec
  - charge $Q$ - C

## Non-dimensionalization

- write a model with dimensionless variables

#### Example: radioactive decay

We model a decaying mass with $m(t)$

$$
\begin{align*}
\frac{dm}{dt} &= -km \\
m(0) &= m_0
\end{align*}
$$

This model has 2 variables, $m$ and $t$, and 2 parameters, $k$ and $m_0$.

Considering dimensions,

$$
\begin{align*}
\brackets{\frac{dm}{dt}} = \frac{M}{T} \\
[km] = [k]M \rightarrow [k] = \frac{1}{T}
\end{align*}
$$

Then $\tau = kt$ and $\ds \mbar(\tau) = \frac{m}{m_0}$ are non-dimensional time and mass.

$$
\begin{align*}
-km &= \frac{dm}{dt} \\
&= \frac{d(m_0 \mbar)}{d(\tau / k)} \\
-km &= km_0 \frac{d \mbar}{d \tau} \\
-km_0 \mbar &= km_0 \frac{d \mbar}{d \tau} \\
-\mbar &= \frac{d \mbar}{d \tau} \\
\text{also, } m(0) &= m_0 \\
\mbar(0) &= \frac{m(0)}{m_0} = 1
\end{align*}
$$

So our model can now be written with two variables, $\mbar$ and $\tau$, and 0 parameters.

### Buckingham Pi Theorem

*Any physical relation involving $N$ dimensional variables can be written in terms of a complete set of $N-r$ independent dimensionless variables where $r$ is the rank of the dimensional matrix.*

The dimensionless variables $\Pi_1, ..., \Pi_{N-r}$ have some relationship $F(\Pi_1, ..., \Pi_{N-r}) = 0$

#### Example: Period of ideal pendulum

- $\theta$ is amplitude of swinging pendulum - pendulum swings between $-\theta$ and $\theta$
  - $[\theta] = 1$
- $\ell$ is length of pendulum
  - $[\ell] = L$
- $m$ is mass of pendulum
  - $[m] = M$
- $p$ is period of pendulum
  - $[p] = T$
- $g$ is acceleration due to gravity
  - $\ds [g] = LT^{-2}$

Using these, we can construct the dimensional matrix by considering how each variable has each dimension:

$$
\begin{align*}
&\quad\begin{matrix}
\small p & \small m & \small \ell & \small g & \small \theta
\end{matrix}\\
D = 
\begin{matrix}
\small M \\ \small L \\ \small T
\end{matrix}
&\begin{pmatrix}
0 & 1 & 0 & 0 & 0 \\
0 & 0 & 1 & 1 & 0 \\
1 & 0 & 0 & -2 & 0 \\
\end{pmatrix}
\end{align*}
$$

$D$ has rank $r=3$, so using the Buckingham Pi Theorem we can model this problem with $N-r = 2$ dimensionless variables

Our first one can be $\Pi_1 = \theta$, which corresponds to the vector $(0, 0, 0, 0, 1)$ in the null space of $D$

Another vector in the null space is $(2, 0, -1, 1, 0)$, so this shows us that our second one can be $\ds \Pi_2 = \frac{p^2 g}{\ell}$

Modelling the relationship,

$$
\begin{align*}
F(\Pi_1, \Pi_2) = 0 \rightarrow \Pi_2 &= f(\Pi_1) \\
\frac{p^2 g}{\ell} &= f(\theta) \\
...
\end{align*}
$$

This already shows us that mass is not relevant to the model!

#### Example: Flow past a sphere

- $v$ velocity of fluid
  - $[v] = LT^{-1}$
- $\mu$ viscosity of fluid
  - $[\mu] = ML^{-1}T^{-1}$
- $\rho$ density of fluid
  - $[\rho] = ML^{-3}$
- $D$ diameter of sphere
  - $[D] = L$
- $F$ force of sphere moving along direction of flow
  - $[F] = MLT^{-2}$

Making the dimensional matrix,

$$
\begin{align*}
&\quad\ \begin{matrix}
\small F & \ \ \small v & \ \ \small \mu & \ \ \small \rho & \ \ \small D
\end{matrix}\\
D = 
\begin{matrix}
\small M \\ \small L \\ \small T
\end{matrix}
&\begin{pmatrix}
1 & 0 & 1 & 1 & 0 \\
1 & 1 & -1 & -3 & 1 \\
-2 & -1 & -1 & 0 & 0
\end{pmatrix}
\end{align*}
$$

This has rank $3$ so just as in the last example it can be modelled with two variables.
