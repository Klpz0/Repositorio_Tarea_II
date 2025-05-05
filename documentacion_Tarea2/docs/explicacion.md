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

## Polinomios de Legendre

Los polinomios de Legendre son un sistema de polinomios ortogonales que pueden ser definidos de manera recursiva. Tenemos:
\begin{align}
\forall (M, N) \in\mathbb N^2, \quad \int_{-1}^1 {\rm{d}}x P_N(x)P_M(x) = \frac{2\delta_{MN}}{2N+1}.
\end{align}
Note que los polinomios están definidos en el intervalo $[-1, 1]$.
Los se definen empezando con
\begin{align}
P_0(x) = 1 \Rightarrow P_1(x) = x,
\end{align}
tal que los siguientes órdenes se generan con la regla de recursividad
\begin{align}
(N+1)P_{N+1}(x) = (2N+1)xP_N(x) -NP_{N-1}(x).
\end{align}
Alternativamente, los polinomios pueden ser definidos de manera iterativa bajo la regla (fórmula de Rodrigues)
\begin{align}
P_N(x) = \frac1{2^N N!}\frac{d^N}{dx^N}\left[(x^2-1)^N\right].
\end{align}
