# Mathmatical Modelling

## reaction modelling - enzyme kinetics

1. principles of mass action: the rate of the chemical reaction is directly proportional to the probability of reactant collision, i.e the concentrations of the participating molecules to the power of the molecularity.

   limitations: huge systems (hundreds of ODEs) due to combinatorial complexity (one protein can have multiple binding sites for different substrates)

2. rule-based modelling: use only the set of sensible biochemical rules

   rules include: generation & degradation, complex formation & dissociation

3. Quasi-steady state: processes occur at a very different timescale, that within a certain time interval some variable remains constant. 

4. Michaelis-Menten approximation: $\ce{S + E<=>[{k_1}][k_{-1}]ES->[k_2]E + P}$

   + Assumption: quasi-steady state $\rightarrow$ the substrate is in excess, i.e the enzyme is saturated but total concentration is constant; the complex formation step is not the rate-limiting step, i.e it reaches the steady state much faster than the 2nd step
   + $\frac{d[P]}{dt}=v_m\frac{[S]}{[S]+K_M}$, $v_m = k_2[E]_T$, $K_M = \frac{k_{-1}+k_2}{k_1}$
   + limitation: cooperativity, inhibition, not valid if substrate and enzyme are of similar concentrations 

   Goldbeter-Koshlan approximation: $\ce{X<-->[K_{M1},E_1][K_{M2},E_2]X_p}$

   + Assumption: a steady-state solution for a 2-state biological system. In this system, the interconversion between these two states is performed by two enzymes with opposing effect. [ref](https://en.wikipedia.org/wiki/Goldbeter–Koshland_kinetics) Both the forward the backward reactions can be described with MM equation. The total concentration of X+Xp is constant.
   + $\frac{d[X_p]}{dt} = u_1\frac{[X]_T - [X_p]}{K_{M1}+[X]_T-[X_p]} - u_2\frac{[X_p]}{K_{M2}+{X_p}}$, from the steady state solution, $\frac{[X_p]}{[X]_T}=\frac{2u_1J_2}{B + \sqrt{B^2-4(u_2-u_1)u_1J_2}}$, where $B = u_2 - u_1 + J_1u_2+J_2u_1$ and $J_1 = \frac{K_{M1}}{[X]_T}, J_2 = \frac{K_{M2}}{[X]_T}$
   + Limitation: assumptions for MM eqn should be applicable i.e saturated enzymes

5. Ultrasensitivity: Goldbeter-Koshland zero-order.

   fraction of $X_p$ vs. $\frac{u_1}{u_2}$: increase the $v_m$ for the slower reaction does not improve much until a certain threshold

   Ultra is applicable when both enzymes are effectively saturated. regulatory systems can change the $v_m$ here.

6. Coopertivity: how the binding of the previous ligand affect the next one. 

   Positive: promote the binding of the next one (K is smaller, i.e higher binding affinity), n >1; negative: inhibite (larger), n <1

   Hill kinetics: $v = v_m \frac{[X]^n}{K + [X]^n}, K = \prod_{i=1}^{n}K_i$

## phase plane analysis 

1. phase plane: a visual display of a certain characteristics of certain kinds of differential equations. the x and y axis are the state of varaiables of concern; a phase protrait represents the moving path of a certain point along time; vector field is the direction and relative magnitude of the speed on a certain point on the phase plane.
2. steps to draw the plane: start from the nullclines $\rightarrow$ directions on the nullclines $\rightarrow$ directions in each subsection of the plane

## Linear stability analysis

1. steps of linear stability analysis: 

   + Taylor expansion around the steady state: $f(\vec{x}) = f(\vec{x}^*) + \frac{f'(\vec{x}^*)}{1!}(\vec{x}-\vec{x}^*) + \frac{f''(\vec{x}^*)}{2!}(\vec{x}-\vec{x}^*)^2 + ...$

   + Ignore the higher order terms (linear terms only): $\frac{d(\vec{x}-\vec{x}^*)}{dt}=J(\vec{x}-\vec{x}^*)$, where J is the Jacobian matrix $\rightarrow$ **How will the perturbation around the steady state ** is now the solution to $\frac{d\vec{w}}{dt}=J\vec{w}$, and $\vec{w}$ is the perturbation

   + $$
     \begin{align}
     \frac{d\vec{w}}{dt} &= J\vec{w}\\
     \sum_i \frac{d\gamma_i(t)}{dt}\vec{v}_i &= \sum_i\gamma_i(t)\lambda_i\vec{v}_i\\
     \frac{d\gamma_i(t)}{dt} &=\gamma_i(t)\lambda_i \\
     \Longrightarrow \gamma_i(t) &= \gamma_i(0)e^{\lambda_it}
     \end{align}
     $$

2. Application: it is useful to study the local stability of a fix point. The evolution of the perturbation around the SS is now dependent on the eigenvalue of the Jacobian; more specifically, the real part of the eigenvalues. For a 2D system, linearization tells us the stability by the trace of the Jacobian.

$$
J =
\begin{pmatrix}
a & b\\
c & d
\end{pmatrix}
$$

$$
\lambda_{1,2} = \frac{\text{tr}(J) \pm \sqrt{\text{tr}(J)^2-4\text{det}(J)}}{2}
$$

3. Higher dimension systems $P(\lambda) = \sum_{i=0}^n \alpha_i \lambda^i$
   + Descartes' Rule of Signs: if the sign of coefficient has n times of change, then there is n, n-2, n-4 ... real positive roots of $\lambda$. NOTE that similarly we can let $w = - \lambda$
   + Routh-Hurwitz criterion: if the determinant of matrix arranged in row of odd coefficient + row of even coefficient + ... are all positive, then all the real parts of roots of $\lambda$ are negative

## Dynamical systems

1. Bifurcation: changing the parameters (i.e the regulatory components) result the change of stability in the fixed point or generation of a new steady state solution.

   + transcritical bifurcation: stability of two fixed points exchanges after collision
   + Saddle-node bifurcation: two equilibrium points collide and annihilate each other 
   + Hopf-bifurcation: equilibrium point changes its stability, usually comes with generation of a limit cycle. $\rightarrow$ The real part of the eigenvalues crosses the imaginary axis.

   Supercirtical bifurcation: after the original equilibrium point lost its stability, a new stable steady state solution is generated to catch the trajectories $\rightarrow$ there is no sudden jump from one FP to the other. Even the new equilibrium is a stable limit cycle, the amplitude of the oscillation is gradually changing with the parameter.

   Subcritical bifurcation: the trajectories jump to a more distant attractor, if there is any.

2. Hysteresis: the dependence of the state of a system on its history. Visually, it is the jumping from one branch of stable soluion to the other, but cannot jump back to the original point.
3. Poincaré-Bendixson theorem (2D): bounded in a region with no fixed points
4. Limit cycles:
   + Only in nonlinear systems 
   + Isolated closed trajectory: neighbouring trajectories are either attracted in or repelled out
   + Amplitude is determined by the structure of the system but not the initial values

## Regulatory principles 

1. Signalling cascade: $\ce{X_i <=>[\alpha, X_{p,i-1}][\beta] X_{p,i}}$ 

   | Signalling in one step                                       | Probablity                                                   |
   | ------------------------------------------------------------ | ------------------------------------------------------------ |
   | Concentration $[X_i] = X_i(t)$                               | Probability density: $f(t)$                                  |
   | Total amount of activated X over time: $I_i = \int_0^{\infty}X_i(t)dt$ | Cumulative probability density: $1=\int_0^{\infty}f(t)dt$    |
   | Signalling time (normalized): $\tau_i = \frac{T_i}{I_i} = \frac{1}{I_i}\int_0^{\infty}tX_i(t)dt$ | Expected value: $E(t) = \int_0^{\infty}tf(t)dt$              |
   | Signal duration (normalized): $\theta_i = \sqrt{\frac{1}{I_i}\int_0^{\infty}t^2X_i(t)dt - \tau_i^2}\\ =\sqrt{\frac{Q_i}{I_i} - \tau_i^2}$ | Standard deviation: $\text{sd} = \sqrt{Var(t)} = \sqrt{E(t^2)-E(t)^2} \\ = \sqrt{\int_0^{\infty}t^2f(t)dt - E(t)^2} $ |
   | Signal amplitude (averaged): $\sigma_i = \frac{I_i}{2\theta_i}$ |                                                              |

   For receptors, $R(t) = R(0)e^{-\lambda t}$

   + both signalling time and duration are $\frac{1}{\lambda}$ and the signal amplitude is $\frac{R(0)}{2}$

   For weakly activated cascade 

   + Assumptions: 
     $$
     [X_i] \approx[X]_T \Longrightarrow \frac{d[X_{p,i}]}{dt} = \alpha_i[X_{p,i-1}] - \beta_i[X_{p,i}]
     $$
     integrate over t on both sides
     $$
     0 = \alpha_iI_{i-1}-\beta_iI_i
     $$
     times t on both sides and integrate over t 
     $$
     -I_i = \alpha_iT_{i-1}-\beta_iT_i
     $$
     times $t^2$ on both sides and integrate over t
     $$
     -2T_i = \alpha_iQ_{i-1} - \beta_iQ_i
     $$

   + Signalling time $\tau_i = \tau_{i-1} + \frac{1}{\beta_i}$, which is only related to $\beta$, the rate of phosphatase removes the P-group, and the effect is regardless of which i the phosphatase is. In later steps of the cascade, the signalling time of this step is longer than previous one. 

   + Signalling duration $\theta_i^2 = \theta_{i-1}^2 + \frac{1}{\beta_i^2}$. Similarly, it is only related to the phosphatase.

   + Signalling amplitude $\sigma_i = \frac{I_i}{2\theta_i}= \frac{R(0)}{2} \cdot \frac{\prod_{k=1}^{i}\frac{\alpha_k}{\beta_k}}{\sqrt{1 + \lambda^2\sum_{k=1}^{i}\frac{1}{\beta_k^2}}}$. 

     + The signal amplitude is related to both receptors, kinase and phosphatase. Note that **kinase $(\alpha)$ has a stronger effect **, as the impact from phosphatase is on both numerator and denumerator (sort of cancel each other out)

     + for signal amplitude to increase in each step, 
       $$
       \begin{align}
       \frac{\sigma_i}{\sigma_{i-1}} &> 1\\
       \frac{I_i}{I_{i-1}} \cdot \frac{\theta_{i-1}}{\theta_i} &>1\\
       (\frac{\alpha_i}{\beta_i})^2 &> (\frac{\theta_i}{\theta_{i-1}})^2 = 1 + \frac{1}{\beta_i^2\theta_{i-1}^2}\\
       \alpha_i^2 &> \beta_i^2 + \frac{1}{\theta_{i-1}^2}
       \end{align}
       $$
       Signal amplification is likely to happen when $\alpha_i > \beta_i$ (i.e for each step, the phosphatase is faster than the kinase) and when  $\alpha_i > \frac{1}{\theta_{i-1}} \Longrightarrow \theta_{i-1}>\frac{1}{\alpha_i}$ (i.e, the signal duration in the previous step is longer than the characteristics time of the phosphatase in the next step).

     + cascading signal amplification is possible. To achieve the same amplification, if we have more steps in between (i.e, larger i), then individual $\beta_k$ can be larger (i.e, we allow faster phosphatase )$\rightarrow$ faster (smaller $\tau$) and sharper (smaller $\theta$) signal response.

   For strongly activating cascade,

   + Assumption:
     $$
     \begin{align}
     \frac{d[X_{p,i}]}{dt} = \alpha_i[X_{p,i-1}](1-\frac{[X_{p,i}]}{[X]_T}) - \beta_i[X_{p,i}]
     \end{align}
     $$
     at steady state,  
     $$
     [X_{p,i}] = \frac{1}{\frac{1}{[X]_T}+\frac{\beta_i}{\alpha_1}\cdot\frac{1}{[X_{p,i-1}]}}
     $$

   + Signaling duration: 

     + If it is limited by receptors, $\theta = \frac{1}{\lambda}\ln(2+\frac{R(0)}{K_n})$
     + If limited by a particularly slow phosphatase, $\theta \approx \frac{n-j}{\beta_j}\ln\frac{\alpha}{\beta}$
     + if it is limited by a particularly fast kinase, $\theta \approx \theta_{j-1}\ln\frac{\alpha_j}{\beta}$
     + for a strongly activation case, both kinase and phosphatase affect the signal duration. But the effect from phosphatase is larger, as limiting $\beta$ is outside of the ln but $\alpha$ is within. 

   + Signaling amplitude: in this case, signal amplitude is defined as the concentration of $[X_p]$ at steady state.

     + Amplification happens if $[X_{p,i}]>[X_{p,i-1}]$. Therefore, a slow phosphatase and a fast kinase are desired. But it also depends on the total concentration of [X]

2. Feedback: how a component x affect its own dynamics. For $\frac{d[X]}{dt} = f(x,t)$, if $\frac{\partial f}{\partial x} > 0$, then it is positive feedback. if negative, then it is negative feedback.

3. Systems with more than one steady states: nullclines have more than one intersect 

   eg. in a two component system, the two species are either in mutual inhibition or mutual activation (both are positive feedback). In this simple system, negative feedback tends to drag the system back to the steady state but positive ones can amplify the perturbation, for which we can enter a new steady state. 

4. biological switch: biological systems response to input in a switch-like way $\rightarrow$ input change leads to a change in steady state

   Types: 

   + ultrasensitivity in Goldbeter-Koshland kinetics: a simple system with two opposing enzymes if both enzymes are saturated. If now the input parameter s can change the $v_m$ (of the slower enzyme), then at some point even a small change in s can lead to a big change in the steady state response. NOTE that the ultrasensitive switch is reversible.
   + Auto-activation: inhibit one's own degradation (also construct a sigmoidal like nullcline)
   + Auto-inhibition: inhibit one's own synthesis $\rightarrow$ transcritical bifurcation 
   + One-way switch (mutual activation): the hystersis made by saddle node bifurcations, which cannot jump back even if the inducer (input) is removed
   + Toggle switch (mutual inhibition): the hystersis made by saddle node bifurcation, but may still jump between 2 steady states branches.

5. Bistablility: 2 stable states

6. Requirements of oscillation in biology:

   + Non-linearity
   + Delay (it is like introducing a new variable to the system)
   + Negative feedback
   + Appropriate kinetics and parameter values

   Examples: oscillatory protein expression  

   + One component system: negative feedback (inhibit one's own synthesis) with a delay
   + Two component system: a simple negative feed back network $\rightarrow$ mRNA promotes the synthesis of protein, but the protein inhibits the synthesis of the mRNA with a delay
   + Three component system: $\text{mRNA} \rightarrow \text{cytoplasmic protein} \rightarrow \text{nuclear protein} \dashv \text{mRNA}...$

   Example: negative feedback oscillator 

   + e.g TGF-$\beta$: $R \rightarrow M \rightarrow I \dashv R ...$
   + it is a 3 component negative feedback system (R), and the input paramter is S, which activates R (can be simple linear activation or ultrasensitivity)
   + supercritical Hopf bifurcation: a gradual change of R amplitude 

   Example: activator-inhibitor oscilator 

   + e.g toggle switch + positive feed back: $E^* \rightleftarrows R \rightarrow X \dashv R$
   + a mutual activation toggle switch with a negative feedback from additional component X. The toggle switch creates 2 stable steady states, and the negative feedback drags the system from one brach to the other 
   + Intuitively, R is created in an autocatalytic process through ultrasensitivity from parameter S, and then it promotes the production of an inhibitor, X, which speeds up R removal. First, R builds up, then comes X to force R back down, then X disappears and R can rise again.
   + Subcritical Hopf bifurcation: the original stable FP now lost its stability $\rightarrow$ a sudden jump to a stable limit cycle somewhere

   Example: substrate - depletion oscillator 

   + e.g toggle switch + positive feedback: $E^* \rightleftarrows R \dashv X \rightarrow R$
   + at first, X is in excess while R is little. As R builds up, the production of R accelerates until there is an explosive conversion of the entire pool of X into R. Then the autocatalytic reaction shuts off for lack of substrate, X. R is degraded, and X must build up again before another burst of R is produced.
   
7. Adaption: a system (output) has a transient response to the change of input, i.e the system will come back to its pre-simulation steady state. A perfect adaption is if $O_2 =O_1$.

   Requirements for a perfect adaption:

   + steady state is stable and not sensitive to the pertubation 
   + the kinetic parameters must be such that there is a transient response before the system returns to the steady state.

   For a general ODE system
   $$
   \frac{dx}{dt} = f(x,p,t)
   $$
   After the changes in $p = p + \Delta p$ 
   $$
   f(x, p + \Delta p, t) = f(x,p,t) + \frac{df}{dp}\Delta p + \frac{1}{2} \cdot \frac{d^2f}{dp^2} \cdot (\Delta p)^2 + h.o.t
   $$
   Ignore the higher oder terms and as $f(x, p+\Delta p,t) = f(x,p,t) = 0$ (steady state before and after the pertubation in x), $\Delta p \neq 0$
   $$
   \begin{align}
   \frac{df}{dp} &= 0\\
   \frac{\partial f}{\partial p} + \frac{\partial f}{\partial x} \cdot \frac{dx}{dp} &= 0\\
   \end{align}
   $$
   So the response of the system to the change in parameters, 
   $$
   \frac{dx}{dp} = -(\frac{\partial f}{\partial x})^{-1} \cdot \frac{\partial f}{\partial p}
   $$
   All the values are evalueated at the steady state.

   The perfect adaption is when $\frac{dx}{dp} = 0$, i.e the system is insensitive to the parameter change and when $\frac{\partial f}{\partial p} \neq 0$, i.e there is still transient response 

8. (1) One-component system:
   $$
   J = (\frac{\partial f}{\partial x}) = 0
   $$

   + Not making much sense if f is irrelevant to x

   

   (2) Two-component system:
   $$
   J = 
   \begin{pmatrix}
   \frac{\partial f_1}{\partial x_1} & \frac{\partial f_1}{\partial x_2} \\
   \frac{\partial f_2}{\partial x_1} & \frac{\partial f_2}{\partial x_2}
   \end{pmatrix}
   =
   \begin{pmatrix}
   J_{11} & J_{12}\\
   J_{21} & J_{22}
   \end{pmatrix}
   \\
   \Rightarrow 
   J^{-1} = \frac{1}{det(J)}
   \begin{pmatrix}
   J_{22} & -J_{12}\\
   -J_{21} & J_{11}
   \end{pmatrix}
   $$
   so now the response of the system to changes in parameters are
   $$
   \begin{pmatrix}
   \frac{dx_1}{dp}\\
   \frac{dx_2}{dp}
   \end{pmatrix}
   =
   -\frac{1}{det(J)}
   \begin{pmatrix}
   J_{22} & -J_{12}\\
   -J_{21} & J_{11}
   \end{pmatrix}
   \begin{pmatrix}
   \frac{\partial f_1}{\partial p}\\
   \frac{\partial f_2}{\partial p}
   \end{pmatrix}
   $$
   **NOTE** that we assume the pertubation only affects one component, i.e one of $\frac{\partial f_1}{\partial p},
   \frac{\partial f_2}{\partial p}$ is zero. We assume that $x_1$ is our measurement, i.e the term that we want to be insensitive to the pertubation $\frac{dx_1}{dp}=0$

   + If $x_2$ is the sensor, $\frac{\partial f_1}{\partial p}=0 \Rightarrow J_{12}\frac{\partial f_2}{\partial p}=0 \Rightarrow J_{12}=0$. It means that the sensor $x_2$ does not impact measurement $x_1$, which does not make sense.
   + If $x_1$ is the sensor, $\frac{\partial f_2}{\partial p}=0 \Rightarrow J_{22}\frac{\partial f_1}{\partial p}=0 \Rightarrow J_{22}=0$. It means that the net effect of $x_2$ on itself is zero. **In this way, $x_1$ is both the sensor and response while $x_2$ is a buffer node**
     + Further considering the stability of the system, $J_{12}J_{21} < 0$, therefore it is a negative feedback

   

   (3) Three-component system (A, B, C) with corresponding ODEs ($f_A, f_B, f_C$):
   $$
   J = 
   \begin{pmatrix}
   f_{AA} & f_{AB} &f_{AC} \\
   f_{BA} & f_{BB} &f_{BC} \\
   f_{CA} & f_{CB} &f_{CC}
   \end{pmatrix}
   $$
   so now the reponse of the system is
   $$
   \begin{pmatrix}
   \frac{dA}{dp}\\
   \frac{dB}{dp} \\
   \frac{dC}{dp}
   \end{pmatrix}
   =
   - J^{-1}
   \begin{pmatrix}
   \frac{\partial f_A}{\partial p}\\
   \frac{\partial f_B}{\partial p} \\
   \frac{\partial f_C}{\partial p}
   \end{pmatrix}
   =
   - J^{-1}
   \begin{pmatrix}
   f_{Ap}\\
   0 \\
   0
   \end{pmatrix}
   $$
   If we consider A to be the sensor, i.e $\frac{\partial f_B}{\partial p} = \frac{\partial f_C}{\partial p} = 0$. Similarly, let C be the measurement (response), then we want $\frac{dC}{dp}=0$
   $$
   \begin{align}
   \frac{dC}{dp} &= -(J^{-1})_{31}\cdot f_{Ap}\\
   &= - \frac{1}{det(J)}\cdot det
   \begin{pmatrix}
   J_{21} & J_{22}\\
   J_{31} & J_{32}
   \end{pmatrix}
   \cdot f_{Ap}
   \end{align}
   $$
   To have the above equation is zero, $J_{21}J_{32}-J_{22}J_{31} = 0$, that is
   $$
   f_{BA}f_{CB}-f_{BB}f_{CA}=0
   $$

   + Case I: negative feedback with a buffer node - integral control
     $$
     f_{BA}f_{CB} = f_{BB}f_{CA}=0
     $$
     As $f_{CA} \neq 0$, because we want sensor to affect the responser, $f_{BB}=0$. Besides, the stability of the FP requires $det(J)<0$.

     + Subcase I: $f_{BA}=0$
       $$
       det(J) = -f_{AA}f_{BC}f_{CB}+f_{AB}f_{BC}f_{CA} <0
       $$
       Normally we assume negative self-feedback ($f_{AA}<0$), therefore in $f_{BC}f_{CB}, f_{AB}f_{BC}f_{CA}$ there should be at least one negative value. Hence the **negative feedback**.

       In further simplification, we cut off the connection between B and A, That is, $f_{BA}=f_{AB}=0$. So that now 
       $$
       \begin{align}
       \frac{dB}{dt}&=f_{BA}\Delta A + f_{BB} \Delta B + f_{BC}\Delta C\\
       &=f_{BC}\Delta C
       \end{align}
       $$
       It can be an integral control if we have $f_{BC}=\text{const.}$ Some requirement for that (in a cascading pathway):
       $$
       \frac{dB}{dt}= Ck_1\frac{1-B}{1-B+K_1} - k_2\frac{B}{B+K_2}
       $$

       + $f_{BC} = \text{const.} \Rightarrow (1-B) \gg K_1$, meaning that activation of C on B is very efficient
       + $f_{BB} = 0 \Rightarrow B \gg K_2$, meaning that the decay of B on itself is also very efficient
       + $\frac{dB}{dt}=Ck_1-k_2 \Rightarrow B = B^* + \int_0^t(C-C^*)dt$ 
       + **The B is a buffer node that integrate out the changes in the response C**

     + Subcase II: $f_{CB}=0$
       $$
       det(J)= f_{AB}(f_{BC}f_{CA}-f_{BA}f_{CC})<0
       $$
       Still, in $f_{AB}f_{BC}f_{CA}, f_{AB}f_{BA}$ there should be a **negative feedback**. If we cut off the connection between B and C, similar results can be obtained as above. In this case, **B is a buffer node that integrate out the changes in the sensor A**

   + Case II: incoherent feedforward loop with a proportional node
     $$
     f_{BA}f_{CB} = f_{BB}f_{CA}\neq 0
     $$
     Still, normally we have negatvie self-regulation. That is $f_{CB}f_{BA}, f_{CA}$ have different sign, **meaning that from A to B to C, and from A directly to C, they have different impacts (incoherent)**.

     Further, the impact of path way A to B to C and the impact from C to A follows $\frac{f_{BA}f_{CB}}{f_{CA}}=f_{BB}$. It can be a proportional node if $f_{BB}$ here is a constant, i.e **the node B pass the effect from A proportionally to the effect from A to C**
     $$
     \begin{align}
     \frac{dB}{dt}&=Ak_1\frac{1-B}{1-B+K_1} - k_2\frac{B}{B+K_2}\\
     \frac{dC}{dt}&=Ak_3\frac{1-C}{1-C+K_3} - Bk_4\frac{C}{C+K_4}
     \end{align}
     $$
     + To have B proportionally pass the effect of A, $f_{BA} = \text{const.} \Rightarrow (1-B) \gg K_1$, activation of B is 1st order in A, hence proportional 
     + To have $f_{BB} = \text{const.} \Rightarrow B \ll K_2$, degradation of B is zeroth order in B, hence proportional
     + If $\frac{dB}{dt}$ consists of 2 linear terms, at steady state, A and B are proportional. Then to let $\frac{dC}{dt}=0$, the steady state value is independent of B and A (therefore the input).

   + More component system: consider that we have changes in both signal (input) and response. Taylor expansion as well and see only the linear terms:

   $$
   \begin{align}
   f(x + \Delta x, p + \Delta p, t) &= f(x, p,t) + \frac{\partial f}{\partial x} \Delta x + \frac{\partial f}{\partial p} \Delta p \\
   \Rightarrow
   \frac{d}{dt} \Delta x &=\frac{\partial f}{\partial x} \Delta x + \frac{\partial f}{\partial p} \Delta p
   \end{align}
   $$

9. Requirements for perfect adaption 

   + negative feedback with a buffer node
     $$
     \frac{dB}{dt}=Ck_1 - k_2
     $$
     Therefore, B can integrate out the changes in C

     **C to B is saturated, self-decay of B is also saturated**

   + incoherent feedforward loop with a propotional node
     $$
     \begin{align}
     \frac{dB}{dt} &= Ak_1 - Bk_2\\
     \frac{dC}{dt} &= Af(C)-Bg(C)
     \end{align}
     $$
     Therefore, at steady state, A and B are proportional to each other. Solve for $C^*$, the steady state of C is not related to A or B.

     **A to B is saturated, but the decay of B is linear **

10. Phase plane - B and C

    + negative feedback with a buffer node

      when C changes its nullcline, B remains constant. The new intersection after parameter changes has the same C value $\rightarrow$ B need to be flat $\rightarrow$ Goldbeter-Koshland model can do that.

    + incoherent feedward loop with a propotional control

      Since ther is no direct action from C to B, on the B-C plane, B-nullcline is a straight line.  Both B and C changes its nullcline, but the change is "equal" in a way that the new intersection has the same C value as before.

## Plasticity of signalling

1. Definition: flexibility in signalling responses to the parameter (input) changes. Responses can be sustained, transient and oscillatory.

2. Sensitivity 

   + from the graph: $S = \vert \frac{(O_{peak}-O_i)/O_1}{(I_2-I_1)/I_1} \vert$

   + from ODE system
     $$
     \begin{align}
     \frac{dx}{dt} &= f(x,p)\\
     \frac{d}{dp} \cdot \frac{dx}{dt} &= \frac{\partial f}{\partial p}+ \frac{\partial f}{\partial x} \cdot  \frac{dx}{dp}\\
     \Rightarrow \frac{dS}{dt} &= \frac{\partial f}{\partial p} + J \cdot S
     \end{align}
     $$

## Parameter Estimation 

1. pupose of parameter estimation 

   the dynamics of the system depends not only on the topology but also the choice of parameters (strength of the wiring)

2. Bayesian approach
   $$
   P(X|D,I) = \frac{P(D|X,I)P(X|I)}{P(D|I)}
   $$
   Posterior = Likelihood x Prior \ Evidence

   The X is the parameter set, we evaluate the probability of the X, i.e if we have parameter $X_1$ and $X_2$, we choose the one with higher probability.

3. Maximum-likelihood estimate

   The best estimate is the one that maximum the likelihood of the data given the parameter, i.e the one that maximize $P(D|X,I)$. 

   Some assumptions fro the following operations:

   + the dataset contains multiple **independent** measurement
   + the measurement **error** follows a **Gaussian distribution** around the real (noiseless) data
   + **Standard deviation** $\sigma_k$ of the Gaussian distribution is known (for each measurement, the sd does not need to be the same)

4. Objective function
   $$
   \begin{align}
   P(D|X,I) &= \prod_{k=1}^nP(D_k|X,I) \\
   &= \text{const.}  \times 
   \exp(-\sum_{k=1}^n\frac{1}{2}(\frac{D_k-F_k}{\sigma_k})^2)\\
   \Rightarrow L &= \ln(P(D|X,I))\\
   &= \text{const.} - \frac{1}{2}\chi^2
   \end{align}
   $$
   Therefore, maximize the likelihood is to minimise the sum of normalized residuals, i.e the $\chi^2 = (\frac{D_k - F_k}{\sigma_k})^2$. The objective function is now the log-likelihood. $F_k$ is some function of the parameter X, so now L is some function of X. **NOTE** that now only $F_k$ changes with parameters, **measurement and sd are constant (known values)**

5. Optimisation algorithm 

   To optimize the L, $\nabla L = 0, \nabla \nabla L < 0$. To find zero, we use iterative algorithm based on Taylor expansion starting from an initial guess $X_1$
   $$
   \nabla L (X_0) = \nabla L (X_1) + \nabla \nabla L (X_1)(X_0-X_1) + h.o.t
   $$
   The best estimate 
   $$
   X_0 = X_1 - [\nabla \nabla L (X_1) ]^{-1}\nabla L(X_1)
   $$
   Computers take iterative methods to find the roots of zeros

   +  Newton - Raphson Iterative Algorithm 

     Start with a good estimate $X_1$. Evaluate the gradient vector and Laplace matrix at this estimate. Use this information to up data estimate to $X_2$. Repeat until the root is found.

   + Levenberg - Marquardt algorithm 

     with the old iterative methods.
     $$
     \begin{align}
     X_{n+1} &= X_n - [\nabla \nabla L (X_n) ]^{-1}\nabla L(X_n) \\
     &= X_n - \frac{adj(H)}{det(H)}\nabla L(X_n)\\
     &= X_n - \frac{adj(H)}{\prod \lambda_i} \nabla L(X_n)
     \end{align}
     $$
     If we have really small eigenvalues,  the iteration stepsize will be large. Therefore, we add a smaller constant term to each eigenvalue (the effect on the smaller $\lambda$ would be larger). New iteration methods will be 
     $$
     X_{n+1} = X_n - [\nabla \nabla L (X_n) +cI]^{-1}\nabla L(X_n)
     $$
     The $cI$ term adds the constant c to all the eigenvalues, since
     $$
     [\nabla \nabla L (X_n) +cI]\vec{e}_i=\lambda_i\vec{e}_i + c\vec{e}_i
     $$
     Now the stepsize is not that large. 

6. incorporation of prior information

   Prior information is in the Bayesian approach $P(X|I)$

   + If we now assume that we do not have a flat prior but a Gaussian one, where $X_j= X_{0,j} + \epsilon_j$ for **each parameter in the parameter set**. Therefore, the prior is now also the product of all the pdf for Gaussian 
     $$
     \begin{align}
     P(X|I) &= \text{const.}\times \exp(-\frac{1}{2}\sum(\frac{X_j - X_{0,k}}{\epsilon_j})^2)\\
     \Rightarrow P(X|D,I) &\propto P(D|X,I)\cdot P(X|I)\\
     &=\text{const.} \times \exp(-\frac{1}{2}(\chi^2+C))\\
     \Rightarrow L(\text{posterior pdf}) &=\text{const.}-\frac{1}{2}(\chi^2+C)
     \end{align}
     $$
      The objective function is changed as one more function C is added.

   + Between 2 sets of parameters, which one to choose depends on the posterior probability ratio
     $$
     \frac{P(X_1|D,I)}{P(X_2|D,I)} = \frac{P(D|X_1,I)}{P(D|X_2,I)} \cdot \frac{P(X_1|I)}{P(X_2|I)}
     $$
     The **ratio between the likelihood** is called Bayes factor. The way to obtain the likelihood
     $$
     \begin{align}
     P(D|X,I) &= \int P(D,\lambda|X,I)d\lambda\\
     &= \int P(D|\lambda, X,I)P(\lambda|X,I)d\lambda
     \end{align}
     $$
     Assume we have that $$ and 
     $$
     \begin{align}
     P(\lambda|X,I) &= \frac{1}{\lambda_{max}-\lambda_{min}}\\
     P(D|\lambda,X,I) &= P(D|\lambda_0,X,I) \times \exp(-\frac{1}{2}(\frac{\lambda-\lambda_0}{\sigma_{\lambda}})^2)
     \end{align}
     $$
     Integrate over $\lambda$, i.e the likelihood estimated at $\lambda_0$ is constant. Therefore
     $$
     P(D|X,I) = \frac{1}{{\lambda_{max}-\lambda_{min}}} \cdot \sigma_{\lambda}\sqrt{2\pi}\cdot P(D|\lambda_0,X,I)
     $$

     + for larger range of $\lambda$, likelihood becomes smaller, i.e if the given range of this parameter is too large, we don't like it
     + for smaller variance in $\lambda$, likelihood also becomes smaller, i.e **if the data is good enough (so the variance in parameter will also be small)**, using a range of $\lambda$ is not better than using just one value.

7. Pre-regression diagnosis: should we include all these parameters in the model? 

   + sensitivity matrix: how your measurement (output, data) changes towards the change in parameters (input)
   + each column is how one parameter affects all the measurements $\rightarrow$ they need to have at least one large value (at least affect one measurement) and each column should be linearly independent.

8. Post-regression diagnosis:

   + Goodness of Fit (GOF): sum of normalized residuals follows a $\chi^2$ distribution with df = #total measurement - #parameter (it gives a p-value)

   + Co-variance matrix 

     + The co-variance matrix of **parameters** is related to the Hessian matrix as 
       $$
       \text{cov}[\vec{X}, \vec{X}] = -[\nabla \nabla L]^{-1}
       $$
       Variance in parameters is now related to L, a function that is related to the variance in **data**

     + Taylor expansion of the likelihood function (in vector form)
       $$
       L(\vec{X}) = L(\vec{X_0}) + (\vec{X}-\vec{X_0})^T [\nabla L]+\frac{1}{2}(\vec{X}-\vec{X_0})^T [\nabla \nabla L](\vec{X}-\vec{X_0})
       $$
       L is a scalar: scalar = scalar + (1,n)(n,1) + (1,n)(n,n)(n,1)

       

     + Let Q be the second term,
       $$
       \begin{align}
       Q &= (\vec{X}-\vec{X_0})^T [\nabla \nabla L](\vec{X}-\vec{X_0})\\
       &= (\vec{X}-\vec{X_0})^T E\Lambda E^{-1}(\vec{X}-\vec{X_0})\\
       & = \sum\lambda_i(E^T(\vec{X}-\vec{X_0}))_{i}^2
       
       \end{align}
       $$
       where E is the normalized eigenvectors. **For the L to be the maxima,** all the eigenvalues of Hessian matrix should be negative, and then Q < 0 (which makes sense, since $L(X_0)$ is the maximum). 

       **The Q maps the X to the eigenvectors with a scaling factor**. Let Q = k < 0, then the X after eigen basis transfer now locates on an eclipse contour with $a = \sqrt{\frac{k}{\lambda_i}}$ on the direction $\vec{e_i}$. **But the error bar is still the on projected on x/y axis**

       **NOTE** that if we have two strongly related parameters, the eclipse is elongated in the direction with smaller eigenvalue. Also, if we have weird (no eclipse-like) contours, it means that the Gaussian process is not good.

9. Main steps of parameter estimation

   + Pre-regression diagnosis: should the parameters be included - sensitivity matrix

   + Regression: 

     + Bayesian approach, posterier pdf, likelihood estimate - Gaussian process assumptions 
     + in-cooperation of prior information
     + probability ratio: integrate out the uncertain parameter (marginalisation)
     + maximize the objective function: iterative algorithm 

   + Post-regression diagnosis:

     + Goodness of fit test

     + confidence interval: contour

     + parameter correlation and identifiablity: should we couple parameters or separate them

       Practical unidentifiable - data is too small or bad; structural unidentifiable: should not separate them

10. Model selection
    $$
    \begin{align}
    AIC &= -2L + 2k \\
    BIC &= -2L + k\ln(n)
    \end{align}
    $$
    

