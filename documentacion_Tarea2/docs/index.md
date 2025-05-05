# Introduccion

El presente trabajo tiene como objetivo el estudio e implementación del método numérico de cuadratura Gaussiana para integrales que no tinen soluciones analiticas.
En esta página se presenta la documentación de la implementación del método para la resolución de la siguiente integral:

\begin{equation}
I = \int_0^{\pi} \sin(x^2) \, dx
\end{equation}

Esta integral no tiene solución analítica, por lo que se recurre a métodos numéricos. Se utiliza `numpy` y `matplotlib` para realizar el cálculo y la visualización.

