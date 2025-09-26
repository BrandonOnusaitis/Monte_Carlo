# Monte Carlo

This repository contains code written for simulating a 2D **[Ising Model](https://en.wikipedia.org/wiki/Ising_model)**. This model is related to studying the dipole moments of magnets on lattices, but finds relevance in the study of critical phenomena. The report, titled **Onusaitis_Brandon_FinalProjectChem444.pdf** outlines the derivation for free energy sampling of the Ising Model using markov chain monte carlo. The steps include, 

1. Establish the hamiltonian for the system of interest
    1. $$E_{ising} = -\sum_{i} \sum_{j} J_{ij} \sigma_{i} \sigma_{j} - \mu \sum_{j} h_{j} \sigma_{j}$$
2. Derive an expression to relate the free energy of a system existing in state A given that it's prior state was B.
    1. $$\log{\frac{P_{A}(\Delta E)}{P_{B}(\Delta E)}} = \beta\log{\Delta F} - \beta \Delta E$$
3. Establish a relation that can be used to estimate $P_{i}(\Delta E)$ numerically
    1. $P_{0}^{est} = \frac{\sum_{i} H_{i}}{\sum_{i} C_{i} \frac{Q_0 (N,V,T)}{Q_i (N,V,T)} e^{-\beta V_{bias,i}}}$
4. Develop a recursion relation for a window function that can be used to iteratively solve for $Q_i$ which can be used to calculate $P_{0}^{est}$ and subsequently $\beta\log{\Delta F}$
    1. $Q_{i+1} = - \frac{Q_i Q_{i-1}A_i + (Q_{i}Q_{i-1} + Q_{i} Q_{i})B_{i}}{Q_{i-1} A_{i} + (Q_{i-1} + Q_{i} )B_{i} + (Q_{i-1} + Q_{i})C_i}$
5. Use recursion relation and other equations to analyse magnetization data from the markov chain monte carlo simulations.

In markov chain monte carlo of ising models, one typically picks a spin on the lattice, flips it, then computes the energy difference between the original and new states. The probability to accept the spin flip is calculated using the **[metropolis criteria](https://en.wikipedia.org/wiki/Metropolis%E2%80%93Hastings_algorithm)**. The code for both the analysis and simulations is in a jupyter notebook called MC.ipynb. A report of the findings is written in a pdf, and this work was done as a final project for a graduate physical chemistry course at Northwestern University.  
