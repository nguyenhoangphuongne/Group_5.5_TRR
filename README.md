# Traveling Salesperson Problem (TSP) Optimization Benchmark

A comprehensive algorithmic research framework implemented in Python to solve and visually analyze the Traveling Salesperson Problem (TSP) using standard TSPLIB benchmark configurations (`pr144.tsp`). This project profiles the structural and temporal behavioral trade-offs between initial greedy constructive insertions and advanced multi-state iterative local search metaheuristics.

## 📌 Project Architecture & Workflow
The optimization engine follows a robust, modular pipeline designed to evaluate combinatorial optimization properties across four clear execution phases:
1. **Topological Parsing:** Imports geometric structural components from TSPLIB configurations, extracting raw geographic vectors to instantiate spatial Euclidean coordinate pools and distance matrices $D_{i, j}$.
2. **Greedy Macro-Construction:** Generates foundational baseline tours through localized and distributed node insertion heuristics.
3. **Iterative Local Search Descent:** Refines active edge configurations via localized structural disruptions to eliminate sub-optimal crossings.
4. **Dynamic Grid Tuning:** Executes a comprehensive sensitivity sweep over control configurations to establish empirical Pareto-optimal parameters.

---

## 🛠️ Core Algorithmic Frameworks

### 1. Constructive Insertion Heuristics
* **Nearest Insertion Heuristic (NIH):** Constructs the baseline path by prioritizing unvisited nodes that exhibit the minimum spatial distance to any node currently mapped inside the sub-tour cluster.
* **Cheapest Insertion Heuristic (CIH):** Minimizes total tour extension metrics by progressively embedding unvisited nodes that yield the absolute smallest path expansion delta $\Delta d = d_{i,k} + d_{k,j} - d_{i,j}$.
* **Farthest Insertion Heuristic (FIH):** Establishes a macro-geometric skeleton early in the loop by isolating unvisited nodes maximally distant from the active sub-tour, naturally preventing complex localized crossings.

### 2. Local Search Operators & Metaheuristics
* **2-opt (First Improvement):** Executes rapid neighbor sweeps, immediately accepting and applying the first found edge-pair exchange $(u, v)$ that yields a negative delta path weight to ensure low execution latency.
* **2-opt (Best Improvement):** Performs an exhaustive neighborhood exploration, screening all possible transformations per iteration to systematically select only the globally optimal edge-swap within that generation.
* **Local Beam Search:** Evaluates $B$ multiple candidate states concurrently across generations. Incorporates a diversity gating mechanism via unique path distance filtration to prevent premature convergence onto identical local minima attrac-tor basins.

---

## 🔬 Computational Bounds & Parameter Tuning

### Complexity Modeling
The spatial screening of the combinatorial search space introduces predictable computational scaling bounds:
* **Constructive Insertion Phase:** Evaluates remaining open nodes against active path boundaries, rendering an $\mathcal{O}(N^2)$ tracking constraint.
* **Exhaustive 2-opt Neighborhood Scan:** Evaluates exactly $\frac{N(N-3)}{2}$ edge combinations per loop, requiring quadratic scaling properties $\mathcal{O}(N^2)$.
* **Local Beam Search Matrix:** Multiplies the combinatorial neighborhood screening workload across parallel states, defining a maximum generational complexity bottleneck of:
  $$\mathcal{O}(N^2 \cdot B)$$
  *(where $B$ represents the active Beam Width).*

### Sensitivity Analysis & Hyperparameter Investigation
To isolate the ideal inflection point balancing optimization accuracy against execution latency, a continuous **Grid Search** sweep is performed by scaling the Beam Width parameter $B$ linearly from $1$ to $30$. This evaluation uncovers distinct saturation thresholds and diminishing-return characteristics as the parallel search volume scales.

---

## 📊 Visual Diagnostics & Analytics
The project integrates a professional multi-panel grid visualizer powered by `matplotlib` that maps geometric path mutations in real-time. Each subplot dynamically injects quantitative performance metrics (**Tour Length** and **Execution Time in ms**) into the canvas title for parallel evaluation.

The graphical assets adopt a highly unified, academic color palette:
* 🔴 **Vertices:** Node placements are rendered as solid red scatter markers (`#d62728`) mapping node distribution density.
* 🔵 **Current Tour:** All active pathways currently constituting the validated solution are rendered uniformly as thick, solid blue lines (`#1f77b4`).
* 🩶 **Discarded Paths:** Sub-optimal, crossed edge pairs broken and deleted during the refinement descent are preserved underneath as light gray dashed lines (`#b0b0b0`), capturing the visual footprint of the optimization history.

---

## 📂 Repository Layout
```text
├── Dataset/
│   └── pr144.tsp         # TSPLIB symmetric Euclidean coordinate file (N = 144)
├── Code_project.ipynb    # Monolithic Jupyter Notebook with complete executable pipeline
└── README.md             # Formal documentation and algorithmic breakdown
