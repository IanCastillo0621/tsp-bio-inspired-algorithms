# Google Colab – Genetic Algorithm TSP Experiments

This repository contains a **Google Colab notebook (.ipynb)** that runs multiple experiments solving TSP instances using a **Genetic Algorithm**.

This README only describes **what is implemented inside the notebook**.

---

## Notebook Contents

### 1. Data Loading

* A dataset of geographic coordinates corresponding to addresses in **Jalisco, México** was loaded into the notebook.
* Coordinates were used directly to compute distances between nodes.

---

### 2. Instance Generation

Multiple independent problem instances were generated for different sizes:

| Nodes | Instances |
| ----: | --------: |
|    40 |        10 |
|   100 |        10 |
|   150 |        10 |
|   200 |        10 |
|   250 |        10 |

Each **instance** was created as a different random subset of locations of the specified size. All instances were processed independently.

Each **instance** is a different random subset of locations of the specified size. Instances are processed independently.

To find the instance generator please refer to `Algoritmo_Exacto.ipynb` inside the `Algoritmo_Exacto` folder within this repository.

---

### 3. Distance Computation

* Distance matrices were constructed from the geographic coordinates.
* These matrices were used by the Genetic Algorithm to evaluate route costs.

---

### 4. Genetic Algorithm Implementation

A complete Genetic Algorithm was implemented with:

* Route (chromosome) representation as permutations of nodes
* Random population initialization
* Fitness evaluation based on total route distance
* Parent selection
* Crossover operator for valid routes
* Mutation operator to maintain diversity
* Elitism to preserve the best solutions

GA parameters (population size, mutation rate, number of generations, etc.) were defined within the notebook and can be adjusted.

---

### 5. Experiment Execution

* The Genetic Algorithm was executed for **each instance of each problem size**.
* Results were computed independently for every run.

---

### 6. Results and Visualization

For each run, the following outputs were produced:

* Best route found
* Total distance of the best solution
* Fitness evolution across generations
* Optional visualizations of routes and convergence

---

## Usage

1. Open the notebook in Google Colab.
2. Run all cells in order.
3. All experiments and outputs are generated automatically.

---

## Notes

* Results may vary between runs due to randomness.
* Larger instances require more computation time.
* No external configuration is required beyond running the notebook.

---

