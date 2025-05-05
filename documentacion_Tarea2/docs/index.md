# Introducción: Cuadratura Gaussiana

La cuadratura gaussiana es un método numérico que nos sirve para calcular integrales definidas forma precisa y eficiente, este método es especialmente útil cuando no se tiene un resultado analítico para una integral. Se basa en polinomios ortogonales, como los de Legendre, para integrar de manera exacta funciones polinómicas de hasta $ 2N - 1$, lo que nos da un resultado muy preciso de forma eficiente pues usa menos evaluaciones de la función.


En esta página se presenta la documentación de la implementación del método para la resolución de la siguiente integral:

\begin{equation}
I = \int_0^{\pi} \sin(x^2) \, dx
\end{equation}

Esta integral no tiene solución analítica, por lo que se recurre a métodos numéricos. Se utiliza `numpy` y `matplotlib` para realizar el cálculo y la visualización.

