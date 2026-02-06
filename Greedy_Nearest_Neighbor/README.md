# Travelling Salesman Problem (TSP) – Algoritmos Greedy

Este repositorio contiene implementaciones de dos heurísticas para resolver el **Problema del Agente Viajero (TSP)**:

1. **Greedy simple (Nearest Neighbor)**
2. **Greedy mejorado con 2-Opt**

Ambos algoritmos permiten generar tours factibles para instancias de TSP con **decenas o cientos de nodos**.

---

## 1. Greedy simple

### Descripción

* Construye un tour **seleccionando en cada paso la ciudad más cercana aún no visitada**.
* Comienza en un nodo de inicio (puede ser el primero de la lista o un nodo elegido).
* Al final, regresa al nodo inicial para cerrar el ciclo.

### Características

* **Complejidad:** O(n²)
* **Velocidad:** Muy rápida, incluso para 200–500 nodos.
* **Calidad:** La solución inicial puede estar lejos del óptimo; depende del nodo de inicio.

### Uso

```python
path, total_cost = greedy_tsp_dict(costs, start_node)
```

* `costs`: diccionario de diccionarios con los costes entre nodos `{i: {j: costo}}`
* `start_node`: nodo desde el cual comenzar el tour

---

## 2. Greedy mejorado con 2-Opt

### Descripción

* Primero construye un tour usando **Greedy simple**.
* Luego aplica **2-Opt** para mejorar localmente el tour: invierte segmentos de nodos si esto reduce la distancia total.
* Opcionalmente, puede realizar **multi-start**, probando distintos nodos iniciales y seleccionando el mejor resultado.

### Características

* **Complejidad:** O(n²) – O(n³), dependiendo de las iteraciones y la restricción del vecindario.
* **Velocidad:** Más lenta que el Greedy simple, pero aún razonable para instancias de hasta 200–300 nodos si se limita el número de rondas (`max_rounds`) y se usan vecindarios restringidos (`K-nearest`).
* **Calidad:** Mejora considerable del tour inicial; suele acercarse al óptimo en instancias medianas.

### Uso

```python
best_path, best_cost = improved_tsp(costs, sample_starts=5)
```

* `sample_starts`: número de nodos iniciales distintos a probar
* Internamente combina **Greedy simple + 2-Opt limitado**

---

## 3. Funciones auxiliares

### `tour_cost(path, costs)`

* Calcula el costo total de un tour dado.

```python
total = tour_cost(path, costs)
```

### `two_opt(path, costs, max_rounds=3)`

* Aplica 2-Opt para mejorar localmente un tour inicial.
* `max_rounds`: límite de iteraciones de mejora para controlar el tiempo.

---

## 4. Formato de los datos

* Los costos entre nodos se deben representar como un **diccionario de diccionarios**:

```python
costs = {
    1: {1:0, 2:10, 3:15},
    2: {1:10, 2:0, 3:20},
    3: {1:15, 2:20, 3:0}
}
```

* También se pueden generar a partir de un **DataFrame de Pandas**:

```python
costs = df.to_dict(orient='index')
```

---

## 5. Comparación de algoritmos

| Algoritmo      | Velocidad  | Calidad    | Complejidad   |
| -------------- | ---------- | ---------- | ------------- |
| Greedy simple  | Muy rápida | Baja-media | O(n²)         |
| Greedy + 2-Opt | Razonable  | Media-alta | O(n²) – O(n³) |

* **Greedy simple:** útil para obtener rápidamente un tour factible.
* **Greedy + 2-Opt:** recomendable cuando se requiere una solución más corta sin comprometer demasiado tiempo.

---

## 6. Recomendaciones

1. Para **instancias grandes (n>200)**:

   * Limitar `max_rounds` en 2-Opt
   * Usar vecindario K-nearest para acelerar swaps

2. Para **mejor calidad**:

   * Aumentar `sample_starts` y usar multi-start

3. Para **rápido prototipado**:

   * Usar solo Greedy simple

---

## 7. Ejemplo de uso completo

```python
# Crear costos desde DataFrame
costs = df.to_dict(orient='index')

# Greedy simple
path_g, cost_g = greedy_tsp_dict(costs, start=costs.keys()[0])
print("Greedy simple:", path_g, cost_g)

# Greedy mejorado
path_i, cost_i = improved_tsp(costs, sample_starts=5)
print("Greedy + 2-Opt:", path_i, cost_i)
```

---

## 8. Referencias

* E. Lawler et al., *The Traveling Salesman Problem: A Guided Tour of Combinatorial Optimization*, 1985.
* M. Dorigo & T. Stützle, *Ant Colony Optimization*, MIT Press, 2004.
* P. Larrañaga et al., *Genetic Algorithms for the Traveling Salesman Problem: A Review*, 1999.
* Artículos recientes sobre heurísticas Greedy y 2-Opt para TSP.
