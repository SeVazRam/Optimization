# Basic Multi-Objective Optimization: Weighted Sum and Particle Swarm Optimization (PSO)

This notebook explores basic techniques for solving multi-objective optimization problems through two different approaches:

- **Weighted Sum Method**:  
  A classic technique that transforms a multi-objective problem into a single-objective one using a weighted linear combination.

- **Particle Swarm Optimization (PSO)**:  
  A heuristic inspired by the social behavior of swarms, used to approximate the Pareto front in multi-objective scenarios.

The goal is to find solutions that balance two objective functions under a linear constraint.

---

## Problem Description

We aim to minimize two objective functions:

- $f_1(x, y) = x^2 + y^2$  (minimize distance to the origin)
- $f_2(x, y) = (x-1)^2 + y^2$  (minimize distance to the point (1,0))

Subject to the constraint:

- $x + y \geq 1$

---

## Notebook Contents

| Section | Description |
|:---|:---|
| 1. Problem Definition | Definition of the objectives and constraint. |
| 2. Visual Interpretation | Graphical understanding of the objectives and feasible region. |
| 3. Weighted Sum Method | Scalarization of the problem and solution using `scipy.optimize.minimize`. |
| 4. Particle Swarm Optimization (PSO) | Basic PSO implementation to approximate the Pareto front. |
| 5. Results Visualization | Plots of feasible regions, approximate Pareto fronts, and summary tables. |

---

## Key Results

- Visualization of the feasible region $x + y \geq 1$.
- Approximate Pareto front generated using weighted sum method.
- Approximate Pareto front generated using PSO.
- Summary tables for both optimization strategies.

---

## What you will learn

- How to structure and solve a simple multi-objective optimization problem.
- How to implement and use the weighted sum method.
- How to develop a basic Particle Swarm Optimization (PSO) algorithm.
- How to compare classical and heuristic optimization approaches.
- How to visualize feasible regions and Pareto fronts in multi-objective problems.

---

## Technologies Used

- Python 3
- Numpy
- Scipy
- Matplotlib
- Pandas

---

## Author

Sebastián Vazquez  
*(GitHub: [SeVazRam](https://github.com/SeVazRam))*

