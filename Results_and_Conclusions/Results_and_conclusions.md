# Bio‑Inspired Algorithms for the Traveling Salesman Problem

This document is an **English explanation and synthesis** of the contents, results, graphs, and conclusions presented in the original Spanish PDF *“Resultados y Conclusiones”*. It reflects **all reported analyses**, including interpretations of tables and highlighted results.

---

## Methods Compared

The study compares four approaches for solving the Traveling Salesman Problem (TSP):

1. **Exact Mathematical Model (GAMS / NEOS server)**
2. **Genetic Algorithm (GA)**
3. **Ant Colony Optimization (ACO)**
4. **Greedy Heuristic**

All methods were evaluated on randomly generated TSP instances, primarily focusing on **40-node problems**, with additional discussion for larger instances.

---

## Experimental Setup

* **Instances:** 10 randomly generated networks of 40 nodes
* **Objective:** Minimize total tour distance
* **Evaluation Metrics:**

  * Solution quality (distance error vs. optimal)
  * Execution time

In result tables, **yellow-highlighted cells** indicate solutions that are very close to the optimal value.

---

## Genetic Algorithm Configuration

The GA used the following parameters:

* Population size: **220**
* Maximum generations: **1200**
* Elite size: **2**
* Tournament size: **3**
* Mutation probability: **0.25**
* Crossover rate: **100%**
* Early stopping patience: **250 generations** without improvement

**Encoding:**

* Chromosome = permutation of nodes from 0 to n−1

**Fitness function:**

* ( fitness = 1 / (1 + L) ), where ( L ) is the total tour length

---

## Results Summary (40 Nodes)

### Greedy Heuristic

* Fastest method in all experiments
* Very low and stable execution times
* Slight loss of accuracy as the number of nodes increases
* Still produced solutions close to optimal in many cases

**Conclusion:** Ideal when fast, reasonably good solutions are required.

---

### Ant Colony Optimization (ACO)

* Intermediate performance between GA and Greedy
* Produced near-optimal solutions in several instances
* Execution time increased with problem size due to pheromone updates and iterations

**Conclusion:** Good balance between exploration and solution quality, but higher computational cost.

---

### Genetic Algorithm (GA)

* Most consistent method in approximating the exact solution
* Achieved an average error of **1.63%** for 40-node instances
* Majority of its results were highlighted as near-optimal
* Execution time higher than Greedy, but significantly lower than the exact method

**Conclusion:** Best balance between accuracy, stability, and scalability.

---

### Exact Method (GAMS / NEOS)

* Guaranteed optimal solutions
* Extremely high execution times
* Became impractical beyond **100 nodes**
* Some instances failed to return results even after extended execution times (30–60 minutes)

**Conclusion:** Useful only as a reference for small instances.

---

## Scalability Observations (100+ Nodes)

* Exact method showed severe limitations, with average times exceeding **179 seconds** for 100 nodes
* GA maintained strong accuracy with **1.28% average error**
* Greedy remained extremely fast (**~38 seconds**) with minimal deviation (**1.30% error**)
* ACO continued to provide competitive solutions but with higher runtimes

---

## Additional Experiments

* A Greedy + 2‑Opt improvement was tested
* Although local routes improved, execution times exceeded **1 hour**
* This variant was excluded from the comparative analysis due to inefficiency

---

## Mathematical Model (Exact Method)

The exact formulation:

* Minimizes total travel cost
* Ensures exactly one outgoing edge per node
* Ensures exactly one incoming edge per node
* Prevents subtours using **MTZ constraints**, enforcing a single Hamiltonian cycle

---

## Overall Conclusions

* There is **no single best method** for all problem sizes
* Performance depends on the trade‑off between accuracy and execution time

**Key takeaways:**

* **Genetic Algorithm:** Best overall balance between precision and robustness
* **Greedy:** Best choice when speed is the priority
* **ACO:** Strong exploratory behavior with moderate cost
* **Exact Method:** Optimal but computationally infeasible at scale

---

## Authors

* Carola Vázquez Arjona
* Paola Michelle Martínez Galeazzi
* Andrés Alarcón Navarro
* Alicia Josefina de la Garza Montelongo
* Ian Fernando Castillo Cortés

---

## Repository

Original project repository:
[https://github.com/Andrews2114/Situacion-Problema-Algoritmos-Bio-Inspirados](https://github.com/Andrews2114/Situacion-Problema-Algoritmos-Bio-Inspirados)

---

---
## Demo Video

[![Genetic Algorithm TSP Demo](https://img.youtube.com/vi/1ToqqOZR-kk/0.jpg)](https://www.youtube.com/watch?v=1ToqqOZR-kk)

---

## References

Alexander, A., & Sriwindono, H. (2020). *The comparison of genetic algorithm and ant colony optimization in completing travelling salesman problem*. In **Proceedings of the 2nd International Conference of Science and Technology for the Internet of Things (ICSTI 2019)**. EAI. [https://doi.org/10.4108/eai.20-9-2019.2292121](https://doi.org/10.4108/eai.20-9-2019.2292121)

Boyko, N., & Pytel, A. (2020). *Aspects of the study of genetic algorithms and mechanisms for their optimization for the travelling salesman problem*. **International Journal of Computing, 20**(4). [https://doi.org/10.47839/ijc.20.4.2442](https://doi.org/10.47839/ijc.20.4.2442)

Chalarux, T., & Sripratak, P. (2020). *Worst case analyses of nearest neighbor heuristic for finding the minimum weight k-cycle*. **CURRENT Applied Science and Technology**. [https://li01.tci-thaijo.org](https://li01.tci-thaijo.org)

Diaby, M. (2008). *A O(n⁸) × O(n⁷) linear programming model of the traveling salesman problem*. **arXiv**. [https://arxiv.org/abs/0803.4354](https://arxiv.org/abs/0803.4354)

Eido, W. M., & Ibrahim, I. M. (2025). *Ant Colony Optimization (ACO) for Traveling Salesman Problem: A review*. **Asian Journal of Research in Computer Science, 18**(2), 20–45. [https://doi.org/10.9734/ajrcos/2025/v18i2559](https://doi.org/10.9734/ajrcos/2025/v18i2559)

Islam, A. H. M., Tanzim, M., Afreen, S., & Rozario, G. (2019). *Evaluation of ant colony optimization algorithm compared to genetic algorithm, dynamic programming and branch and bound algorithm regarding travelling salesman problem*. **Global Journal of Computer Science and Technology, 19**(D3), 7–12. [https://computerresearch.org/index.php/computer/article/view/1842](https://computerresearch.org/index.php/computer/article/view/1842)

Kumar, S., & Munapo, E. (2021). *A greedy reconstruction heuristic for solving the minimum travelling salesman tour problem*. **Journal of Graphic Era University**. [https://doi.org/10.13052/jgeu0975-1416.1321](https://doi.org/10.13052/jgeu0975-1416.1321)

Larrañaga, P., Kuijpers, C. M. H., Murga, R. H., Inza, I., & Dizdarevic, S. (1999). *Genetic algorithms for the travelling salesman problem: A review of representations and operators*. **Artificial Intelligence Review, 13**(2), 129–170. [https://doi.org/10.1023/A:1006529012972](https://doi.org/10.1023/A:1006529012972)

Orman, A. J., & Williams, H. P. (n.d.). *A survey of different integer-programming formulations of the travelling salesman problem*. [https://www.dei.unipd.it/~fisch/ricop/OR2/Survey_compact_TSP_models.pdf](https://www.dei.unipd.it/~fisch/ricop/OR2/Survey_compact_TSP_models.pdf)

Rahman, M. Z., Sheikh, S. R., Islam, A., & Azizur Rahman, M. (2024). *Improvement of the nearest neighbor heuristic search algorithm for traveling salesman problem*. **Journal of Engineering Advancements**. [https://doi.org/10.38032/jea.2024.01.004](https://doi.org/10.38032/jea.2024.01.004)

Shyamala, K., & Sudha Prabha, S. (2014). *An ant colony optimization approach to solve travelling salesman problem*. **International Journal on Recent and Innovation Trends in Computing and Communication, 2**(12), 3966–3971. [https://www.academia.edu/17700194/An_Ant_Colony_Optimization_approach_to_solve_Travelling_Salesman_Problem](https://www.academia.edu/17700194/An_Ant_Colony_Optimization_approach_to_solve_Travelling_Salesman_Problem)

Zanaj, B., & Zanaj, E. (2016). *Review of traveling salesman problem for the genetic algorithms*. **Journal of Information Sciences and Computing Technologies, 5**(3), 534–545. [http://comopt.ifi.uni-heidelberg.de/software/TSPLIB95/](http://comopt.ifi.uni-heidelberg.de/software/TSPLIB95/.scitecresearch.com)
