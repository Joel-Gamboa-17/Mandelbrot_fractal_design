# Mandelbrot fractal design
This code is to form the Mandelbrot Set

![image](https://upload.wikimedia.org/wikipedia/commons/b/b8/Self-Similarity-Zoom.gif)
```python
import numpy as np
import matplotlib.pyplot as plt

# Definir el tamaño de la imagen
width, height = 800, 800
max_iter = 100

# Rango en el plano complejo
x_min, x_max = -2.5, 1.5
y_min, y_max = -2.0, 2.0

# Crear una cuadrícula de puntos en el plano complejo
x = np.linspace(x_min, x_max, width)
y = np.linspace(y_min, y_max, height)
X, Y = np.meshgrid(x, y)
C = X + 1j * Y

# Inicializar el conjunto de Mandelbrot
Z = np.zeros_like(C, dtype=np.complex128)
M = np.full(C.shape, True, dtype=bool)

# Iterar para cada punto en el plano complejo
for i in range(max_iter):
    Z[M] = Z[M] * Z[M] + C[M]
    M[np.abs(Z) > 2] = False

# Mostrar el conjunto de Mandelbrot
plt.imshow(M, extent=(x_min, x_max, y_min, y_max), cmap='hot')
plt.colorbar()
plt.title('Conjunto de Mandelbrot')
plt.show()
```
