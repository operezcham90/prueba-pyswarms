# Prueba PySwarms

Documentación de [PySwarms](https://pyswarms.readthedocs.io/en/latest/api/pyswarms.single.html).

En este ejemplo se usa el algoritmo de optimización PSO.

Se recomienda usar [CoCalc](https://cocalc.com/).

# Pasos

Importar librerias.

```python
import pyswarms as ps
from pyswarms.utils.functions import single_obj as fx
```

Dar parametros para el algoritmo PSO, definen cómo las partículas se moverán a través del espacio de parámetros. En particular, `c1` y `c2` son los factores de aprendizaje cognitivo y social, `w` es el peso de inercia, `k` es el número de vecinos que cada partícula tiene, y `p` es la métrica de distancia utilizada para calcular las distancias entre vecinos. En este caso, estamos utilizando la métrica de distancia `2` (Euclidiana).

```python
options = {'c1': 0.5, 'c2': 0.3, 'w': 0.9, 'k': 3, 'p': 2}
```

Inicializar PSO.

```python
optimizer = ps.single.LocalBestPSO(n_particles=10, dimensions=2, options=options)
```

Optimización.

```python
stats = optimizer.optimize(fx.sphere, iters=100)
```

Para ilustrar como fue mejorando con cada iteración.

```python
import matplotlib.pyplot as plt

costs = optimizer.cost_history

plt.plot(costs)
plt.title("Cost History")
plt.xlabel("Iteration")
plt.ylabel("Cost")
plt.show()
```
