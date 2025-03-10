
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

Ej: Observable de 3 bits mas halt flag

$$
| x_1,x_2,x_3 \rangle \;\;\otimes \;\; |y\rangle    
$$

Se analiza el “bit” como la unidad mínima de información no probabilística. En el contexto cuántico, el bit se asocia naturalmente a un sistema de dos estados (por ejemplo, el spin de una partícula, aunque conviene mas tomar una base como $\{0,1\}$ en vez de la típica $\{\frac{1}{2}, -\frac{1}{2}\}$ de cuántica).  

Se asume que la computación se realiza en pasos discretos, lo que implica que la preparación de entradas, la evolución y la medición (incluida la observación del halt flag) ocurren en instantes bien definidos.

### Puertas Cuánticas 

Al igual que su análogo clásico, las puertas cuánticas reciben una cantidad de observables de entrada y generan otra cantidad de salida. La diferencia radica en que tanto los estados de entrada como de salida pueden ser estados arbitrarios del espacio de Hilbert, i.e. estados superpuestos. Incluso cuando el input son estados bases (estados propios del sistema), las puertas cuánticas generalmente dan como resultado un estado superpuesto.

Las puertas se pueden representar en forma de diagrama con cajas donde los inputs son recibidos por la part izquierda y los outputs salen por la derecha. La puerta se dice reversible si sus inputs y sus outputs están relacionados por una función invertible

![[Pasted image 20250310134745.png]]

![[Pasted image 20250310134831.png]]

A continuación se detalla la forma en que se definirá la acción de una puerta sobre un observable.

En la computación clásica, cuando una operación es reversible, esta siempre resulta ser una permutación entre los $2^n$ posibles estados de los $n$ bits que pasan por ella, por lo que una alternativa es definir explícitamente esta permutación 

![[Pasted image 20250310135628.png]]

Pero hay una forma mejor de definir las puertas que nos permite extenderlo al contexto cuantico.
Consideremos la matriz de $4\times 4 \;\;\; S$  con componentes
$$S^{ab}_{a'b'} = \delta_{a'}^{a\oplus b} \delta_{b'}^b$$
cuyo efecto sobre el estado de input $|a,b\rangle$ es 
$$|a,b\rangle \Rightarrow \sum_{a',b' \in \{0,1\}} S_{a',b'}^{ab} |a',b'\rangle \equiv S|a,b\rangle$$
$$
\begin{aligned}
|0,1\rangle &\Rightarrow  \sum_{a^{\prime}, b^{\prime} \in\{0,1\}} S_{a^{\prime} b^{\prime}}^{01}\left|a', b'\right\rangle \\
&= \;\;\;  S_{00}^{01}|0,0\rangle+S_{01}^{01}|0,1\rangle + S_{10}^{01}|1,0\rangle+S_{11}^{01}|1,1\rangle \\
&= \;\;\;  \cancel{\delta_0^{0\oplus 1}} \delta_0^1|0,0\rangle+\cancel{\delta_0^{0\oplus 1}}\delta_1^1|0,1\rangle + \delta_1^{0 \oplus 1} \cancel{\delta_0^1}|1,0\rangle+\delta_1^{0 \oplus 1}|1,1\rangle\\
&=\;\;\; |1,1\rangle = M|0,1\rangle
\end{aligned}
$$
Si una puerta cuántica $G$ tiene la $S$-matriz $S_G$ , entonces la puerta inversa $G^{-1}$ tiene la $S$-matriz $S_G^\dagger$ que es su operador hermitiano adjunto (traspuesta conjugada) . Decimos que dos puertas son computacionalmente distintas cuando sus $S$-matrices son distintas salvo multiplicación por un factor de fase 

Para puertas clásicas de un solo bit de entrada y salida existen cuatro computacionalmente distintas, de las cuales solo dons son reversibles, la identidad y la puerta NOT. En cambio, existen muchas puertas cuánticas de 1 bit que son reversibles (una para cada elemento del grupo $SU(2)$, para ser exactos) 

Para las conexiones entre puertas consideramos puertas unitarias llamadas cable unitario, que son simplemente aplicaciones de la identidad.

Uni circuito lógico es una maquina de computación que consiste de puertas lógicas cuyos pasos de computo están sincronizados. Los outputs de algunas puertas son conectados por cables unitarios a los inputs de otras puertas, algunos inputs no provienen de ningún output y son usados como el input general de la red. El resto de inputs son conectados a "fuentes", las cuales son puertas con ningún input y solo un output, el cual en cada paso de computación emite un bit con valor '0' o '1' de manera fija.

![[Pasted image 20250310145141.png]]

Algunos outputs no estan conectados a ningun input y son considerados el output de la red, el resto se conecta a sumideros, los cuales son irreversibles, esto ya que pueden absorber cualquier valor, mientras que las fuentes si son invertibles porque solo emiten 