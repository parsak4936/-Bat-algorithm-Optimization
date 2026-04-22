# Swarm vs. Evolutionary Metaheuristics: Combinatorial Optimization

## Overview
This repository contains a comprehensive comparative analysis between Evolutionary Computation (Baseline Genetic Algorithm) and Swarm Intelligence (Standard Bat Algorithm & Discrete Memetic Bat Algorithm) applied to NP-hard combinatorial optimization problems.

The core objective of this project is to address the severe "domain mismatch" inherent in applying continuous velocity-based swarms to strict discrete constraints. Because the native Standard Bat Algorithm operates in a continuous floating-point domain, it suffers from fatal structural failures (Information Cascades, Sigmoid Traps, and geometric Triangle Inequality violations) when applied to permutations and binary arrays. 

To solve this, a **Discrete Memetic Bat Algorithm (MBA)** was engineered. This upgraded architecture integrates custom mathematical transfer engines, native memetic local search operators ($\mathcal{O}(k)$ time complexity), and a secondary **Meta-Genetic Algorithm Tuner** to scientifically breed the optimal hyperparameter boundaries—entirely removing human bias from the tuning process.

## Problem Domains and Transfer Engines
The algorithms are benchmarked and stress-tested for scalability across three distinct spatial constraints:

### 1. The N-Queens Problem (Integer Space)
* **Objective:** Minimize attacking pairs on an $N \times N$ chessboard.
* **The Failure:** The continuous Standard BA suffers a massive *Information Cascade*, prematurely converging into identical genetic clones.
* **The Memetic Upgrade:** Replaces continuous random walks with a **Memetic Discrete Swap** and an integer-snapping modulo engine. 
* **Result:** The Memetic BA scales flawlessly to $8 \times 8$ boards, maintaining a 100% success rate and solving the space in 0.06 seconds, heavily outperforming the baseline.

### 2. The 0/1 Knapsack Problem (Binary Space)
* **Objective:** Maximize total item value without exceeding a strict capacity limit.
* **The Failure:** Uncapped velocity vectors in the standard swarm trigger the *Sigmoid Trap*, forcing the transfer function to output absolute ones/zeros, killing exploration and causing fatal weight penalties.
* **The Memetic Upgrade:** A Meta-Tuned maximum frequency cap prevents target overshoot, while continuous movement is replaced by a targeted **Memetic Bit-Flip**.
* **Result:** Tested up to a $2^{100}$ combinatorial search space (100 items). The Memetic BA achieved absolute dominance, finding significantly higher profit peaks (\$4,308) while executing faster than the baseline GA.

### 3. The Travelling Salesman Problem (Permutation Space)
* **Objective:** Find the shortest closed-loop routing utilizing the standard `berlin52.tsp` geographic dataset.
* **The Failure:** Continuous velocity applied to permutations geometrically guarantees *Triangle Inequality violations*, resulting in highly inefficient, crossing flight paths.
* **The Memetic Upgrade:** Velocity is redefined entirely as a **Discrete Swap Sequence** ($V_i = x_{*} \ominus x_i^{t-1}$). The local search utilizes a **Memetic Two-Opt** operator to surgically untangle crossing lines in $\mathcal{O}(k)$ time.
* **Result:** At a 50-city scalability scale, the Memetic BA found routes literally half the distance of the Genetic Algorithm's best effort (576.74 vs 1148.49), while running significantly faster due to bypassing the heavy $\mathcal{O}(n)$ Order Crossover operations.

## Repository Structure
The project is divided into three primary Jupyter Notebooks, containing the core algorithm logic, the Meta-Tuning engines, and the scalability stress tests:

* `BA_nqueennew.ipynb` - Implementation, Meta-Tuning, and scalability tests for the N-Queens domain.
* `knapsacknew.ipynb` - Implementation, Meta-Tuning, and scalability tests for the 0/1 Knapsack constraint satisfaction.
* `tsp_new.ipynb` - Implementation, Meta-Tuning, and scalability tests for the Travelling Salesman routing problem.
* `berlin52.tsp` - The standardized geographic coordinate dataset utilized for the TSP routing.
* `Bio_inspired_report_D1.pdf` - The comprehensive academic research report detailing the mathematical proofs, Big-O complexities, and empirical findings.
* `/images/` - Directory containing the high-resolution diagnostic dashboards (Convergence, Swarm Health, Biodiversity, and Route Mapping).

## Installation and Execution

### Prerequisites
Ensure you have Python 3.10+ installed on your system. 

### 1. Clone the Repository
```bash
git clone [https://github.com/parsak4936/-Bat-algorithm-Optimization.git](https://github.com/parsak4936/-Bat-algorithm-Optimization.git)
cd -Bat-algorithm-Optimization