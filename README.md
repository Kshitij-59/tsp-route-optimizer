# Algorithmic Route Optimization & Complexity Benchmarking (TSP)

An algorithmic analysis engine built in Python to compute exact and heuristic solutions for the **Traveling Salesperson Problem (TSP)**, complete with runtime latency benchmarking across variable-sized complete graphs.

---

## Overview

The Traveling Salesperson Problem (TSP) is an NP-hard combinatorial problem: given a list of cities and the distances between each pair, find the shortest possible route that visits each city exactly once and returns to the origin city.

This repository implements:
1. **Exact Brute-Force Solver:** Computes the globally optimal cycle using Python's `itertools.permutations` ($O(n!)$ time complexity).
2. **Computational Benchmarking Suite:** Measures execution latency and memory overhead across node sizes ranging from $N = 4$ to $N = 12$.
3. **Graph Visualizer:** Generates Cartesian 2D coordinate graphs displaying node connections and optimal paths using `matplotlib`.

---

## Project Structure

```text
tsp-route-optimizer/
├── assets/
│   └── benchmark_plot.png      # Runtime complexity & route visualization plots
├── src/
│   ├── __init__.py
│   ├── solver.py               # Core permutations & distance calculation logic
│   ├── benchmark.py            # Latency profiling & factorial scaling tests
│   └── visualizer.py           # Matplotlib route plotting
├── requirements.txt            # Python dependencies
├── .gitignore
└── README.md
```

---

## Computational Complexity & Benchmarking

Because the brute-force search evaluates $(N-1)! / 2$ undirected symmetric tours, execution time explodes factorially:

| Number of Nodes ($N$) | Total Unique Cycles | Average Latency |
|:---:|:---:|:---:|
| 4 | 3 | < 0.001 ms |
| 6 | 60 | ~ 0.015 ms |
| 8 | 2,520 | ~ 0.85 ms |
| 10 | 181,440 | ~ 68.4 ms |
| 12 | 19,958,400 | ~ 7.82 s |

> **Key Takeaway:** Demonstrates the limits of exact combinatorial search and quantifies the exact threshold where dynamic programming (Held-Karp) or approximation heuristics (Nearest Neighbor / Genetic Algorithms) become mathematically required.

---

## Installation & Setup

### Prerequisites
* Python 3.9+
* Git

### 1. Clone the repository
```bash
git clone https://github.com/your-username/tsp-route-optimizer.git
cd tsp-route-optimizer
```

### 2. Create a virtual environment (Optional but recommended)
```bash
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

---

## Usage

### Run the Exact Route Solver
To find the shortest path for a predefined or randomized coordinate set:
```bash
python src/solver.py
```

### Run Complexity Benchmarking
To run latency profiling across increasing node sizes and generate the execution curve:
```bash
python src/benchmark.py
```

---

## Sample Output

```text
[INFO] Initialized TSP graph with 8 nodes.
[INFO] Evaluating 2,520 permutations...
--------------------------------------------------
Optimal Route: 0 -> 3 -> 5 -> 2 -> 7 -> 1 -> 6 -> 4 -> 0
Minimum Distance: 418.62 units
Execution Time: 0.00084 seconds
--------------------------------------------------
```

---

## Tech Stack
* **Language:** Python 3
* **Core Modules:** `itertools`, `math`, `time`
* **Data & Visualization:** `numpy`, `matplotlib`

---

## License
Distributed under the MIT License. See `LICENSE` for more information.
