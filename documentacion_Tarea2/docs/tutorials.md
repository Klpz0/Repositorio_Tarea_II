# Tutorial: Codigo de prueba
```python
import numpy as np
import matplotlib.pyplot as plt

def gaussxw(N):
    """
    Calcula los nodos y pesos para la cuadratura de Gauss-Legendre.

    Parameters:
        N (int): Número de nodos a usar.

    Returns:
        tuple: (x, w) donde `x` son los puntos de evaluación y `w` los pesos.

    Example:
        >>> x, w = gaussxw(4)
        >>> print(x)
        [-0.86113631 -0.33998104  0.33998104  0.86113631]
        >>> print(w)
        [0.34785485 0.65214515 0.65214515 0.34785485]
    """
    x, w = np.polynomial.legendre.leggauss(N)
    return x, w

def gaussxwab(a, b, x, w):
    """
    Escala los nodos y pesos de la cuadratura desde el intervalo [-1, 1] al intervalo [a, b].

    Parameters:
        a (float): Límite inferior del intervalo de integración.
        b (float): Límite superior del intervalo de integración.
        x (np.ndarray): Nodos en [-1, 1].
        w (np.ndarray): Pesos en [-1, 1].

    Returns:
        tuple: (xp, wp) nodos y pesos escalados a [a, b].

    Example:
        >>> x, w = gaussxw(2)
        >>> xp, wp = gaussxwab(0, 1, x, w)
        >>> print(xp)
        [0.21132487 0.78867513]
        >>> print(wp)
        [0.5 0.5]
    """
    xp = 0.5 * (b - a) * x + 0.5 * (b + a)
    wp = 0.5 * (b - a) * w
    return xp, wp

def integrando(x):
    """
    Función a integrar: sin(x²).

    Parameters:
        x (np.ndarray or float): Puntos donde evaluar la función.

    Returns:
        np.ndarray or float: Resultado de evaluar sin(x²).

    Example:
        >>> integrando(np.pi)
        0.4303012170000917
        >>> integrando(np.array([0, 1]))
        array([0.        , 0.84147098])
    """
    return np.sin(x**2)

def main():
    """
    Ejecuta la integración para varios valores de N y genera un gráfico
    del valor de la integral en función de N.

    Este script grafica el valor de la integral de sin(x²) en el intervalo [0, π]
    usando cuadratura de Gauss-Legendre con diferentes cantidades de nodos.
    """
    a, b = 0, np.pi
    N_vals = range(2, 31)
    integrales = []

    for N in N_vals:
        x, w = gaussxw(N)
        xp, wp = gaussxwab(a, b, x, w)
        integral = np.sum(wp * integrando(xp))
        integrales.append(integral)

    # Mostrar gráfico
    plt.figure(dpi=100)
    plt.plot(N_vals, integrales, marker='o')
    plt.axhline(1.77245, color='red', linestyle='--', label="Referencia ~1.77245")
    plt.xlabel("N (número de nodos)")
    plt.ylabel("Valor de la integral")
    plt.title("Integral de sin(x²) con cuadratura de Gauss-Legendre")
    plt.grid(True)
    plt.legend()
    plt.tight_layout()
    plt.show()

main()
```
