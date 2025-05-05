# Código Fuente

```python
import numpy as np
import matplotlib.pyplot as plt


def gaussxw(N):
    """
    Calcula los nodos y pesos para la cuadratura de Gauss-Legendre.

    Args:
        N (int): Número de nodos.

    Returns:
        tuple: Nodos (x) y pesos (w) en el intervalo [-1, 1].
    """
    x, w = np.polynomial.legendre.leggauss(N)
    return x, w


def gaussxwab(a, b, x, w):
    """
    Escala nodos y pesos del intervalo [-1, 1] al intervalo [a, b].

    Args:
        a (float): Límite inferior del intervalo.
        b (float): Límite superior del intervalo.
        x (ndarray): Nodos en [-1, 1].
        w (ndarray): Pesos en [-1, 1].

    Returns:
        tuple: Nodos y pesos escalados al intervalo [a, b].
    """
    xp = 0.5 * (b - a) * x + 0.5 * (b + a)
    wp = 0.5 * (b - a) * w
    return xp, wp


def integrando(x):
    """
    Función a integrar: sin(x^2).

    Args:
        x (float or ndarray): Punto(s) donde se evalúa.

    Returns:
        float or ndarray: Valor(es) de sin(x^2).
    """
    return np.sin(x**2)


def main():
    """
    Ejecuta la integración para varios valores de N y genera un gráfico
    del valor de la integral en función de N.
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
