# GUÍA 3 DE LENGUAJES: PROCEDIMIENTOS EFECTIVOS

Un concepto importante en ciencias de la computación es el de procedimiento o método para realizar alguna tarea determinada. Nos interesan los procedimientos que están definidos en forma precisa e inambigua, es decir aquellos en los cuales en cada paso a seguir, la tarea a realizar está objetivamente descripta. También deben ser repetibles, en el sentido de que si realizamos un procedimiento dos veces con el mismo dato de entrada, entonces ambas ejecuciones deben ser idénticas, es decir se realizarán las mismas tareas y en el mismo orden.

Nos interesan los procedimientos $\mathbb{P}$ que posean las siguientes características:

&#40;1&#41; El interprete o ejecutante de $\mathbb{P}$ es una persona que trabajará con papel y lápiz (ambos recursos disponibles en forma ilimitada).

&#40;2&#41; Cada paso o tarea que $\mathbb{P}$ encomiende a realizar debe ser simple y fácil de realizar en forma efectiva por cualquier persona.

&#40;3&#41; El procedimiento $\mathbb{P}$ comienza a funcionar siempre a partir de cierto dato de entrada y una vez que haya comenzado, siempre sucederá una de las dos siguientes posibilidades

**(a)** $\mathbb{P}$ luego de cierta cantidad de pasos realizados, se detiene y da cierto dato de salida

**(b)** $\mathbb{P}$ nunca se detiene, es decir a medida que se van realizando las instrucciones o tareas, $\mathbb{P}$ siempre direcciona a realizar nuevas tareas y lo hace sucesiva e indefinidamente.

En el caso (a) diremos que $\mathbb{P}$ se detiene partiendo del dato de entrada en cuestión y en el caso (b) diremos que $\mathbb{P}$ no se detiene partiendo de dicho dato

&#40;4&#41; Hay $n, m \in \omega$ y un alfabeto $\Sigma$ tales que el conjunto de datos de entrada de $\mathbb{P}$ es $\omega^n \times \Sigma^{\ast m}$. Cabe aclarar que para ciertas $(n+m)$-uplas de $\omega^n \times \Sigma^{\ast m}$ el procedimiento $\mathbb{P}$ se detendrá y para ciertas otras no lo hará.

Llamaremos procedimientos efectivos a aquellos procedimientos que posean las características arriba mencionadas.

El conjunto de datos de salida de $\mathbb{P}$ es el conjunto de todos los datos que el procedimiento $\mathbb{P}$ dará como salida en alguna de las posibles ejecuciones al variar todos los datos de entrada posibles. Si bien siempre el conjunto de datos de entrada será de la forma $\omega^n \times \Sigma^{\ast m}$, puede ser muy difícil o imposible, en general, conocer con precisión el conjunto de datos de salida de un procedimiento (esto lo justificaremos más adelante).

Ya que el interprete de $\mathbb{P}$ es una persona dotada de lápiz y papel, supondremos que los elementos de $\omega$ que intervienen en los datos de entrada y de salida estarán representados por palabras de $Num$ usando la notación decimal.

Quizás el procedimiento efectivo más famoso de la matemática es aquel que se enseña en los colegios para sumar dos números naturales expresados en notación decimal. Notar que el conjunto de datos de entrada de dicho procedimiento es $\omega^2$ y el conjunto de datos de salida es el conjunto formado por todas las sumas posibles de pares de elementos de $\omega$, es decir $\omega$. Por supuesto este procedimiento solo usa lápiz, papel y pasos extremadamente simples a seguir en cada momento de la computación, es decir, en algún sentido, no es necesario "entender qué es lo que se está haciendo" para llegar al final y obtener la palabra que representa en notación decimal a la suma de los números iniciales. Dejamos al lector repasar este procedimiento así como el que calcula dado un número $x$ no nulo de $\omega$, al número $x - 1$, los cuales nos harán falta más adelante en los ejemplos.

## Funciones $\Sigma$-efectivamente computables

Una función $\Sigma$-mixta $f : D_f \subseteq \omega^n \times \Sigma^{\ast m} \to \omega$ será llamada $\Sigma$-efectivamente computable si hay un procedimiento efectivo $\mathbb{P}$ tal que

&#40;1&#41; El conjunto de datos de entrada de $\mathbb{P}$ es $\omega^n \times \Sigma^{\ast m}$

&#40;2&#41; El conjunto de datos de salida está contenido en $\omega$.

&#40;3&#41; Si $(\overrightarrow{x}, \overrightarrow{\alpha}) \in D_f$, entonces $\mathbb{P}$ se detiene partiendo de $(\overrightarrow{x}, \overrightarrow{\alpha})$, dando como dato de salida $f(\overrightarrow{x}, \overrightarrow{\alpha})$.

&#40;4&#41; Si $(\overrightarrow{x}, \overrightarrow{\alpha}) \in (\omega^n \times \Sigma^{\ast m}) - D_f$, entonces $\mathbb{P}$ no se detiene partiendo desde $(\overrightarrow{x}, \overrightarrow{\alpha})$

Análogamente una función $\Sigma$-mixta $f : D_f \subseteq \omega^n \times \Sigma^{\ast m} \to \Sigma^\ast$ será llamada $\Sigma$-efectivamente computable si hay un procedimiento efectivo $\mathbb{P}$ tal que

&#40;1&#41; El conjunto de datos de entrada de $\mathbb{P}$ es $\omega^n \times \Sigma^{\ast m}$

&#40;2&#41; El conjunto de datos de salida está contenido en $\Sigma^\ast$.

&#40;3&#41; Si $(\overrightarrow{x}, \overrightarrow{\alpha}) \in D_f$, entonces $\mathbb{P}$ se detiene partiendo de $(\overrightarrow{x}, \overrightarrow{\alpha})$, dando como dato de salida $f(\overrightarrow{x}, \overrightarrow{\alpha})$.

&#40;4&#41; Si $(\overrightarrow{x}, \overrightarrow{\alpha}) \in (\omega^n \times \Sigma^{\ast m}) - D_f$, entonces $\mathbb{P}$ no se detiene partiendo desde $(\overrightarrow{x}, \overrightarrow{\alpha})$

Cuando un procedimiento $\mathbb{P}$ cumpla los ítems (1), (2), (3) y (4) de arriba diremos que $\mathbb{P}$ computa a la función $f$ o que $f$ es computada por $\mathbb{P}$.

Veamos algunos ejemplos:

**(E1)** La función $\lambda xy[x+y]$ es $\Sigma$-efectivamente computable, cualquiera sea el alfabeto $\Sigma$ ya que el procedimiento enseñado en la escuela primaria para sumar números en notación decimal es efectivo y computa esta función.

**(E2)** La función $C_3^{1,2}$ es $\Sigma$-efectivamente computable ya que el siguiente procedimiento $\mathbb{P}$ con conjunto de datos de entrada $\omega \times \Sigma^{\ast 2}$ la computa:

- Independientemente de quién sea el dato de entrada $(x_1, \alpha_1, \alpha_2)$, detenerse dando como salida el número 3

**(E3)** La función $p_3^{2,3}$ es $\Sigma$-efectivamente computable ya que el siguiente procedimiento con conjunto de datos de entrada $\omega^2 \times \Sigma^{\ast 3}$ la computa:

- Dado el dato de entrada $(x_1, x_2, \alpha_1, \alpha_2, \alpha_3)$, detenerse y dar como salida la palabra $\alpha_1$

**(E4)** $Pred$ es $\Sigma$-efectivamente computable. Para realizar el procedimiento efectivo que compute a $Pred$ necesitaremos el procedimiento de la escuela primaria que dado un número no nulo $x$, expresado en notación decimal, calcula el número $x - 1$, en notación decimal. Llamemos $\mathbb{P}_{-1}$ a dicho procedimiento. El siguiente procedimiento (con conjunto de datos de entrada igual a $\omega$) computa a $Pred$:

Dado como dato de entrada un elemento $x \in \omega$, realizar lo siguiente:

Etapa 1

Si $x = 0$, entonces ir a Etapa 3, en caso contrario ir a Etapa 2.

Etapa 2

Correr $\mathbb{P}_{-1}$ con dato de entrada $x$ obteniendo $y$ como dato de salida. Detenerse y dar $y$ como dato de salida.

Etapa 3

Si $x = 0$, entonces ir a Etapa 1.

Como puede notarse el procedimiento anterior es efectivo ya que como todos sabemos, los sucesivos pasos efectuados al correr $\mathbb{P}_{-1}$ en la Etapa 2 son todos simples y efectivamente realizables. Por supuesto si uno quisiera ser más prolijo, debería reemplazar la Etapa 2 por las distintas instrucciones de $\mathbb{P}_{-1}$, referidas a $x$.

**(E5)** El predicado $\lambda xy[x < y]$ es $\Sigma$-efectivamente computable cualquiera sea el alfabeto $\Sigma$. Describiremos con palabras un procedimiento $\mathbb{P}_{<}$ que computa a $\lambda xy[x < y]$. Su conjunto de datos de entrada es $\omega^2$. Dado un par $(x, y) \in \omega^2$, el procedimiento primero compara las longitudes de las palabras que en notación decimal representan a $x$ y $y$. Por supuesto esto lo hace borrando de a un símbolo y viendo si alguna se termina primero. Si resultan de distinta longitud, es fácil darse cuenta cómo sigue. En caso de que las palabras resulten de igual longitud, entonces se hace el procedimiento clásico de ir comparando dígitos de izquierda a derecha.

**(E6)** Veamos que la función $\lambda\alpha[|\alpha|]$ es $\Sigma$-efectivamente computable. Como en los lenguajes de programación, usaremos variables y asignaciones para diseñar el procedimiento. Además llamemos $\mathbb{P}_{+1}$ al procedimiento de la escuela primaria que dado un número no nulo $x$, expresado en notación decimal, calcula el número $x + 1$, en notación decimal. Sea $\mathbb{P}_{||}$ el siguiente procedimiento.

Dado como dato de entrada un elemento $\alpha \in \Sigma^\ast$, realizar lo siguiente:

Etapa 1: Hacer las siguientes asignaciones

$$
\begin{aligned}
A &\leftarrow \alpha\\
B &\leftarrow 0
\end{aligned}
$$

e ir a Etapa 2.

Etapa 2: Si $A$ no es $\varepsilon$, ir a Etapa 3. En caso contrario detenerse y dar como salida $B$.

Etapa 3: Correr $\mathbb{P}_{+1}$ con dato de entrada igual al contenido de $B$, obteniendo $y$ como salida. Hacer las siguientes asignaciones

$$
\begin{aligned}
A &\leftarrow \text{resultado de remover el 1er símbolo de } A\\
B &\leftarrow y
\end{aligned}
$$

e ir a Etapa 2.

**Ejercicio 1:** Convénzase que el uso de asignaciones puede realizarse usando solo lápiz y papel. Imagine cómo lo haría en el caso anterior y corrobore que dicho procedimiento es efectivo y además computa a $\lambda\alpha[|\alpha|]$.

**Ejercicio 2:** Use los procedimientos $\mathbb{P}_{<}$ y $\mathbb{P}_{||}$ de los dos ejemplos anteriores para diseñar usando asignaciones un procedimiento que compute a la función $\lambda i\alpha[[\alpha]_i]$

Un último ejemplo:

**(E7)** Si $\le$ es el orden total sobre $\Sigma = \{\text{▲}, \%\}$ dado por $\text{▲} < \%$, entonces veremos que la función $s^{\le}$ es $\Sigma$-efectivamente computable. En un par de ejercicios de la Guía 2 vimos que cualquiera sea $\alpha \in \Sigma^\ast$, se cumple

$$
\begin{aligned}
s^{\le}(\varepsilon) &= \text{▲}\\
s^{\le}(\alpha\text{▲}) &= \alpha\%\\
s^{\le}(\alpha\%) &= s^{\le}(\alpha)\text{▲}
\end{aligned}
$$

y que estas ecuaciones permiten calcular el valor de $s^{\le}$. Usaremos esta idea para dar un procedimiento efectivo (con conjunto de datos de entrada igual a $\Sigma^\ast$) que compute a $s^{\le}$. Como en los lenguajes de programación, usaremos variables y asignaciones para diseñar el procedimiento.

Etapa 1: Dado el dato de entrada $\alpha \in \Sigma^\ast$, hacer las siguientes asignaciones

$$
\begin{aligned}
A &\leftarrow \alpha\\
B &\leftarrow \varepsilon\\
F &\leftarrow \text{▲}
\end{aligned}
$$

e ir a Etapa 2.

Etapa 2: Si $A$ comienza con $\text{▲}$, entonces hacer las siguientes asignaciones

$$
\begin{aligned}
A &\leftarrow \text{resultado de remover el 1er símbolo de } A\\
F &\leftarrow B\%\\
B &\leftarrow B\text{▲}
\end{aligned}
$$

e ir a la Etapa 2. En caso contrario ir a la Etapa 3.

Etapa 3: Si $A$ comienza con $\%$, entonces hacer las siguientes asignaciones

$$
\begin{aligned}
A &\leftarrow \text{resultado de remover el 1er símbolo de } A\\
F &\leftarrow F\text{▲}\\
B &\leftarrow B\%
\end{aligned}
$$

e ir a la Etapa 2. En caso contrario ir a la Etapa 4.

Etapa 4: Dar como salida $F$

Observación: Nótese que la definición de función $\Sigma$-efectivamente computable para el caso $f = \emptyset$ tiene a priori cierta ambigüedad ya que cualesquiera sean $n, m \in \omega$ y $O \in \{\omega, \Sigma^\ast\}$ tenemos que $\emptyset : \emptyset \subseteq \omega^n \times \Sigma^{\ast m} \to O$ ya que $D_\emptyset = \emptyset$ y $I_\emptyset = \emptyset$. De todas maneras, cualesquiera sean los $n, m$ y $O$ elegidos, siempre hay un procedimiento efectivo que computa a $f = \emptyset$, i.e. un procedimiento que nunca se detiene, cualesquiera sea el dato de entrada de $\omega^n \times \Sigma^{\ast m}$. Es decir que la función $\emptyset$ es $\Sigma$-efectivamente computable cualesquiera sea el alfabeto $\Sigma$. Cabe destacar que para el caso de una función $f \ne \emptyset$, nuestra definición es inambigua ya que hay únicos $n, m \in \omega$ y $O \in \{\omega, \Sigma^\ast\}$ tales que $f : D_f \subseteq \omega^n \times \Sigma^{\ast m} \to O$.

**Ejercicio 3:** Sea $\mathbb{P}_{+}$ un procedimiento efectivo que compute a la función $\lambda xy[x+y]$. Basado en $\mathbb{P}_{+}$ diseñe un procedimiento efectivo que compute a $\lambda xy[x.y]$

**Ejercicio 4:** Sea $\le$ es el orden total sobre $\Sigma = \{\text{▲}, \%\}$ dado por $\text{▲} < \%$. Usando que $s^{\le}$ es $\Sigma$-efectivamente computable diseñe un procedimiento efectivo que compute a $\ast^{\le} : \omega \to \Sigma^\ast$

**Ejercicio 5:** Sea $\Sigma = \{\text{▲}, \%\}$ y sea $f : D_f \subseteq \omega \times \omega \times \Sigma^\ast \to \omega$ dada por:

$$
\begin{aligned}
D_f &= \{(0, 1, \varepsilon), (55, 54, \text{▲\%▲\%▲}), (1, 1, \text{▲▲})\}\\
f(0, 1, \varepsilon) &= 1\\
f(55, 54, \text{▲\%▲\%▲}) &= 2\\
f(1, 1, \text{▲▲}) &= 3
\end{aligned}
$$

Pruebe que $f$ es $\Sigma$-efectivamente computable.

Nota Importante: en lo que sigue muchas veces nos permitiremos trabajar con procedimientos que son efectivos en términos de otros que ya se han dado, es decir daremos procedimientos que en principio no es claro que sean efectivos pero los cuales se volverían efectivos si reemplazáramos ciertas instrucciones por la manera efectiva de simularlas. Para hacer más dinámico el discurso no distinguiremos entre este tipo de procedimientos (efectivizables) y los efectivos propiamente dichos.

**Ejercicio 6:** De un procedimiento efectivo (efectivizable) que compute la función $\lambda ix[(x)_i]$

**Ejercicio 7:** Sean

$$
\begin{aligned}
f &: D_f \subseteq \omega \times \omega \times \Sigma^\ast \to \omega\\
f_1 &: D_{f_1} \subseteq \omega \times \Sigma^\ast \to \omega\\
f_2 &: D_{f_2} \subseteq \omega \times \Sigma^\ast \to \omega\\
f_3 &: D_{f_3} \subseteq \omega \times \Sigma^\ast \to \Sigma^\ast
\end{aligned}
$$

**(a)** Es verdad que $D_{f \circ [f_1, f_2, f_3]} = D_{f_1} \cap D_{f_2} \cap D_{f_3}$?

**(b)** De una descripción del dominio de $f \circ [f_1, f_2, f_3]$.

**(c)** Si $f, f_1, f_2, f_3$ son $\Sigma$-efectivamente computables, entonces $f \circ [f_1, f_2, f_3]$ lo es.

**Ejercicio 8:** V o F o I. Justifique

**(a)** Si $\mathbb{P}$ es un procedimiento efectivo que computa una función no vacía $f : D_f \subseteq \omega \to \omega$ entonces el conjunto de datos de salida de $\mathbb{P}$ es $\omega$

**(b)** Si $\mathbb{P}$ y $\mathbb{Q}$ son procedimientos efectivos, entonces $\mathbb{P}\mathbb{Q}$ lo es.

**(c)** Denotemos con $e$ a la cantidad de veces que estornudó Alan Turing a lo largo de su vida. Sea $f : \omega \to \omega$, dada por $f(x) = x^e$. Entonces $f$ es $\emptyset$-efectivamente computable.

**(d)** Si $f$ y $g$ son $\Sigma$-efectivamente computables entonces $f.g$ lo es

**Ejercicio 9:** Si $f : D_f \subseteq \omega \times \omega \times \{@, \text{↑}\}^\ast \to \omega$ es tal que $D_f$ es finito, entonces $f$ es $\{@, \text{↑}\}$-efectivamente computable

**Ejercicio 10:** Sean $f : D_f \subseteq \omega \times \Sigma^\ast \to \omega$ y $g : D_g \subseteq \omega \times \Sigma^\ast \to \omega$ funciones $\Sigma$-efectivamente computables tales que $D_f \cap D_g = \emptyset$. Sea $F : D_f \cup D_g \to \omega$ dada por

$$
e \mapsto
\begin{cases}
f(e) & \text{si } e \in D_f\\
g(e) & \text{si } e \in D_g
\end{cases}
$$

Pruebe que $F$ es $\Sigma$-efectivamente computable.

## Conjuntos $\Sigma$-efectivamente computables

Sea $X$ un conjunto cualquiera y sea $S \subseteq X$. Usaremos $\chi_S^X$ para denotar la función

$$
\begin{aligned}
\chi_S^X : X &\to \omega\\
x &\mapsto
\begin{cases}
1 & \text{si } x \in S\\
0 & \text{si } x \notin S
\end{cases}
\end{aligned}
$$

Llamaremos a $\chi_S^X$ la función característica de $S$ con respecto a $X$.

Un conjunto $S \subseteq \omega^n \times \Sigma^{\ast m}$ será llamado $\Sigma$-efectivamente computable cuando la función $\chi_S^{\omega^n \times \Sigma^{\ast m}}$ sea $\Sigma$-efectivamente computable. O sea $S$ es $\Sigma$-efectivamente computable sii hay un procedimiento efectivo $\mathbb{P}$, el cual computa $\chi_S^{\omega^n \times \Sigma^{\ast m}}$, es decir:

- El conjunto de datos de entrada de $\mathbb{P}$ es $\omega^n \times \Sigma^{\ast m}$, siempre termina y da como dato de salida un elemento de $\{0, 1\}$.
- Dado $(\overrightarrow{x}, \overrightarrow{\alpha}) \in \omega^n \times \Sigma^{\ast m}$, $\mathbb{P}$ da como salida al número 1 si $(\overrightarrow{x}, \overrightarrow{\alpha}) \in S$ y al número 0 si $(\overrightarrow{x}, \overrightarrow{\alpha}) \notin S$.

Nótese que la definición de conjunto $\Sigma$-efectivamente computable, para el caso $S = \emptyset$, tiene a priori cierta ambigüedad ya que cualesquiera sean $n, m \in \omega$ tenemos que $\emptyset \subseteq \omega^n \times \Sigma^{\ast m}$. De todas maneras, cualesquiera sean los $n, m$ elegidos, siempre hay un procedimiento efectivo que computa a $\chi_\emptyset^{\omega^n \times \Sigma^{\ast m}}$, i.e. un procedimiento que siempre da como salida 0, cualesquiera sea el dato de entrada de $\omega^n \times \Sigma^{\ast m}$. Es decir que el conjunto $\emptyset$ es $\Sigma$-efectivamente computable cualesquiera sea el alfabeto $\Sigma$. Cabe destacar que para el caso de un conjunto $S \ne \emptyset$, nuestra definición es inambigua ya que hay únicos $n, m \in \omega$ tales que $S \subseteq \omega^n \times \Sigma^{\ast m}$.

Si $\mathbb{P}$ es un procedimiento efectivo el cual computa a $\chi_S^{\omega^n \times \Sigma^{\ast m}}$, diremos que $\mathbb{P}$ decide la pertenencia a $S$, con respecto al conjunto $\omega^n \times \Sigma^{\ast m}$.

**Ejercicio 11:** $\omega^3 \times \Sigma^{\ast 2}$ es $\Sigma$-efectivamente computable

**Ejercicio 12:** Sea $\Sigma = \{\text{▲}, \%\}$ y sea

$$
S = \{(0, 1, \varepsilon), (55, 54, \text{▲\%▲\%▲}), (1, 1, \text{▲▲})\}
$$

Pruebe que $S$ es $\Sigma$-efectivamente computable.

**Ejercicio 13:** Convénzase que todo conjunto finito $S \subseteq \omega^n \times \Sigma^{\ast m}$ es $\Sigma$-efectivamente computable.

**Ejercicio 14:** $\{(x, \alpha) \in \omega \times \Sigma^\ast : |\alpha|^x \text{ es par}\}$ es $\Sigma$-efectivamente computable

**Ejercicio 15:** Sean $S_1, S_2 \subseteq \omega^n \times \Sigma^{\ast m}$ conjuntos $\Sigma$-efectivamente computables. Entonces $S_1 \cup S_2$, $S_1 \cap S_2$ y $(\omega^n \times \Sigma^{\ast m}) - S_1$ son $\Sigma$-efectivamente computables.

**Ejercicio 16:** Sean $S \subseteq \omega$ y $L \subseteq \{@, \text{↑}\}^\ast$ tales que $(0, \varepsilon) \in S \times L$. Entonces $S$ y $L$ son ambos $\{@, \text{↑}\}$-efectivamente computables sii $S \times L$ es $\{@, \text{↑}\}$-efectivamente computable

## Conjuntos $\Sigma$-efectivamente enumerables

Supongamos que $k, l, n, m \in \omega$ y que $F : D_F \subseteq \omega^k \times \Sigma^{\ast l} \to \omega^n \times \Sigma^{\ast m}$. Supongamos además que $n + m \ge 1$. Entonces denotaremos con $F_{(i)}$ a la función $p_i^{n,m} \circ F$. Notar que

$$
F_{(i)} : D_F \subseteq \omega^k \times \Sigma^{\ast l} \to \omega, \text{ para cada } i = 1, \ldots, n
$$

$$
F_{(i)} : D_F \subseteq \omega^k \times \Sigma^{\ast l} \to \Sigma^\ast, \text{ para cada } i = n+1, \ldots, n+m
$$

Por lo cual cada una de las funciones $F_{(i)}$ son $\Sigma$-mixtas.

**Ejercicio 17:** Sea $F : \{(x, \alpha) \in \omega \times \Sigma^\ast : |\alpha|^x \text{ es par}\} \subseteq \omega \times \Sigma^\ast \to \omega^2 \times \Sigma^\ast$ dada por $F(x, \alpha) = (x, x^2 + |\alpha|, \varepsilon)$. Diga quiénes son $F_{(1)}$, $F_{(2)}$ y $F_{(3)}$. Qué función es $[F_{(1)}, F_{(2)}, F_{(3)}]$?

**Ejercicio 18:** En la definición anterior, para el caso $n + m = 1$, quién es $F_{(1)}$?

**Ejercicio 19:** Pruebe que si $F : D_F \subseteq \omega^k \times \Sigma^{\ast l} \to \omega^n \times \Sigma^{\ast m}$, con $k, l, n, m \in \omega$, entonces $F = [F_{(1)}, \ldots, F_{(n+m)}]$

Un conjunto $S \subseteq \omega^n \times \Sigma^{\ast m}$ será llamado $\Sigma$-efectivamente enumerable cuando sea vacío o haya una función $F : \omega \to \omega^n \times \Sigma^{\ast m}$ tal que $I_F = S$ y $F_{(i)}$ sea $\Sigma$-efectivamente computable, para cada $i \in \{1, \ldots, n+m\}$.

Observación: Nótese que para el caso $n = m = 0$, la condición anterior de que $F_{(i)}$ sea $\Sigma$-efectivamente computable, para cada $i \in \{1, \ldots, n+m\}$ se cumple vacuamente y por lo tanto la definición anterior nos dice que un conjunto $S \subseteq \omega^0 \times \Sigma^{\ast 0} = \{\diamond\}$ será $\Sigma$-efectivamente enumerable sii es vacío o hay una función $F : \omega \to \{\diamond\}$, tal que $I_F = S$. Por supuesto, esto nos dice que $\emptyset$ y $\{\diamond\}$ son $\Sigma$-efectivamente enumerables.

Para entender mejor la idea de esta definición consideremos el siguiente resultado.

**Lema 1.** Un conjunto no vacío $S \subseteq \omega^n \times \Sigma^{\ast m}$ es $\Sigma$-efectivamente enumerable sii hay un procedimiento efectivo $\mathbb{P}$ tal que

&#40;1&#41; El conjunto de datos de entrada de $\mathbb{P}$ es $\omega$

&#40;2&#41; $\mathbb{P}$ se detiene para cada $x \in \omega$

&#40;3&#41; El conjunto de datos de salida de $\mathbb{P}$ es igual a $S$. (Es decir, siempre que $\mathbb{P}$ se detiene, da como salida un elemento de $S$, y para cada elemento $(\overrightarrow{x}, \overrightarrow{\alpha}) \in S$, hay un $x \in \omega$ tal que $\mathbb{P}$ da como salida a $(\overrightarrow{x}, \overrightarrow{\alpha})$ cuando lo corremos con $x$ como dato de entrada)

**Ejercicio 20:** Pruebe el lema anterior. (Hacer el caso $n = 1, m = 2$).

Cuando un procedimiento $\mathbb{P}$ cumpla (1), (2) y (3) del lema anterior, diremos que $\mathbb{P}$ enumera a $S$. O sea que $S$ es $\Sigma$-efectivamente enumerable sii es vacío o hay un procedimiento efectivo el cual enumera a $S$.

Dicho de otra forma un conjunto no vacío $S$ es $\Sigma$-efectivamente enumerable sii hay un procedimiento efectivo $\mathbb{P}$ el cual tiene conjunto de datos de entrada $\omega$ y además para los sucesivos datos de entrada $0, 1, 2, 3, \ldots$, el procedimiento $\mathbb{P}$ produce respectivamente los datos de salida $e_0, e_1, e_2, e_3, \ldots$ de manera que $S = \{e_0, e_1, e_2, \ldots\}$. Cabe destacar aquí que puede suceder que $e_i = e_j$, para ciertos $i, j$, con $i \ne j$.

Algunos ejemplos:

**(E1)** Un procedimiento efectivo que enumera $\omega \times \omega$ es el siguiente:

Etapa 1

Si $x = 0$, dar como salida el par $(0, 0)$ y terminar. Si $x \ne 0$, calcular $x_1 = (x)_1$ y $x_2 = (x)_2$.

Etapa 2

Dar como dato de salida el par $(x_1, x_2)$ y terminar

Como puede notarse el procedimiento es efectivo (efectivizable) y además el conjunto de datos de salida es $\omega \times \omega$ ya que si tomamos un par cualquiera $(a, b) \in \omega \times \omega$, el procedimiento lo dará como dato de salida para la entrada $x = 2^a3^b$.

**(E2)** Veamos que $\omega^2 \times \Sigma^{\ast 3}$ es $\Sigma$-efectivamente enumerable cualquiera sea el alfabeto no vacío $\Sigma$. Sea $\le$ un orden total para el alfabeto $\Sigma$. Utilizando el orden $\le$ podemos diseñar el siguiente procedimiento para enumerar $\omega^2 \times \Sigma^{\ast 3}$:

Etapa 1

Si $x = 0$, dar como salida $(0, 0, \varepsilon, \varepsilon, \varepsilon)$ y terminar. Si $x \ne 0$, calcular

$$
\begin{aligned}
x_1 &= (x)_1\\
x_2 &= (x)_2\\
\alpha_1 &= \ast^{\le}((x)_3)\\
\alpha_2 &= \ast^{\le}((x)_4)\\
\alpha_3 &= \ast^{\le}((x)_5)
\end{aligned}
$$

Etapa 2

Dar como dato de salida la 5-upla $(x_1, x_2, \alpha_1, \alpha_2, \alpha_3)$.

**Ejercicio 21:** Explique por qué es efectivo el procedimiento de (E2)

**Ejercicio 22:** Pruebe que el procedimiento de (E2) tiene conjunto de datos de salida igual a $\omega^2 \times \Sigma^{\ast 3}$.

**Ejercicio 23:** Sea $S = \{(x, \text{↑}^x) : x \text{ es par}\}$. Pruebe que $S$ es $\{@, \text{↑}\}$-efectivamente enumerable.

**Ejercicio 24:** Sea $S = \{(x, \alpha) \in \omega \times \{@, \text{↑}\}^\ast : \alpha \text{ tiene exactamente } x \text{ ocurrencias de } @\}$. Pruebe que $S$ es $\{@, \text{↑}\}$-efectivamente enumerable.

**Ejercicio 25:** Sean $S_1, S_2 \subseteq \omega^n \times \Sigma^{\ast m}$ conjuntos $\Sigma$-efectivamente enumerables. Entonces $S_1 \cup S_2$ es $\Sigma$-efectivamente enumerable

**Ejercicio 26:** Sean $S_1, S_2 \subseteq \omega^n \times \Sigma^{\ast m}$ conjuntos $\Sigma$-efectivamente enumerables. Entonces $S_1 \cap S_2$ es $\Sigma$-efectivamente enumerable. (En el apunte está probado en forma de lema.)

**Ejercicio 27:** (Explicado en video en granlogico.com) Si $\mathbb{P}$ es un procedimiento efectivo cuyo conjunto de datos de entrada es $\omega \times \Sigma^\ast$ entonces el conjunto

$$
\{(x, \alpha) \in \omega \times \Sigma^\ast : \mathbb{P} \text{ termina partiendo de } (x, \alpha)\}
$$

es $\Sigma$-efectivamente enumerable. Saque como conclusión que el dominio de una función $\Sigma$-efectivamente computable es $\Sigma$-efectivamente enumerable.

**Lema 2.** Si $S \subseteq \omega^n \times \Sigma^{\ast m}$ es $\Sigma$-efectivamente computable entonces $S$ es $\Sigma$-efectivamente enumerable.

Proof. Supongamos $S \ne \emptyset$. Sea $(\overrightarrow{z}, \overrightarrow{\gamma}) \in S$, fijo. Sea $\mathbb{P}$ un procedimiento efectivo que compute a $\chi_S^{\omega^n \times \Sigma^{\ast m}}$. Ya vimos en el ejemplo anterior que $\omega^2 \times \Sigma^{\ast 3}$ es $\Sigma$-efectivamente enumerable. En forma similar se puede ver que $\omega^n \times \Sigma^{\ast m}$ lo es. Sea $\mathbb{P}_1$ un procedimiento efectivo que enumere a $\omega^n \times \Sigma^{\ast m}$. Entonces el siguiente procedimiento enumera a $S$:

Dato de entrada: $x \in \omega$

Etapa 1

Realizar $\mathbb{P}_1$ con $x$ de entrada para obtener como salida un $(\overrightarrow{x}, \overrightarrow{\alpha}) \in \omega^n \times \Sigma^{\ast m}$.

Etapa 2

Realizar $\mathbb{P}$ con $(\overrightarrow{x}, \overrightarrow{\alpha})$ de entrada para obtener el valor Booleano $e$ de salida.

Etapa 3

Si $e = 1$ dar como dato de salida $(\overrightarrow{x}, \overrightarrow{\alpha})$. Si $e = 0$ dar como dato de salida $(\overrightarrow{z}, \overrightarrow{\gamma})$. $\blacksquare$

Como veremos más adelante en la Guía 9, hay conjuntos que son $\Sigma$-efectivamente enumerables y no $\Sigma$-efectivamente computables. Sin embargo tenemos el siguiente interesante resultado:

**Teorema 3.** Sea $S \subseteq \omega^n \times \Sigma^{\ast m}$. Son equivalentes

**(a)** $S$ es $\Sigma$-efectivamente computable

**(b)** $S$ y $(\omega^n \times \Sigma^{\ast m}) - S$ son $\Sigma$-efectivamente enumerables

Proof. $(a)\Rightarrow(b)$. Por el lema anterior tenemos que $S$ es $\Sigma$-efectivamente enumerable. Nótese además que, dado que $S$ es $\Sigma$-efectivamente computable, $(\omega^n \times \Sigma^{\ast m}) - S$ también lo es (por qué?). Es decir que aplicando nuevamente el lema anterior tenemos que $(\omega^n \times \Sigma^{\ast m}) - S$ es $\Sigma$-efectivamente enumerable.

$(b)\Rightarrow(a)$. Si $S = \emptyset$ o $S = \omega^n \times \Sigma^{\ast m}$ es claro que se cumple (a). O sea que podemos suponer que ni $S$ ni $(\omega^n \times \Sigma^{\ast m}) - S$ son igual al conjunto vacío. Sea $\mathbb{P}_1$ un procedimiento efectivo que enumere a $S$ y sea $\mathbb{P}_2$ un procedimiento efectivo que enumere a $(\omega^n \times \Sigma^{\ast m}) - S$. Es fácil ver que el siguiente procedimiento computa el predicado $\chi_S^{\omega^n \times \Sigma^{\ast m}}$:

Dato de entrada: $(\overrightarrow{x}, \overrightarrow{\alpha}) \in \omega^n \times \Sigma^{\ast m}$

Etapa 1

Darle a la variable $T$ el valor 0.

Etapa 2

Realizar $\mathbb{P}_1$ con el valor de $T$ como entrada para obtener de salida la upla $(\overrightarrow{y}, \overrightarrow{\beta})$.

Etapa 3

Realizar $\mathbb{P}_2$ con el valor de $T$ como entrada para obtener de salida la upla $(\overrightarrow{z}, \overrightarrow{\gamma})$.

Etapa 4

Si $(\overrightarrow{y}, \overrightarrow{\beta}) = (\overrightarrow{x}, \overrightarrow{\alpha})$, entonces detenerse y dar como dato de salida el valor 1. Si $(\overrightarrow{z}, \overrightarrow{\gamma}) = (\overrightarrow{x}, \overrightarrow{\alpha})$, entonces detenerse y dar como dato de salida el valor 0. Si no suceden ninguna de las dos posibilidades antes mencionadas, aumentar en 1 el valor de la variable $T$ y dirigirse a la Etapa 2. $\blacksquare$

**Ejercicio 28:** Sea $\Sigma = \{@, !, \%\}$. Si $f : S \subseteq \omega \times \omega \times \Sigma^\ast \to \omega$ es $\Sigma$-efectivamente computable, entonces $\operatorname{Im}(f)$ es $\Sigma$-efectivamente enumerable

**Ejercicio 29:** Sea $\Sigma = \{@, !, \%\}$. Supongamos $f : S \subseteq \omega \times \Sigma^\ast \to \Sigma^\ast$ es $\Sigma$-efectivamente computable. Suponga además que $(1, @@) \in S$ y $f(1, @@) = @!!$. Pruebe que el conjunto

$$
\{(x, \alpha) \in S : f(x, \alpha) = @!!\}
$$

es $\Sigma$-efectivamente enumerable.

**Ejercicio 30:** Sea $\Sigma = \{@, \&\}$. Supongamos $f : S \subseteq \omega \times \omega \to \omega$ es $\Sigma$-efectivamente computable. Suponga además que $(0, 0) \in S$ y $f(0, 0) = 0$. Pruebe que el conjunto

$$
\{(x, y) \in S : (f(x, y), y) \in S \text{ y } f(f(x, y), y) = 0\}
$$

es $\Sigma$-efectivamente enumerable.

**Ejercicio 31:** (Explicado en video en granlogico.com) Si $f : S \subseteq \omega \to \omega$ es $\Sigma$-efectivamente computable, entonces el conjunto

$$
\{x \in S : x \text{ es par } x/2 \in S \text{ y } f(x) = f(x/2)\}
$$

es $\Sigma$-efectivamente enumerable.

**Ejercicio 32:** Si $f : S \subseteq \omega \to \omega$ es $\Sigma$-efectivamente computable, entonces el conjunto

$$
\{x \in S : x^2 \in S \text{ y } f(x) = f(x^2)\}
$$

es $\Sigma$-efectivamente enumerable.

**Ejercicio 33:** Sea $\Sigma = \{@, !, \%\}$. Supongamos $L_1, L_2 \subseteq \Sigma^\ast$ son $\Sigma$-efectivamente enumerables. Entonces

$$
\{\alpha \in L_1 : \text{hay un } \beta \in L_2 \text{ tal que } |\beta| = |\alpha|\}
$$

es $\Sigma$-efectivamente enumerable.

**Ejercicio 34:** Sean $S \subseteq \omega$ y $L \subseteq \{@, \text{↑}\}^\ast$ tales que $(0, \varepsilon) \in S \times L$. Entonces $S \times L$ es $\{@, \text{↑}\}$-efectivamente enumerable si y solo si ambos $S$ y $L$ son $\{@, \text{↑}\}$-efectivamente enumerables

**Ejercicio 35:** Sea $f : S \subseteq \Sigma^\ast \to \Sigma^\ast$ una función $\Sigma$-efectivamente computable. Supongamos que $\varepsilon \in S$ y que $f(\varepsilon) = \varepsilon$. Sea

$$
L = \{\alpha \in S : f(\alpha) \in S \text{ y } f(f(\alpha)) = \alpha\}
$$

Notar que $\varepsilon \in L$. Pruebe que $L$ es $\Sigma$-efectivamente enumerable

**Ejercicio 36:** V o F o I. Justifique

**(a)** Denotemos con $e$ a la cantidad de veces que estornudó Alan Turing a lo largo de su vida. Sea $S = \{e\}$. Entonces $S$ es un conjunto $\emptyset$-efectivamente computable

**(b)** $(2, 4, 6, 8, 10, \ldots)$ es $\Sigma$-efectivamente enumerable

**(c)** Si $\mathbb{P}$ es un procedimiento efectivo, entonces $I_\mathbb{P}$ es $\Sigma$-efectivamente enumerable

**(d)** Sea $S \subseteq \omega$ y supongamos $\mathbb{P}$ es un procedimiento efectivo el cual enumera a $S$. Entonces el siguiente procedimiento (con dato de entrada $x \in \omega$) enumera a $\{u \in S : u \text{ es par}\}$:

**(i)** Etapa 1: Guardar en la variable $X$ el valor $x$.

**(ii)** Etapa 2: Correr $\mathbb{P}$ con dato de entrada $X$ y guardar en la variable $E$ el dato de salida dado por $\mathbb{P}$

**(iii)** Etapa 3: Si $E$ es par, dar como salida $E$ y detenerse. Caso contrario aumentar en 1 el valor de $X$ e ir a Etapa 2

## Ejercicios de examen

No se puede usar que el dominio (o la imagen) de una función $\Sigma$-efectivamente computable es $\Sigma$-efectivamente enumerable. Los procedimientos efectivos pueden ser escritos en forma "efectivizable", por ejemplo puede usar las funciones $\#^{\le}$, $\ast^{\le}$, $\lambda ix[(x)_i]$, $\lambda xy[x \le y]$, $\lambda\alpha[|\alpha|]$, $\lambda xy[x = y]$, $\lambda\alpha\beta[\alpha = \beta]$, $\lambda xy[x+y]$, $\lambda xy[x.y]$, $\lambda xy[x \mathbin{\dot{-}} y]$, $\lambda x\alpha[\alpha^x]$, $\lambda xy[x^y]$, etc sin explicar en su procedimiento cómo haría para calcularlas en forma efectiva.

&#40;1&#41; Sean

$$
\begin{aligned}
f &: D_f \subseteq \omega \times \omega \times \Sigma^\ast \to \omega\\
f_1 &: D_{f_1} \subseteq \omega \times \Sigma^\ast \to \omega\\
f_2 &: D_{f_2} \subseteq \omega \times \Sigma^\ast \to \omega\\
f_3 &: D_{f_3} \subseteq \omega \times \Sigma^\ast \to \Sigma^\ast
\end{aligned}
$$

&#40;a&#41; Es verdad que $D_{f \circ [f_1, f_2, f_3]} = D_{f_1} \cap D_{f_2} \cap D_{f_3}$?

&#40;b&#41; De una descripción del dominio de $f \circ [f_1, f_2, f_3]$.

&#40;c&#41; Si $f, f_1, f_2, f_3$ son $\Sigma$-efectivamente computables, entonces $f \circ [f_1, f_2, f_3]$ lo es.

&#40;2&#41; Sean

$$
\begin{aligned}
f &: D_f \subseteq \omega \times \Sigma^\ast \to \omega\\
f_1 &: D_{f_1} \subseteq \omega \to \omega\\
f_2 &: D_{f_2} \subseteq \omega \to \Sigma^\ast
\end{aligned}
$$

&#40;a&#41; Es verdad que $D_{f \circ [f_1, f_2]} = D_{f_1} \cap D_{f_2}$?

&#40;b&#41; De una descripción del dominio de $f \circ [f_1, f_2]$.

&#40;c&#41; Si $f, f_1, f_2$ son $\Sigma$-efectivamente computables, entonces $f \circ [f_1, f_2]$ lo es.

&#40;3&#41; Sean

$$
\begin{aligned}
f &: D_f \subseteq \omega \times \omega \times \Sigma^\ast \to \omega\\
f_1 &: D_{f_1} \subseteq \Sigma^\ast \to \omega\\
f_2 &: D_{f_2} \subseteq \Sigma^\ast \to \omega\\
f_3 &: D_{f_3} \subseteq \Sigma^\ast \to \Sigma^\ast
\end{aligned}
$$

&#40;a&#41; Es verdad que $D_{f \circ [f_1, f_2, f_3]} = D_{f_1} \cap D_{f_2} \cap D_{f_3}$?

&#40;b&#41; De una descripción del dominio de $f \circ [f_1, f_2, f_3]$.

&#40;c&#41; Si $f, f_1, f_2, f_3$ son $\Sigma$-efectivamente computables, entonces $f \circ [f_1, f_2, f_3]$ lo es.

&#40;4&#41; Sean

$$
\begin{aligned}
f &: D_f \subseteq \omega \times \omega \to \omega\\
f_1 &: D_{f_1} \subseteq \omega \times \omega \times \Sigma^\ast \times \Sigma^\ast \to \omega\\
f_2 &: D_{f_2} \subseteq \omega \times \omega \times \Sigma^\ast \times \Sigma^\ast \to \omega
\end{aligned}
$$

&#40;a&#41; Es verdad que $D_{f \circ [f_1, f_2]} = D_{f_1} \cap D_{f_2}$?

&#40;b&#41; De una descripción del dominio de $f \circ [f_1, f_2]$.

&#40;c&#41; Si $f, f_1, f_2$ son $\Sigma$-efectivamente computables, entonces $f \circ [f_1, f_2]$ lo es.

&#40;5&#41; Sea $\Sigma = \{@, !, \%\}$. Supongamos $f : L_1 \to L_2$, con $L_1, L_2 \subseteq \Sigma^\ast$, es $\Sigma$-efectivamente computable y biyectiva.

&#40;a&#41; Defina (dando dominio, imagen y regla) la función $f^{-1}$.

&#40;b&#41; Pruebe que $f^{-1}$ es $\Sigma$-efectivamente computable.

&#40;6&#41; Sea $\Sigma = \{@, !, \%\}$. Supongamos $S_1 \subseteq \omega \times \Sigma^\ast$ y $S_2 \subseteq \omega$. Supongamos además que $f : S_1 \to S_2$ es $\Sigma$-efectivamente computable y biyectiva.

&#40;a&#41; Defina (dando dominio, imagen y regla) la función $f^{-1}$.

&#40;b&#41; Sean $g_1 : S_2 \to \omega$ y $g_2 : S_2 \to \Sigma^\ast$ funciones tales que $f^{-1} = [g_1, g_2]$. Pruebe que $g_1$ y $g_2$ son $\Sigma$-efectivamente computables.

&#40;7&#41; Sea $\Sigma = \{@, !, \%\}$. Supongamos $S \subseteq \omega \times \Sigma^\ast$ y $L \subseteq \Sigma^\ast$. Supongamos además que $f : S \to L$ es $\Sigma$-efectivamente computable y biyectiva.

&#40;a&#41; Defina (dando dominio, imagen y regla) la función $f^{-1}$.

&#40;b&#41; Sean $g_1 : L \to \omega$ y $g_2 : L \to \Sigma^\ast$ funciones tales que $f^{-1} = [g_1, g_2]$. Pruebe que $g_1$ y $g_2$ son $\Sigma$-efectivamente computables.

&#40;8&#41; Sea $\Sigma = \{@, !, \%\}$. Supongamos $S_1 \subseteq \omega$ y $S_2 \subseteq \omega \times \Sigma^\ast$. Supongamos además que $F : S_1 \to S_2$ es biyectiva.

&#40;a&#41; Defina (dando dominio, imagen y regla) la función $F^{-1}$.

&#40;b&#41; Pruebe que si $F_{(1)}$ y $F_{(2)}$ son $\Sigma$-efectivamente computables, entonces $F^{-1}$ es $\Sigma$-efectivamente computable.

&#40;9&#41; Un conjunto no vacío $S \subseteq \omega^n \times \Sigma^{\ast m}$ es $\Sigma$-efectivamente enumerable sii hay un procedimiento efectivo $\mathbb{P}$ tal que

&#40;a&#41; El conjunto de datos de entrada de $\mathbb{P}$ es $\omega$

&#40;b&#41; $\mathbb{P}$ se detiene para cada $x \in \omega$

&#40;b&#41; El conjunto de datos de salida de $\mathbb{P}$ es igual a $S$. (Es decir, siempre que $\mathbb{P}$ se detiene, da como salida un elemento de $S$, y para cada elemento $(\overrightarrow{x}, \overrightarrow{\alpha}) \in S$, hay un $x \in \omega$ tal que $\mathbb{P}$ da como salida a $(\overrightarrow{x}, \overrightarrow{\alpha})$ cuando lo corremos con $x$ como dato de entrada)

(Hacer el caso $n = 1, m = 2$).

&#40;10&#41; Sean $S_1, S_2 \subseteq \omega^n \times \Sigma^{\ast m}$ conjuntos $\Sigma$-efectivamente enumerables. Entonces $S_1 \cap S_2$ es $\Sigma$-efectivamente enumerable.

&#40;11&#41; Sea $\Sigma = \{@, !, \%\}$. Supongamos $f : S \subseteq \omega \times \omega \times \Sigma^\ast \to \omega$ es $\Sigma$-efectivamente computable. Suponga además que $(0, 0, \varepsilon) \in S$ y $f(0, 0, \varepsilon) = 0$. Pruebe que el conjunto

$$
\{(x, y, \alpha) \in S : f(x, y, \alpha) = 0\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;12&#41; Sea $\Sigma = \{@, \&\}$. Supongamos $f : S \subseteq \omega \times \omega \to \omega$ es $\Sigma$-efectivamente computable. Suponga además que $(0, 0) \in S$ y $f(0, 0) = 0$. Pruebe que el conjunto

$$
\{(x, y) \in S : f(x, y) = x\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;13&#41; Sea $\Sigma = \{@, \&\}$. Supongamos $f : L \subseteq \Sigma^\ast \times \Sigma^\ast \to \Sigma^\ast$ es $\Sigma$-efectivamente computable. Suponga además que $(@, \&) \in L$ y $f(@, \&) = @@@$. Pruebe que el conjunto

$$
\{(\alpha, \beta) \in L : f(\alpha, \beta) = \alpha\alpha\alpha\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;14&#41; Sea $\Sigma = \{@, \&\}$. Supongamos $f : S \subseteq \omega \times \omega \to \omega$ es $\Sigma$-efectivamente computable. Suponga además que $(0, 0) \in S$ y $f(0, 0) = 0$. Pruebe que el conjunto

$$
\{(x, y) \in S : (y, x) \in S \text{ y } f(x, y) = f(y, x)\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;15&#41; Sea $\Sigma = \{@, \&\}$. Supongamos $f : S \subseteq \omega \times \omega \to \omega$ es $\Sigma$-efectivamente computable. Suponga además que $(0, 0) \in S$ y $f(0, 0) = 0$. Pruebe que el conjunto

$$
\{(x, y) \in S : (f(x, y), y) \in S \text{ y } f(f(x, y), y) = 0\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;16&#41; Sea $\Sigma = \{@, \&\}$. Supongamos $f : S \subseteq \omega \times \omega \to \omega$ es $\Sigma$-efectivamente computable. Suponga además que $(0, 0) \in S$ y $f(0, 0) = 0$. Pruebe que el conjunto

$$
\{x \in \omega : \text{hay un } y\text{tal que } (x, y) \in S \text{ y } f(x, y) = 0\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;17&#41; Sea $\Sigma = \{@, \&\}$. Supongamos $f : S \subseteq \omega \times \omega \to \omega$ es $\Sigma$-efectivamente computable. Suponga además que $(0, 0) \in S$ y $f(0, 0) = 0$. Pruebe que el conjunto

$$
\{(x, x) : (x, x) \in S \text{ y } f(x, x) = x\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;18&#41; Sea $\Sigma = \{@, \&\}$. Supongamos $f : L \subseteq \Sigma^\ast \times \Sigma^\ast \to \Sigma^\ast$ es $\Sigma$-efectivamente computable. Suponga además que $(@, @) \in L$. Pruebe que el conjunto

$$
\{(\alpha, \beta) \in L : (\beta, \alpha) \in L \text{ y } f(\alpha, \beta) = f(\beta, \alpha)\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;19&#41; Sea $\Sigma = \{@, \&\}$. Sea $f : S \subseteq \Sigma^\ast \to \omega$ una función $\Sigma$-efectivamente computable. Supongamos que $\varepsilon \in S$ y que $f(\varepsilon) = 0$. Sea

$$
L = \{\alpha \in S : @^{f(\alpha)} \in S \text{ y } f(@^{f(\alpha)}) = 0\}
$$

Notar que $\varepsilon \in L$. Pruebe que $L$ es $\Sigma$-efectivamente enumerable

&#40;20&#41; Sea $\Sigma = \{@, !, \%\}$. Supongamos $f : S \subseteq \omega \times \omega \times \Sigma^\ast \to \omega$ es $\Sigma$-efectivamente computable. Suponga además que $(0, 0, \varepsilon) \in S$ y $f(0, 0, \varepsilon) = 0$. Pruebe que el conjunto

$$
\{(x, y, \alpha) \in S : (y, x, \alpha) \in S \text{ y } f(x, y, \alpha) = f(y, x, \alpha)\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;21&#41; Si $\mathbb{P}_1$ y $\mathbb{P}_2$ son procedimientos efectivos ambos con conjunto de datos de entrada igual a $\omega \times \Sigma^\ast$, entonces el conjunto

$$
\{(\alpha, \beta) \in \Sigma^\ast \times \Sigma^\ast : \mathbb{P}_1 \text{ termina partiendo de } (0, \alpha) \text{ y } \mathbb{P}_2 \text{ termina partiendo de } (0, \beta)\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;22&#41; Sea $\Sigma = \{@, !, \%\}$. Si $f : S \subseteq \omega \times \omega \times \Sigma^\ast \to \omega$ es $\Sigma$-efectivamente computable, entonces $S$ es $\Sigma$-efectivamente enumerable

&#40;23&#41; Sea $\Sigma = \{@, !, \%\}$. Si $f : S \subseteq \omega \times \omega \times \Sigma^\ast \to \omega$ es $\Sigma$-efectivamente computable, entonces $\operatorname{Im}(f)$ es $\Sigma$-efectivamente enumerable

&#40;24&#41; Sea $\Sigma = \{@, !, \%\}$. Si $f : L \subseteq \Sigma^\ast \times \Sigma^\ast \to \omega$ es $\Sigma$-efectivamente computable, entonces $\operatorname{Im}(f)$ es $\Sigma$-efectivamente enumerable

&#40;25&#41; Sea $\Sigma = \{@, !, \%\}$. Si $f_1 : S_1 \subseteq \omega \times \omega \times \Sigma^\ast \to \omega$ y $f_2 : S_2 \subseteq \omega \times \omega \times \Sigma^\ast \to \Sigma^\ast$ son $\Sigma$-efectivamente computables, entonces $\operatorname{Im}([f_1, f_2])$ es $\Sigma$-efectivamente enumerable

&#40;26&#41; Sea $\Sigma = \{@, !, \%\}$. Si $f : S \subseteq \omega \to \omega$ y $g : L \subseteq \Sigma^\ast \to \omega$ son $\Sigma$-efectivamente computables, entonces

$$
\{x : x \in S,\ @^x \in L \text{ y } f(x) = g(@^x)\}
$$

es $\Sigma$-efectivamente enumerable

&#40;27&#41; Sea $\Sigma = \{@, !, \%\}$. Si $f : S \subseteq \omega \to \omega$ y $g : L \subseteq \Sigma^\ast \to \omega$ son $\Sigma$-efectivamente computables, entonces

$$
\{\alpha \in L : g(\alpha) \in S \text{ y } f(g(\alpha)) = 0\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;28&#41; Sea $\Sigma = \{@, !, \%\}$. Si $f : \omega \to \Sigma^\ast$ es $\Sigma$-efectivamente computable y biyectiva, entonces $f^{-1}$ es $\Sigma$-efectivamente computable

&#40;29&#41; Sea $\Sigma = \{@, !, \%\}$. Si $f : L \subseteq \Sigma^\ast \to \omega$ y $g : S \subseteq \omega \to \Sigma^\ast$ son $\Sigma$-efectivamente computables, entonces $f \circ g$ es $\Sigma$-efectivamente computable

&#40;30&#41; Si $f : S \subseteq \omega \to \omega$ es $\Sigma$-efectivamente computable, entonces el conjunto

$$
\{x \in S : x^2 \in S \text{ y } f(x) = f(x^2)\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;31&#41; Si $f : S \subseteq \omega \to \omega$ es $\Sigma$-efectivamente computable, entonces el conjunto

$$
\{x \in S : x \text{ es par } x/2 \in S \text{ y } f(x) = f(x/2)\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;32&#41; Sea $\Sigma = \{@, !, \%\}$. Supongamos $L_1, L_2 \subseteq \Sigma^\ast$ son $\Sigma$-efectivamente enumerables. Entonces

$$
\{\alpha \in L_1 : \text{hay un } \beta \in L_2 \text{ tal que } |\beta| = |\alpha|\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;33&#41; Sea $\Sigma = \{!, \%\}$. Supongamos $S \subseteq \omega \times \omega \times \Sigma^\ast$ y $L \subseteq \Sigma^\ast$ son $\Sigma$-efectivamente enumerables. Entonces

$$
\{(x, y, \alpha) \in S : \text{hay un } \beta \in L \text{ tal que } |\beta| = |\alpha|\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;34&#41; Sea $\Sigma = \{!, \%\}$. Supongamos $S \subseteq \omega \times \omega$ y $S' \subseteq \omega$ son $\Sigma$-efectivamente enumerables. Entonces

$$
\{(x, y) : (x, y) \in S \text{ y } x + y \in S'\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;35&#41; Sea $\Sigma = \{!, \%\}$. Supongamos $S \subseteq \Sigma^\ast \times \Sigma^\ast$ y $L \subseteq \Sigma^\ast$ son $\Sigma$-efectivamente enumerables. Entonces

$$
\{(\alpha, \beta) \in S : \text{hay un } \gamma \in L \text{ tal que } \alpha = \beta\gamma\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;36&#41; Sean $f : D_f \subseteq \omega \times \Sigma^\ast \to \omega$ y $g : D_g \subseteq \omega \times \Sigma^\ast \to \omega$ funciones $\Sigma$-efectivamente computables tales que $D_f \cap D_g = \emptyset$. Sea $F : D_f \cup D_g \to \omega$ dada por

$$
e \mapsto
\begin{cases}
f(e) & \text{si } e \in D_f\\
g(e) & \text{si } e \in D_g
\end{cases}
$$

Pruebe que $F$ es $\Sigma$-efectivamente computable.

&#40;37&#41; Sea $\Sigma = \{@, !, \%\}$. Supongamos $L_1, L_2 \subseteq \Sigma^\ast$ son $\Sigma$-efectivamente enumerables. Entonces

$$
\{\alpha \in L_1 : \text{hay un } \beta \in L_2 \text{ tal que } \beta^3 = \alpha\}
$$

es $\Sigma$-efectivamente enumerable.

&#40;38&#41; Sean $S \subseteq \omega$ y $L \subseteq \{@, \text{↑}\}^\ast$ tales que $(0, \varepsilon) \in S \times L$. Entonces $S \times L$ es $\{@, \text{↑}\}$-efectivamente enumerable si y solo si ambos $S$ y $L$ son $\{@, \text{↑}\}$-efectivamente enumerables
