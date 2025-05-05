# Método Numérico: Cuadratura de Gauss-Legendre

La cuadratura de Gauss-Legendre permite calcular integrales de la forma:

\begin{equation}
\int_{a}^{b} f(x) dx \approx \sum_{i=1}^{N} w_i f(x_i)
\end{equation}

Donde:

- $\( x_i \)$: nodos (raíces del polinomio de Legendre)
- $\( w_i \)$: pesos asociados


En este caso, la integral se transforma de $\([0, \pi]\)$ al intervalo estándar $\([-1, 1]\)$, y luego se aplican las fórmulas de cambio de variable para escalar los nodos y pesos.

El método es particularmente eficiente para funciones suaves, aunque presenta desafíos en funciones oscilatorias como $\( \sin(x^2) \)$.

