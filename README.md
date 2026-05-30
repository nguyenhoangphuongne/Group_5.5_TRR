# Traveling Salesperson Problem (TSP) Optimization Benchmark

This repository contains a comprehensive algorithmic framework implemented in Python to solve and visually analyze the Traveling Salesperson Problem (TSP) using standard TSPLIB benchmark configurations (`pr144.tsp`).

- **Core Focus:** Advanced Combinatorial Optimization & Heuristic Evaluation
- **Course Context:** Discrete Mathematics, Data Structures, and Algorithmic Logic
- **Benchmark Instance:** Symmetric Euclidean Coordinate Pool (N = 144)

---

## 📝 Project Background

The Traveling Salesperson Problem (TSP) is a classic NP-hard challenge in combinatorial optimization. While finding the absolute global optimum becomes computationally prohibitive as the node scale $N$ increases, heuristic approaches offer high-quality solutions within reasonable execution bounds. 

This project implements and systematically compares two major algorithmic paradigms: greedy constructive heuristics for baseline tour initialization, and iterative local search metaheuristics for path refinement and edge-crossing elimination.

### Key Contributions & Implemented Features:
1. **Multi-Strategy Construction:** Implemented **Nearest Insertion (NIH)**, **Cheapest Insertion (CIH)**, and **Farthest Insertion (FIH)** to analyze how different initial skeletons affect final optimization outcomes.
2. **Iterative Local Refinement:** Implemented **2-opt (First Improvement)** for low-latency descent and **2-opt (Best Improvement)** for exhaustive neighborhood screening.
3. **Advanced Metaheuristic Search:** Developed a **Local Beam Search** pipeline running parallel candidate states across generations with unique path filters to maintain structural diversity.
4. **End-to-End Analytics Grid:** Built a professional data processing and visualization pipeline that outputs comprehensive $2 \times 2$ comparative spatial charts using `matplotlib`.
5. **Empirical Performance Profiling:** Benchmarked all algorithm configurations in terms of absolute **Tour Length** (optimization quality) and **Execution Time in ms** (temporal efficiency).

---

## 📂 Repository Layout

```text
├── Dataset/
│   └── pr144.tsp         # TSPLIB symmetric Euclidean coordinate benchmark file
├── Code_project.ipynb    # Monolithic Jupyter Notebook containing the full implementation
└── README.md             # Project documentation, theoretical bounds, and user guide
