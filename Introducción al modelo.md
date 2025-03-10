
## [D. Deutsch] Quantum Theory, the Church-Turing Principle and the Universal Quantum Computer

### El computador Cuántico $\mathcal{L}$

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

Para satisfacer los requerimientos "físicos" esperables de una maquina de computo, se pide que los elementos de la matriz unitaria $U$ tomen la siguiente forma:

$\langle x'\;;\;n'\;;\;m'|\;\;U\;\;|x\;;\;n\;;\;m \rangle = [\delta_{x'}^{x+1} U^+(n',m'_x | n,m_x) + \delta_{x'}^{x-1}U^- (n',m_x ' | n, m_x)]\prod_{x\neq y}\delta_{m_y}^{m_y}$   

Explicación de la notación:
![[Pasted image 20250309180922.png]]

Los productos iterados de la derecha se aseguran de que solo el bit de memoria x-esimo sea parte del paso de computación. Las deltas de Kronecker se aseguran de que en cada paso, x se desplace solo una unidad a la izquierda (x-1) o a la derecha (x+1), y las funciones $U^\pm(n',m' | n,m)$ representan la transformación del estado dependiendo solo de los observables "locales" $\hat n$ y $\hat m_x$. Estos operadores pueden ser arbitrarios mientras sean unitarios, con el fin de mantener unitaria toda la transformación $U$ . Cada posible elección de estos operadores define un computador cuántico distinto $\mathcal{L}[U^+, U^-]$ .


En computación clásica, podemos definir la parada de una Maquina de Turing cuando dos estados consecutivos son idénticos. Un programa "valido" es aquel que asegura que la maquina se detendrá en un numero finito de pasos. Sin embargo, por la naturaleza de la definición de las transiciones de estados en nuestra maquina cuántica, esta nunca puede estar en un estado idéntico luego de una computación no trivial. 

Tampoco podemos hacer ninguna observación antes de que la computación se detenga porque esto alteraría de forma irreversible es estado del sistema cuántico. La forma mas efectiva de señalar al observador del computo que este ha concluido es usar uno de los bits internos del procesador, digamos $\hat n_0$ y apartarlo con este objetivo. De esta forma sabremos que el programa ha concluido cuando $\hat n_0$ valga 1, y este puede ser observador periodicamente sin alterar el estado del sistema. Diremos que un programa de $\mathcal{L}$ es valido si el valor esperado de su tiempo de computación (es decir, que $\hat n_0$ = 1) sea finito.

![[Pasted image 20250309183323.png]]

### Prop.
La Computadora cuántica $\mathcal{L}$ posee la propiedad universal de computar cualquier función recursiva, al igual que la Maquina de Turing.

### Base para la computación cuántica universal

![[Pasted image 20250309183656.png]]



![[a.svg]]

## [Deutsch 1989]  Quantum Computational Networks

### Introducción 
Comienza definiendo la computación como un proceso físico en el que un sistema transforma unos estados iniciales (entradas) en otros estados finales (salidas) de acuerdo con una función determinada. Se explica que, si bien los símbolos (entradas y salidas) pueden ser abstractos, en una implementación real son estados físicos de un sistema. Para formalizar la idea, se introducen tres observables:  
	• El observable de entrada, que se prepara en uno de varios estados posibles.  
	• El observable de salida, cuyos valores se interpretan como el resultado del cómputo.  
	• La “bandera de parada” (halt flag), que indica cuándo la computación ha concluido.
	
Se analiza el “bit” como la unidad mínima de información no probabilística. En el contexto cuántico, el bit se asocia naturalmente a un sistema de dos estados (por ejemplo, el spin de una partícula).  
• Se subraya que la estructura discreta de la información —tan intrínseca en la palabra “cuántico” (indivisible) como lo es “bit”— encaja de forma natural en la teoría cuántica, a diferencia de la física clásica donde los observables suelen tener espectros continuos.  
• Se asume que la computación se realiza en pasos discretos, lo que implica que la preparación de entradas, la evolución y la medición (incluida la observación de la bandera de parada) ocurren en instantes bien definidos.