# Swarm vs. Evolutionary Metaheuristics: Combinatorial Optimization

## Overview
This repository contains a comparative analysis between the **Bat Algorithm (BA)** (a continuous Swarm Intelligence paradigm) and a **Genetic Algorithm (GA)** (a discrete Evolutionary paradigm) applied to NP-hard combinatorial problems. 

The core objective of this project is to address the "domain mismatch" inherent in applying continuous velocity-based swarms to strict discrete environments. To achieve this, custom mathematical transfer engines were engineered to forcefully adapt the Bat Algorithm's floating-point mechanics into Integer, Binary, and Permutation spaces.

## Problem Domains and Transfer Engines
The algorithms are benchmarked across three distinct spatial constraints:

1. **The N-Queens Problem (Integer Space):**
   * **Objective:** Minimize attacking pairs on an 8x8 chessboard.
   * **BA Adaptation:** Utilizes an **Integer Snapping** engine with modulo arithmetic to translate continuous spatial coordinates into valid discrete board indices.
   
2. **The 0/1 Knapsack Problem (Binary Space):**
   * **Objective:** Maximize packed value strictly under a 30% total weight capacity penalty limit.
   * **BA Adaptation:** Utilizes a **Sigmoid Transfer Function** to squash continuous momentum into a probability threshold ($0$ to $1$), dictating binary packing states.

3. **The Travelling Salesman Problem (Permutation Space):**
   * **Objective:** Find the shortest closed-loop routing utilizing the standard `berlin52.tsp` dataset.
   * **BA Adaptation:** Redefines standard mathematical addition by computing a **Discrete Swap Sequence Velocity**, allowing bats to mathematically subtract routes from the global best and execute a partial sequence of 2-opt style swaps based on their current frequency momentum.

## Project Structure
* `BA on queen.ipynb` - Implementation and statistical robustness tests for the N-Queens domain.
* `BA on Knap sack.ipynb` - Implementation for the 0/1 Knapsack constraint satisfaction.
* `BA on TSP.ipynb` - Implementation for the Travelling Salesman routing problem.
* `berlin52.tsp` - The standardized geographic coordinate dataset utilized for the TSP routing.
* `requirements.txt` - Python dependencies for reproducing the environment.

## Installation and Execution

### Prerequisites
Ensure you have Python 3.10+ installed on your system. 

### 1. Clone the Repository
```bash
git clone [https://github.com/parsak4936/-Bat-algorithm-Optimization.git](https://github.com/parsak4936/-Bat-algorithm-Optimization.git)
cd -Bat-algorithm-Optimization