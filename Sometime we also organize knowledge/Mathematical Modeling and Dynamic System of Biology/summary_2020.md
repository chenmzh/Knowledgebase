## Prof. Dagmar Iber, D-BSSE 2020/21
# Mathematical Modeling in Systems Biology _ Summary

## 1. Reaction Modeling - Enzyme kinetics.

### a) What is the principle of mass action? What are the limitations in using it in systems biology?
The law of mass action states that the rate of a reaction is proportional to the concentrations of the participating molecules. The most accurate model can be obtained when the law of mass action is used to formulate kinetic laws for all elementary reactions.
Limitation: the principle of mass action is applied to elementary reactions. If the mechanism of a reaction is not clear, that we do not clearly know each elementary reaction steps in the reaction, the principle of mass action cannot be applied.
The principle of mass action assume number of molecule is large and well mixed, this assumption is not well applied for molecules in cell systems, especially for biomacromolecules.
(https://doi.org/10.1007/978-3-642-21934-4_42)

### b) How can rule-based modelling be useful?
Rule-based modelling is a simplified approach for modelling. Rule-based modelling describe interactions between bio-molecules as a rule-set. The rule-set can either be translated into an ODE model, or be processed by tools working on the rule-set.
In rule-based modelling, a useful way to describe the interactions is by contact map, the set of possible interactions among the basic elements of our system, without writing down the actual transitions from reactants to products explicitly.
Rule-based modelling make it easier to model complex systems, in which a large number of species and interactions are involved. For example, bio-molecules undergo a variety of modifications which change their behaviors. In an ODE model we will need to treat every modified molecule as a component, which will lead to incredible number of ODEs. In rule-based modelling, such modifications are processed as changing the state label of a component, making the model much easier.

### c) What is a quasi-steady state?
Quasi-Steady State Approximation is a frequently used approximation of a reaction. In a reaction if some steps are much faster than the others, the fast steps will reach equilibrium at very early stage, and the impacts of slow reactions on the concentrations could be ignored in small time windows – the species are in a quasi-steady state and their concentrations could be determined by the equilibrium constants of fast reactions.
Michaelis-Menten Kinetics is based on quasi-steady state approximation.

### d) Write down the scheme for the Michaelis-Menten and the Goldbeter-Koshland approximation. What are the underlying assumptions? When do they apply and when do they
fail?
Michaelis-Menten: a quasi-steady state approximation
Michaelis-Menten approximation is only valid at sufficiently long times: it fails in the initial phase. Quasi-stationarity requires the first step much faster than the C → P transition step. M-M also requires the amount of substrate >> the amount of enzyme. Otherwise the enzymatic reaction is limited by the formation of the complex relative to the processing rate and the reaction then proceeds at Vmax.

Goldbeter-Koshland approximation describe the situation where a kinase and a phosphorylase catalyze a reaction in different directions. Both the phosphorylation reaction and the dephosphorylation reaction could be described by a Michaelis-Menten function. In equilibrium the rates of two reactions are equal and the percentage of phosphorylated species is driven as ...

### e) When can we observe ultrasensitivity?
The term ultrasensitivity indicates cases in which the sensitivity to changes in Vmax is greater than that to be expected from the standard hyperbolic (Michaelis-Menten) response.
(1) positive cooperativity of allosteric proteins (2)multistep effect when the same effector acts at several places in the pathway (3) zero-order effect in covalent modifications when at least one of the converter enzymes is saturated with protein substrate
Zero-order effect: when two enzymes work in contrast and one enzyme saturated, the increase of the amount of another enzyme cannot be compensated by the saturated enzyme (because it is already in Vmax)

### f) What do we mean by positive and negative cooperativity? What are Hill kinetics?
Many proteins have more than one binding site for their interaction partners. Binding of the first ligand can trigger a conformational change that alters the binding characteristics at all binding sites. If the alteration is positive then it is a positive cooperativity, if negative then a negative cooperativity.

## 2. Phase Plane analysis.

### a) What is a phase plane?

Phase plane analysis is a mathematical technique to understand dynamical behavior of a small set (2-3) of ODEs Enables the graphical analysis of steady state location and stability Allows you to identify and characterize switches & oscillators
Nullclines = setting the time derivatives to zero
The phase plane with the trajectories and phase vector field is called a phase portrait.

### b) In a system with two components explain how you can draw the plane and the phase vectors.
(1) draw nullclines (2) on different areas of the plane, determine the sign of derivatives and determine the direction of phase vector (3) The intersection points are steady states, their stability (global or local or unstable) can be determined by the directions of phase vectors.

## 3. Linear stability analysis.

### a) Describe the steps of a linear stability analysis of a nonlinear system around a steady state. Why is it useful?
Steps:
Determine the steady states
Linearize the ODE system at the steady states; determine the Jacobian J
Introduce a perturbation w~ around the steady states
Use the eigenvalues and eigenvectors of J to solve the ODE system for w~
Use the eigenvalues to determine the stability of the steady states
Linear stability analysis is useful because:
it helps determine the stability of steady states and determine the pattern of oscillation

### b) How can one evaluate the stability of steady states of a 2D system based on the eigenvalues of the Jacobian?
Sign of real part → stability (go to 0 or not) and imaginary part →  conciliation. The eigenvalues are determined by solving the characteristic polynomial, thus the signs of real part and existences of imaginary part are determined by the trace and the determinant of the matrix.

## 4. Dynamical Systems.

### a) What is a bifurcation? Describe briefly the characteristics of transcritical, saddle-node, and a Hopf bifurcation. What is the difference between a subcritical and a supercritical bifurcation?

Bifurcation means in a dynamic system when the change in parameters change the stability of steady states.
Bifurcation Parameter = As the value of a bifurcation parameter is changed the stability of at least one equilibrium point changes.
Bifurcation Points = Those parameter values, at which the stability of an equilibrium point changes or new steady state solutions appear or disappear, are called bifurcation points.

Transcritical: Both before and after the bifurcation, there is one unstable and one stable fixed point. However, their stability is exchanged when they collide. So the unstable fixed point becomes stable and vice versa.
Saddle-node: When two equilibrium points collide and annihilate each other we speak of a saddle-
node bifurcation.
Hopf: a fixed point jump to a limit cycle.
Supercritical Hopf bifurcation: amplitude of limit cycle increase gradually; Subcritical Hopf bifurcation: one fixed point suddenly jump to a limit cycle of a certain amplitude.


### b) What is hysteresis?

Hysteresis describes systems which have memory: different steady state value on a same signal depends on the previous steady state
Importantly the concentrations at which the system switches from one steady state branch to the other are different dependent on whether the system starts on the higher or lower steady state branch. The behavior of the system thus depends on its history. The phenomenon itself is referred to as hysteresis.

### c) State the Poincare-Bendixson theorem and explain how it can be used in a 2D phase plane.
Poincare-Bendixson Theorem is used to determine a limit cycle
Suppose that
1. R is a closed bounded subset of the plane
2. dx/dt is a continuously differentiable vector field on an open set containing R
3. R does not contain any fixed points
4. There exists a trajectory C that is confined in R in the sense that it starts in R and stays in R for all future time
Then either C is a closed orbit or it spirals towards a closed orbit as t ! 1. So, R contains a closed orbit.
To ensure the existence of C:
1. Construct a trapping region R
2. arrange that there are no fixed points in R
Also there is a negative criterion:
If the trace of the Jacobian does not change sign within a region of the phase plane, then there is no closed trajectory in this area.

### d) What is the difference between limit cycles and linear oscillators?
Unlike for center solutions, the amplitude of a limit cycle oscillator is determined by the structure of the system itself and not by the initial conditions.
Limit cycles are inherently nonlinear phenomena; they cannot occur in linear systems.

## 5. Regulatory principles.

### a) What determines the speed, duration, and amplification of a signal in a signalling cascade?

Definition of signalling time, duration and amplitude…

Weakly:

Signaling time: t_i = t_0 + \sum (1/b_i), where b_i is the dephosphorylation rates, that means the signaling time is only dependent on dephosphorylation rate, not the phosphorylation rate.

Signaling duration: (\theta_i)^2 = (\theta_{i-1})^2 + 1/(\beta^2), so the duration also only dependent on the deactivation rate.

(activation = phosphorylation, deactivation = dephosphorylation)

Amplitude \delta = I/(2*\theta), while I_i = I_{i-1} *a/b (total “amount” of signalling is amplified by the ratio between phosphorylation and dephosphorylation)
The signal amplitude thus depends on all pathway components, i.e. receptors, kinases, phosphatases. The kinases have, however, the strongest impact. Morerover, we note that a high amplitude correlates with long signal duration and time.

In strongly activated pathway, The signal duration can be determined either by
the receptor activity
a slow phosphatase
a fast kinase


### b) What does positive and what does negative feedback stand for?

dx/dt = f (x, t);
there is a negative feedback if @f/@x < 0,
there is a positive feedback if @f/@x > 0.
@ = partial deritive
Negative feedback: allows the system to return to its previous state after a perturbation as required for oscillations and adaptation
Positive feedback: amplifies the perturbation, and allows for bistability and switches

In a two-component network we have a positive feedback if either both components affect each other positively or both affect each other negatively. If the two components have different effects on each other (one positive, one negative) they constitute a negative feedback.

### c) How can the system have more than one steady state based on these feedbacks?

In the case of positive feedback control and different slopes

### d) What is a biological switch? How many types of switches do you know?

A biological switch is system with two or more steady states which can transit to each other when there is a trigger.
Types of Switches:
(1) Ultrasensitive Switch was also seen in ultrasensitivity part as zero-order ultrasensitivity, in a Goldberger-Koshland system with at least one enzyme is saturated, a signal promote the reaction to one direction can not be compensated.  Ultrasensitive Switch is reversible
(2) Hysteric Switch: based on saddle-node bifurcation. In a system with two stable steady state and one unstable state, when a stable state collide with a unstable steady state, they annihilate and the system jump to another steady state. The Hysteric Switch can be one-way switch when only one stable ss can collide with the unstable ss, or toggle-switch when two stable ss are both possible to collide.


### e) What is bistability?

Bistability is a result of positive feedback control, a system have two steady state which are inhibited and active, and positive feedback control allow transit from one state to another.

### f) How can oscillations emerge in Biology? Provide a biological example of a molecular oscillator.

(1) A negative feedback oscillation requires: Negative feedback + time delay + a non-linearity and appropriate rate constants/parameter values → a circle on the phase plane
(2) A hysteresis oscillator is based on an oscillator switch, the real fixed point on phase plane can never be reached.  A hysteresis oscillator can be built by modifying  an oscillator switch, this can be done in two ways: the oscillator is either an activator-inhibitor oscillators or a substrate depletion oscillator

Example:
Circadian rhythm
Somitogenesis (Hes genes)
Action potentials
Calcium oscillations
Metabolic states: glycolytic oscillations
Signalling and gene expression in many regulatory contexts, i.e.
oscillations in the p53, ERK, and NF-kB pathways

The example of hes gene oscillator: long intron cause long expression and splicing time (delay time)

### g) What is adaptation? When can we claim that we observe perfect adaptation?

An adaptation is, for an output and an input in a system, the output stay at a steady state for a constant input, and when the input is changed, the output make a response (a sudden change) and its level go back to near (or equal to) the starting level.

We observe a perfect adaptation when the steady state of the output afterwards the change of input is exactly the same as it before the change.

### h) Provide two different examples of 3-node network topologies that are able to exhibit adaptation.

Negative Feedback with a buffer node and Incoherent Feedforward

### i) Derive these two network topologies mathematically from the requirements for perfect adaptation.

### j) Define proportional and integral control. Relate them to the two network topologies and their phase planes.

Integral control is related to negative feedback, buffer node and and output node have a relation of negative feedback, and the perfect adaption are achieved when the buffer node (B) shows ultrasensitivity towards the change of output node (C), such that the change in C has a minimal affect on B. Therefore the conversion between B and C need to be zero-order. So that the integral of the change of C is proportional to the change of B.

Proportional control is related to Incoherent Feedforward. A = input node, B = buffer node, C = output node. The change in A pass to C in two ways: directly or indirectly through C. If the change of C is proportional to A, so that the change through two ways will eliminate each other. On phase plane, B nullcline move the same distance as the C nullcline in response to an input change.

## 6. Plasticity of Signalling.

### a) What is meant with plasticity of signalling? Why is it relevant in biology?

Plasticity of signalling means small alterations of parameter values can dramatically alter the pattern of system (oscillation, adaption …). In biology, the pattern is determined by the combination of parameters but not the single parameters. The plasticity of signalling increase the difficult for the models to predict the behavior of systems.

### b) How can you quantify sensitivity in an ODE model?

Sensitivity is defined by S = (dX/X)/(dp/p), the ratio of relative change in steady state
values and the parameters

The sensitivity matrix is defined as …
and we have Fp + J S = 0 at steady state, then the time-dependent sensitivity is dS/dt = JS + Fp

## 7. Parameter Estimation.

### a) What is the purpose of parameter estimation?

Once we come up with a model and we have a dataset of measurements, we want to find the best estimation of a set of parameters in the model to fit the measurements.

### b) Describe the Bayesian approach for parameter estimation.

X = parameter set, D = data of measurements, I = background information
$P(X|D,I) = P(D|X,I)*P(D|I)/P(X|D)$ i.e. posterior = likelihood * prior / evidence

### c) What is the maximum-likelihood estimate?

To get the best parameter estimation, we optimize the probability of the parameter set given a model and measurement. Since the evidence is irreverent to parameter, and if we assume the prior is a constant, the posterior is proportional to the likelihood, then we could maximize the likelihood to maximize the prior.

### d) What is the objective function?

Object function = likelihood function. We use the log of the likelihood (log likelihood) as the object function to maximize. And if assume independence between parameters and Gaussian distribution, the object function will be L = constant - Chi^2/2

### e) Why do we need an optimization algorithm? Derive the Newton-Raphson algorithm. How does the Levenberg-Marquardt algorithm differ? Why does this help? What other local and global optimization algorithms do you know? What are their advantages and disadvantages?

We want to get the maximum of the likelihood function (i.e. the solution for first deritive ) which can not usually be done analytically. So we need optimization algorithm to solve numerically.

Newton-Raphson: to optimize p, we use $p_{n+1} = p_n - \delta\delta L * \delta L$ to iterate.

Levenberg-Marquardt algorithm change the [ΔΔL]^-1 term in Newton-Raphson algorithm to [ΔΔL + CI], i.e. adds a constant, this helps because when the correlation is high, the determinant of ΔΔL approach 0, [ΔΔL]^-1 became very large, which means the steps in the Newton-Raphson algorithm is large, which leads to oscillation while applying Newton-Raphson algorithm. By adding a constant, the eigenvector are not affected, but the eigenvalues are increased. This avoid extremely small eigenvalues.

Other methods: Monte-carlo, grid search

### f) How can prior information be incorporated in the parameter estimation process?

Based on Bayes theorem, posterior = likelihood * prior / evidence,so the posterior can be incorporated directly to the likelihood. In log likelihood function that will be change from $-1/2 (x^2)$ to $-1/2 (x^2 + C)$. If our prior is normal distributions around several likely points, C will be the sum of these distribution.


### g) What are pre-regression diagnostics and post-regression ∗ diagnostics? Why do we need them?


### h) How can we evaluate the quality of the fit? What is a co-variance matrix? How does it relate to the log-likelihood and the confidence intervals of the estimate?

Based on Taylor expansion of L, L(x_0) is constant, first derivative is 0 at maximum, so the second derivative is use to determine the quality of the fit, i.e. determine the confidence interval. The second derivative can be regarded as a Gaussian distribution.

Co-variance between X and Y by definition is E(XY)-E(X)E(Y). The relation is, $co-variance matrix = - \delta \delta L ^(-1). Which could be derived by: calculating P for X and Y by integration, and regard the distribution as a normal distribution and read out variances and co-variance.

### i) ∗ What is the Fisher Information Matrix? What is the Cramer-Rao bound?
### j) Summarize the main steps of parameter estimation.

(0) Check the identifiability  – if the Sensitivity matrix have full rank
(1) Get likelihood function: in the simplified version three assumptions are made: flat prior, error follows Gaussian Distribution, and Independence of measurements
(2) Optimization – Newton-Raphson
(3) Identify the quality of the fit, i.e. the confidence interval. This could be done based on the co-variance matrix, from the co-variance matrix we got Hessian matrix ($\delta \delta L$), Q(X*Hessian*X) has a ellipse contour whose axis are the eigenvalues of the Hessian matrix and the shape is determined by eigenvalues. We can set different level of confidence (different K) to get the confidence intervals.

### k) If we have several competing models, how can we select the most appropriate model? What are BIC and AIC? When do they work? How can models be compared when BIC and AIC fail to work?

We can evaluate the posterior ratio: $P(A|D,I)/P(B|D,I)$

Then if there are adjustable parameters in the model: we start from one parameter in one model: we will calculate marginalization, based on $prob(D|B, I) = \int prob(D, λ|B, I)dλ
= \int prob(D|λ, B, I)*prob(λ|B, I)dλ$, finally we got an item Ockham factor → short range of parameter will be a favor.

$Ockham factor  =  (λmax − λmin) / (δλ√2π)$

Similar when there are multiple parameters.

BIC = −2 ln Lˆ + k ln n
AIC = −2 ln Lˆ + 2k

AIC and BIC are information criteria for determine the Bayes Factor (BF, which is the ratio of the likelihood of data under two models). They punish big number of parameters, BIC reduce the punishment this when the size of dataset is big.

These approximations are generally valid only if the likelihood function is near normal and peaked These approximation are only valid for sample size n much larger than the number k of parameters in the model. The BIC cannot handle complex collections of models.

