# Evolution Strategies (ES)

This folder contains implementations and examples of **Evolution Strategies (ES)**, a class of Evolutionary Algorithms designed for real-valued optimization in continuous search spaces.

Inspired by biological evolution, ES rely heavily on **mutation** as the primary search operator, while employing optional recombination and selection mechanisms to evolve a population of candidate solutions toward optimality.

## What are Evolution Strategies?

- **Evolution Strategies (ES)** were introduced in the 1960s by Ingo Rechenberg and Hans-Paul Schwefel.
- They are optimization algorithms particularly suited for **continuous, nonlinear, non-convex, and noisy** problems.
- Unlike Genetic Algorithms, ES focus more on **mutation and self-adaptation** rather than crossover and binary encodings.

## Core Concepts

- **Representation**: Real-valued vectors.
- **Mutation**: Gaussian perturbations to solution vectors.
- **Selection**: Survival of the fittest — elitist or non-elitist mechanisms.
- **Adaptation**: Step-size (`sigma`) evolves to control the scale of mutations.
- **Recombination**: Optional, for combining information from multiple parents.

## Standard Notations

Evolution Strategies are usually denoted as:

\[
( $\mu$ $\rho$, $\lambda$) $\quad \text{or} \quad$ ($\mu$ $\rho$ + $\lambda$)
\]

where:

- \( $\mu$ \): Number of parents.
- \( $\rho$ \): Number of parents participating in recombination (optional).
- \( $\lambda$ \): Number of offspring.
- `(μ, λ)` : Only offspring are eligible for selection (non-elitist).
- `(μ + λ)` : Both parents and offspring compete (elitist).

## Algorithm Workflow

1. **Initialization**:  
   Generate an initial population of candidate solutions, each with associated strategy parameters (e.g., mutation strength \( \sigma \)).

2. **Mutation**:  
   Perturb solutions by adding Gaussian noise:
   \[
   x' = x + \sigma \cdot N(0, I)
   \]

3. **Recombination** (optional):  
   Combine multiple parents to produce offspring.

4. **Evaluation**:  
   Assess the fitness of each offspring.

5. **Selection**:  
   Choose the best individuals based on fitness to form the next generation.

6. **Self-adaptation**:  
   Allow mutation parameters (e.g., \( \sigma \)) to evolve alongside the solutions.

7. **Termination**:  
   Repeat until a stopping criterion is met (e.g., maximum generations or satisfactory fitness).

## Variants Covered

- **(1+1) Evolution Strategy**: Single parent, single offspring.
- **(μ, λ) Evolution Strategy**: Multiple parents, offspring-only selection.
- **(μ + λ) Evolution Strategy**: Multiple parents, elitist selection.
- **Self-Adaptive ES**: Each individual carries and evolves its own mutation parameters.
- **CMA-ES (Covariance Matrix Adaptation Evolution Strategy)**: Advanced variant that adapts full covariance matrices for intelligent mutation scaling and directionality.

## PseudoCodes
(1+1) Evolution Strategy

Description:
Single parent generates one offspring. The offspring replaces the parent only if it has better fitness.

Pseudocode:
1. Initialize x (solution) and σ (mutation step size)
2. While stopping criterion not met:
    a. Generate offspring: x' = x + σ * N(0, I)
    b. If f(x') < f(x):
        - x ← x'
    c. Optionally adapt σ
3. Return best solution found

(μ, λ) Evolution Strategy

Description:
A population of μ parents generates λ offspring (λ > μ). Only offspring compete for survival. The best μ offspring form the next generation.

Pseudocode:
1. Initialize a population of μ parents and σ
2. While stopping criterion not met:
    a. For i = 1 to λ:
        - Randomly select a parent
        - Generate offspring: child_i = parent + σ * N(0, I)
    b. Evaluate fitness of all offspring
    c. Select the μ best offspring to form new parents
3. Return best solution found

(μ+1) Evolution Strategy

Description:
A population of μ parents generates a single offspring per generation. The offspring competes against the parents, and the μ best individuals are selected for the next generation.

Pseudocode:
1. Initialize a population of μ parents and σ
2. While stopping criterion not met:
    a. Randomly select one parent
    b. Generate offspring: child = parent + σ * N(0, I)
    c. Evaluate fitness of all parents and the child
    d. Select the μ best individuals from parents + child
3. Return best solution found

 (μ + λ) Evolution Strategy

Description:
A population of μ parents generates λ offspring. Both parents and offspring compete together, and the μ best individuals form the next generation (elitist strategy).

Pseudocode:
1. Initialize a population of μ parents and σ
2. While stopping criterion not met:
    a. For i = 1 to λ:
        - Randomly select a parent
        - Generate offspring: child_i = parent + σ * N(0, I)
    b. Evaluate fitness of all offspring and parents
    c. Select the μ best individuals from parents + offspring
3. Return best solution found  

## Applications

- Engineering optimization (e.g., aerodynamic design)
- Hyperparameter tuning in machine learning
- Robotics and control systems
- Financial modeling
- Any continuous, black-box, or noisy optimization problem

## Technologies Used

- **Python 3.11+**
- Core libraries:
  - `numpy`
  - `matplotlib` (for convergence plots)
  - *(for advanced algorithms like CMA-ES)* `pycma`, `deap`, or custom implementations

