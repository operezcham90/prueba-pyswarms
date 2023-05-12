# Prueba PySwarms

Este código es un ejemplo básico de cómo utilizar [PySwarms](https://pyswarms.readthedocs.io/en/latest/api/pyswarms.single.html) para resolver un problema de optimización. El ejemplo utiliza la función esférica (sphere) para demostrar cómo funciona el algoritmo de optimización PSO para encontrar el mínimo global de una función.

Primero, se importan las librerías necesarias de PySwarms y se define la función de optimización `sphere` de la librería `utils.functions`.

```python
import pyswarms as ps
from pyswarms.utils.functions import single_obj as fx
```

Luego, se definen los parámetros para el algoritmo PSO. `c1` y `c2` son los factores de aprendizaje cognitivo y social, `w` es el peso de inercia, `k` es el número de vecinos que cada partícula tiene, y `p` es la métrica de distancia utilizada para calcular las distancias entre vecinos. En este caso, estamos utilizando la métrica de distancia `2` (Euclidiana).

```python
options = {'c1': 0.5, 'c2': 0.3, 'w': 0.9, 'k': 3, 'p': 2}
```

A continuación, se inicializa el algoritmo PSO y se ejecuta la optimización utilizando la función `optimize`, que recibe como argumentos la función a optimizar (`fx.sphere`) y el número de iteraciones (`iters`). El resultado de la optimización se guarda en la variable `stats`.

```python
optimizer = ps.single.LocalBestPSO(n_particles=10, dimensions=2, options=options)
stats = optimizer.optimize(fx.sphere, iters=100)
```

Finalmente, se muestra una gráfica del historial de costos utilizando la librería `matplotlib.pyplot`. La variable `costs` contiene la evolución del costo en cada iteración.

```python
import matplotlib.pyplot as plt

costs = optimizer.cost_history

plt.plot(costs)
plt.title("Cost History")
plt.xlabel("Iteration")
plt.ylabel("Cost")
plt.show()
```

Es importante mencionar que este ejemplo es muy básico y se puede utilizar PySwarms para resolver problemas de optimización más complejos, utilizando diferentes algoritmos y técnicas de optimización.

En este ejemplo se usa el algoritmo de optimización PSO. Se puede usar [CoCalc](https://cocalc.com/) para probarlo.
