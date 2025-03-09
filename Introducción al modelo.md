
[D. Deutsch] Quantum Theory, the Church-Turing Principle and the Universal Quantum Computer


Tenemos un procesador que consiste de $M$ observables de dos estados

$$
\{ \hat{n_i} \} \;\;\;\;\;\ (i \in \mathbb{Z}_M)
$$
y una memoria que consiste en una secuencia infinita de observables de dos estados

$$
\{ \hat{m_i} \} \;\;\;\;\;\ (i \in \mathbb{Z})
$$
Esto hace el análogo de la cinta infinita de una maquina de Turing clásica.

Tambien tenemos otro observable $\hat x$ con todos los enteros como espectro, el cual actuará como el puntero, o posición de la cinta, de una maquina de Turing clasica.

Luego, el estado de la maquina $\mathcal{L}$ corresponde a un vector unitario en el espacio $\mathcal{H}$ generado por los vectores propios

$$
| x;n;m \rangle \equiv |x; n_0, n_1,...,n_{M-1};...,m_{-1},m_0,m_1,...\rangle
$$
de $\hat x$, $\hat n$ y $\hat m$ etiquetados por sus correspondientes valores propios $x$,$n$ y $m$ 


La evolución de todo el sistema $\mathcal{L}$ puede ser resumida por un operador unitario constante $U$ de $\mathcal{H}$. en $U$ se sintetiza la evolución de cualquier estado $|\psi(t)\rangle \in \mathcal{H}$ durante cada paso de computación

$$
|\psi(nT)\rangle = \mathbf{U}^n |\psi(0) \rangle \;\;\;\;\; (n\in \mathbb{Z}^+),
$$
$$
\mathbf{U}^\dagger \mathbf U  =  \mathbf U \mathbf{U}^\dagger = 1
$$

La computación inicia con $t=0$. En este momento, tanto $\hat x$ (el puntero) como $\hat n$ (el procesador, o espacio de trabajo) están seteados a 0, mientras que una porción finita de los $\hat m$ se preparan como el "programa" y el input, y el resto se coloca en 0. Es decir

$$
| \psi (0) \rangle = \sum_m \lambda_m |0 ; 0; m \rangle,
$$
$$
\sum_m | \lambda_m | ^2 = 1
$$
donde solo una cantidad finita de $\lambda_m$ son distintos de 0, o $\lambda_m$ se desvanece en el caso contrario

Para satisfacer los requerimientos "fisicos" esperables de una maquina de computo, se pide que los elementos de la matriz unitaria $U$ tomen la siguiente forma:

$\langle x'\;;\;n'\;;\;m'|U|x\;;\;n\;;\;m \rangle$ 