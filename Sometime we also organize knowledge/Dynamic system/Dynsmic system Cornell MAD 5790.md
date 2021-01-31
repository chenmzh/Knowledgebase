## MAE 5790

### Lecture 1 Course Introduction and overview

#### Chapter 1 

**Historical overview**

* 1660 Newton - invent ODEs explains planetary orbits

  * Beginning of dynamics
  * 2-body problem
  * 3-body and n-body problem -- can not solve (problem of the moon)

* late 1800's

  * Nobody can solve 3-body problem
    * Poincare - geometric approach. Recognize the difficulty of the fundamental approach to solve 3-body problems
      * Based on the concept of phase space
      * a glimpse of chaos
        * Chaos -- deterministic system that displays "sensitivity dependence on initial conditions"
          * aperiodic seemingly unpredictable behavior in the deterministic system

* Early 1900's 

  * Quantum and relativity

* 1920s - 1950s  

  * Nonlinear oscillators in physics engineering 
    * Radio, radar phase-lasers

* 1950s

  * Computer invented

* 1960s

  * Lorenz @ MIT -- chaotic system in a model of convection of atmosphere
  * Smale, KAM theory 

* 1975

  * May -- chaos in iterated maps -- simple dynamic system $x_{n+1} = f(x_n)$ 

    * Logistic equation in population biology

  * Mandelbrot-fractals 

    ![Mandelbrot set - Wikipedia](https://i.loli.net/2021/02/01/eOtivNHPLd9Fa2k.jpg)

  * Winfree -- nonlinear oscillators in biology

  * Ruelle & Takens -- chaos -- turbulence -- NS equation ?

* 1978 

  * Feigenbaum 
    * universal route to chaos
    * connections to phase transitions in statistical physics
    * Renormalization

* 1980s

  * Chaos and nonlinear dynamics, fractals got HOT!
  * Experimental confirmation of the chaos theory

* 1990s 

  * Engineering applications of chaos
  * Complex systems (millions of variables)

* 2000s -- present

  * Networks

**Logical structure of dynamics**

* Anything change regards to time

* Differential equations $\underline{\dot{x}}=\underline{f}(\underline{x})$  *dot means time derivative and underline means vector* $\underline{x} \in \R^n, x = (x_1,\dots,x_n)$ $\R$ is the phase space

* In components
  $$
  \begin{aligned}
  \dot{x_1} & = f_1(x_1,\dots,x_n)\\
  \vdots& \\
  \dot{x_n}& = f_n(x_1,\dots,x_n)
  \end{aligned}
  $$

  * $f_1, \dots, f_n$ are the given functions
  * System in linear if all $x_i$ on RHS appear to first power only (no products, powers, or functions of the $x_i$, such as $x_1^2, x_2x_3, sin(x_4), e^{x_5}$)
  * autonomous system if the RHS only depends on x and on depends on time
  * By introducing $\dot{t} = 1$ to make the time-contained system as the autonomous system
  * autonomous system is good for the geometric means (picture to be frozen) so the graph should not change regard to time.

* Other system is <u>nonlinear</u>

  * simple harmonic oscillator

    * $m\ddot{x}+kx =0$

    * Convert to our framework $\underline{\dot{x}}=\underline{f}(\underline{x})$ 

      * $x_1 = x, x_2 =\dot{x}$

      * $$
        \dot{x_1}=x_2\\
        \dot{x_2}=-\frac{kx_1}{m}
        $$

    * Pendulum: $\ddot{x}+sinx = 0$

      * $\dot{x_1}=x_2\\
        \dot{x_2}=-sin(x_1)$
      * Solution $(x_1(t),x_2(t))$ point move along the trajectory in space with coards $(x_1,x_2)$
      * Think about trajectory in the space
      * ![image-20210131192641862](https://i.loli.net/2021/02/01/yFlxrn2zQYkGu7p.png) 
      * Find what people called a phase portrait
      * Phase portrait = picture of all qualitatively different trajectories
      * We'll find it without solving the ODE analytically!

|           | n=1                       | n=2                        | n$\ge$3                                       | n>>1     | n=$\infty$(continuous)                                       |
| --------- | ------------------------- | -------------------------- | --------------------------------------------- | -------- | ------------------------------------------------------------ |
| Linear    | RC circuit                | simple harmonic oscillator |                                               |          | Wave equation; E+M equations(electromagnetic)<br />Schrodinger equation |
| Nonlinear | Logistic growth, skydiver | Pendulum                   | Lorenz system (chaos); fractal; iterated maps | networks | GR(general relativity); turbulence; fibrillation             |

#### Chapter 2

**1-D system**

$\dot{x} = f(x), x \in \R$

* Ex: $\dot{x} = sinx$
  * Formulas:
    *  $\int\frac{dx}{sinx}=\int dt = t + C\\
      \int csc(x) dx = -ln|cscx+cotx|$
  * Initial condition $x=x_0, t = 0$
  * $t = ln|\frac{cscx_0+cotx_0}{csc_x+cot_x}|$
  * Question: if $x_0 = \pi/4$, what's the $\lim\limits_{t \to \infty}x(t)?$
  * Use picture to illustrate the movement 
  * ![image-20210131200119391](https://i.loli.net/2021/02/01/GujlmUx2B69L4Cz.png)
  * ![image-20210131200516665](https://i.loli.net/2021/02/01/OqUVgeT2HlzWnIv.png)

* Logistic equation in pop biology: $\dot{x} = rx(1-\frac{x}{k}), r > 0 and k >0$
  * x as the population size, $\dot{x}/x$ is the per capita growth rate
  * ![image-20210131201004439](https://i.loli.net/2021/02/01/GsWIAuP1BC8l5JL.png)
  * ![image-20210131201124872](https://i.loli.net/2021/02/01/BJADCGUhcVLajNn.png)



***Power of this method: come to the conclusion with little effort and calculation.***

### Lecture 2: One dimensional systems

* For one dim system, it's pretty easy to figure out the property of fixed point by looking at the phase space and imagine a point and how it move.
* For continuous differentiable function, it will not come to the fixed point in finite time, but approach and get to it asymptotically within infinite time. But still possible to construct some function to hit  the fixed point.

#### Chapter 2.4 Linearization

*  Examine the dynamics close to a fixed point at $x^*$
* ![image-20210131201738404](https://i.loli.net/2021/02/01/owKqjSUCDPzOvHF.png)
* Let $x(t) = x^*+\eta(t)$ where $|\eta|<<1$ $\dot{x}=(x^*+\eta)\dot{} = \dot{\eta} \\= \dot{x}= f(x) = f(x^*+\eta) \\= f(x^*)+\eta f'(x^*)+\eta^2/2f''(x^*) + h.o.t$

