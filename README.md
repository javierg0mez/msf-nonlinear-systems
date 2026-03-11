# Master Stability Function for Chaotic Dynamical Systems

This repository contains Python implementations used to compute the Master Stability Function (MSF) for several well-known nonlinear dynamical systems under different linear coupling schemes.

The numerical experiments reproduce and explore typical MSF behaviors for chaotic systems, illustrating how the choice of coupling protocol affects the stability of the synchronization manifold in networks of coupled dynamical systems.

## Systems analyzed

The following dynamical systems are considered:
- Rössler system  
- Lorenz system  
- Chen system  
- Chua circuit  
- Hindmarsh–Rose neuron model  
- Forced Duffing oscillator  
- Forced Van der Pol oscillator  

For each system, the MSF is computed for different **single-component coupling schemes** between the state variables.

For three-dimensional systems with state vector (x, y, z), the possible linear coupling configurations are:
x → x, x → y, x → z  
y → x, y → y, y → z  
z → x, z → y, z → z  

where the notation $x^i \rightarrow x^j$ indicates that the i-th component of one system is coupled to the j-th component of another system.

## Numerical methodology

The Master Stability Function is obtained from the variational equation

$\dot{\xi}= \left[Df\left( s \right)  - r Dh\left( s \right)\right]\xi$

integrated along the synchronized trajectory $s(t)$ of the isolated system.

The numerical procedure is the following:

1. The trajectory $s(t)$ of the isolated dynamical system is obtained by integrating the equation  
   $\dot{s} = f(s)$ using **SciPy's `odeint` solver** with adaptive time step.

2. For each value of the normalized coupling parameter \(r\), the linear variational equation is integrated.

3. The perturbation vector is iteratively renormalized and the largest Lyapunov exponent is estimated from

\[
\Lambda(r) = \lim_{M \to \infty} \frac{1}{T} \sum_{k=1}^{M} \ln \|\xi_k\|
\]

where \(T = M\Delta t\) is the total integration time.

4. Repeating this procedure for many values of \(r\) yields the Master Stability Function \(\Lambda(r)\).

## Requirements

Python ≥ 3.11

Required libraries:

- numpy  
- scipy  
- matplotlib  

## Repository purpose

The codes in this repository were developed to generate the numerical simulations used to study the Master Stability Function for several chaotic dynamical systems under different coupling schemes.

These numerical experiments illustrate how the dynamics of individual systems and the coupling protocol determine the stability of synchronization in networks of coupled nonlinear systems.

## Author

Javier Gómez Fuentes  
PhD Student – Institute of Physics Gleb Wataghin (IFGW)  
University of Campinas (UNICAMP)

## Supervisor

Prof. Dr. Marcus de Aguiar  
Institute of Physics Gleb Wataghin (IFGW)  
University of Campinas (UNICAMP)
