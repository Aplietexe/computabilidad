# GUÍA 6 DE LENGUAJES: MINIMIZACIÓN Y FUNCIONES \(\Sigma\)-RECURSIVAS

Tal como fue explicado en el comienzo de la Guía 5, para obtener la clase de las funciones \(\Sigma\)-recursivas debemos agregar un nuevo constructor a los ya definidos de composición y recursión primitiva, a saber, el constructor de minimización. Tiene dos casos aunque solo usaremos el primero para la definición de función \(\Sigma\)-recursiva.

## Minimización de variable numérica

Sea \(\Sigma\) un alfabeto finito y sea \(P:D_P\subseteq\omega\times\omega^n\times\Sigma^{\ast m}\to\omega\) un predicado. Dado \((\overrightarrow{x},\overrightarrow{\alpha})\in\omega^n\times\Sigma^{\ast m}\), cuando exista al menos un \(t\in\omega\) tal que \(P(t,\overrightarrow{x},\overrightarrow{\alpha})=1\), usaremos \(\min_t P(t,\overrightarrow{x},\overrightarrow{\alpha})\) para denotar al menor de tales \(t\)'s. Nótese que la expresión \(\min_t P(t,\overrightarrow{x},\overrightarrow{\alpha})\) está definida sólo para aquellas \((n+m)\)-uplas \((\overrightarrow{x},\overrightarrow{\alpha})\) para las cuales hay al menos un \(t\) tal que se da \(P(t,\overrightarrow{x},\overrightarrow{\alpha})=1\). Dicho de otra forma, \(\min_t P(t,\overrightarrow{x},\overrightarrow{\alpha})\) no estará definida cuando para cada \(t\in\omega\) se dé que \((t,\overrightarrow{x},\overrightarrow{\alpha})\) no pertenece a \(D_P\) o \(P(t,\overrightarrow{x},\overrightarrow{\alpha})=0\). Otro detalle importante a tener en cuenta es que la expresión \(\min_t P(t,\overrightarrow{x},\overrightarrow{\alpha})\) no depende de la variable \(t\). Por ejemplo, las expresiones \(\min_t P(t,\overrightarrow{x},\overrightarrow{\alpha})\) y \(\min_i P(i,\overrightarrow{x},\overrightarrow{\alpha})\) son equivalentes en el sentido que están definidas en las mismas \((n+m)\)-uplas y cuando están definidas asumen el mismo valor.

Definamos

\[
M(P)=\lambda\overrightarrow{x}\overrightarrow{\alpha}[\min_t P(t,\overrightarrow{x},\overrightarrow{\alpha})]
\]

Nótese que

\[
D_{M(P)}=\{(\overrightarrow{x},\overrightarrow{\alpha})\in\omega^n\times\Sigma^{\ast m}:(\exists t\in\omega)\ P(t,\overrightarrow{x},\overrightarrow{\alpha})\}
\]

\[
M(P)(\overrightarrow{x},\overrightarrow{\alpha})=\min_t P(t,\overrightarrow{x},\overrightarrow{\alpha}),
\quad\text{para cada }(\overrightarrow{x},\overrightarrow{\alpha})\in D_{M(P)}
\]

Diremos que \(M(P)\) se obtiene por minimización de variable numérica a partir de \(P\). Nótese que \(M(P)\) está definido sólo cuando \(P\) es un predicado cuyo dominio sea un conjunto \(\Sigma\)-mixto de tipo \((n,m)\), con \(n\in\mathbf{N}\).

Veamos algunos ejemplos:

**(E1)** Tomemos \(P=\lambda tx_1[t^2=x_1]\). Tenemos que:

\[
\begin{aligned}
D_{M(P)}
&=\{x_1\in\omega:(\exists t\in\omega)\ P(t,x_1)\}\\
&=\{x_1\in\omega:(\exists t\in\omega)\ t^2=x_1\}
\end{aligned}
\]

Es decir el dominio de \(M(P)\) es el conjunto de los cuadrados. Además para cada \(x_1\in D_{M(P)}\) tenemos que

\[
M(P)(x_1)=\min_t P(t,x_1)=\min_t(t^2=x_1)
\]

por lo cual \(M(P)(x)=\sqrt{x}\), para cada \(x\in D_{M(P)}\).

**(E2)** Cuando \(n=m=0\), tenemos que \(P:D_P\subseteq\omega\to\omega\). O sea que

\[
M(P)=\lambda[\min_t P(t)]
\]

Esto nos dice que \(D_{M(P)}\subseteq\{\diamond\}\). Además \(D_{M(P)}=\{\diamond\}\) si y solo si \(P(t)=1\), para algún \(t\in D_P\), y en tal caso \(M(P)(\diamond)=\min_t P(t)\).

**(E3)** Recordemos que dados \(x_1,x_2\in\omega\), con \(x_2\) no nulo, el cociente de dividir \(x_1\) por \(x_2\) se define como el máximo elemento del conjunto \(\{t\in\omega:t.x_2\le x_1\}\). Sea

\[
\begin{aligned}
Q:\omega\times\mathbf{N}&\to\omega\\
(x_1,x_2)&\mapsto\text{ cociente de dividir }x_1\text{ por }x_2
\end{aligned}
\]

Sea \(P=\lambda tx_1x_2[x_1<t.x_2]\). Notar que

\[
\begin{aligned}
D_{M(P)}
&=\{(x_1,x_2)\in\omega^2:(\exists t\in\omega)\ P(t,x_1,x_2)=1\}\\
&=\{(x_1,x_2):(\exists t\in\omega)\ x_1<t.x_2\}\\
&=\omega\times\mathbf{N}
\end{aligned}
\]

Además si \((x_1,x_2)\in\omega\times\mathbf{N}\), es fácil de probar que

\[
\min_t x_1<t.x_2=Q(x_1,x_2)+1
\]

por lo que \(M(P)=Suc\circ Q\). Si quisiéramos encontrar un predicado \(P'\) tal que \(M(P')=Q\), entonces podemos tomar \(P'=\lambda tx_1x_2[x_1<(t+1).x_2]\) y con un poco de concentración nos daremos cuenta que \(M(P')=Q\). Por supuesto esto tiene una cuota de artificialidad ya que no es tan obvio que

\[
Q(x_1,x_2)=\text{menor }t\in\omega\text{ tal que }x_1<(t+1).x_2
\]

Hay una forma más intuitiva de hacerlo y es diseñando \(P'\) con la consigna de que para cada \((x_1,x_2)\in D_Q\) se dé que

\[
Q(x_1,x_2)=\text{único }t\in\omega\text{ tal que }P'(t,x_1,x_2)
\]

Es decir diseñamos \(P'\) de manera que

\[
P'(t,x_1,x_2)=1\text{ si y solo si }t=Q(x_1,x_2)
\]

Por ejemplo se puede tomar \(P'=\lambda tx_1x_2[x_1\ge t.x_2\text{ y }x_1<(t+1).x_2]\) que dicho sea de paso es justo la definición de cociente dada en la escuela primaria. Dejamos al lector corroborar que \(M(P')=Q\), para este último \(P'\), pero nótese que lo único que queda por chequear es que \(M(P')\) y \(Q\) tienen el mismo dominio ya que las reglas de asignación obviamente producen lo mismo.

Tal como lo vimos recién muchas veces que queramos diseñar un predicado \(P\) tal que \(M(P)\) sea igual a una función dada \(f\), será más fácil diseñar \(P\) de manera que cumpla

\[
f(\overrightarrow{x},\overrightarrow{\alpha})=
\text{único }t\in\omega\text{ tal que }P(t,\overrightarrow{x},\overrightarrow{\alpha})
\]

cada vez que \((\overrightarrow{x},\overrightarrow{\alpha})\in D_f\). Es decir un predicado \(P\) que caracterice al valor que toma \(f\), es decir el cual cumpla

\[
P(t,\overrightarrow{x},\overrightarrow{\alpha})=1
\text{ si y solo si }t=f(\overrightarrow{x},\overrightarrow{\alpha})
\]

Luego por supuesto deberemos prestar atención a que \(D_{M(P)}=D_f\), es decir deberemos también lograr que para cada \((\overrightarrow{x},\overrightarrow{\alpha})\in\omega^n\times\Sigma^{\ast m}\) se dé que

\[
(\overrightarrow{x},\overrightarrow{\alpha})\in D_f
\text{ si y solo si }\exists t\in\omega\ P(t,\overrightarrow{x},\overrightarrow{\alpha})
\]

Enunciamos esto en forma de regla.

**REGLA U:** Si tiene una función \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) y busca un predicado \(P\) tal que \(f=M(P)\), intente diseñar \(P\) de manera que para cada \((\overrightarrow{x},\overrightarrow{\alpha})\in D_f\) se dé que

\[
f(\overrightarrow{x},\overrightarrow{\alpha})=
\text{único }t\in\omega\text{ tal que }P(t,\overrightarrow{x},\overrightarrow{\alpha})
\]

Luego chequee que además para cada \((\overrightarrow{x},\overrightarrow{\alpha})\in\omega^n\times\Sigma^{\ast m}\) se dé que

\[
(\overrightarrow{x},\overrightarrow{\alpha})\in D_f
\text{ si y solo si }\exists t\in\omega\ P(t,\overrightarrow{x},\overrightarrow{\alpha})
\]

**Ejercicio 1:** Sea \(\Sigma=\{\text{@},\text{!},\%\}\). Para cada caso describa la función \(M(P)\):

**(a)** \(P=\lambda tx_1[x_1<t]\)

**(b)** \(P=\lambda tx_1[t<x_1]\)

**(c)** \(P=\lambda t\alpha\beta[\alpha^t=\beta]\)

**(d)** \(P=\lambda t\alpha\beta[\alpha=\beta]\)

**(e)** \(P=\lambda tx_1x_2[x_2+t=x_1]\)

**(f)** \(P=\lambda t\alpha_1[[\alpha_1]_t=\%]\)

**(g)** \(P=\lambda xy[y<x]\)

**(h)** \(P=\lambda x_1t[x_1<t]\)

**(i)** \(P=\lambda yx\alpha[[\alpha]_x=\%]\)

**Ejercicio 2:** Sea \(E=\lambda x_1[\text{parte entera de }\sqrt{x_1}]\). Note que por notación lambda \(D_E=\omega\). Aplique la REGLA U para encontrar un predicado \(P\) tal que \(M(P)=E\).

**Ejercicio 3:** Encuentre un predicado \(P\) tal que \(M(P)=\lambda x_1x_2[x_1\mathbin{\dot{-}}x_2]\). (Aquí es natural hacerlo sin la idea de la REGLA U.)

**Ejercicio 4:** Sea \(F:\{z^2:z\in\omega\}\to\omega\) dada por \(F(x)=\sqrt{x}\). Encuentre un predicado \(P\) tal que \(M(P)=F\).

**Ejercicio 5:** Sea \(F:\{(x,y)\in\omega\times\mathbf{N}:y\text{ divide a }x\}\to\omega\) dada por \(F(x,y)=x/y\). Encuentre un predicado \(P\) tal que \(M(P)=F\).

El siguiente lema nos muestra que en algunos casos el constructor de minimización preserva la computabilidad efectiva.

**Lema 1.** Si \(P:D_P\subseteq\omega\times\omega^n\times\Sigma^{\ast m}\to\omega\) es un predicado \(\Sigma\)-efectivamente computable y \(D_P\) es \(\Sigma\)-efectivamente computable, entonces la función \(M(P)\) es \(\Sigma\)-efectivamente computable.

**Proof.** Sea \(\mathbb{P}_P\) un procedimiento efectivo que compute a \(P\) y sea \(\mathbb{P}_{D_P}\) un procedimiento efectivo que compute a \(\chi_{D_P}^{\omega\times\omega^n\times\Sigma^{\ast m}}\). Nótese que el siguiente procedimiento efectivo (con dato de entrada \((\overrightarrow{x},\overrightarrow{\alpha})\in\omega^n\times\Sigma^{\ast m}\)) computa la función \(M(P)\).

Etapa 1: Hacer \(T=0\) e ir a Etapa 2

Etapa 2: Correr \(\mathbb{P}_{D_P}\) con dato de entrada \((T,\overrightarrow{x},\overrightarrow{\alpha})\) y guardar la salida en \(A\). Ir a Etapa 3.

Etapa 3: Si \(A=1\) ir a Etapa 4, caso contrario ir a etapa 6.

Etapa 4: Correr \(\mathbb{P}_P\) con dato de entrada \((T,\overrightarrow{x},\overrightarrow{\alpha})\) y guardar la salida en \(B\). Ir a Etapa 5.

Etapa 5: Si \(B=1\), dar como salida \(T\) y terminar. Caso contrario ir a Etapa 6.

Etapa 6: Hacer \(T=T+1\) e ir a Etapa 2. \(\blacksquare\) Como corolario obtenemos que la minimización de predicados \(\Sigma\)-totales preserva la computabilidad efectiva:

**Corolario 2.** Si \(P:\omega\times\omega^n\times\Sigma^{\ast m}\to\omega\) es un predicado \(\Sigma\)-efectivamente computable, entonces la función \(M(P)\) es \(\Sigma\)-efectivamente computable.

Lamentablemente si quitamos la hipótesis en el lema anterior de que \(D_P\) sea \(\Sigma\)-efectivamente computable, el lema resulta falso. Más adelante veremos un ejemplo de esto, basado en la Tesis de Church (esta tesis básicamente dice que el modelo Gödeliano de la computabilidad efectiva es correcto (Guía 8)).

**Ejercicio 6:** Intente construir un procedimiento efectivo que compute a \(M(P)\) teniendo un procedimiento efectivo que compute a un predicado \(P:D_P\subseteq\omega\times\omega^n\times\Sigma^{\ast m}\to\omega\). Seguro fallará en sus intentos pero entenderá cuál es la dificultad subyacente.

**Ejercicio 7:** (Responder V o F) Si \(P:D_P\subseteq\omega\times\omega^2\to\omega\) es un predicado \(\Sigma\)-efectivamente computable, entonces el siguiente procedimiento computa a \(M(P)\):

Etapa 1: Hacer \(T=0\) e ir a Etapa 2

Etapa 2: Si \((T,x,y)\in D_P\) y \(P(T,x,y)=1\), entonces ir a Etapa 4, en caso contrario ir a Etapa 3.

Etapa 3: Hacer \(T=T+1\) e ir a Etapa 2.

Etapa 4: Dar \(T\) como salida y terminar

**Ejercicio 8:** V o F o I. Justifique.

**(a)** Sea \(P:D_P\subseteq\omega\times\omega^n\to\omega\) un predicado. Si \(\overrightarrow{x}\in\omega^n\) es tal que existe \(t\) en \(\omega\) que cumple \((t,\overrightarrow{x})\in D_P\), entonces \(\overrightarrow{x}\in D_{M(P)}\).

**(b)** Sea \(P:D_P\subseteq\omega\times\omega^n\to\omega\) un predicado. Entonces \(M(P)(\overrightarrow{x})\le t\)

**(c)** Sea \(P:\omega^n\to\omega\) un predicado, con \(n\ge 1\). Entonces \(D_{M(P)}\subseteq\omega^{n-1}\)

**(d)** Sea \(\Sigma\) un alfabeto finito. Entonces \(M(p_1^{1,2})=C_0^{0,2}\)

## Definición de función \(\Sigma\)-recursiva

Con este nuevo constructor de funciones estamos en condiciones de definir la clase de las funciones \(\Sigma\)-recursivas. Definamos los conjuntos \(R_0^\Sigma\subseteq R_1^\Sigma\subseteq R_2^\Sigma\subseteq\cdots\subseteq R^\Sigma\) de la siguiente manera

\[
R_0^\Sigma=PR_0^\Sigma
\]

\[
\begin{aligned}
R_{k+1}^\Sigma=R_k^\Sigma
&\cup\{f\circ[f_1,\ldots,f_r]:f,f_1,\ldots,f_r\in R_k^\Sigma,\ r\ge 1\}\\
&\cup\{R(f,\mathcal{G}):R(f,\mathcal{G})\text{ está definida y }\{f\}\cup\{\mathcal{G}_a:a\in\Sigma\}\subseteq R_k^\Sigma\}\\
&\cup\{R(f,g):R(f,g)\text{ está definida y }f,g\in R_k^\Sigma\}\\
&\cup\{M(P):M(P)\text{ está definida, }P\text{ es }\Sigma\text{-total y }P\in R_k^\Sigma\}
\end{aligned}
\]

\[
R^\Sigma=\bigcup_{k\ge 0}R_k^\Sigma
\]

Una función \(f\) es llamada \(\Sigma\)-recursiva si pertenece a \(R^\Sigma\). Cabe destacar que aunque \(M(P)\) fue definido para predicados no necesariamente \(\Sigma\)-totales, en la definición de los conjuntos \(R_k^\Sigma\), nos restringimos al caso en que \(P\) es \(\Sigma\)-total. Obviamente esto lo hacemos ya que como se explicó antes el constructor de minimización no siempre preserva la computabilidad efectiva.

Nótese que \(PR_k^\Sigma\subseteq R_k^\Sigma\), para cada \(k\in\omega\), por lo cual \(PR^\Sigma\subseteq R^\Sigma\). Por supuesto el modelo de Gödel sería incorrecto si no fuera cierto el siguiente resultado.

**Proposición 3 (Leibniz vence a Gödel).** Si \(F\in R^\Sigma\), entonces \(F\) es \(\Sigma\)-efectivamente computable.

**Proof.** Lo probaremos usando la Regla de Inducción desde 0. Para cada \(k\in\omega\) sea Enu\(_k\) el siguiente enunciado:

Enu\(_k\): Si \(F\in R_k^\Sigma\), entonces \(F\) es \(\Sigma\)-efectivamente computable.

Hagamos entonces lo que nos encomienda la Regla de Inducción desde 0.

Prueba de que Enu\(_0\) es verdadero. Fácil.

Prueba de que si Enu\(_k\) es verdadero entonces Enu\(_{k+1}\) lo es. Supongamos entonces que \(F\in R_{k+1}^\Sigma\) y que vale Enu\(_k\). Veamos que entonces \(F\) es \(\Sigma\)-efectivamente computable. Ya que vale Enu\(_k\), podemos suponer que \(F\in R_{k+1}^\Sigma-R_k^\Sigma\). Hay varios casos:

Caso \(F=f\circ[f_1,\ldots,f_r]\), con \(f,f_1,\ldots,f_r\in R_k^\Sigma\), \(r\ge 1\). Ya que Enu\(_k\) es verdadero, las funciones \(f,f_1,\ldots,f_r\) son \(\Sigma\)-efectivamente computables. Entonces por un Lema del comienzo de la Guía 5 tenemos que \(F\) es \(\Sigma\)-efectivamente computable.

Caso \(F=M(P)\), con \(P:\omega\times\omega^n\times\Sigma^{\ast m}\to\omega\) un predicado perteneciente a \(R_k^\Sigma\). Ya que Enu\(_k\) es verdadero, el predicado \(P\) es \(\Sigma\)-efectivamente computable. Ahora podemos aplicar el corolario anterior y concluir que \(F\) es \(\Sigma\)-efectivamente computable.

Los distintos casos en los que \(F\) se obtiene por recursión primitiva a partir de funciones de \(R_k^\Sigma\) se siguen de Enu\(_k\) y los respectivos lemas dados en la Guía 5 los cuales prueban que cada uno de los cuatro casos de recursión primitiva preserva la computabilidad efectiva. \(\blacksquare\)

Daremos sin prueba el siguiente conceptualmente importante resultado.

**Proposición 4.** Sea \(\Sigma\) un alfabeto finito. Entonces no toda función \(\Sigma\)-recursiva es \(\Sigma\)-p.r.. Es decir que \(PR^\Sigma\subseteq R^\Sigma\) y \(PR^\Sigma\ne R^\Sigma\).

Este resultado no es fácil de probar. Más adelante veremos ejemplos naturales de funciones \(\Sigma\)-recursivas que no son \(\Sigma\)-p.r.. Otro ejemplo natural es la famosa función de Ackermann.

**Lema de minimización acotada de variable numérica de predicados \(\Sigma\)-p.r.** Como veremos más adelante, no siempre que \(P\in R^\Sigma\), tendremos que \(M(P)\in R^\Sigma\). Sin embargo, el siguiente lema nos garantiza que cuando \(P\in PR^\Sigma\), se da que \(M(P)\in R^\Sigma\) y además da condiciones para que \(M(P)\) sea \(\Sigma\)-p.r..

**Lema 5 (Lema de minimización acotada).** Sean \(n,m\ge 0\). Sea \(P:D_P\subseteq\omega\times\omega^n\times\Sigma^{\ast m}\to\omega\) un predicado \(\Sigma\)-p.r.. Entonces

**(a)** \(M(P)\) es \(\Sigma\)-recursiva.

**(b)** Si hay una función \(\Sigma\)-p.r. \(f:\omega^n\times\Sigma^{\ast m}\to\omega\) tal que

\[
M(P)(\overrightarrow{x},\overrightarrow{\alpha})
=\min_t P(t,\overrightarrow{x},\overrightarrow{\alpha})
\le f(\overrightarrow{x},\overrightarrow{\alpha}),
\quad\text{para cada }(\overrightarrow{x},\overrightarrow{\alpha})\in D_{M(P)},
\]

entonces \(M(P)\) es \(\Sigma\)-p.r..

**Proof.** **(a)** Sea \(\overline{P}=P\cup C_0^{n+1,m}|_{(\omega^{n+1}\times\Sigma^{\ast m})-D_P}\). Note que \(\overline{P}\) es \(\Sigma\)-p.r. (por qué?). Veremos a continuación que \(M(P)=M(\overline{P})\). Nótese que

\[
\{t\in\omega:P(t,\overrightarrow{x},\overrightarrow{\alpha})=1\}
=\{t\in\omega:\overline{P}(t,\overrightarrow{x},\overrightarrow{\alpha})=1\}
\]

Esto claramente dice que \(D_{M(P)}=D_{M(\overline{P})}\) y que \(M(P)(\overrightarrow{x},\overrightarrow{\alpha})=M(\overline{P})(\overrightarrow{x},\overrightarrow{\alpha})\), para cada \((\overrightarrow{x},\overrightarrow{\alpha})\in D_{M(P)}\), por lo cual \(M(P)=M(\overline{P})\).

Veremos entonces que \(M(\overline{P})\) es \(\Sigma\)-recursiva. Sea \(k\) tal que \(\overline{P}\in PR_k^\Sigma\). Ya que \(\overline{P}\) es \(\Sigma\)-total y \(\overline{P}\in PR_k^\Sigma\subseteq R_k^\Sigma\), tenemos que \(M(\overline{P})\in R_{k+1}^\Sigma\) y por lo tanto \(M(\overline{P})\in R^\Sigma\).

**(b)** Ya que \(M(P)=M(\overline{P})\), basta con probar que \(M(\overline{P})\) es \(\Sigma\)-p.r. Primero veremos que \(D_{M(\overline{P})}\) es un conjunto \(\Sigma\)-p.r.. Nótese que

\[
\chi_{D_{M(\overline{P})}}^{\omega^n\times\Sigma^{\ast m}}
=\lambda\overrightarrow{x}\overrightarrow{\alpha}
[(\exists t\in\omega)_{t\le f(\overrightarrow{x},\overrightarrow{\alpha})}\ \overline{P}(t,\overrightarrow{x},\overrightarrow{\alpha})]
\]

lo cual nos dice que

\[
\chi_{D_{M(\overline{P})}}^{\omega^n\times\Sigma^{\ast m}}
=\lambda x\overrightarrow{x}\overrightarrow{\alpha}
[(\exists t\in\omega)_{t\le x}\ \overline{P}(t,\overrightarrow{x},\overrightarrow{\alpha})]
\circ[f,p_1^{n,m},\ldots,p_{n+m}^{n,m}]
\]

Pero el Lema de Cuantificación acotada probado en la Guía 5 nos dice que el predicado \(\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\exists t\in\omega)_{t\le x}\ \overline{P}(t,\overrightarrow{x},\overrightarrow{\alpha})]\) es \(\Sigma\)-p.r. por lo cual tenemos que \(\chi_{D_{M(\overline{P})}}^{\omega^n\times\Sigma^{\ast m}}\) lo es. Sea

\[
P_1=\lambda t\overrightarrow{x}\overrightarrow{\alpha}
[\overline{P}(t,\overrightarrow{x},\overrightarrow{\alpha})
\land(\forall j\in\omega)_{j\le t}(j=t\lor\neg\overline{P}(j,\overrightarrow{x},\overrightarrow{\alpha}))]
\]

Note que \(P_1\) es \(\Sigma\)-total. Dejamos al lector usando lemas anteriores probar que \(P_1\) es \(\Sigma\)-p.r. Además nótese que para \((\overrightarrow{x},\overrightarrow{\alpha})\in\omega^n\times\Sigma^{\ast m}\) se tiene que

\[
P_1(t,\overrightarrow{x},\overrightarrow{\alpha})=1
\text{ si y solo si }(\overrightarrow{x},\overrightarrow{\alpha})\in D_{M(\overline{P})}
\text{ y }t=M(\overline{P})(\overrightarrow{x},\overrightarrow{\alpha})
\]

Esto nos dice que

\[
M(\overline{P})=
\left(
\lambda\overrightarrow{x}\overrightarrow{\alpha}
\left[
\prod_{t=0}^{f(\overrightarrow{x},\overrightarrow{\alpha})}
t^{P_1(t,\overrightarrow{x},\overrightarrow{\alpha})}
\right]
\right)\Bigg|_{D_{M(\overline{P})}}
\]

por lo cual para probar que \(M(\overline{P})\) es \(\Sigma\)-p.r. solo nos resta probar que

\[
F=\lambda\overrightarrow{x}\overrightarrow{\alpha}
\left[
\prod_{t=0}^{f(\overrightarrow{x},\overrightarrow{\alpha})}
t^{P_1(t,\overrightarrow{x},\overrightarrow{\alpha})}
\right]
\]

lo es. Pero

\[
F=\lambda xy\overrightarrow{x}\overrightarrow{\alpha}
\left[
\prod_{t=x}^{y}t^{P_1(t,\overrightarrow{x},\overrightarrow{\alpha})}
\right]\circ[C_0^{n,m},f,p_1^{n,m},\ldots,p_{n+m}^{n,m}]
\]

y por lo tanto el Lema de la Sumatoria probado en la Guía 5 nos dice que \(F\) es \(\Sigma\)-p.r.. \(\blacksquare\)

**OBSERVACIÓN:** No siempre que \(P\) sea \(\Sigma\)-p.r. tendremos que \(M(P)\) lo será. Nótese que si \(M(P)\) fuera \(\Sigma\)-p.r., cada vez que \(P\) lo sea, entonces tendríamos que \(PR^\Sigma=R^\Sigma\) (justifique) lo cual contradiría la Proposición 4. Más adelante veremos un ejemplo natural de un predicado \(P\) el cual es \(\Sigma\)-p.r. pero \(M(P)\) no es \(\Sigma\)-p.r.

El lema de minimización recién probado es muy útil como lo veremos a continuación.

**Lema 6.** Sea \(\Sigma\) un alfabeto finito. Las siguientes funciones son \(\Sigma\)-p.r.:

**(a)**

\[
\begin{aligned}
Q:\omega\times\mathbf{N}&\to\omega\\
(x,y)&\mapsto\text{ cociente de la división de }x\text{ por }y
\end{aligned}
\]

**(b)**

\[
\begin{aligned}
R:\omega\times\mathbf{N}&\to\omega\\
(x,y)&\mapsto\text{ resto de la división de }x\text{ por }y
\end{aligned}
\]

**Proof.** **(a)** Ya vimos anteriormente que \(Q=M(P')\), donde \(P'=\lambda tx_1x_2[x_1\ge t.x_2\text{ y }x_1<(t+1).x_2]\). Ya que \(P'\) es \(\Sigma\)-p.r. y

\[
Q(x_1,x_2)\le p_1^{2,0}(x_1,x_2),\quad\text{para cada }(x_1,x_2)\in\omega\times\mathbf{N}
\]

**(b)** del Lema 5 implica que \(Q\in PR^\Sigma\).

**(b)** Nótese que

\[
R=\lambda xy[x\mathbin{\dot{-}}Q(x,y).y]
\]

y por lo tanto \(R\in PR^\Sigma\). \(\blacksquare\)

**Ejercicio 9:** Dados \(x,y\in\omega\) tales que \(x\ne 0\) o \(y\ne 0\), usaremos \(mcd(x,y)\) para denotar el máximo común divisor de \(x\) e \(y\), es decir el mayor número que divide a \(x\) y divide a \(y\). Note que la función \(M=\lambda xy[mcd(x,y)]\) tiene dominio igual a \(\omega^2-\{(0,0)\}\). Pruebe que \(M\) es \(\Sigma\)-p.r.. (Hint: use la REGLA U).

**Ejercicio 10:** Dados \(x,y\in\mathbf{N}\), usaremos \(mcm(x,y)\) para denotar el mínimo común múltiplo de \(x\) e \(y\), es decir el menor número no nulo que es múltiplo de \(x\) y de \(y\). Note que la función \(G=\lambda xy[mcm(x,y)]\) tiene dominio igual a \(\mathbf{N}^2\). Pruebe que \(G\) es \(\Sigma\)-p.r..

**Ejercicio 11:** Sea \(F:\{z^2:z\in\omega\}\to\omega\) dada por \(F(x)=\sqrt{x}\). Pruebe que \(F\) es \(\Sigma\)-p.r..

**Ejercicio 12:** Sea \(F:\Sigma^\ast\times\Sigma^\ast\to\omega\) dada por \(F(\alpha,\beta)=\max\{|\rho|:\rho\text{ es tramo inicial de }\alpha\text{ y }\beta\}\). Pruebe que \(F\) es \(\Sigma\)-p.r..

**Lema 7.** Sea \(\Sigma\) un alfabeto finito. Entonces la función

\[
\begin{aligned}
pr:\mathbf{N}&\to\omega\\
n&\mapsto n\text{-ésimo número primo}
\end{aligned}
\]

es \(\Sigma\)-p.r.

**Proof.** Para ver que \(pr\) es \(\Sigma\)-p.r., veremos que la extensión \(h:\omega\to\omega\), dada por \(h(0)=0\) y \(h(n)=pr(n)\), \(n\ge 1\), es \(\Sigma\)-p.r.. Luego \(pr=h|_{\mathbf{N}}\) resultará \(\Sigma\)-p.r. por ser la restricción de una función \(\Sigma\)-p.r. a un conjunto \(\Sigma\)-p.r.. Primero note que

\[
h(0)=0
\]

\[
h(t+1)=\min_i(i\text{ es primo}\land i>h(t))
\]

O sea que \(h=R(C_0^{0,0},g)\), donde

\[
\begin{aligned}
g:\omega\times\omega&\to\omega\\
(A,t)&\mapsto \min_i(i\text{ es primo}\land i>A)
\end{aligned}
\]

Es decir que solo nos resta ver que \(g\) es \(\Sigma\)-p.r.. Pero nótese que \(g=M(P)\), donde \(P=\lambda iAt[i\text{ es primo}\land i>A]\). Claramente \(P\) es \(\Sigma\)-p.r. por lo cual para poder aplicar **(b)** del lema anterior debemos encontrar una función \(f:\omega\times\omega\to\omega\) tal que

\[
M(P)(A,t)\le f(A,t),\quad\text{para cada }(A,t)\in\omega^2
\]

Aceptaremos sin prueba que

\[
\min_i(i\text{ es primo}\land i>A)\le A!+1,\quad\text{para cada }A\in\omega
\]

Es decir que \(f=\lambda At[A!+1]\) cumple lo deseado, lo cual implica que \(g=M(P)\) es \(\Sigma\)-p.r.. \(\blacksquare\)

**Ejercicio 13:** (Opcional) Si tiene ganas y recuerda las propiedades básicas de divisibilidad, intente un rato probar que

\[
\min_i(i\text{ es primo}\land i>A)\le A!+1,\quad\text{para cada }A\in\omega
\]

(Hint: factorice \(A!+1\) en producto de primos y vea que alguno debe ser mayor que \(A\).)

**Ejercicio 14:** Sea \(\Sigma\) un alfabeto finito.

**(a)** Pruebe que \(\lambda xi[(x)_i]\) es \(\Sigma\)-p.r. (Hint: repase el significado de la expresión \((x)_i\) y encuentre entonces el dominio de \(\lambda xi[(x)_i]\) antes de hacer el ejercicio)

**(b)** Pruebe que la función \(Lt\) es \(\Sigma\)-p.r.

**Ejercicio 15:** Sea \(F:\mathbf{N}\to\omega\) dada por \(F(x)=\max\{t\in\omega:t!\le x\}\). Pruebe que \(F\) es \(\Sigma\)-p.r..

**Ejercicio 16:** Sea \(\Sigma=\{\text{@},\text{!},\%\}\). Sea \(F=\lambda\alpha\beta[\max\{t\in\mathbf{N}:\alpha^t\text{ es tramo inicial de }\beta\}]\).

**(a)** Encuentre (según manda notación lambda) el dominio de \(F\)

**(b)** Pruebe que \(F\) es \(\Sigma\)-p.r. (Hint: use la Regla U).

**Ejercicio 17:** Sea \(F:\Sigma^+\to\omega\) dada por \(F(\alpha)=\max\{t\in\mathbf{N}:t\le|\alpha|\text{ y }[\alpha]_1[\alpha]_2\ldots[\alpha]_t\text{ es capicúa}\}\). Pruebe que \(F\) es \(\Sigma\)-p.r..

**Ejercicio 18:** Sea \(\Sigma=\{\text{@},\text{!}\}\). Sea \(f:\Sigma^\ast\to\omega\) dada por:

\[
f(\alpha)=\max\{|\beta|:\beta\text{ ocurre en }\alpha\text{ y }\beta\text{ es capicúa}\}
\]

Pruebe que \(f\) es \(\Sigma\)-p.r. (Hint: use la Regla U). Ojo, puede haber un \(\beta\) capicúa que ocurra en \(\alpha\) de manera "inextensible" pero que \(f(\alpha)\) no sea igual a \(|\beta|\).

## Minimización de variable alfabética

Supongamos que \(\Sigma\ne\emptyset\). Sea \(\le\) un orden total sobre \(\Sigma\). Recordemos que \(\le\) puede ser naturalmente extendido a un orden total sobre \(\Sigma^\ast\). Sea \(P:D_P\subseteq\omega^n\times\Sigma^{\ast m}\times\Sigma^\ast\to\omega\) un predicado. Cuando \((\overrightarrow{x},\overrightarrow{\alpha})\in\omega^n\times\Sigma^{\ast m}\) es tal que existe al menos un \(\alpha\in\Sigma^\ast\) tal que \(P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)=1\), usaremos \(\min_\alpha^\le P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)\) para denotar al menor \(\alpha\in\Sigma^\ast\) tal que \(P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)=1\). Nótese que la expresión \(\min_\alpha^\le P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)\) está definida sólo para aquellas \((n+m)\)-uplas \((\overrightarrow{x},\overrightarrow{\alpha})\) para las cuales hay al menos un \(\alpha\) tal que se da \(P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)=1\). Dicho de otra forma, \(\min_\alpha^\le P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)\) no estará definida cuando para cada \(\alpha\in\Sigma^\ast\) se dé que \((\overrightarrow{x},\overrightarrow{\alpha},\alpha)\) no pertenece a \(D_P\) o \(P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)=0\). Otro detalle importante a tener en cuenta es que la expresión \(\min_\alpha^\le P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)\) no depende de la variable \(\alpha\). Por ejemplo, las expresiones \(\min_\alpha^\le P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)\) y \(\min_\beta^\le P(\overrightarrow{x},\overrightarrow{\alpha},\beta)\) son equivalentes en el sentido que están definidas en las mismas \((n+m)\)-uplas y cuando están definidas asumen el mismo valor.

Definamos

\[
M^\le(P)=\lambda\overrightarrow{x}\overrightarrow{\alpha}
[\min_\alpha^\le P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)]
\]

Nótese que

\[
D_{M^\le(P)}=
\{(\overrightarrow{x},\overrightarrow{\alpha})\in\omega^n\times\Sigma^{\ast m}:
(\exists\alpha\in\Sigma^\ast)\ P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)\}
\]

\[
M^\le(P)(\overrightarrow{x},\overrightarrow{\alpha})
=\min_\alpha^\le P(\overrightarrow{x},\overrightarrow{\alpha},\alpha),
\quad\text{para cada }(\overrightarrow{x},\overrightarrow{\alpha})\in D_{M^\le(P)}
\]

Diremos que \(M^\le(P)\) es obtenida por minimización de variable alfabética a partir de \(P\).

Algunos ejemplos:

**(E1)** Sea \(\Sigma=\{\text{@},a,b,c,d,e\}\) y sea \(\le\) un orden total sobre \(\Sigma\). Sea \(Dir=\{\alpha_1\in\Sigma^\ast:|\alpha_1|_{\text{@}}=1\}\) y definamos \(U:Dir\to\Sigma^\ast\) de la siguiente manera

\[
U(\alpha_1)=\text{único }\alpha\text{ tal que }\alpha\text{@}\text{ es tramo inicial de }\alpha_1
\]

Sea

\[
P=\lambda\alpha_1\alpha[\alpha_1\in Dir\text{ y }\alpha\text{@}\text{ es tramo inicial de }\alpha_1]
\]

Tenemos que

\[
\begin{aligned}
D_{M^\le(P)}
&=\{\alpha_1\in\Sigma^\ast:(\exists\alpha\in\Sigma^\ast)\ P(\alpha_1,\alpha)\}\\
&=\{\alpha_1\in\Sigma^\ast:\alpha_1\in Dir\text{ y }(\exists\alpha\in\Sigma^\ast)\ \alpha\text{@}\text{ es tramo inicial de }\alpha_1\}\\
&=Dir
\end{aligned}
\]

y además es claro que \(M^\le(P)(\alpha_1)=U(\alpha_1)\), para cada \(\alpha_1\in Dir\), por lo cual \(M^\le(P)=U\).

**(E2)** Cuando \(n=m=0\), tenemos que \(P:D_P\subseteq\Sigma^\ast\to\omega\). O sea que

\[
M^\le(P)=\lambda[\min_\alpha^\le P(\alpha)]
\]

Esto nos dice que \(D_{M^\le(P)}\subseteq\{\diamond\}\). Además \(D_{M^\le(P)}=\{\diamond\}\) si y solo si \(P(\alpha)=1\), para algún \(\alpha\in D_P\), y en tal caso \(M^\le(P)(\diamond)=\min_\alpha^\le P(\alpha)\).

Como puede notarse para el caso alfabético también tenemos:

**REGLA U:** Si tiene una función \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\Sigma^\ast\) y busca un predicado \(P\) tal que \(f=M^\le(P)\), intente diseñar \(P\) de manera que para cada \((\overrightarrow{x},\overrightarrow{\alpha})\in D_f\) se dé que

\[
f(\overrightarrow{x},\overrightarrow{\alpha})=
\text{único }\alpha\in\Sigma^\ast\text{ tal que }P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)
\]

Luego chequee que además para cada \((\overrightarrow{x},\overrightarrow{\alpha})\in\omega^n\times\Sigma^{\ast m}\) se dé que

\[
(\overrightarrow{x},\overrightarrow{\alpha})\in D_f
\text{ si y solo si }\exists\alpha\in\Sigma^\ast\ P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)
\]

**Ejercicio 19:** V o F o I, justifique.

**(a)** Sea \(\Sigma\) un alfabeto no vacío y sea \(\le\) un orden total sobre \(\Sigma\). Entonces \(p_1^{0,2}=M^\le(\lambda\alpha_1\alpha[\alpha=\alpha_1])\)

**(b)** Sea \(\le\) un orden total sobre \(\Sigma\) y sea \(P:D_P\subseteq\omega^n\times\Sigma^{\ast m}\times\Sigma^\ast\to\omega\) un predicado, entonces

\[
D_{M^\le(P)}=
\{(\overrightarrow{x},\overrightarrow{\alpha})\in\omega^n\times\Sigma^{\ast m}:
(\exists\alpha\in\Sigma^\ast)\ (\overrightarrow{x},\overrightarrow{\alpha},\alpha)\in D_P\}
\]

**(c)** Sea \(\le\) un orden total sobre \(\Sigma\) y sea \(P:D_P\subseteq\omega^n\times\Sigma^{\ast m}\times\Sigma^\ast\to\omega\) un predicado, entonces

\[
D_{M^\le(P)}=
\{(\overrightarrow{x},\overrightarrow{\alpha})\in\omega^n\times\Sigma^{\ast m}:
P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)
\land(\forall\beta\in\Sigma^\ast)_{\beta<_\le\alpha}\neg P(\overrightarrow{x},\overrightarrow{\alpha},\beta)\}
\]

\[
M^\le(P)(\overrightarrow{x},\overrightarrow{\alpha})=\alpha
\]

**Ejercicio 20:** Sea \(\Sigma\) un alfabeto no vacío y sea \(\le\) un orden total sobre \(\Sigma\).

**(a)** Diga qué función es \(M^\le(\lambda\alpha_1\alpha_2\alpha[\alpha_1=\varepsilon])\)

**(b)** Diga qué función es \(M^\le(\lambda\alpha_1\alpha[\alpha^2=\alpha_1\lor\alpha=\alpha_1])\)

**(c)** Diga qué función es \(M^\le(\lambda x_1\alpha_1\alpha[\alpha=\alpha_1])\)

**(d)** Diga qué función es \(M^\le(\lambda x_1\alpha_1\alpha[\alpha=\alpha_1\text{ y }x_1<20])\)

**(e)** Diga qué función es \(M^\le(\lambda xy\alpha\beta[y\le|\beta|])\)

**(f)** Diga qué función es \(M^\le(\lambda\alpha_1\alpha_2\alpha[\alpha_1=\alpha\alpha_2])\)

**Lema de minimización acotada de variable alfabética de predicados \(\Sigma\)-p.r.** Aceptaremos sin prueba el siguiente resultado. Su prueba es rutinaria y se basa en el Lema 5 (ver el apunte).

**Lema 8 (Lema de minimización acotada de variable alfabética).** Supongamos que \(\Sigma\ne\emptyset\). Sea \(\le\) un orden total sobre \(\Sigma\), sean \(n,m\ge 0\) y sea \(P:D_P\subseteq\omega^n\times\Sigma^{\ast m}\times\Sigma^\ast\to\omega\) un predicado \(\Sigma\)-p.r.. Entonces

**(a)** \(M^\le(P)\) es \(\Sigma\)-recursiva.

**(b)** Si existe una función \(\Sigma\)-p.r. \(f:\omega^n\times\Sigma^{\ast m}\to\omega\) tal que

\[
|M^\le(P)(\overrightarrow{x},\overrightarrow{\alpha})|
=|\min_\alpha^\le P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)|
\le f(\overrightarrow{x},\overrightarrow{\alpha}),
\quad\text{para cada }(\overrightarrow{x},\overrightarrow{\alpha})\in D_{M^\le(P)},
\]

entonces \(M^\le(P)\) es \(\Sigma\)-p.r..

**Ejercicio 21:** Pruebe que la función \(U\) del ejemplo anterior es \(\Sigma\)-p.r.. Por qué se eligieron los nombres \(Dir\) y \(U\)?

**Ejercicio 22:** Dada una palabra \(\alpha\in\Sigma^\ast\), si hay una palabra \(\rho\) tal que \(\rho^2=\alpha\), usaremos \(\sqrt{\alpha}\) para denotar a \(\rho\). Nótese que la expresión \(\sqrt{\alpha}\) tiene sentido o está definida sólo para ciertas palabras. Pruebe que \(\lambda\alpha[\sqrt{\alpha}]\) es \(\Sigma\)-p.r..

**Ejercicio 23:** Sea \(\Sigma=\{\text{@},\%,\text{!},\$\}\). Sea \(\le\) un orden total sobre \(\Sigma\). Sea

\[
F=\lambda\alpha_1[\max\{\alpha\in\Sigma^\ast:\alpha\text{ ocurre en }\alpha_1\text{ y }\alpha\text{ es capicúa}\}]
\]

(aquí el máximo es tomado respecto del orden total de \(\Sigma^\ast\) inducido por \(\le\)). Pruebe que \(F\) es \(\Sigma\)-p.r..

**Ejercicio 24:** Sea \(F:\Sigma^\ast\to\Sigma^\ast\) dada por \(F(\alpha)=\text{tramo inicial capicúa más largo de }\alpha\). Pruebe que \(F\) es \(\Sigma\)-p.r.. (Hint: use la REGLA U).

**Ejercicio 25:** Sea \(\Sigma=\{\text{@},\bigcirc,\%,\square\}\). Sea \(\le\) un orden total sobre \(\Sigma\). Sea \(L=\{\alpha\beta:\alpha\in\{\text{@},\bigcirc\}^\ast\text{ y }\beta\in\{\%,\square\}^\ast\}\). Sea \(F:L\to\{\%,\square\}^\ast\) dada por \(F(\alpha\beta)=\beta\), cada vez que \(\alpha\in\{\text{@},\bigcirc\}^\ast\) y \(\beta\in\{\%,\square\}^\ast\).

**(a)** Explique por qué la definición de \(F\) es inambigua

**(b)** Encuentre un predicado \(P\) el cual sea \(\Sigma\)-p.r., cumpla que \(D_P=\Sigma^\ast\times\Sigma^\ast\) y además \(F=M^\le(P)\).

**(c)** Pruebe que \(F\) es \(\Sigma\)-p.r..

**Ejercicio 26:** Sea \(\Sigma=\{\text{@},\%,\text{!},\$\}\). Sea \(\le\) un orden total sobre \(\Sigma\). Sea

\[
F=\lambda\beta[\max\{\gamma\in\Sigma^\ast:\gamma\text{ ocurre en }\beta\text{ y }\gamma\in\{\text{@},\%\}^\ast\}]
\]

(aquí el máximo es tomado respecto del orden total de \(\Sigma^\ast\) inducido por \(\le\)). Pruebe que \(F\) es \(\Sigma\)-p.r..

**Ejercicio 27:** Sea \(M=(Q,\Sigma,\Gamma,\delta,q_0,B,F)\) una máquina de Turing y supongamos \(Q\) es un alfabeto disjunto con \(\Gamma\). Usaremos la notación lambda respecto del alfabeto \(\Gamma\cup Q\). Sea \(\le\) un orden total sobre \(\Gamma\cup Q\).

**(a)** Sea \(P=\lambda\alpha_1\alpha[\alpha\in Q\text{ y }\alpha\text{ ocurre en }\alpha_1]\). Encuentre \(D_{M^\le(P)}\). Qué relación hay entre la función \(St:Des\to Q\) y \(M^\le(P)\)

**(b)** Encuentre un predicado \(R\) (modificando \(P\)) tal que \(M^\le(R)=St\).

**(c)** Pruebe que \(St\) es \((\Gamma\cup Q)\)-p.r.

(Puede usar que \(Des\) es un conjunto \((\Gamma\cup Q)\)-p.r.).

## Conjuntos \(\Sigma\)-recursivamente enumerables

Ya que la noción de función \(\Sigma\)-recursiva es el modelo matemático Gödeliano del concepto de función \(\Sigma\)-efectivamente computable, nos podríamos preguntar entonces cuál es el modelo matemático Gödeliano del concepto de conjunto \(\Sigma\)-efectivamente enumerable. Si prestamos atención a la definición de conjunto \(\Sigma\)-efectivamente enumerable, notaremos que depende de la existencia de ciertas funciones \(\Sigma\)-efectivamente computables por lo cual la siguiente definición cae de maduro:

Diremos que un conjunto \(S\subseteq\omega^n\times\Sigma^{\ast m}\) será llamado \(\Sigma\)-recursivamente enumerable cuando sea vacío o haya una función \(F:\omega\to\omega^n\times\Sigma^{\ast m}\) tal que \(I_F=S\) y \(F_{(i)}\) sea \(\Sigma\)-recursiva, para cada \(i\in\{1,\ldots,n+m\}\).

Debería entonces quedar claro que si el concepto de función \(\Sigma\)-recursiva modeliza correctamente al concepto de función \(\Sigma\)-efectivamente computable, entonces el concepto de conjunto \(\Sigma\)-recursivamente enumerable recién definido modeliza correctamente al concepto de conjunto \(\Sigma\)-efectivamente enumerable. Sin embargo para probar algunos de los resultados básicos acerca de los conjuntos \(\Sigma\)-recursivamente enumerables, deberemos esperar a tener probada la equivalencia del paradigma Gödeliano con el imperativo.

## Conjuntos \(\Sigma\)-recursivos

La versión Gödeliana del concepto de conjunto \(\Sigma\)-efectivamente computable es fácil de dar: un conjunto \(S\subseteq\omega^n\times\Sigma^{\ast m}\) será llamado \(\Sigma\)-recursivo cuando la función \(\chi_S^{\omega^n\times\Sigma^{\ast m}}\) sea \(\Sigma\)-recursiva. Todo conjunto \(\Sigma\)-recursivo es \(\Sigma\)-recursivamente enumerable pero esto lo probaremos más adelante junto con otros resultados básicos sobre conjuntos \(\Sigma\)-r.e., los cuales se prueban usando el paradigma imperativo. Más adelante daremos un ejemplo natural de un conjunto que es \(\Sigma\)-r.e. pero el cual no es \(\Sigma\)-recursivo.

**Ejercicio 28:** Sea \(\Sigma\) un alfabeto finito.

**(a)** Si \(P:S\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) y \(Q:S\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) son predicados \(\Sigma\)-r., entonces \((P\lor Q)\), \((P\land Q)\) y \(\neg P\) lo son también.

**(b)** Supongamos \(S_1,S_2\subseteq\omega^n\times\Sigma^{\ast m}\) son conjuntos \(\Sigma\)-recursivos. Entonces \(S_1\cup S_2\), \(S_1\cap S_2\) y \(S_1-S_2\) son \(\Sigma\)-recursivos

## Independencia del alfabeto

El siguiente resultado es conceptualmente muy importante. Su prueba tiene cierta dificultad técnica por lo cual la omitiremos. Se la puede ver en el apunte.

**Teorema 9.** Sean \(\Sigma\) y \(\Gamma\) alfabetos finitos cualesquiera.

**(a)** Supongamos una función \(f\) es \(\Sigma\)-mixta y \(\Gamma\)-mixta, entonces \(f\) es \(\Sigma\)-recursiva (resp. \(\Sigma\)-p.r.) sii \(f\) es \(\Gamma\)-recursiva (resp. \(\Gamma\)-p.r.)

**(b)** Supongamos un conjunto \(S\) es \(\Sigma\)-mixto y \(\Gamma\)-mixto, entonces \(S\) es \(\Sigma\)-recursivo (resp. \(\Sigma\)-r.e., \(\Sigma\)-p.r.) sii \(S\) es \(\Gamma\)-recursivo (resp. \(\Gamma\)-r.e., \(\Gamma\)-p.r.)

**Ejercicio 29:** Explique con palabras por qué no es obvio el resultado anterior

**Ejercicio 30:** Qué hubiera implicado acerca de la completitud del modelo Gödeliano el hecho de que no fuera cierto **(a)** del teorema anterior?

## Ejercicios de examen

Cada resultado teórico que aplique en la resolución deberá enunciarlo por separado detalladamente (en la forma en la que está en las guías). Para los ejercicios listados a continuación puede usar sin demostración que las siguientes funciones son \(\Sigma\)-p.r.: \(Suc\), \(Pred\), \(d_a\) (con \(a\in\Sigma\)), \(p_j^{n,m}\) (con \(n,m,j\in\omega\) y \(1\le j\le n+m\)), \(\lambda xy[x\le y]\), \(\lambda\alpha[|\alpha|]\), \(\lambda xy[x=y]\), \(\lambda\alpha\beta[\alpha=\beta]\), \(\lambda xy[x+y]\), \(\lambda xy[x.y]\), \(\lambda x[x!]\), \(\lambda xy[x\mathbin{\dot{-}}y]\), \(\lambda x\alpha[\alpha^x]\), \(\lambda xy[x^y]\), \(\lambda\alpha[\alpha^R]\), \(\lambda i\alpha[[\alpha]_i]\), \(C_k^{n,m}\), \(C_\alpha^{n,m}\) (con \(n,m,k\in\omega\) y \(\alpha\in\Sigma^\ast\)), \(s^\le\), \(\#^\le\) y \(\ast^\le\) (\(\le\) un orden total sobre \(\Sigma\)), \(\lambda xy[x\text{ divide a }y]\), \(\lambda\alpha\beta[\alpha\text{ ocurre en }\beta]\), \(\lambda\alpha\beta[\alpha\text{ es tramo inicial de }\beta]\), \(\lambda x[x\text{ es impar}]\). También puede usar que si \(\Gamma\subseteq\Sigma\) entonces \(\Gamma^+\) y \(\Gamma^\ast\) son conjuntos \(\Sigma\)-p.r..

**(1)** Pruebe que la función \(pr\) es \(\Sigma\)-p.r.. Puede usar sin demostración que

\[
\min_i(i\text{ es primo}\land i>A)\le A!+1,\quad\text{para cada }A\in\omega
\]

**(2)** Dados \(x,y\in\omega\) tales que \(x\ne 0\) o \(y\ne 0\), usaremos \(mcd(x,y)\) para denotar el máximo común divisor de \(x\) e \(y\), es decir el mayor número que divide a \(x\) y divide a \(y\). Note que la función \(M=\lambda xy[mcd(x,y)]\) tiene dominio igual a \(\omega^2-\{(0,0)\}\). Pruebe que \(M\) es \(\Sigma\)-p.r..

**(3)** Sea \(\Sigma\) un alfabeto finito.

**(a)** Pruebe que \(\lambda xi[(x)_i]\) es \(\Sigma\)-p.r. (Hint: repase el significado de la expresión \((x)_i\) y encuentre entonces el dominio de \(\lambda xi[(x)_i]\) antes de hacer el ejercicio)

**(b)** Pruebe que la función \(Lt\) es \(\Sigma\)-p.r.

Puede usar que \(pr\) es \(\Sigma\)-p.r..

**(4)** Sea \(\Sigma=\{\text{@},\text{!},\%,\text{?}\}\). Sea \(f:\Sigma^\ast\to\omega\) dada por:

\[
f(\alpha)=\max\{|\beta|:\beta\text{ ocurre en }\alpha\text{ y }\beta\in\{\%,\text{?}\}^\ast\}
\]

Pruebe que \(f\) es \(\Sigma\)-p.r.. Ojo, puede haber un \(\beta\in\{\%,\text{?}\}^\ast\) que ocurra en \(\alpha\) de manera "inextensible" pero que \(f(\alpha)\) no sea igual a \(|\beta|\).

**(5)** Sea \(\Sigma=\{\text{@},\text{!},\%\}\). Sea \(L=\{\text{@}\}^\ast\cup\{\text{!}\}^\ast\cup\{\%\}^\ast\). Sea \(f:\Sigma^\ast\to\omega\) dada por:

\[
f(\alpha)=\max\{|\beta|:\beta\text{ ocurre en }\alpha\text{ y }\beta\in L\}
\]

Pruebe que \(f\) es \(\Sigma\)-p.r.. Ojo, puede haber un \(\beta\in L\) que ocurra en \(\alpha\) de manera "inextensible" pero que \(f(\alpha)\) no sea igual a \(|\beta|\).

**(6)** Sea \(\Sigma=\{\text{@},\text{!},\%\}\). Sea \(F=\lambda\alpha\beta[\max\{t\in\mathbf{N}:\alpha^t\text{ es tramo inicial de }\beta\}]\).

**(a)** Encuentre (según manda notación lambda) el dominio de \(F\)

**(b)** Pruebe que \(F\) es \(\Sigma\)-p.r..

**(7)** Sea \(\Sigma=\{\text{@},\text{!},\%\}\). Sea \(F=\lambda\beta[\max\{t\in\mathbf{N}:\text{@}^t\text{ es tramo inicial de }\beta\}]\).

**(a)** Encuentre (según manda notación lambda) el dominio de \(F\)

**(b)** Pruebe que \(F\) es \(\Sigma\)-p.r..

**(8)** Sea \(\Sigma=\{\text{@},\text{!},\%\}\). Sea \(F=\lambda\beta[\max\{t\in\omega:\text{@}^t\text{ ocurre en }\beta\text{ y }t\text{ es impar}\}]\).

**(a)** Encuentre (según manda notación lambda) el dominio de \(F\)

**(b)** Pruebe que \(F\) es \(\Sigma\)-p.r..

**(9)** Sea \(\Sigma=\{\text{@},\text{!},\%\}\). Sea \(F=\lambda x[\max\{t\in\omega:t^2+5\le x\text{ y }t\text{ es impar}\}]\).

**(a)** Encuentre (según manda notación lambda) el dominio de \(F\)

**(b)** Pruebe que \(F\) es \(\Sigma\)-p.r..

**(10)** Sea \(\Sigma=\{\text{@},\text{!},\%\}\). Sea \(F=\lambda xy[\max\{t\in\omega:x\le t^2\le y\}]\).

**(a)** Encuentre (según manda notación lambda) el dominio de \(F\)

**(b)** Pruebe que \(F\) es \(\Sigma\)-p.r..

**(11)** Sea \(\Sigma=\{\text{@},\bigcirc,\%,\square\}\). Sea \(\le\) un orden total sobre \(\Sigma\). Sea \(L=\{\alpha\beta:\alpha\in\{\text{@},\bigcirc\}^\ast\text{ y }\beta\in\{\%,\square\}^\ast\}\). Sea \(F:L\to\{\%,\square\}^\ast\) dada por \(F(\alpha\beta)=\beta\), cada vez que \(\alpha\in\{\text{@},\bigcirc\}^\ast\) y \(\beta\in\{\%,\square\}^\ast\).

**(a)** Explique por qué la definición de \(F\) es inambigua

**(b)** Encuentre un predicado \(P\) el cual sea \(\Sigma\)-p.r., cumpla que \(D_P=\Sigma^\ast\times\Sigma^\ast\) y además \(F=M^\le(P)\).

**(c)** Pruebe que \(F\) es \(\Sigma\)-p.r..

**(12)** Sea \(\Sigma=\{\text{@},\bigcirc,\%,\text{!},\$\}\). Sea \(\le\) un orden total sobre \(\Sigma\). Diremos que \(\alpha\in\Sigma^\ast\) es un auto si \(|\alpha|_{\bigcirc}=2\). Sea \(Au=\{\alpha\in\Sigma^\ast:\alpha\text{ es un auto}\}\). Obviamente todo auto se escribe unívocamente en la forma \(\alpha_1\bigcirc\alpha_2\bigcirc\alpha_3\), con \(\alpha_1,\alpha_2,\alpha_3\in\{\text{@},\%,\text{!},\$\}^\ast\).

**(a)** Explique el "unívocamente"

**(b)** Sea \(F:Au\to\Sigma^\ast\) dada por \(F(\alpha_1\bigcirc\alpha_2\bigcirc\alpha_3)=\alpha_2\), cada vez que \(\alpha_1,\alpha_2,\alpha_3\in\{\text{@},\%,\text{!},\$\}^\ast\). Pruebe que \(F\) es \(\Sigma\)-p.r..

**(13)** Sea \(\Sigma=\{\text{@},\%,\text{!},\$\}\). Sea \(\le\) un orden total sobre \(\Sigma\). Sea

\[
F=\lambda\beta[\max\{\gamma\in\Sigma^\ast:\gamma\text{ ocurre en }\beta\text{ y }\gamma\in\{\text{@},\%\}^\ast\}]
\]

(aquí el máximo es tomado respecto del orden total de \(\Sigma^\ast\) inducido por \(\le\)). Pruebe que \(F\) es \(\Sigma\)-p.r..

**(14)** Sea \(\Sigma=\{\text{@},\%,\text{!},\$\}\). Sea \(\le\) un orden total sobre \(\Sigma\). Sea

\[
F=\lambda\alpha\beta[\max\{\rho\in\{\%,\text{!}\}^+:\rho\text{ es tramo inicial de }\alpha\text{ y }\beta\}]
\]

(aquí el máximo es tomado respecto del orden total de \(\Sigma^\ast\) inducido por \(\le\)).

**(a)** Encuentre (según manda notación lambda) el dominio de \(F\)

**(b)** Pruebe que \(F\) es \(\Sigma\)-p.r..

**(15)** Sea \(M=(Q,\Sigma,\Gamma,\delta,q_0,B,F)\) una máquina de Turing y supongamos \(Q\) es un alfabeto disjunto con \(\Gamma\). Usaremos la notación lambda respecto del alfabeto \(\Gamma\cup Q\). Sea \(\le\) un orden total sobre \(\Gamma\cup Q\).

**(a)** Sea \(P=\lambda\alpha_1\alpha[\alpha\in Q\text{ y }\alpha\text{ ocurre en }\alpha_1]\). Encuentre \(D_{M^\le(P)}\). Qué relación hay entre la función \(St:Des\to Q\) y \(M^\le(P)\)

**(b)** Encuentre un predicado \(R\) (modificando \(P\)) tal que \(M^\le(R)=St\).

**(c)** Pruebe que \(St\) es \((\Gamma\cup Q)\)-p.r.

(Puede usar que \(Des\) es un conjunto \((\Gamma\cup Q)\)-p.r.).
