# GUÍA 5 DE LENGUAJES: FUNCIONES \(\Sigma\)-RECURSIVAS PRIMITIVAS

## El paradigma de Gödel: Funciones \(\Sigma\)-recursivas

En esta guía y la siguiente desarrollaremos el modelo matemático del concepto de función \(\Sigma\)-efectivamente computable, dado por Gödel. Dichas funciones serán llamadas \(\Sigma\)-recursivas. La idea es partir de un conjunto inicial de funciones muy simples y obviamente \(\Sigma\)-efectivamente computables y luego obtener nuevas funciones \(\Sigma\)-efectivamente computables usando constructores que preservan la computabilidad efectiva. Las funciones \(\Sigma\)-recursivas serán las que se obtienen iterando el uso de estos constructores, partiendo del conjunto inicial de funciones antes mencionado. Nos referiremos a este paradigma como el paradigma Gödeliano o recursivo. A veces también lo llamaremos el paradigma funcional.

La familia de funciones simples y obviamente \(\Sigma\)-efectivamente computables de la que partiremos es la siguiente

\[
\{Suc, Pred, C_0^{0,0}, C_\varepsilon^{0,0}\}\cup\{d_a:a\in\Sigma\}\cup\{p_j^{n,m}:1\le j\le n+m\}
\]

Los constructores que usaremos son:

- Composición
- Recursión primitiva
- Minimización de predicados totales

Estos constructores nos permiten dadas ciertas funciones construir o definir una nueva función y tienen la propiedad de preservar la computabilidad efectiva en el sentido que si las funciones iniciales son \(\Sigma\)-efectivamente computables, entonces la función obtenida también lo es. Un concepto fundamental es el de función \(\Sigma\)-recursiva primitiva. Estas funciones serán aquellas que se obtienen a partir de las del conjunto inicial usando solo los dos primeros constructores: composición y recursión primitiva. Nuestro primer objetivo es definir el concepto de función \(\Sigma\)-recursiva primitiva para lo cual en las próximas dos secciones definiremos y estudiaremos los constructores de composición y recursión primitiva. Luego definiremos el concepto de función \(\Sigma\)-recursiva primitiva y nos abocaremos a desarrollar este concepto fundamental. Recién después ya en la Guía 6 estudiaremos el constructor de minimización y definiremos el concepto de función \(\Sigma\)-recursiva.

**Composición.** Dadas funciones \(\Sigma\)-mixtas \(f, f_1,\ldots,f_r\), con \(r\ge 1\), diremos que la función \(f\circ[f_1,\ldots,f_r]\) es obtenida por composición a partir de las funciones \(f,f_1,\ldots,f_r\). Un hecho que a priori no es obvio es que si \(f,f_1,\ldots,f_r\) son \(\Sigma\)-mixtas, entonces \(f\circ[f_1,\ldots,f_r]\) lo es. Esto es consecuencia del siguiente lema.

**Lema 1.** Supongamos que \(f,f_1,\ldots,f_r\) son funciones \(\Sigma\)-mixtas, con \(r\ge 1\). Supongamos además que \(f\circ[f_1,\ldots,f_r]\ne\emptyset\). Entonces hay \(n,m,k,l\in\omega\) y \(s\in\{\#, \ast\}\) tales que

- \(r=n+m\)
- \(f\) es de tipo \((n,m,s)\)
- \(f_i\) es de tipo \((k,l,\#)\), para cada \(i=1,\ldots,n\)
- \(f_i\) es de tipo \((k,l,\ast)\), para cada \(i=n+1,\ldots,n+m\)

Más aún, en tal caso la función \(f\circ[f_1,\ldots,f_{n+m}]\) es de tipo \((k,l,s)\) y:

\[
D_{f\circ[f_1,\ldots,f_{n+m}]}=
\left\{
(\overrightarrow{x},\overrightarrow{\alpha})\in\bigcap_{i=1}^{n+m}D_{f_i}:
(f_1(\overrightarrow{x},\overrightarrow{\alpha}),\ldots,f_{n+m}(\overrightarrow{x},\overrightarrow{\alpha}))\in D_f
\right\}
\]

\[
f\circ[f_1,\ldots,f_{n+m}](\overrightarrow{x},\overrightarrow{\alpha})
=f(f_1(\overrightarrow{x},\overrightarrow{\alpha}),\ldots,f_{n+m}(\overrightarrow{x},\overrightarrow{\alpha})).
\]

**Ejercicio 1:** Justifique con palabras la veracidad del lema anterior (a lo mariposa)

Ahora sí es fácil probar que la composición preserva la computabilidad efectiva. Más formalmente:

**Lema 2.** Si \(f,f_1,\ldots,f_r\), con \(r\ge 1\), son \(\Sigma\)-efectivamente computables, entonces \(f\circ[f_1,\ldots,f_r]\) lo es.

**Proof.** Si \(f\circ[f_1,\ldots,f_r]=\emptyset\), entonces claramente es \(\Sigma\)-efectivamente computable. Supongamos entonces que \(f\circ[f_1,\ldots,f_r]\ne\emptyset\). Por el lema anterior hay \(n,m,k,l\in\omega\) y \(s\in\{\#,\ast\}\) tales que

- \(r=n+m\)
- \(f\) es de tipo \((n,m,s)\)
- \(f_i\) es de tipo \((k,l,\#)\), para cada \(i=1,\ldots,n\)
- \(f_i\) es de tipo \((k,l,\ast)\), para cada \(i=n+1,\ldots,n+m\)

Sean \(P,P_1,\ldots,P_{n+m}\) procedimientos efectivos los cuales computen las funciones \(f,f_1,\ldots,f_{n+m}\), respectivamente. Usando estos procedimientos es fácil definir un procedimiento efectivo el cual compute a \(f\circ[f_1,\ldots,f_{n+m}]\)

**Ejercicio 2:** Complete la prueba anterior

**Recursión primitiva.** La recursión primitiva es un tipo muy particular de recursión. Más adelante lo definiremos matemáticamente pero antes daremos varios ejemplos para aproximarnos gradualmente a la definición. Consideremos por ejemplo las siguientes ecuaciones:

1. \(R(0)=1\)
2. \(R(t+1)=1+R(t)+R(t)^2\)

Nótese que hay una única función \(R:\omega\to\omega\) la cual cumple (1) y (2). Esto es ya que el valor de \(R\) en \(t\) está determinado por sucesivas aplicaciones de las ecuaciones (1) y (2). Por ejemplo la ecuación (1) nos dice que \(R(0)=1\) pero entonces la ecuación (2) nos dice que \(R(1)=1+1+1^2=3\) por lo cual nuevamente la ecuación (2) nos dice que \(R(2)=1+3+3^2=13\) y así podemos notar fácilmente que \(R\) está determinada por dichas ecuaciones.

Se suele decir que las ecuaciones (1) y (2) definen recursivamente a la función \(R\) pero hay que tener cuidado porque esto es una manera de hablar ya que la función \(R\) podría en nuestro discurso ya haber sido definida de otra manera. Más propio es pensar que dichas ecuaciones determinan a \(R\) en el sentido que \(R\) es la única que las cumple. Por ejemplo las ecuaciones:

**(a)** \(R(0)=50\)

**(b)** \(R(t+1)=R(t)\)

"definen recursivamente" a la función \(C_{50}^{1,0}\) pero está claro que la definición de \(C_{50}^{1,0}\) en esta materia no fue dada de esta forma.

**Ejercicio 3:** Encuentre ecuaciones que "definan recursivamente" a la función \(R=\lambda t[2^t]\)

Hay casos de recursiones en las cuales el valor de \(R(t+1)\) no solo depende de \(R(t)\) sino que también depende de \(t\). Por ejemplo

**(i)** \(R(0)=1\)

**(ii)** \(R(t+1)=t.R(t)+1\)

De todas maneras debería quedar claro que las ecuaciones (i) y (ii) determinan una única función \(R:\omega\to\omega\) que las satisface.

**Ejercicio 4:** Encuentre ecuaciones que "definan recursivamente" a la función \(R=\lambda t[t!]\)

También podemos generalizar pensando que la función \(R\) depende no solo de un parámetro \(t\) sino que tiene otras variables. Por ejemplo

**(p)** \(R(0,x_1,x_2,x_3)=x_1+2x_3\)

**(q)** \(R(t+1,x_1,x_2,x_3)=t+x_1+x_2+x_3+R(t,x_1,x_2,x_3)\)

**Ejercicio 5:** Explique con palabras por qué las ecuaciones (p) y (q) determinan una única función \(R:\omega^4\to\omega\). Cuánto vale \(R(3,1,2,3)\)?

Por supuesto la cantidad de variables extra puede ser cualquiera y no justo 3.

**Ejercicio 6:** Encuentre ecuaciones que "definan recursivamente" a la función \(R=\lambda tx_1[t+x_1]\), usando la función \(Suc\).

También podríamos tener variables alfabéticas. Por ejemplo consideremos

**(r)** \(R(0,x_1,x_2,\alpha_1,\alpha_2)=x_1+|\alpha_1|^{x_2}\)

**(s)** \(R(t+1,x_1,x_2,\alpha_1,\alpha_2)=t+x_1+x_2+|\alpha_1|+|\alpha_2|+R(t,x_1,x_2,\alpha_1,\alpha_2)\)

Es claro aquí que las ecuaciones (r) y (s) determinan una única función \(R:\omega^3\times\Sigma^{\ast 2}\to\omega\) que las cumple. Esto se puede explicar de la siguiente manera:

- La ecuación (r) determina los valores de \(R\) sobre el conjunto \(\{0\}\times\omega\times\omega\times\Sigma^\ast\times\Sigma^\ast\). Pero una vez determinados estos valores, la ecuación (s) tomada con \(t=0\), determina los valores de \(R\) sobre el conjunto \(\{1\}\times\omega\times\omega\times\Sigma^\ast\times\Sigma^\ast\). Pero una vez determinados estos valores, la ecuación (s) tomada con \(t=1\), determina los valores de \(R\) sobre el conjunto \(\{2\}\times\omega\times\omega\times\Sigma^\ast\times\Sigma^\ast\), etc

El caso anterior podría generalizarse de la siguiente manera: Si tenemos dadas dos funciones

\[
f:\omega^n\times\Sigma^{\ast m}\to\omega
\]

\[
g:\omega^{n+2}\times\Sigma^{\ast m}\to\omega
\]

entonces las ecuaciones:

**(a)** \(R(0,\overrightarrow{x},\overrightarrow{\alpha})=f(\overrightarrow{x},\overrightarrow{\alpha})\)

**(b)** \(R(t+1,\overrightarrow{x},\overrightarrow{\alpha})=g(R(t,\overrightarrow{x},\overrightarrow{\alpha}),t,\overrightarrow{x},\overrightarrow{\alpha})\)

determinan una única función \(R:\omega^{n+1}\times\Sigma^{\ast m}\to\omega\) que las cumple. Nótese que para el caso

\[
\begin{aligned}
n&=m=2\\
f&=\lambda x_1x_2\alpha_1\alpha_2[x_1+|\alpha_1|^{x_2}]\\
g&=\lambda xtx_1x_2\alpha_1\alpha_2[t+x_1+x_2+|\alpha_1|+|\alpha_2|+x]
\end{aligned}
\]

las ecuaciones (a) y (b) se transforman en las ecuaciones (r) y (s).

**Conjuntos rectangulares.** El primer caso de recursión primitiva que definiremos a continuación engloba todos los ejemplos vistos recién dentro de un marco general. Para enunciarlo necesitaremos una definición muy importante en la materia. Sea \(\Sigma\) un alfabeto finito. Un conjunto \(\Sigma\)-mixto \(S\) es llamado rectangular si es de la forma

\[
S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m
\]

con cada \(S_i\subseteq\omega\) y cada \(L_i\subseteq\Sigma^\ast\). Notar que todo subconjunto de \(\omega\) es rectangular (es el caso \(n=1\) y \(m=0\)). Análogamente, todo subconjunto de \(\Sigma^\ast\) es rectangular (es el caso \(n=0\) y \(m=1\)). También \(\{\diamond\}\) es rectangular (es el caso \(n=m=0\)). Otros ejemplos:

- \(\mathbf{N}\times\{1,2\}\times\{@@,\varepsilon\}\) es rectangular (aquí \(n=2\) y \(m=1\))
- \(\{!!!,!!\}\times\{@@,\varepsilon\}\) es rectangular (aquí \(n=0\) y \(m=2\))

También nótese que \(\emptyset=\emptyset\times\emptyset\) por lo cual \(\emptyset\) es un conjunto rectangular.

El concepto de conjunto rectangular es muy importante en nuestro enfoque. Aunque en general no habrá restricciones acerca del dominio de las funciones y predicados, nuestra filosofía será tratar en lo posible que los dominios de las funciones que utilicemos para hacer nuestro análisis de recursividad de los distintos paradigmas, sean rectangulares.

Aunque en principio puede parecer que todos los conjuntos son rectangulares, el siguiente lema mostrará cuán ingenua es esta visión. Lo aceptaremos sin demostración aunque es fácil de probar.

**Lema 3.** Sea \(S\subseteq\omega\times\Sigma^\ast\). Entonces \(S\) es rectangular si y solo si se cumple la siguiente propiedad:

**(R)** Si \((x,\alpha),(y,\beta)\in S\), entonces \((x,\beta)\in S\)

**Ejercicio 7:** Supongamos \(\Sigma=\{\#,\blacktriangle,\%\}\). Use el lema anterior para probar que \(\{(0,\#\#),(1,\%\%\%)\}\) y \(\{(x,\alpha)\in\omega\times\Sigma^\ast:|\alpha|=x\}\) no son rectangulares.

**Recursión primitiva sobre variable numérica con valores numéricos.** Ahora sí daremos el primer caso del constructor de recursión primitiva. Supongamos tenemos dadas funciones

\[
f:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega
\]

\[
g:\omega\times\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega
\]

con \(S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) conjuntos no vacíos. Usando el razonamiento inductivo usado en los ejemplos anteriores, se puede probar que hay una única función

\[
R:\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega
\]

la cual cumple las ecuaciones

- \(R(0,\overrightarrow{x},\overrightarrow{\alpha})=f(\overrightarrow{x},\overrightarrow{\alpha})\)
- \(R(t+1,\overrightarrow{x},\overrightarrow{\alpha})=g(R(t,\overrightarrow{x},\overrightarrow{\alpha}),t,\overrightarrow{x},\overrightarrow{\alpha})\)

Llamaremos \(R(f,g)\) a esta única función que cumple las ecuaciones anteriores. Resumiendo este hecho, diremos que las ecuaciones

**(1)** \(R(f,g)(0,\overrightarrow{x},\overrightarrow{\alpha})=f(\overrightarrow{x},\overrightarrow{\alpha})\)

**(2)** \(R(f,g)(t+1,\overrightarrow{x},\overrightarrow{\alpha})=g(R(f,g)(t,\overrightarrow{x},\overrightarrow{\alpha}),t,\overrightarrow{x},\overrightarrow{\alpha})\)

definen recursivamente a la función \(R(f,g)\). También diremos que \(R(f,g)\) es obtenida por recursión primitiva a partir de \(f\) y \(g\).

**NOTA IMPORTANTE:** No confundirse y pensar que \(R(f,g)\) es el resultado de aplicar una función \(R\) al par \((f,g)\), de hecho hasta el momento no hemos definido ninguna función \(R\) cuyo dominio sea cierto conjunto de pares ordenados de funciones!

**Ejercicio 8:** Justifique con palabras (a lo mariposa sabia) que la función \(R(f,g)\) está bien definida, es decir que dada una \((1+n+m)\)-upla \((t,\overrightarrow{x},\overrightarrow{\alpha})\) perteneciente a \(\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\), las ecuaciones de (1) y (2) determinan el valor \(R(f,g)(t,\overrightarrow{x},\overrightarrow{\alpha})\)

Nótese que cuando \(n=m=0\), se tiene que \(D_f=\{\diamond\}\) y (1) y (2) se transforman en

**(1)** \(R(f,g)(0)=f(\diamond)\)

**(2)** \(R(f,g)(t+1)=g(R(f,g)(t),t)\)

Veamos algunos ejemplos

**(E1)** Tomemos \(f=p_1^{1,0}\) y \(g=Suc\circ p_1^{3,0}\). De la definición de \(R(f,g)\), obtenemos que su dominio es \(\omega^2\) y

\[
R(f,g)(0,x_1)=p_1^{1,0}(x_1)=x_1
\]

\[
R(f,g)(t+1,x_1)=(Suc\circ p_1^{3,0})(R(f,g)(t,x_1),t,x_1)=R(f,g)(t,x_1)+1
\]

Es fácil notar que la única función que cumple estas dos ecuaciones es \(\lambda tx_1[t+x_1]\), lo cual implica que

\[
\lambda tx_1[t+x_1]=R(p_1^{1,0},Suc\circ p_1^{3,0})
\]

**(E2)** Sean \(f=C_0^{0,0}\) y \(g=p_1^{2,0}\). De la definición de \(R(f,g)\), obtenemos que su dominio es \(\omega\) y

\[
R(f,g)(0)=C_0^{0,0}(\diamond)=0
\]

\[
R(f,g)(t+1)=p_1^{2,0}(R(f,g)(t),t)=R(f,g)(t)
\]

Es fácil notar que la única función que cumple estas dos ecuaciones es \(C_0^{1,0}\) lo cual implica que

\[
C_0^{1,0}=R(C_0^{0,0},p_1^{2,0})
\]

**Nota importante:** En los dos ejemplos anteriores y en todos los casos que manejaremos en la Guía 5, en las aplicaciones del constructor de recursión primitiva (en sus cuatro formas) las funciones iniciales serán \(\Sigma\)-totales (es decir \(S_1=\cdots=S_n=\omega\) y \(L_1=\cdots=L_m=\Sigma^\ast\)). Solo a partir de la Guía 6 veremos aplicaciones con funciones no \(\Sigma\)-totales

Recordemos que por definición teniamos que \(0^0=1\). Esto nos dice que \(D_{\lambda xy[x^y]}=\omega\times\omega\).

**Ejercicio 9:** Encuentre \(f\) y \(g\) tales que:

**(a)** \(R(f,g)=C_k^{n,m}\) (con \(n,m,k\in\omega\) y \(n\ge 1\))

**(b)** \(R(f,g)=\lambda tx_1[t.x_1]\)

**(c)** \(R(f,g)=\lambda tx_1\alpha_1\alpha_2[t.x_1]\)

**(d)** \(R(f,g)=\lambda tx_1[(x_1)^t]\)

**(e)** \(R(f,g)=\lambda t[t!]\)

**Ejercicio 10:** Explique la forma en la que aplicando los constructores de composición y recursión primitiva a las funciones del conjunto inicial se puede obtener la función \(\lambda x_1x_2\alpha_1[x_1!]\)

**Ejercicio 11:** V o F o I, justifique.

**(a)** \(\lambda tx_1[t+x_1]=R(p_1^{1,0},Suc\circ p_1^{2,0})\)

**(b)** \(R(\lambda xy[0],p_2^{4,0})=p_1^{3,0}\)

**(c)** Si \(f:\omega^2\to\omega\) y \(g:\omega^4\to\omega\), entonces para cada \((x,y)\in\omega^2\), se tiene que

\[
R(f,g)(2,x,y)=g\circ(g\circ[f\circ[p_2^{3,0},p_3^{3,0}],p_1^{3,0},p_2^{3,0},p_3^{3,0}])(0,x,y)
\]

Como era de esperar, este caso del constructor de recursión primitiva preserva la computabilidad efectiva

**Lema 4.** Sean

\[
f:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega
\]

\[
g:\omega\times\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega
\]

con \(S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) conjuntos no vacíos. Si \(f\) y \(g\) son \(\Sigma\)-efectivamente computables, entonces \(R(f,g)\) lo es.

**Proof.** Sean \(P_f\) y \(P_g\) procedimientos efectivos que computan a \(f\) y \(g\), respectivamente. Es fácil construir entonces un procedimiento efectivo que compute a \(R(f,g)\).

**Ejercicio 12:** Construya un procedimiento efectivo que compute a \(R(f,g)\) en términos de los procedimientos \(P_f\) y \(P_g\).

**Recursión primitiva sobre variable numérica con valores alfabéticos.** Ahora haremos el caso en el que la función definida recursivamente tiene imagen contenida en \(\Sigma^\ast\). Es claro que entonces \(f\) y \(g\) también deberán tener imagen contenida en \(\Sigma^\ast\). El único detalle a tener en cuenta en la definición de este caso es que si solo hiciéramos estos cambios y pusiéramos las mismas ecuaciones la función \(g\) no resultaría \(\Sigma\)-mixta en general (por qué?). Para que la \(g\) de la recursión siga siendo \(\Sigma\)-mixta deberemos modificar levemente su dominio en relación al caso ya hecho.

Supongamos \(\Sigma\) es un alfabeto finito. Sean

\[
f:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\Sigma^\ast
\]

\[
g:\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times\Sigma^\ast\to\Sigma^\ast
\]

con \(S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) conjuntos no vacíos. Definamos

\[
R(f,g):\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\Sigma^\ast
\]

de la siguiente manera

**(1)** \(R(f,g)(0,\overrightarrow{x},\overrightarrow{\alpha})=f(\overrightarrow{x},\overrightarrow{\alpha})\)

**(2)** \(R(f,g)(t+1,\overrightarrow{x},\overrightarrow{\alpha})=g(t,\overrightarrow{x},\overrightarrow{\alpha},R(f,g)(t,\overrightarrow{x},\overrightarrow{\alpha}))\)

Diremos que \(R(f,g)\) es obtenida por recursión primitiva a partir de \(f\) y \(g\). Nótese que cuando \(m=n=0\), se tiene que \(D_f=\{\diamond\}\) y (1) y (2) se transforman en

**(1)** \(R(f,g)(0)=f(\diamond)\)

**(2)** \(R(f,g)(t+1)=g(t,R(f,g)(t))\)

Veamos algunos ejemplos

**(E1)** Tomemos \(f=C_\varepsilon^{0,1}\) y \(g=\lambda\alpha\beta[\alpha\beta]\circ[p_3^{1,2},p_2^{1,2}]\). De la definición de \(R(f,g)\), obtenemos que

\[
R(f,g)(0,\alpha_1)=C_\varepsilon^{0,1}(\alpha_1)=\varepsilon
\]

\[
R(f,g)(t+1,\alpha_1)=\lambda\alpha\beta[\alpha\beta]\circ[p_3^{1,2},p_2^{1,2}](t,\alpha_1,R(f,g)(t,\alpha_1))=R(f,g)(t,\alpha_1)\alpha_1
\]

Es fácil notar que la única función que cumple estas dos ecuaciones es \(\lambda t\alpha_1[\alpha_1^t]\), lo cual implica que

\[
\lambda t\alpha_1[\alpha_1^t]=R(C_\varepsilon^{0,1},\lambda\alpha\beta[\alpha\beta]\circ[p_3^{1,2},p_2^{1,2}])
\]

**(E2)** Sean \(f=C_\varepsilon^{0,0}\) y \(g=p_2^{1,1}\). De la definición de \(R(f,g)\), obtenemos que

\[
R(f,g)(0)=C_\varepsilon^{0,0}(\diamond)=\varepsilon
\]

\[
R(f,g)(t+1)=p_2^{1,1}(t,R(f,g)(t))=R(f,g)(t)
\]

Es fácil notar que la única función que cumple estas dos ecuaciones es \(C_\varepsilon^{1,0}\) lo cual implica que

\[
C_\varepsilon^{1,0}=R(C_\varepsilon^{0,0},p_2^{1,1})
\]

**Ejercicio 13:** Sea \(\Sigma=\{\%,@,?\}\). Encuentre \(f\) y \(g\) tales que \(\lambda tx_1[\%@\%\%\%\%?^t]=R(f,g)\)

**Ejercicio 14:** V o F o I, justifique.

**(a)** \(C_\varepsilon^{2,2}=R(C_\varepsilon^{1,2},C_\varepsilon^{2,3})\)

**(b)** \(R(C_\varepsilon^{1,1},C_\varepsilon^{1,1})=C_\varepsilon^{1,1}\)

**(c)** Si \(f,g\) son funciones \(\Sigma\)-mixtas tales que \(R(f,g)\) está definida y es de tipo \((1+n,m,\ast)\), entonces \(f\) es de tipo \((n,m,\ast)\) y \(g\) es de tipo \((n,m+1,\ast)\)

La prueba del siguiente lema es completamente análoga a la del lema anterior que fue dejada como ejercicio.

**Lema 5.** Sean

\[
f:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\Sigma^\ast
\]

\[
g:\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times\Sigma^\ast\to\Sigma^\ast
\]

con \(S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) conjuntos no vacíos. Si \(f\) y \(g\) son \(\Sigma\)-efectivamente computables, entonces \(R(f,g)\) lo es.

**Recursión primitiva sobre variable alfabética con valores numéricos.** Ya vimos dos casos de recursión donde el parámetro o variable que comanda la recursión es numérico. Daremos a continuación un ejemplo de recursión en el cual el parámetro principal es alfabético. Sea \(\Sigma=\{\%,@,?\}\) y consideremos las siguientes ecuaciones:

**(1)** \(R(\varepsilon)=15\)

**(2)** \(R(\alpha\%)=R(\alpha)+1\)

**(3)** \(R(\alpha\text{@})=R(\alpha).5\)

**(4)** \(R(\alpha\text{?})=R(\alpha)^{20}\)

Nótese que las ecuaciones anteriores determinan una función \(R:\Sigma^\ast\to\omega\). Esto es ya que \(R\) en \(\varepsilon\) debe valer 15 y sabiendo esto las ecuaciones (2), (3) y (4) (con \(\alpha=\varepsilon\)) nos dicen que

\[
\begin{aligned}
R(\%)&=16\\
R(@)&=75\\
R(?)&=15^{20}
\end{aligned}
\]

por lo cual podemos aplicarlas nuevamente a dichas ecuaciones (con \(\alpha\in\{\%,@,?\}\)) para calcular \(R\) en todas las palabras de longitud 2; y así sucesivamente.

Daremos otro ejemplo un poco más complicado para seguir aproximándonos al caso general. Nuevamente supongamos que \(\Sigma=\{\%,@,?\}\) y supongamos tenemos una función

\[
f:\omega\times\Sigma^\ast\to\omega
\]

y tres funciones

\[
\begin{aligned}
G_\%&:\omega\times\omega\times\Sigma^\ast\times\Sigma^\ast\to\omega\\
G_@&:\omega\times\omega\times\Sigma^\ast\times\Sigma^\ast\to\omega\\
G_?&:\omega\times\omega\times\Sigma^\ast\times\Sigma^\ast\to\omega
\end{aligned}
\]

Entonces hay una única función \(R:\omega\times\Sigma^\ast\times\Sigma^\ast\to\omega\) la cual cumple las siguientes ecuaciones

**(1)** \(R(x_1,\alpha_1,\varepsilon)=f(x_1,\alpha_1)\)

**(2)** \(R(x_1,\alpha_1,\alpha\%)=G_\%(R(x_1,\alpha_1,\alpha),x_1,\alpha_1,\alpha)\)

**(3)** \(R(x_1,\alpha_1,\alpha\text{@})=G_@(R(x_1,\alpha_1,\alpha),x_1,\alpha_1,\alpha)\)

**(4)** \(R(x_1,\alpha_1,\alpha\text{?})=G_?(R(x_1,\alpha_1,\alpha),x_1,\alpha_1,\alpha)\)

**Ejercicio 15:** **(a)** Justifique que las ecuaciones anteriores determinan a la función \(R\)

**(b)** Por qué el parámetro \(\alpha\) de la recursión es la última coordenada de \(R\)?

El ejemplo anterior nos muestra que para hacer recursión sobre parámetro alfabético nos hace falta "una función \(g\) por cada símbolo de \(\Sigma\)". Esto motiva la siguiente definición. Dado un alfabeto \(\Sigma\), una familia \(\Sigma\)-indexada de funciones será una función \(\mathcal{G}\) tal que \(D_\mathcal{G}=\Sigma\) y para cada \(a\in D_\mathcal{G}\) se tiene que \(\mathcal{G}(a)\) es una función. Algunos ejemplos:

**(E1)** Sea \(\mathcal{G}\) dada por

\[
\begin{array}{rcl}
\mathcal{G}:\{\square,\%,\blacktriangle\}&\to&\{Suc,Pred\}\\
\square&\to&Suc\\
\%&\to&Suc\\
\blacktriangle&\to&Pred
\end{array}
\]

Claramente \(\mathcal{G}\) es una familia \(\{\square,\%,\blacktriangle\}\)-indexada de funciones. Notar que

\[
\mathcal{G}=\{(\square,Suc),(\%,Suc),(\blacktriangle,Pred)\}
\]

Se tiene también por ejemplo que \(\mathcal{G}(\%)=Suc\) por lo cual también es cierto que \(\mathcal{G}(\%)(22)=23\), etc.

**(E2)** Si \(\Sigma\) es un alfabeto no vacío, la función

\[
\begin{array}{rcl}
\mathcal{G}:\Sigma&\to&\{f:f\text{ es una función de }\Sigma^\ast\text{ en }\Sigma^\ast\}\\
a&\to&d_a
\end{array}
\]

es una familia \(\Sigma\)-indexada de funciones. Notar que

\[
\mathcal{G}=\{(a,d_a):a\in\Sigma\}
\]

**(E3)** Sea \(\Sigma=\{\square,\%,\blacktriangle\}\). Entonces \(\{(\square,Suc),(\%,p_3^{2,4}),(\blacktriangle,\emptyset)\}\) es una familia \(\{\square,\%,\blacktriangle\}\)-indexada de funciones.

**NOTACIÓN:** Si \(\mathcal{G}\) es una familia \(\Sigma\)-indexada de funciones, entonces para \(a\in\Sigma\), escribiremos \(\mathcal{G}_a\) en lugar de \(\mathcal{G}(a)\).

Ahora sí podemos dar la definición matemática precisa del primero de los dos casos de recursión primitiva sobre parámetro alfabético. Sea

\[
f:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega
\]

con \(S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) conjuntos no vacíos y sea \(\mathcal{G}\) una familia \(\Sigma\)-indexada de funciones tal que

\[
\mathcal{G}_a:\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times\Sigma^\ast\to\omega
\]

para cada \(a\in\Sigma\). Definamos

\[
R(f,\mathcal{G}):S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times\Sigma^\ast\to\omega
\]

de la siguiente manera

**(1)** \(R(f,\mathcal{G})(\overrightarrow{x},\overrightarrow{\alpha},\varepsilon)=f(\overrightarrow{x},\overrightarrow{\alpha})\)

**(2)** \(R(f,\mathcal{G})(\overrightarrow{x},\overrightarrow{\alpha},\alpha a)=\mathcal{G}_a(R(f,\mathcal{G})(\overrightarrow{x},\overrightarrow{\alpha},\alpha),\overrightarrow{x},\overrightarrow{\alpha},\alpha)\)

Diremos que \(R(f,\mathcal{G})\) es obtenida por recursión primitiva a partir de \(f\) y \(\mathcal{G}\).

Nótese que cuando \(n=m=0\), se tiene que \(D_f=\{\diamond\}\) y (1) y (2) se transforman en

**(1)** \(R(f,\mathcal{G})(\varepsilon)=f(\diamond)\)

**(2)** \(R(f,\mathcal{G})(\alpha a)=\mathcal{G}_a(R(f,\mathcal{G})(\alpha),\alpha)\)

**Ejercicio 16:** Sea \(\Sigma=\{\%,@,?\}\). Encuentre \(f\) y \(\mathcal{G}\) tales que

**(a)** \(\lambda\alpha[|\alpha|]=R(f,\mathcal{G})\)

**(b)** \(\lambda\alpha_1\alpha[|\alpha_1|+|\alpha|_{\text{@}}]=R(f,\mathcal{G})\)

**Ejercicio 17:** V o F o I, justifique.

**(a)** Sea \(\Sigma=\{@,\&\}\). Se tiene que \(\lambda\alpha[|\alpha|]=R(C_0^{0,0},\{Suc\circ p_1^{1,1},Suc\circ p_1^{1,1}\})\)

**(b)** \(R(p_1^{2,0},\{(@,p_1^{3,1}),(\&,p_2^{3,1})\})=p_1^{2,1}\)

Tenemos que

**Lema 6.** Sea

\[
f:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega
\]

con \(S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) conjuntos no vacíos y sea \(\mathcal{G}\) una familia \(\Sigma\)-indexada de funciones tal que

\[
\mathcal{G}_a:\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times\Sigma^\ast\to\omega
\]

para cada \(a\in\Sigma\). Si \(f\) y cada \(\mathcal{G}_a\) son \(\Sigma\)-efectivamente computables, entonces \(R(f,\mathcal{G})\) lo es.

**Ejercicio 18:** Haga la prueba del lema anterior para el caso \(\Sigma=\{@,\blacktriangle\}\)

**Recursión primitiva sobre variable alfabética con valores alfabéticos.** Supongamos \(\Sigma\) es un alfabeto finito. Sea

\[
f:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\Sigma^\ast
\]

con \(S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) conjuntos no vacíos y sea \(\mathcal{G}\) una familia \(\Sigma\)-indexada de funciones tal que

\[
\mathcal{G}_a:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times\Sigma^\ast\times\Sigma^\ast\to\Sigma^\ast
\]

para cada \(a\in\Sigma\). Definamos

\[
R(f,\mathcal{G}):S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times\Sigma^\ast\to\Sigma^\ast
\]

de la siguiente manera

**(1)** \(R(f,\mathcal{G})(\overrightarrow{x},\overrightarrow{\alpha},\varepsilon)=f(\overrightarrow{x},\overrightarrow{\alpha})\)

**(2)** \(R(f,\mathcal{G})(\overrightarrow{x},\overrightarrow{\alpha},\alpha a)=\mathcal{G}_a(\overrightarrow{x},\overrightarrow{\alpha},\alpha,R(f,\mathcal{G})(\overrightarrow{x},\overrightarrow{\alpha},\alpha))\).

Diremos que \(R(f,\mathcal{G})\) es obtenida por recursión primitiva a partir de \(f\) y \(\mathcal{G}\). Nótese que cuando \(n=m=0\), se tiene que \(D_f=\{\diamond\}\) y (1) y (2) se transforman en

**(1)** \(R(f,\mathcal{G})(\varepsilon)=f(\diamond)\)

**(2)** \(R(f,\mathcal{G})(\alpha a)=\mathcal{G}_a(\alpha,R(f,\mathcal{G})(\alpha))\)

**Ejercicio 19:** Encuentre \(f\) y \(\mathcal{G}\) tales que \(\lambda\alpha_1\alpha[\alpha_1\alpha]=R(f,\mathcal{G})\)

**Ejercicio 20:** Sea \(\Sigma=\{\triangle,\blacktriangle\}\). Diga qué función conocida es \(R(C_\varepsilon^{0,1},\mathcal{G})\), donde \(\mathcal{G}\) es dada por \(\mathcal{G}_\triangle=d_\triangle\circ p_3^{0,3}\) y \(\mathcal{G}_\blacktriangle=d_\blacktriangle\circ p_3^{0,3}\)

Sea \(\Sigma\) un alfabeto finito. Dada \(\gamma\in\Sigma^\ast\), definamos

\[
\gamma^R=
\begin{cases}
[\gamma]_{|\gamma|}[\gamma]_{|\gamma|-1}\cdots[\gamma]_1 & \text{si }|\gamma|\ge 1\\
\varepsilon & \text{caso contrario}
\end{cases}
\]

La palabra \(\gamma^R\) es llamada la recíproca de \(\gamma\). Para \(a\in\Sigma\), definamos la función

\[
\begin{array}{rcl}
I_a:\Sigma^\ast&\to&\Sigma^\ast\\
\alpha&\to&a\alpha
\end{array}
\]

Recordemos que \(\alpha^0=\varepsilon\), para cada \(\alpha\in\Sigma^\ast\), por lo cual tenemos que \(D_{\lambda x\alpha[\alpha^x]}=\omega\times\Sigma^\ast\).

**Ejercicio 21:** Sea \(\Sigma=\{\triangle,\blacktriangle\}\). Explique la forma en la que aplicando los constructores de composición y recursión primitiva a las funciones del conjunto inicial se pueden obtener las siguientes funciones

**(a)** \(I_a\)

**(b)** \(\lambda\alpha[\alpha^R]\)

**(c)** \(\lambda t\alpha[\alpha^t]\)

**Ejercicio 22:** V o F o I, justifique.

**(a)** Sea \(\Sigma=\{\triangle,\blacktriangle\}\). Entonces \(R(p_1^{0,1},\{(\triangle,p_3^{0,3}),(\blacktriangle,d_\blacktriangle\circ p_3^{0,3})\})(\triangle\blacktriangle,\triangle\blacktriangle)=\triangle\blacktriangle\blacktriangle\blacktriangle\)

**(b)** \(R(p_1^{0,1},d_\alpha\circ p_3^{0,3})=\lambda\alpha_1\alpha[\alpha_1\alpha]\)

Tenemos que

**Lema 7.** Sea

\[
f:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\Sigma^\ast
\]

con \(S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) conjuntos no vacíos y sea \(\mathcal{G}\) una familia \(\Sigma\)-indexada de funciones tal que

\[
\mathcal{G}_a:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times\Sigma^\ast\times\Sigma^\ast\to\Sigma^\ast
\]

para cada \(a\in\Sigma\). Si \(f\) y cada \(\mathcal{G}_a\) son \(\Sigma\)-efectivamente computables, entonces \(R(f,\mathcal{G})\) lo es.

**Cosmética.** Como hemos visto muchas veces para poder aplicar más naturalmente algún lema, nos es útil cambiar las variables que están siendo usadas en la notación lambda que describe alguna función. Por ejemplo si queremos ver que la función \(\lambda xy\alpha[x+y]\) es de la forma \(R(f,g)\), con \(f\) de tipo \((1,1,\#)\) y \(g\) de tipo \((3,1,\#)\), nos conviene escribir a la función \(\lambda xy\alpha[x+y]\) en la forma \(\lambda tx_1\alpha_1[t+x_1]\), donde se ve mejor cuál es el parámetro de la recursión primitiva y cuál es el bloque fijo. Obviamente esto es posible ya que \(\lambda xy\alpha[x+y]=\lambda tx_1\alpha_1[t+x_1]\). Esto da lugar a nuestra regla de cosmética:

**REGLA DE COSMÉTICA:** Si ud tiene una expresión lambda \(\lambda x_1\ldots x_n\alpha_1\ldots\alpha_m[E]\) que denota una función \(f\), entonces puede reemplazar en dicha expresión cada ocurrencia de una de las variables de la lista \(x_1\ldots x_n\alpha_1\ldots\alpha_m\) por una nueva variable (del mismo tipo, i.e. numérica o alfabética) la cual no figure en la lista y el resultado será una expresión lambda que también denota a \(f\).

Por supuesto que dicha regla la puede aplicar varias veces para modificar su notación lambda. Por ejemplo en el caso de \(\lambda xy\alpha[x+y]\) aplicamos tres veces la regla y obtenemos \(\lambda tx_1\alpha_1[t+x_1]\).

**Funciones \(\Sigma\)-recursivas primitivas.** Intuitivamente hablando ya sabemos que una función es \(\Sigma\)-recursiva primitiva si se puede obtener de las iniciales usando los constructores de composición y recursión primitiva. Daremos ahora una definición matemática de este concepto. Definamos los conjuntos \(PR_0^\Sigma\subseteq PR_1^\Sigma\subseteq PR_2^\Sigma\subseteq\cdots\subseteq PR^\Sigma\) de la siguiente manera

\[
PR_0^\Sigma=\{Suc,Pred,C_0^{0,0},C_\varepsilon^{0,0}\}\cup\{d_a:a\in\Sigma\}\cup\{p_j^{n,m}:1\le j\le n+m\}
\]

\[
\begin{aligned}
PR_{k+1}^\Sigma
=&\ PR_k^\Sigma
\cup\{f\circ[f_1,\ldots,f_r]:f,f_1,\ldots,f_r\in PR_k^\Sigma,\ r\ge 1\}\\
&\cup\{R(f,\mathcal{G}):R(f,\mathcal{G})\text{ está definida y }\{f\}\cup\{\mathcal{G}_a:a\in\Sigma\}\subseteq PR_k^\Sigma\}\\
&\cup\{R(f,g):R(f,g)\text{ está definida y }f,g\in PR_k^\Sigma\}
\end{aligned}
\]

\[
PR^\Sigma=\bigcup_{k\ge 0}PR_k^\Sigma
\]

Una función es llamada \(\Sigma\)-recursiva primitiva (\(\Sigma\)-p.r.) si pertenece a \(PR^\Sigma\).

**Proposición 8.** Si \(f\in PR^\Sigma\), entonces \(f\) es \(\Sigma\)-efectivamente computable.

**Ejercicio 23:** Explique con palabras (a lo mariposa) por qué es cierta la proposición anterior

**Algunas funciones \(\Sigma\)-recursivas primitivas.** En los siguientes lemas se prueba bien formalmente que varias funciones bien conocidas son \(\Sigma\)-primitivas recursivas. La mayoria de estas funciones ya fueron obtenidas usando los constructores de composición y recursión primitiva, en los desarrollos anteriores o en los ejercicios.

**Lema 9.** Sea \(\Sigma\) un alfabeto finito.

1. \(\emptyset\in PR^\Sigma\).
2. \(\lambda xy[x+y]\in PR^\Sigma\).
3. \(\lambda xy[x.y]\in PR^\Sigma\).
4. \(\lambda x[x!]\in PR^\Sigma\).

**Proof.** **(1)** Nótese que \(\emptyset=Pred\circ C_0^{0,0}\in PR_1^\Sigma\).

**(2)** Notar que

\[
\lambda xy[x+y](0,x_1)=x_1=p_1^{1,0}(x_1)
\]

\[
\begin{aligned}
\lambda xy[x+y](t+1,x_1)&=\lambda xy[x+y](t,x_1)+1\\
&=(Suc\circ p_1^{3,0})(\lambda xy[x+y](t,x_1),t,x_1)
\end{aligned}
\]

lo cual implica que \(\lambda xy[x+y]=R(p_1^{1,0},Suc\circ p_1^{3,0})\in PR_2^\Sigma\).

**(3)** Primero note que

\[
\begin{aligned}
C_0^{1,0}(0)&=C_0^{0,0}(\diamond)\\
C_0^{1,0}(t+1)&=C_0^{1,0}(t)
\end{aligned}
\]

lo cual implica que \(C_0^{1,0}=R(C_0^{0,0},p_1^{2,0})\in PR_1^\Sigma\). También note que

\[
\lambda tx[t.x]=R(C_0^{1,0},\lambda xy[x+y]\circ[p_1^{3,0},p_3^{3,0}]),
\]

lo cual por (2) implica que \(\lambda tx[t.x]\in PR_4^\Sigma\).

**(4)** Note que

\[
\begin{aligned}
\lambda x[x!](0)&=1=C_1^{0,0}(\diamond)\\
\lambda x[x!](t+1)&=\lambda x[x!](t).(t+1),
\end{aligned}
\]

lo cual implica que

\[
\lambda x[x!]=R(C_1^{0,0},\lambda xy[x.y]\circ[p_1^{2,0},Suc\circ p_2^{2,0}]).
\]

Ya que \(C_1^{0,0}=Suc\circ C_0^{0,0}\), tenemos que \(C_1^{0,0}\in PR_1^\Sigma\). Por (3), tenemos que

\[
\lambda xy[x.y]\circ[p_1^{2,0},Suc\circ p_2^{2,0}]\in PR_5^\Sigma,
\]

obteniendo que \(\lambda x[x!]\in PR_6^\Sigma\).

Ahora consideraremos dos funciones las cuales son obtenidas naturalmente por recursión primitiva sobre variable alfabética.

**Lema 10.** Supongamos \(\Sigma\) es un alfabeto finito.

**(a)** \(\lambda\alpha\beta[\alpha\beta]\in PR^\Sigma\)

**(b)** \(\lambda\alpha[|\alpha|]\in PR^\Sigma\)

**Proof.** **(a)** Ya que

\[
\lambda\alpha\beta[\alpha\beta](\alpha_1,\varepsilon)=\alpha_1=p_1^{0,1}(\alpha_1)
\]

\[
\lambda\alpha\beta[\alpha\beta](\alpha_1,\alpha a)=d_a(\lambda\alpha\beta[\alpha\beta](\alpha_1,\alpha)),\quad a\in\Sigma
\]

tenemos que \(\lambda\alpha\beta[\alpha\beta]=R(p_1^{0,1},\mathcal{G})\), donde \(\mathcal{G}_a=d_a\circ p_3^{0,3}\), para cada \(a\in\Sigma\).

**(b)** Ya que

\[
\lambda\alpha[|\alpha|](\varepsilon)=0=C_0^{0,0}(\diamond)
\]

\[
\lambda\alpha[|\alpha|](\alpha a)=\lambda\alpha[|\alpha|](\alpha)+1
\]

tenemos que \(\lambda\alpha[|\alpha|]=R(C_0^{0,0},\mathcal{G})\), donde \(\mathcal{G}_a=Suc\circ p_1^{1,1}\), para cada \(a\in\Sigma\).

**Lema 11.** Sea \(\Sigma\) un alfabeto finito. Entonces \(C_k^{n,m},C_\alpha^{n,m}\in PR^\Sigma\), para cada \(n,m,k\ge 0\) y \(\alpha\in\Sigma^\ast\).

**Proof.** **(a)** Note que \(C_{k+1}^{0,0}=Suc\circ C_k^{0,0}\), lo cual implica \(C_k^{0,0}\in PR_k^\Sigma\), para \(k\ge 0\). También note que \(C_{\alpha a}^{0,0}=d_a\circ C_\alpha^{0,0}\), lo cual dice que \(C_\alpha^{0,0}\in PR^\Sigma\), para \(\alpha\in\Sigma^\ast\). Para ver que \(C_k^{0,1}\in PR^\Sigma\) notar que

\[
C_k^{0,1}(\varepsilon)=k=C_k^{0,0}(\diamond)
\]

\[
C_k^{0,1}(\alpha a)=C_k^{0,1}(\alpha)=p_1^{1,1}(C_k^{0,1}(\alpha),\alpha)
\]

lo cual implica que \(C_k^{0,1}=R(C_k^{0,0},\mathcal{G})\), con \(\mathcal{G}_a=p_1^{1,1}\), \(a\in\Sigma\). En forma similar podemos ver que \(C_k^{1,0},C_\alpha^{1,0},C_\alpha^{0,1}\in PR^\Sigma\). Supongamos ahora que \(m>0\). Entonces

\[
C_k^{n,m}=C_k^{0,1}\circ p_{n+1}^{n,m}
\]

\[
C_\alpha^{n,m}=C_\alpha^{0,1}\circ p_{n+1}^{n,m}
\]

de lo cual obtenemos que \(C_k^{n,m},C_\alpha^{n,m}\in PR^\Sigma\). El caso \(n>0\) es similar.

**Lema 12.** Sea \(\Sigma\) un alfabeto finito.

**(a)** \(\lambda xy[x^y]\in PR^\Sigma\).

**(b)** \(\lambda t\alpha[\alpha^t]\in PR^\Sigma\).

**Proof.** **(a)** Note que

\[
\lambda tx[x^t]=R(C_1^{1,0},\lambda xy[x.y]\circ[p_1^{3,0},p_3^{3,0}])\in PR^\Sigma.
\]

O sea que \(\lambda xy[x^y]=\lambda tx[x^t]\circ[p_2^{2,0},p_1^{2,0}]\in PR^\Sigma\).

**(b)** Note que

\[
\lambda t\alpha[\alpha^t]=R(C_\varepsilon^{0,1},\lambda\alpha\beta[\alpha\beta]\circ[p_3^{1,2},p_2^{1,2}])\in PR^\Sigma.
\]

**Ejercicio 24:** Sea \(\Sigma=\{@,\%,\$\}\) y sea \(\le\) el orden total sobre \(\Sigma\) dado por \(@<\%<\text{\$}\). Pruebe que \(s^\le,\#^\le\) y \(\ast^\le\) pertenecen a \(PR^\Sigma\) (está probado en el apunte).

**Ejercicio 25:** Sea \(\Sigma=\{\$,?,@,\forall,\to,(\}\) y sea \(S=\{\$,?\}^\ast\). Pruebe que

\[
\begin{array}{rcl}
\chi_S^{\Sigma^\ast}:\Sigma^\ast&\to&\omega\\
\alpha&\to&
\begin{cases}
1 & \text{si }\alpha\in S\\
0 & \text{si }\alpha\notin S
\end{cases}
\end{array}
\]

es \(\Sigma\)-p.r.

Recordemos que llamabamos numerales a los siguientes símbolos

\[
0123456789
\]

También recordemos que \(Num\) denotaba el conjunto de los numerales. Sea \(Sig:Num^\ast\to Num^\ast\) definida de la siguiente manera

\[
\begin{aligned}
Sig(\varepsilon)&=1\\
Sig(\alpha0)&=\alpha1\\
Sig(\alpha1)&=\alpha2\\
Sig(\alpha2)&=\alpha3\\
Sig(\alpha3)&=\alpha4\\
Sig(\alpha4)&=\alpha5\\
Sig(\alpha5)&=\alpha6\\
Sig(\alpha6)&=\alpha7\\
Sig(\alpha7)&=\alpha8\\
Sig(\alpha8)&=\alpha9\\
Sig(\alpha9)&=Sig(\alpha)0
\end{aligned}
\]

Definamos \(Dec:\omega\to Num^\ast\) de la siguiente manera

\[
\begin{aligned}
Dec(0)&=\varepsilon\\
Dec(n+1)&=Sig(Dec(n))
\end{aligned}
\]

Nótese que para \(n\in\mathbf{N}\), la palabra \(Dec(n)\) es la notación usual decimal de \(n\). Nótese que \(Sig=R(C_1^{0,0},\mathcal{G})\), donde \(\mathcal{G}\) es la familia \(Num\)-indexada de funciones dada por:

\[
\begin{aligned}
\mathcal{G}_0&=d_1\circ p_2^{0,2}\\
\mathcal{G}_1&=d_2\circ p_2^{0,2}\\
\mathcal{G}_2&=d_3\circ p_2^{0,2}\\
\mathcal{G}_3&=d_4\circ p_2^{0,2}\\
\mathcal{G}_4&=d_5\circ p_2^{0,2}\\
\mathcal{G}_5&=d_6\circ p_2^{0,2}\\
\mathcal{G}_6&=d_7\circ p_2^{0,2}\\
\mathcal{G}_7&=d_8\circ p_2^{0,2}\\
\mathcal{G}_8&=d_9\circ p_2^{0,2}\\
\mathcal{G}_9&=d_0\circ p_1^{0,2}
\end{aligned}
\]

por lo cual \(Sig\) es \(Num\)-p.r.. También tenemos que \(Dec=R(C_\varepsilon^{0,0},Sig\circ p_2^{1,1})\) por lo cual \(Dec\) es \(Num\)-p.r.. En la batalla Gödel vence a Neumann (Guía 8) utilizaremos el siguiente resultado.

**Lema 13.** Sea \(\Gamma\) un alfabeto que contiene a \(Num\). Entonces \(Dec\) es \(\Gamma\)-p.r..

**Proof.** Sea \(\widetilde{Sig}:\Gamma^\ast\to\Gamma^\ast\) definida de la siguiente manera:

\[
\begin{aligned}
\widetilde{Sig}(\varepsilon)&=1\\
\widetilde{Sig}(\alpha0)&=\alpha1\\
\widetilde{Sig}(\alpha1)&=\alpha2\\
\widetilde{Sig}(\alpha2)&=\alpha3\\
\widetilde{Sig}(\alpha3)&=\alpha4\\
\widetilde{Sig}(\alpha4)&=\alpha5\\
\widetilde{Sig}(\alpha5)&=\alpha6\\
\widetilde{Sig}(\alpha6)&=\alpha7\\
\widetilde{Sig}(\alpha7)&=\alpha8\\
\widetilde{Sig}(\alpha8)&=\alpha9\\
\widetilde{Sig}(\alpha9)&=\widetilde{Sig}(\alpha)0\\
\widetilde{Sig}(\alpha a)&=\varepsilon,\quad \text{palabra }a\in\Gamma-Num
\end{aligned}
\]

Nótese que \(\widetilde{Sig}=R(C_1^{0,0},\widetilde{\mathcal{G}})\), donde \(\widetilde{\mathcal{G}}\) es la familia \(\Gamma\)-indexada de funciones dada por:

\[
\begin{aligned}
\widetilde{\mathcal{G}}_0&=d_1\circ p_2^{0,2}\\
\widetilde{\mathcal{G}}_1&=d_2\circ p_2^{0,2}\\
\widetilde{\mathcal{G}}_2&=d_3\circ p_2^{0,2}\\
\widetilde{\mathcal{G}}_3&=d_4\circ p_2^{0,2}\\
\widetilde{\mathcal{G}}_4&=d_5\circ p_2^{0,2}\\
\widetilde{\mathcal{G}}_5&=d_6\circ p_2^{0,2}\\
\widetilde{\mathcal{G}}_6&=d_7\circ p_2^{0,2}\\
\widetilde{\mathcal{G}}_7&=d_8\circ p_2^{0,2}\\
\widetilde{\mathcal{G}}_8&=d_9\circ p_2^{0,2}\\
\widetilde{\mathcal{G}}_9&=d_0\circ p_1^{0,2}\\
\widetilde{\mathcal{G}}_a&=C_\varepsilon^{0,2},\quad \text{para }a\in\Gamma-Num
\end{aligned}
\]

por lo cual \(\widetilde{Sig}\) es \(\Gamma\)-p.r. (ojo que aquí las funciones \(p_2^{0,2},C_\varepsilon^{0,2},C_1^{0,0}\) y \(d_0,d_1,d_2,\ldots,d_9\) son relativas al alfabeto \(\Gamma\)). Pero nótese que

\[
\begin{aligned}
Dec(0)&=\varepsilon\\
Dec(n+1)&=\widetilde{Sig}(Dec(n)),\quad\text{para cada }n\in\omega
\end{aligned}
\]

lo cual nos dice que \(Dec=R(C_\varepsilon^{0,0},\widetilde{Sig}\circ p_2^{1,1})\) por lo cual \(Dec\) es \(\Gamma\)-p.r. (de nuevo, aquí las funciones \(C_\varepsilon^{0,0}\) y \(p_2^{1,1}\) son relativas al alfabeto \(\Gamma\)). Dados \(x,y\in\omega\), definamos

\[
x\mathbin{\dot{-}}y=\max(x-y,0).
\]

**Lema 14.** Se tiene

**(a)** \(\lambda xy[x\mathbin{\dot{-}}y]\in PR^\Sigma\)

**(b)** \(\lambda xy[\max(x,y)]\in PR^\Sigma\)

**(c)** \(\lambda xy[x=y]\in PR^\Sigma\)

**(d)** \(\lambda xy[x\le y]\in PR^\Sigma\)

**(e)** \(\lambda\alpha\beta[\alpha=\beta]\in PR^\Sigma\)

**Proof.** **(a)** Primero notar que \(\lambda x[x\mathbin{\dot{-}}1]=R(C_0^{0,0},p_2^{2,0})\in PR^\Sigma\). También note que

\[
\lambda tx[x\mathbin{\dot{-}}t]=R(p_1^{1,0},\lambda x[x\mathbin{\dot{-}}1]\circ p_1^{3,0})\in PR^\Sigma.
\]

O sea que \(\lambda xy[x\mathbin{\dot{-}}y]=\lambda tx[x\mathbin{\dot{-}}t]\circ[p_2^{2,0},p_1^{2,0}]\in PR^\Sigma\).

**(b)** Note que \(\lambda xy[\max(x,y)]=\lambda xy[x+(y\mathbin{\dot{-}}x)]\).

**(c)** Note que \(\lambda xy[x=y]=\lambda xy[1\mathbin{\dot{-}}((x\mathbin{\dot{-}}y)+(y\mathbin{\dot{-}}x))]\).

**(d)** Note que \(\lambda xy[x\le y]=\lambda xy[1\mathbin{\dot{-}}(x\mathbin{\dot{-}}y)]\).

**(e)** Sea \(\le\) un orden total sobre \(\Sigma\). Ya que

\[
\alpha=\beta\text{ sii }\#^\le(\alpha)=\#^\le(\beta)
\]

tenemos que

\[
\lambda\alpha\beta[\alpha=\beta]=\lambda xy[x=y]\circ[\#^\le\circ p_1^{0,2},\#^\le\circ p_2^{0,2}]
\]

lo cual nos dice que \(\lambda\alpha\beta[\alpha=\beta]\) es \(\Sigma\)-p.r.

**Ejercicio 26:** Complete las pruebas de (b), (c), (d) y (e) del lema anterior

**Ejercicio 27:** Sea \(\Sigma\) un alfabeto finito.

**(a)** \(\lambda x[x\text{ es par}]\) es \(\Sigma\)-p.r..

**(b)** \(\lambda xyz\alpha\beta\gamma[x.y+\max(x,|\alpha|)|\beta|]\) es \(\Sigma\)-p.r.

**(c)** \(\lambda x\alpha[x=|\alpha|]\) es \(\Sigma\)-p.r..

**(d)** \(\lambda xy\alpha\beta[\alpha^x=\beta]\) es \(\Sigma\)-p.r..

**Operaciones lógicas entre predicados.** Dados predicados \(P:S\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) y \(Q:S\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\), con el mismo dominio, definamos nuevos predicados \((P\lor Q)\), \((P\land Q)\) y \(\neg P\) de la siguiente manera

\[
\begin{array}{rcl}
(P\lor Q):S&\to&\omega\\
(\overrightarrow{x},\overrightarrow{\alpha})&\to&
\begin{cases}
1 & \text{si }P(\overrightarrow{x},\overrightarrow{\alpha})=1\text{ o }Q(\overrightarrow{x},\overrightarrow{\alpha})=1\\
0 & \text{caso contrario}
\end{cases}
\end{array}
\]

\[
\begin{array}{rcl}
(P\land Q):S&\to&\omega\\
(\overrightarrow{x},\overrightarrow{\alpha})&\to&
\begin{cases}
1 & \text{si }P(\overrightarrow{x},\overrightarrow{\alpha})=1\text{ y }Q(\overrightarrow{x},\overrightarrow{\alpha})=1\\
0 & \text{caso contrario}
\end{cases}
\end{array}
\]

\[
\begin{array}{rcl}
\neg P:S&\to&\omega\\
(\overrightarrow{x},\overrightarrow{\alpha})&\to&
\begin{cases}
1 & \text{si }P(\overrightarrow{x},\overrightarrow{\alpha})=0\\
0 & \text{si }P(\overrightarrow{x},\overrightarrow{\alpha})=1
\end{cases}
\end{array}
\]

**Lema 15.** Si \(P:D_P\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) y \(Q:D_Q\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) son predicados \(\Sigma\)-p.r. tales que \(D_P=D_Q\), entonces \((P\lor Q)\), \((P\land Q)\) y \(\neg P\) son \(\Sigma\)-p.r.

**Proof.** Note que

\[
\neg P=\lambda xy[x\mathbin{\dot{-}}y]\circ[C_1^{n,m},P]
\]

\[
(P\land Q)=\lambda xy[x.y]\circ[P,Q]
\]

\[
(P\lor Q)=\neg(\neg P\land\neg Q)
\]

**Ejercicio 28:** V o F o I, justifique.

**(a)** Si \(P_1,P_2,P_3\) son predicados \(\Sigma\)-p.r. y \(D_{P_1}=D_{P_2}=D_{P_3}\), entonces el predicado \((P_1\lor P_2\land P_3)\) es \(\Sigma\)-p.r.

**(b)** Sea \(\Sigma\) un alfabeto finito. Entonces \(\lambda x\alpha\beta[x=|\alpha|\land\alpha=\beta]=(\lambda x\alpha[x=|\alpha|]\land\lambda\alpha\beta[\alpha=\beta])\)

**(c)** Sea \(\Sigma\) un alfabeto finito. Entonces \((\lambda x[x=1]\land\lambda\alpha[\alpha=\varepsilon])(2,\varepsilon)=0\)

**(d)** Si \(S,T\subseteq\omega\), entonces \(\chi_{S\times T}^{\omega\times\omega}=(\chi_S^\omega\land\chi_T^\omega)\)

**Conjuntos \(\Sigma\)-recursivos primitivos.** Un conjunto \(\Sigma\)-mixto \(S\subseteq\omega^n\times\Sigma^{\ast m}\) es llamado \(\Sigma\)-recursivo primitivo si su función característica \(\chi_S^{\omega^n\times\Sigma^{\ast m}}\) es \(\Sigma\)-p.r.. Nótese que

\[
\chi_S^{\omega^n\times\Sigma^{\ast m}}=\lambda\overrightarrow{x}\overrightarrow{\alpha}[(\overrightarrow{x},\overrightarrow{\alpha})\in S].
\]

**Ejercicio 29:** Sea \(\Sigma=\{@,!\}\). Pruebe que los siguientes conjuntos son \(\Sigma\)-p.r.

**(a)** \(\omega\)

**(b)** \(\Sigma^\ast\)

**(c)** \(\{(x,y)\in\omega^2:x=y\}\)

**(d)** \(\{(x,\alpha)\in\omega\times\Sigma^\ast:x=|\alpha|\}\)

**(e)** \(\{x\in\omega:x\text{ es par}\}\)

**(f)** \(\{(x,y,\alpha,\beta,\gamma)\in\omega^2\times\Sigma^{\ast 3}:x\le|\gamma|\}\)

**Lema 16.** Si \(S_1,S_2\subseteq\omega^n\times\Sigma^{\ast m}\) son \(\Sigma\)-p.r., entonces \(S_1\cup S_2\), \(S_1\cap S_2\) y \(S_1-S_2\) lo son.

**Proof.** Note que

\[
\chi_{S_1\cup S_2}^{\omega^n\times\Sigma^{\ast m}}=
(\chi_{S_1}^{\omega^n\times\Sigma^{\ast m}}\lor\chi_{S_2}^{\omega^n\times\Sigma^{\ast m}})
\]

\[
\chi_{S_1\cap S_2}^{\omega^n\times\Sigma^{\ast m}}=
(\chi_{S_1}^{\omega^n\times\Sigma^{\ast m}}\land\chi_{S_2}^{\omega^n\times\Sigma^{\ast m}})
\]

\[
\chi_{S_1-S_2}^{\omega^n\times\Sigma^{\ast m}}=
\lambda xy[x\mathbin{\dot{-}}y]\circ[\chi_{S_1}^{\omega^n\times\Sigma^{\ast m}},\chi_{S_2}^{\omega^n\times\Sigma^{\ast m}}]
\]

**Ejercicio 30:** Si \(S\subseteq\omega^n\times\Sigma^{\ast m}\) es finito, entonces \(S\) es \(\Sigma\)-p.r. Haga el caso \(n=m=1\). (Hint: haga el caso en que \(S\) tiene un solo elemento y luego aplique el lema anterior).

**Ejercicio 31:** Sea \(\Sigma\) un alfabeto finito.

**(a)** Pruebe que \(\Sigma\) es \(\Sigma\)-p.r.

**(b)** Pruebe que \(\Sigma^\ast-\{\varepsilon\}\) es \(\Sigma\)-p.r.

**(c)** Pruebe que \(\Sigma^\ast-(\{\varepsilon\}\cup\Sigma)\) es \(\Sigma\)-p.r.

**(d)** Pruebe que \(\omega-\{0,1\}\) es \(\Sigma\)-p.r.

**(e)** Pruebe que \(\{(x,y,\alpha,\beta,\gamma)\in\omega^2\times\Sigma^{\ast 3}:\alpha\ne\varepsilon\lor x\le|\gamma|\}\) es \(\Sigma\)-p.r.

**(f)** Pruebe que \(\{(x,\alpha,\beta):|\alpha|>6\}\) es \(\Sigma\)-p.r.

El siguiente lema caracteriza cuando un conjunto rectangular es \(\Sigma\)-p.r..

**Lema 17.** Supongamos \(S_1,\ldots,S_n\subseteq\omega\), \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) son conjuntos no vacíos. Entonces \(S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\) es \(\Sigma\)-p.r. sii \(S_1,\ldots,S_n,L_1,\ldots,L_m\) son \(\Sigma\)-p.r.

**Ejercicio 32:** Haga la prueba del lema anterior para el caso de \(n=m=1\) (en el apunte está la prueba general)

Dada una función \(f\) y un conjunto \(S\subseteq D_f\), usaremos \(f|_S\) para denotar la restricción de \(f\) al conjunto \(S\), i.e. \(f|_S=f\cap(S\times I_f)\). Nótese que \(f|_S\) es la función dada por

\[
D_{f|_S}=S
\]

\[
f|_S(e)=f(e),\quad\text{para cada }e\in S
\]

Nótese que cualesquiera sea la función \(f\) tenemos que \(f|_\emptyset=\emptyset\) y \(f|_{D_f}=f\).

**Lema 18.** Supongamos \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to O\) es \(\Sigma\)-p.r., donde \(O\in\{\omega,\Sigma^\ast\}\). Si \(S\subseteq D_f\) es \(\Sigma\)-p.r., entonces \(f|_S\) es \(\Sigma\)-p.r..

**Proof.** Supongamos \(O=\Sigma^\ast\). Entonces

\[
f|_S=\lambda x\alpha[\alpha^x]\circ[Suc\circ Pred\circ\chi_S^{\omega^n\times\Sigma^{\ast m}},f]
\]

lo cual nos dice que \(f|_S\) es \(\Sigma\)-p.r.. El caso \(O=\omega\) es similar usando \(\lambda xy[x^y]\) en lugar de \(\lambda x\alpha[\alpha^x]\).

Usando el lema anterior en combinación con el Lema 15 podemos ver que muchos predicados usuales son \(\Sigma\)-p.r.. Por ejemplo sea

\[
P=\lambda x\alpha\beta\gamma[x=|\gamma|\land\alpha=\gamma^{Pred(|\beta|)}].
\]

Nótese que

\[
D_P=\omega\times\Sigma^\ast\times(\Sigma^\ast-\{\varepsilon\})\times\Sigma^\ast
\]

Además \(D_P\) es \(\Sigma\)-p.r. ya que

\[
\chi_{D_P}^{\omega\times\Sigma^{\ast 3}}=\neg\lambda\alpha\beta[\alpha=\beta]\circ[p_3^{1,3},C_\varepsilon^{1,3}]
\]

También note que los predicados

\[
P_1=\lambda x\alpha\beta\gamma[x=|\gamma|]
\]

\[
P_2=\lambda x\alpha\beta\gamma[\alpha=\gamma^{Pred(|\beta|)}]
\]

son \(\Sigma\)-p.r. ya que pueden obtenerse componiendo funciones \(\Sigma\)-p.r.. Un error sería pensar que \(P=(P_1\land P_2)\) ya que \(P_1\) y \(P_2\) tienen dominios distintos por lo cual no está definido \((P_1\land P_2)\). Sin embargo tenemos que \(P=(P_1|_{D_P}\land P_2)\), lo cual nos dice que \(P\) es \(\Sigma\)-p.r. ya que \(P_1|_{D_P}\) es \(\Sigma\)-p.r. por el Lema 18 y por lo tanto podemos aplicar el Lema 15.

**Ejercicio 33:** Sea \(\Sigma=\{@,!\}\). Sea \(P=\lambda xy\alpha\beta\gamma[Pred(Pred(|\beta|))\ne 6\land\alpha^x=\beta]\)

**(a)** Encuentre por definición de notación lambda el dominio de \(P\)

**(b)** Pruebe que \(P\) es \(\Sigma\)-p.r.

Aceptaremos sin prueba el siguiente resultado (ver el apunte por una prueba)

**Lema 19.** Sean \(O\in\{\omega,\Sigma^\ast\}\) y \(n,m\in\omega\). Si \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to O\) es \(\Sigma\)-p.r., entonces existe una función \(\Sigma\)-p.r. \(\overline{f}:\omega^n\times\Sigma^{\ast m}\to O\), tal que \(f=\overline{f}|_{D_f}\).

Ahora podemos probar una proposición muy importante.

**Proposición 20.** Sea \(S\subseteq\omega^n\times\Sigma^{\ast m}\). Se tiene que \(S\) es \(\Sigma\)-p.r. sii \(S\) es el dominio de alguna función \(\Sigma\)-p.r..

**Proof.** \((\Rightarrow)\) Note que \(S=D_{Pred\circ\chi_S^{\omega^n\times\Sigma^{\ast m}}}\).

\((\Leftarrow)\) Probaremos por inducción en \(k\) que \(D_F\) es \(\Sigma\)-p.r., para cada \(F\in PR_k^\Sigma\). El caso \(k=0\) es fácil. Supongamos el resultado vale para un \(k\) fijo y supongamos \(F\in PR_{k+1}^\Sigma\). Veremos entonces que \(D_F\) es \(\Sigma\)-p.r.. Hay varios casos. Consideremos primero el caso en que \(F=R(f,g)\), donde

\[
f:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\Sigma^\ast
\]

\[
g:\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times\Sigma^\ast\to\Sigma^\ast,
\]

con \(S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) conjuntos no vacíos y \(f,g\in PR_k^\Sigma\). Nótese que por definición de \(R(f,g)\), tenemos que

\[
D_F=\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m.
\]

Por hipótesis inductiva tenemos que \(D_f=S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\) es \(\Sigma\)-p.r., lo cual por el Lema 17 nos dice que los conjuntos \(S_1,\ldots,S_n,L_1,\ldots,L_m\) son \(\Sigma\)-p.r.. Ya que \(\omega\) es \(\Sigma\)-p.r., el Lema 17 nos dice que \(D_F\) es \(\Sigma\)-p.r..

Los otros casos de recursión primitiva son dejados al lector.

Supongamos ahora que \(F=g\circ[g_1,\ldots,g_r]\) con \(g,g_1,\ldots,g_r\in PR_k^\Sigma\). Si \(F=\emptyset\), entonces es claro que \(D_F=\emptyset\) es \(\Sigma\)-p.r.. Supongamos entonces que \(F\) no es la función \(\emptyset\). Tenemos entonces que \(r\) es de la forma \(n+m\) y

\[
\begin{aligned}
g&:D_g\subseteq\omega^n\times\Sigma^{\ast m}\to O\\
g_i&:D_{g_i}\subseteq\omega^k\times\Sigma^{\ast l}\to\omega,\quad i=1,\ldots,n\\
g_i&:D_{g_i}\subseteq\omega^k\times\Sigma^{\ast l}\to\Sigma^\ast,\quad i=n+1,\ldots,n+m
\end{aligned}
\]

con \(O\in\{\omega,\Sigma^\ast\}\) y \(k,l\in\omega\). Por Lema 19, hay funciones \(\Sigma\)-p.r. \(\overline{g}_1,\ldots,\overline{g}_{n+m}\) las cuales son \(\Sigma\)-totales y cumplen

\[
g_i=\overline{g}_i|_{D_{g_i}},\quad\text{para }i=1,\ldots,n+m.
\]

Por hipótesis inductiva los conjuntos \(D_g,D_{g_i}\), \(i=1,\ldots,n+m\), son \(\Sigma\)-p.r. y por lo tanto

\[
S=\bigcap_{i=1}^{n+m}D_{g_i}
\]

lo es. Nótese que

\[
\chi_{D_F}^{\omega^k\times\Sigma^{\ast l}}=
(\chi_{D_g}^{\omega^n\times\Sigma^{\ast m}}\circ[\overline{g}_1,\ldots,\overline{g}_{n+m}]\land\chi_S^{\omega^k\times\Sigma^{\ast l}})
\]

lo cual nos dice que \(D_F\) es \(\Sigma\)-p.r..

**Lema de división por casos para funciones \(\Sigma\)-p.r.** Una observación interesante es que si \(f_i:D_{f_i}\to O\), \(i=1,\ldots,k\), son funciones tales que \(D_{f_i}\cap D_{f_j}=\emptyset\) para \(i\ne j\), entonces \(f_1\cup\cdots\cup f_k\) es la función

\[
\begin{array}{rcl}
D_{f_1}\cup\cdots\cup D_{f_k}&\to&O\\
e&\to&
\begin{cases}
f_1(e)&\text{si }e\in D_{f_1}\\
\vdots&\vdots\\
f_k(e)&\text{si }e\in D_{f_k}
\end{cases}
\end{array}
\]

**Lema 21.** Sean \(O\in\{\omega,\Sigma^\ast\}\) y \(n,m\in\omega\). Supongamos \(f_i:D_{f_i}\subseteq\omega^n\times\Sigma^{\ast m}\to O\), \(i=1,\ldots,k\), son funciones \(\Sigma\)-p.r. tales que \(D_{f_i}\cap D_{f_j}=\emptyset\) para \(i\ne j\). Entonces \(f_1\cup\cdots\cup f_k\) es \(\Sigma\)-p.r..

**Proof.** Supongamos \(O=\Sigma^\ast\) y \(k=2\). Sean

\[
\overline{f_i}:\omega^n\times\Sigma^{\ast m}\to\Sigma^\ast,\quad i=1,2,
\]

funciones \(\Sigma\)-p.r. tales que \(\overline{f_i}|_{D_{f_i}}=f_i\), \(i=1,2\) (Lema 19). Por la Proposición 20 los conjuntos \(D_{f_1}\) y \(D_{f_2}\) son \(\Sigma\)-p.r. y por lo tanto lo es \(D_{f_1}\cup D_{f_2}\). Ya que

\[
f_1\cup f_2=
\left(
\lambda\alpha\beta[\alpha\beta]\circ
\left[
\lambda x\alpha[\alpha^x]\circ[\chi_{D_{f_1}}^{\omega^n\times\Sigma^{\ast m}},\overline{f_1}],
\lambda x\alpha[\alpha^x]\circ[\chi_{D_{f_2}}^{\omega^n\times\Sigma^{\ast m}},\overline{f_2}]
\right]
\right)\Big|_{D_{f_1}\cup D_{f_2}}
\]

tenemos que \(f_1\cup f_2\) es \(\Sigma\)-p.r..

El caso \(k>2\) puede probarse por inducción ya que

\[
f_1\cup\cdots\cup f_k=(f_1\cup\cdots\cup f_{k-1})\cup f_k.
\]

**CONSEJO IMPORTANTE:** Si uno quiere usar el lema de división por casos para probar que una función \(f\) es \(\Sigma\)-p.r., entonces lo primero que hay que hacer, antes de ver que algo sea \(\Sigma\)-p.r. o no, es (a lo mariposa) definir correctamente funciones \(f_1,\ldots,f_k\) tales que \(D_{f_i}\cap D_{f_j}=\emptyset\) para \(i\ne j\) y además \(f_1\cup\cdots\cup f_k=f\). Consejos para encontrar dichas funciones:

1. Determinar el \(k\), es decir, \(k\) es justamente la cantidad de "casos" en la descripción de \(f\)
2. Para cada "caso" de la descripción de \(f\), asociar un subconjunto del dominio de \(f\) el cual sea justamente definido por la propiedad correspondiente a ese caso. Ojo que dijimos subconjunto de \(D_f\), no confundir los tipos!! (a veces los casos se describen usando no todas las variables de las cuales depende la función)
3. Notar que los subconjuntos \(S_1,\ldots,S_k\) así definidos deben ser disjuntos de a pares y unidos deben dar el dominio de \(f\)
4. Para cada \(i\) defina \(f_i\) de la siguiente manera:
   **(a)** dominio de \(f_i=S_i\)
   **(b)** regla de \(f_i\) dada por la regla que describe \(f\) para el caso \(i\)-ésimo
5. En general suele suceder que \(f_i\) es la restricción a \(S_i\) de una función con dominio más amplio y se prueba entonces que tanto dicha función como \(S_i\) son \(\Sigma\)-p.r., resultando así que \(f_i\) es \(\Sigma\)-p.r.

**Ejercicio 34:** Sea \(\Sigma=\{@,!,\%\}\). Pruebe que \(f\) es \(\Sigma\)-p.r..

**(a)**

\[
\begin{array}{rcl}
f:\omega\times\Sigma^\ast&\to&\omega\\
(x,\alpha)&\to&
\begin{cases}
|\alpha|.x^2&\text{si }x+|\alpha|\text{ es impar}\\
0&\text{si }x+|\alpha|\text{ es par}
\end{cases}
\end{array}
\]

**(b)**

\[
\begin{array}{rcl}
f:\{10,11,17\}\times\Sigma^+&\to&\omega\\
(x,\alpha)&\to&
\begin{cases}
Pred(x)&\text{si }x\text{ es impar}\\
|\alpha|&\text{si }x\text{ es par}
\end{cases}
\end{array}
\]

**(c)**

\[
\begin{array}{rcl}
f:\mathbf{N}\times\Sigma^+&\to&\omega\\
(x,\alpha)&\to&
\begin{cases}
x^2&\text{si }x+|\alpha|\text{ es par}\\
0&\text{si }x+|\alpha|\text{ es impar}
\end{cases}
\end{array}
\]

**(d)**

\[
\begin{array}{rcl}
f:\{(x,y,\alpha):x\le y\}&\to&\omega\\
(x,y,\alpha)&\to&
\begin{cases}
x^2&\text{si }|\alpha|\le y\\
0&\text{si }|\alpha|>y
\end{cases}
\end{array}
\]

(Explicado en video colgado en granlogico.com)

**(e)**

\[
\begin{array}{rcl}
f:\{1,2,3,4,5\}\times\mathbf{N}\times\{@,\%\}^\ast&\to&\Sigma^\ast\\
(x,y,\alpha)&\to&
\begin{cases}
\alpha^2&\text{si }\alpha=\text{@@}\\
\text{!!!}&\text{si }\alpha\ne\text{@@}\land|\alpha|>y\\
\alpha^{x+y}&\text{si }\alpha\ne\text{@@}\land|\alpha|\le y
\end{cases}
\end{array}
\]

**Ejercicio 35:** Sea \(F:\omega\to\omega\) dada por

\[
\begin{aligned}
F(0)&=2\\
F(1)&=2^2\\
F(2)&=(2^2)^3\\
F(3)&=((2^2)^3)^2\\
F(4)&=(((2^2)^3)^2)^3\\
&\vdots
\end{aligned}
\]

Pruebe que \(F\) es \(\Sigma\)-p.r..

**Ejercicio 36:** Sean \(f_1,f_2:\omega\to\omega\) funciones \(\Sigma\)-p.r.. Sea \(F:\omega\to\omega\) dada por

\[
\begin{aligned}
F(0)&=0\\
F(1)&=f_1(0)\\
F(2)&=f_2(f_1(0))\\
F(3)&=f_1(f_2(f_1(0)))\\
F(4)&=f_2(f_1(f_2(f_1(0))))\\
&\vdots
\end{aligned}
\]

Pruebe que \(F\) es \(\Sigma\)-p.r.. Obtenga el ejercicio anterior a partir de este resultado.

Usaremos el lema de división por casos para probar que la función \(\lambda i\alpha[[\alpha]_i]\) es \(\Sigma\)-p.r.. Recordemos que dados \(i\in\omega\) y \(\alpha\in\Sigma^\ast\), definimos

\[
[\alpha]_i=
\begin{cases}
i\text{-ésimo elemento de }\alpha&\text{si }1\le i\le|\alpha|\\
\varepsilon&\text{caso contrario}
\end{cases}
\]

Nótese que \(D_{\lambda i\alpha[[\alpha]_i]}=\omega\times\Sigma^\ast\).

**Lema 22.** \(\lambda i\alpha[[\alpha]_i]\) es \(\Sigma\)-p.r..

**Proof.** Supongamos \(\Sigma=\{@,!\}\). Note que

\[
[\varepsilon]_i=\varepsilon
\]

\[
[\alpha\text{@}]_i=
\begin{cases}
[\alpha]_i&\text{si }i\ne|\alpha|+1\\
@&\text{si }i=|\alpha|+1
\end{cases}
\]

\[
[\alpha\text{!}]_i=
\begin{cases}
[\alpha]_i&\text{si }i\ne|\alpha|+1\\
!&\text{si }i=|\alpha|+1
\end{cases}
\]

lo cual dice que \(\lambda i\alpha[[\alpha]_i]=R(C_\varepsilon^{1,0},\mathcal{G})\), donde \(\mathcal{G}_a:\omega\times\Sigma^\ast\times\Sigma^\ast\to\Sigma^\ast\) es dada por

\[
\mathcal{G}_a(i,\alpha,\zeta)=
\begin{cases}
\zeta&\text{si }i\ne|\alpha|+1\\
a&\text{si }i=|\alpha|+1
\end{cases}
\]

para cada \(a\in\Sigma\). O sea que solo resta probar que cada \(\mathcal{G}_a\) es \(\Sigma\)-p.r.. Veamos que \(\mathcal{G}_@\) es \(\Sigma\)-p.r.. Primero note que los conjuntos

\[
S_1=\{(i,\alpha,\zeta)\in\omega\times\Sigma^\ast\times\Sigma^\ast:i\ne|\alpha|+1\}
\]

\[
S_2=\{(i,\alpha,\zeta)\in\omega\times\Sigma^\ast\times\Sigma^\ast:i=|\alpha|+1\}
\]

son \(\Sigma\)-p.r. ya que

\[
\chi_{S_1}^{\omega\times\Sigma^\ast\times\Sigma^\ast}
=\lambda xy[x\ne y]\circ[p_1^{1,2},Suc\circ\lambda\alpha[|\alpha|]\circ p_2^{1,2}]
\]

\[
\chi_{S_2}^{\omega\times\Sigma^\ast\times\Sigma^\ast}
=\lambda xy[x=y]\circ[p_1^{1,2},Suc\circ\lambda\alpha[|\alpha|]\circ p_2^{1,2}]
\]

Nótese que por el Lema 18 tenemos que \(p_3^{1,2}|_{S_1}\) y \(C_@^{1,2}|_{S_2}\) son \(\Sigma\)-p.r.. Además

\[
\mathcal{G}_@=p_3^{1,2}|_{S_1}\cup C_@^{1,2}|_{S_2}
\]

por lo cual el Lema 21 nos dice que \(\mathcal{G}_@\) es \(\Sigma\)-p.r.. Análogamente se prueba que \(\mathcal{G}_!\) es \(\Sigma\)-p.r..

**Sumatoria, productoria y concatenatoria de funciones \(\Sigma\)-p.r.** Sea \(\Sigma\) un alfabeto finito. Sea \(f:\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega\), con \(S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) no vacíos. Para \(x,y\in\omega\) y \((\overrightarrow{x},\overrightarrow{\alpha})\in S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\), definamos

\[
\sum_{t=x}^{t=y} f(t,\overrightarrow{x},\overrightarrow{\alpha})=
\begin{cases}
0&\text{si }x>y\\
f(x,\overrightarrow{x},\overrightarrow{\alpha})+f(x+1,\overrightarrow{x},\overrightarrow{\alpha})+\cdots+f(y,\overrightarrow{x},\overrightarrow{\alpha})&\text{si }x\le y
\end{cases}
\]

\[
\prod_{t=x}^{t=y} f(t,\overrightarrow{x},\overrightarrow{\alpha})=
\begin{cases}
1&\text{si }x>y\\
f(x,\overrightarrow{x},\overrightarrow{\alpha}).f(x+1,\overrightarrow{x},\overrightarrow{\alpha})\cdots f(y,\overrightarrow{x},\overrightarrow{\alpha})&\text{si }x\le y
\end{cases}
\]

En forma similar, cuando \(I_f\subseteq\Sigma^\ast\), definamos

\[
\operatorname*{C}_{t=x}^{t=y} f(t,\overrightarrow{x},\overrightarrow{\alpha})=
\begin{cases}
\varepsilon&\text{si }x>y\\
f(x,\overrightarrow{x},\overrightarrow{\alpha})f(x+1,\overrightarrow{x},\overrightarrow{\alpha})\cdots f(y,\overrightarrow{x},\overrightarrow{\alpha})&\text{si }x\le y
\end{cases}
\]

Note que, en virtud de la definición anterior, el dominio de las funciones

\[
\lambda xy\overrightarrow{x}\overrightarrow{\alpha}\left[\sum_{t=x}^{t=y} f(t,\overrightarrow{x},\overrightarrow{\alpha})\right],
\quad
\lambda xy\overrightarrow{x}\overrightarrow{\alpha}\left[\prod_{t=x}^{t=y} f(t,\overrightarrow{x},\overrightarrow{\alpha})\right],
\quad
\lambda xy\overrightarrow{x}\overrightarrow{\alpha}\left[\operatorname*{C}_{t=x}^{t=y} f(t,\overrightarrow{x},\overrightarrow{\alpha})\right]
\]

es \(\omega\times\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\).

Dejamos al lector que analice en las consideraciones de recién el caso \(n=m=0\) (es decir cuando \(D_f=\omega\)).

**Lema 23 (Lema de la sumatoria).** Sea \(\Sigma\) un alfabeto finito.

**(a)** Si \(f:\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega\) es \(\Sigma\)-p.r., con \(S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) no vacíos, entonces las funciones

\[
\lambda xy\overrightarrow{x}\overrightarrow{\alpha}\left[\sum_{t=x}^{t=y} f(t,\overrightarrow{x},\overrightarrow{\alpha})\right]
\quad\text{y}\quad
\lambda xy\overrightarrow{x}\overrightarrow{\alpha}\left[\prod_{t=x}^{t=y} f(t,\overrightarrow{x},\overrightarrow{\alpha})\right]
\]

son \(\Sigma\)-p.r.

**(b)** Si \(f:\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\Sigma^\ast\) es \(\Sigma\)-p.r., con \(S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) no vacíos, entonces la función

\[
\lambda xy\overrightarrow{x}\overrightarrow{\alpha}\left[\operatorname*{C}_{t=x}^{t=y} f(t,\overrightarrow{x},\overrightarrow{\alpha})\right]
\]

es \(\Sigma\)-p.r.

**Proof.** **(a)** Sea \(G=\lambda tx\overrightarrow{x}\overrightarrow{\alpha}\left[\sum_{i=x}^{i=t}f(i,\overrightarrow{x},\overrightarrow{\alpha})\right]\). Ya que

\[
\lambda xy\overrightarrow{x}\overrightarrow{\alpha}\left[\sum_{i=x}^{i=y}f(i,\overrightarrow{x},\overrightarrow{\alpha})\right]
=G\circ[p_2^{n+2,m},p_1^{n+2,m},p_3^{n+2,m},\ldots,p_{n+m+2}^{n+2,m}]
\]

solo tenemos que probar que \(G\) es \(\Sigma\)-p.r.. Primero note que

\[
G(0,x,\overrightarrow{x},\overrightarrow{\alpha})=
\begin{cases}
0&\text{si }x>0\\
f(0,\overrightarrow{x},\overrightarrow{\alpha})&\text{si }x=0
\end{cases}
\]

\[
G(t+1,x,\overrightarrow{x},\overrightarrow{\alpha})=
\begin{cases}
0&\text{si }x>t+1\\
G(t,x,\overrightarrow{x},\overrightarrow{\alpha})+f(t+1,\overrightarrow{x},\overrightarrow{\alpha})&\text{si }x\le t+1
\end{cases}
\]

O sea que si definimos

\[
\begin{array}{rcl}
h:\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m&\to&\omega\\
(x,\overrightarrow{x},\overrightarrow{\alpha})&\to&
\begin{cases}
0&\text{si }x>0\\
f(0,\overrightarrow{x},\overrightarrow{\alpha})&\text{si }x=0
\end{cases}
\end{array}
\]

\[
\begin{array}{rcl}
g:\omega^3\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m&\to&\omega\\
(A,t,x,\overrightarrow{x},\overrightarrow{\alpha})&\to&
\begin{cases}
0&\text{si }x>t+1\\
A+f(t+1,\overrightarrow{x},\overrightarrow{\alpha})&\text{si }x\le t+1
\end{cases}
\end{array}
\]

tenemos que \(G=R(h,g)\). Es decir que solo nos falta probar que \(h\) y \(g\) son \(\Sigma\)-p.r.. Nótese que

\[
h=C_0^{n+1,m}|_{D_1}\cup\lambda x\overrightarrow{x}\overrightarrow{\alpha}[f(0,\overrightarrow{x},\overrightarrow{\alpha})]|_{D_2}
\]

\[
g=C_0^{n+3,m}|_{H_1}\cup\lambda Atx\overrightarrow{x}\overrightarrow{\alpha}[A+f(t+1,\overrightarrow{x},\overrightarrow{\alpha})]|_{H_2}
\]

así que para ver que \(h\) y \(g\) son \(\Sigma\)-p.r. podemos aplicar el Lema 21 una vez que hayamos visto que las funciones

\[
\begin{aligned}
&C_0^{n+1,m}|_{D_1},\\
&\lambda x\overrightarrow{x}\overrightarrow{\alpha}[f(0,\overrightarrow{x},\overrightarrow{\alpha})]|_{D_2},\\
&C_0^{n+3,m}|_{H_1},\\
&\lambda Atx\overrightarrow{x}\overrightarrow{\alpha}[A+f(t+1,\overrightarrow{x},\overrightarrow{\alpha})]|_{H_2}
\end{aligned}
\]

son \(\Sigma\)-p.r.. Es claro que \(C_0^{n+1,m}\) y \(C_0^{n+3,m}\) son \(\Sigma\)-p.r.. También nótese que

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[f(0,\overrightarrow{x},\overrightarrow{\alpha})]
=f\circ[C_0^{n+1,m},p_2^{n+1,m},p_3^{n+1,m},\ldots,p_{n+1+m}^{n+1,m}]
\]

\[
\begin{aligned}
&\lambda Atx\overrightarrow{x}\overrightarrow{\alpha}[A+f(t+1,\overrightarrow{x},\overrightarrow{\alpha})]\\
&\quad=\lambda xy[x+y]\circ
\left[
p_1^{n+3,m},
f\circ[Suc\circ p_2^{n+3,m},p_4^{n+3,m},\ldots,p_{n+3+m}^{n+3,m}]
\right]
\end{aligned}
\]

lo cual, ya que \(f\) es \(\Sigma\)-p.r., nos dice que \(\lambda x\overrightarrow{x}\overrightarrow{\alpha}[f(0,\overrightarrow{x},\overrightarrow{\alpha})]\) y \(\lambda Atx\overrightarrow{x}\overrightarrow{\alpha}[A+f(t+1,\overrightarrow{x},\overrightarrow{\alpha})]\) son \(\Sigma\)-p.r.. O sea que el Lema 18 nos dice que solo nos resta probar que

\[
D_1=\{(x,\overrightarrow{x},\overrightarrow{\alpha})\in\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m:x>0\}
\]

\[
D_2=\{(x,\overrightarrow{x},\overrightarrow{\alpha})\in\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m:x=0\}
\]

\[
H_1=\{(z,t,x,\overrightarrow{x},\overrightarrow{\alpha})\in\omega^3\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m:x>t+1\}
\]

\[
H_2=\{(z,t,x,\overrightarrow{x},\overrightarrow{\alpha})\in\omega^3\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m:x\le t+1\}
\]

son \(\Sigma\)-p.r.. Veamos por ejemplo que \(H_1\) lo es. Es decir debemos ver que \(\chi_{H_1}^{\omega^{3+n}\times\Sigma^{\ast m}}\) es \(\Sigma\)-p.r.. Ya que \(f\) es \(\Sigma\)-p.r. tenemos que \(D_f=\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\) es \(\Sigma\)-p.r., lo cual por el Lema 17 nos dice que los conjuntos \(S_1,\ldots,S_n,L_1,\ldots,L_m\) son \(\Sigma\)-p.r.. Ya que \(\omega\) es \(\Sigma\)-p.r., el Lema 17 nos dice que

\[
R=\omega^3\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m
\]

es \(\Sigma\)-p.r.. Nótese que

\[
\chi_{H_1}^{\omega^{3+n}\times\Sigma^{\ast m}}=
(\chi_R^{\omega^{3+n}\times\Sigma^{\ast m}}\land\lambda ztx\overrightarrow{x}\overrightarrow{\alpha}[x>t+1])
\]

por lo cual \(\chi_{H_1}^{\omega^{3+n}\times\Sigma^{\ast m}}\) es \(\Sigma\)-p.r. ya que es la conjunción de dos predicados \(\Sigma\)-p.r.. La prueba de que \(D_1,D_2\) y \(H_2\) son \(\Sigma\)-p.r. es similar.

**Nota:** Aceptaremos sin prueba (b) y el caso de la productoria en (a). Las pruebas son muy similares a la dada para la sumatoria.

Veamos un ejemplo de cómo se puede aplicar el lema anterior. Sea \(F=\lambda yx_1\left[\sum_{t=0}^{t=y}(x_1)^t\right]\). Es claro que \(D_F=\omega^2\). Para ver que \(F\) es \(\Sigma\)-p.r. aplicaremos el lema anterior por lo cual es importante encontrar la \(f\) adecuada a la cual se le aplicará el lema. Tomemos \(f=\lambda tx_1[(x_1)^t]\). Claramente \(f\) es \(\Sigma\)-p.r. por lo cual el lema anterior nos dice que

\[
G=\lambda xyx_1\left[\sum_{t=x}^{t=y}f(t,x_1)\right]
=\lambda xyx_1\left[\sum_{t=x}^{t=y}(x_1)^t\right]
\]

es \(\Sigma\)-p.r.. Notar que \(G\) no es la función \(F\) pero es en algún sentido "más amplia" que \(F\) ya que tiene una variable más y se tiene que \(F(y,x_1)=G(0,y,x_1)\), para cada \(y,x_1\in\omega\). Es fácil ver que

\[
F=G\circ[C_0^{2,0},p_1^{2,0},p_2^{2,0}]
\]

por lo cual \(F\) es \(\Sigma\)-p.r..

Haga los siguientes ejercicios aplicando el lema anterior. No caiga en la tentación de hacerlos aplicando recursión primitiva ya que no se ejercitará en la habilidad de aplicar el lema en forma madura.

**Ejercicio 37:** Pruebe que las siguientes funciones son \(\Sigma\)-p.r..

**(a)** \(\lambda x\left[\prod_{t=10}^{t=x}t^t\right]\)

**(b)** \(\lambda xy\alpha\left[\prod_{t=y+1}^{t=|\alpha|}(t+|\alpha|)\right]\)

**(c)** \(\lambda xyz\alpha\beta\left[\operatorname*{C}_{t=3}^{t=z+5}\alpha^t\right]\)

**(d)** \(\lambda xyx_1\beta\left[\sum_{t=0}^{t=y}|\beta|.(x_1+t)\right]\)

**(e)** \(\lambda x_2xyz\alpha\beta\left[\operatorname*{C}_{t=x_2}^{t=z+5}\alpha^{y.x.t}\beta^z\right]\)

**Ejercicio 38:** Describa el dominio de \(G\) y pruebe que \(G\) es \(\Sigma\)-p.r.

**(a)** \(G=\lambda xx_1\left[\sum_{t=1}^{t=x}Pred(x_1)^t\right]\)

**(b)** \(G=\lambda xyz\alpha\beta\left[\operatorname*{C}_{t=3}^{t=z+5}\alpha^{Pred(z).t^x}\beta^{Pred(Pred(|\alpha|^y))}\right]\)

(Ojo que la la \(f\) a la cual le debe aplicar el lema de la sumatoria no es \(\Sigma\)-total)

**Cuantificación acotada de predicados \(\Sigma\)-p.r. con dominio rectangular.** Sea \(P:S\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega\) un predicado, con \(n,m\in\omega\). Supongamos además que \(S,S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) son no vacíos. Sea \(\overline{S}\subseteq S\). Entonces la expresión Booleana

\[
(\forall t\in\overline{S})_{t\le x}\ P(t,\overrightarrow{x},\overrightarrow{\alpha})
\]

depende de las variables \(x,\overrightarrow{x},\overrightarrow{\alpha}\) y valdrá 1 en una \((1+n+m)\)-upla \((x,\overrightarrow{x},\overrightarrow{\alpha})\) cuando \(P(t,\overrightarrow{x},\overrightarrow{\alpha})\) sea igual a 1 para cada \(t\in\{u\in\overline{S}:u\le x\}\); y 0 en caso contrario. Nótese que aquí es crucial que \(\overline{S}\subseteq S\) ya que si no sucediera esto no tendría sentido preguntarnos si \(P(t,\overrightarrow{x},\overrightarrow{\alpha})\) es 1 para cada \(t\in\{u\in\overline{S}:u\le x\}\). Además también para que la expresión \((\forall t\in\overline{S})_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})\) esté definida es preciso que \((\overrightarrow{x},\overrightarrow{\alpha})\in S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\). Sobre la variable \(x\) no hay ninguna restricción o sea que puede ser cualquier elemento de \(\omega\). Tenemos entonces que el dominio del predicado

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\forall t\in\overline{S})_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]
\]

es \(\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\). En forma análoga se define la forma de interpretar la expresión Booleana

\[
(\exists t\in\overline{S})_{t\le x}\ P(t,\overrightarrow{x},\overrightarrow{\alpha})
\]

Cabe destacar que

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\exists t\in\overline{S})_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]
=\neg\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\forall t\in\overline{S})_{t\le x}\neg P(t,\overrightarrow{x},\overrightarrow{\alpha})]
\]

Analicemos un poco por separado el caso \(\overline{S}=\emptyset\). Nos queda la expresión

\[
(\forall t\in\emptyset)_{t\le x}\ P(t,\overrightarrow{x},\overrightarrow{\alpha})
\]

la cual para que esté definida requiere que \((x,\overrightarrow{x},\overrightarrow{\alpha})\) esté en \(\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\) (ver (12) (d) de la notación lambda dada en la Guía 1); y siempre es verdadera. O sea que

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\forall t\in\emptyset)_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]
=C_1^{1+n,m}|_{\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m}
\]

Análogamente

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\exists t\in\emptyset)_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]
=C_0^{1+n,m}|_{\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m}
\]

También podemos cuantificar sobre variable alfabética. Sea \(P:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times L\to\omega\) un predicado, con \(S_1,\ldots,S_n\subseteq\omega\) y \(L,L_1,\ldots,L_m\subseteq\Sigma^\ast\) no vacíos. Supongamos \(\overline{L}\subseteq L\). Entonces la expresión Booleana

\[
(\forall\alpha\in\overline{L})_{|\alpha|\le x}\ P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)
\]

depende de las variables \(x,\overrightarrow{x},\overrightarrow{\alpha}\) y está definida cuando \((x,\overrightarrow{x},\overrightarrow{\alpha})\) pertenece a \(\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\). Dejamos al lector analizar cuando vale 1 el predicado

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\forall\alpha\in\overline{L})_{|\alpha|\le x}P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)]
\]

También dejamos al lector estudiar el comportamiento de la función

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\exists\alpha\in\overline{L})_{|\alpha|\le x}P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)]
\]

Cabe destacar que también

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\exists\alpha\in\overline{L})_{|\alpha|\le x}P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)]
=\neg\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\forall\alpha\in\overline{L})_{|\alpha|\le x}\neg P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)]
\]

Dejamos al lector que analice el caso \(\overline{L}=\emptyset\) y también el caso \(n=m=0\) para ambos tipos de cuantificación (es decir cuando \(P:S\subseteq\omega\to\omega\) o \(P:L\subseteq\Sigma^\ast\to\omega\)).

**Lema 24 (Lema de cuantificación acotada).** Sea \(\Sigma\) un alfabeto finito.

**(a)** Sea \(P:S\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega\) un predicado \(\Sigma\)-p.r., con \(S,S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) no vacíos. Supongamos \(\overline{S}\subseteq S\) es \(\Sigma\)-p.r.. Entonces

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\forall t\in\overline{S})_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]
\]

y

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\exists t\in\overline{S})_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]
\]

son predicados \(\Sigma\)-p.r..

**(b)** Sea \(P:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times L\to\omega\) un predicado \(\Sigma\)-p.r., con \(S_1,\ldots,S_n\subseteq\omega\) y \(L,L_1,\ldots,L_m\subseteq\Sigma^\ast\) no vacíos. Supongamos \(\overline{L}\subseteq L\) es \(\Sigma\)-p.r.. Entonces

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\forall\alpha\in\overline{L})_{|\alpha|\le x}P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)]
\]

y

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\exists\alpha\in\overline{L})_{|\alpha|\le x}P(\overrightarrow{x},\overrightarrow{\alpha},\alpha)]
\]

son predicados \(\Sigma\)-p.r..

**Proof.** **(a)** Sea

\[
\overline{P}=P|_{\overline{S}\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m}\cup C_1^{1+n,m}|_{(\omega-\overline{S})\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m}
\]

Nótese que \(\overline{P}\) tiene dominio \(\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\). Veamos que \(\overline{P}\) es \(\Sigma\)-p.r.. Ya que \(P\) es \(\Sigma\)-p.r. tenemos que \(D_P=S\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\) es \(\Sigma\)-p.r., lo cual por el Lema 17 nos dice que los conjuntos \(S_1,\ldots,S_n,L_1,\ldots,L_m\) son \(\Sigma\)-p.r.. Si \(\overline{S}\ne\emptyset\), ya que es \(\Sigma\)-p.r. por hipótesis, el Lema 17 nos dice que

\[
\overline{S}\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m
\]

es \(\Sigma\)-p.r.. Si \(\overline{S}=\emptyset\) entonces

\[
\overline{S}\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m
\]

es también \(\Sigma\)-p.r. ya que es igual al conjunto vacío. O sea que el Lema 18 nos dice que

\[
P|_{\overline{S}\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m}
\]

es \(\Sigma\)-p.r.. En forma similar, ya que \(\omega-\overline{S}\) es \(\Sigma\)-p.r. (Lema 16), obtenemos que

\[
C_1^{1+n,m}|_{(\omega-\overline{S})\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m}
\]

es \(\Sigma\)-p.r.. Pero entonces el Lema 21 nos dice que \(\overline{P}\) es \(\Sigma\)-p.r.. El Lema 23 nos dice que \(\lambda xy\overrightarrow{x}\overrightarrow{\alpha}\left[\prod_{t=x}^{t=y}\overline{P}(t,\overrightarrow{x},\overrightarrow{\alpha})\right]\) es \(\Sigma\)-p.r.. Ya que

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\forall t\in\overline{S})_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]
=\lambda x\overrightarrow{x}\overrightarrow{\alpha}\left[\prod_{t=0}^{t=x}\overline{P}(t,\overrightarrow{x},\overrightarrow{\alpha})\right]
\]

\[
=
\lambda xy\overrightarrow{x}\overrightarrow{\alpha}\left[\prod_{t=x}^{t=y}\overline{P}(t,\overrightarrow{x},\overrightarrow{\alpha})\right]\circ
[C_0^{1+n,m},p_1^{1+n,m},\ldots,p_{1+n+m}^{1+n,m}]
\]

tenemos que \(\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\forall t\in\overline{S})_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]\) es \(\Sigma\)-p.r..

Ya que

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\exists t\in\overline{S})_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]
=\neg\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\forall t\in\overline{S})_{t\le x}\neg P(t,\overrightarrow{x},\overrightarrow{\alpha})]
\]

tenemos que \(\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\exists t\in\overline{S})_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]\) es \(\Sigma\)-p.r.

**Nota:** Aceptaremos (b) sin prueba. Su prueba se basa en (a) y el lector puede verla en el apunte.

**OBSERVACIÓN:** La cuantificación no acotada no preserva la propiedad de ser \(\Sigma\)-p.r.. Como veremos más adelante hay un predicado \(\Sigma\)-p.r., \(P:\omega\times L_1\to\omega\), tal que el predicado \(\lambda\alpha[(\exists t\in\omega)P(t,\alpha)]\) no es \(\Sigma\)-efectivamente computable, por lo cual tampoco es \(\Sigma\)-p.r. (ni siquiera podrá ser \(\Sigma\)-recursivo).

Veamos por ejemplo que el predicado \(\lambda xy[x\text{ divide }y]\) es \(\Sigma\)-p.r.. Sea \(P=\lambda tx_1x_2[x_2=t.x_1]\). Es claro que \(P\) es \(\Sigma\)-p.r.. El lema anterior nos dice que \(\lambda xx_1x_2[(\exists t\in\omega)_{t\le x}P(t,x_1,x_2)]\) es \(\Sigma\)-p.r.. Nótese que \(x_1\) divide \(x_2\) si y solo si hay un \(t\le x_2\) tal que \(x_2=t.x_1\). Esto nos dice que

\[
\lambda x_1x_2[x_1\text{ divide }x_2]=\lambda x_1x_2[(\exists t\in\omega)_{t\le x_2}P(t,x_1,x_2)]
\]

Pero

\[
\lambda x_1x_2[(\exists t\in\omega)_{t\le x_2}P(t,x_1,x_2)]
=\lambda xx_1x_2[(\exists t\in\omega)_{t\le x}P(t,x_1,x_2)]\circ[p_2^{2,0},p_1^{2,0},p_2^{2,0}]
\]

por lo cual \(\lambda x_1x_2[x_1\text{ divide }x_2]\) es \(\Sigma\)-p.r.

La idea fundamental subyacente en la aplicación anterior es que en muchos casos de predicados obtenidos por cuantificación a partir de otros predicados, la variable cuantificada tiene una cota natural en términos de las otras variables y entonces componiendo adecuadamente se lo puede presentar como un caso de cuantificación acotada

**Ejercicio 39:** Use que

\[
x\text{ es primo sii }x>1\land((\forall t\in\omega)_{t\le x}\ t=1\lor t=x\lor\neg(t\text{ divide }x))
\]

para probar que \(\lambda x[x\text{ es primo}]\) es \(\Sigma\)-p.r.

A continuación enunciamos una regla que es útil cuando queremos probar que cierto conjunto es \(\Sigma\)-p.r..

**Regla Caracterizar Pertenencia:** Si Ud está intentando probar que cierto conjunto \(S\subseteq\omega^n\times\Sigma^{\ast m}\) es \(\Sigma\)-p.r., entonces puede ser útil primero caracterizar la pertenencia a \(S\), es decir escribir algo del tipo:

- Para cada \((\overrightarrow{x},\overrightarrow{\alpha})\in\omega^n\times\Sigma^{\ast m}\) se tiene que: \((\overrightarrow{x},\overrightarrow{\alpha})\in S\) si y solo si ...

Por ejemplo si queremos probar que \(S=\{\beta^2:\beta\in\Sigma^\ast\}\) es un conjunto \(\Sigma\)-p.r. podemos primero notar que

- Para cada \(\alpha\in\Sigma^\ast\) se tiene que: \(\alpha\in S\) si y solo si \((\exists\beta\in\Sigma^\ast)\) tal que \(\alpha=\beta^2\)

lo cual ya nos deja en evidencia que podemos aplicar el Lema de Cuantificación Acotada para probar que \(\chi_S^{\Sigma^\ast}=\lambda\alpha[\alpha\in S]\) es \(\Sigma\)-p.r.. A esta regla la llamaremos Regla CP por brevedad.

**Ejercicio 40:** Pruebe que

**(a)** \(\lambda\alpha\beta[\alpha\text{ inicial }\beta]\) es un predicado \(\Sigma\)-p.r..

**(b)** \(\{\beta^2:\beta\in\Sigma^\ast\}\) es un conjunto \(\Sigma\)-p.r..

**(c)** \(\{2^x:x\in\omega\text{ y }x\text{ es impar}\}\) es un conjunto \(\Sigma\)-p.r.. (Aplique Regla CP).

**(d)** \(\{(x,\alpha,\beta)\in\omega\times\Sigma^\ast\times\Sigma^\ast:(\exists t\in\omega)\ \alpha^x=\beta^t\}\) es un conjunto \(\Sigma\)-p.r..

**(e)** \(\{(2^x,@^x,\$):x\in\omega\text{ y }x\text{ es impar}\}\) es un conjunto \(\Sigma\)-p.r. (aquí asuma \(\Sigma=\{@,\$\}\)). (Aplique Regla CP).

**Ejercicio 41:** Dos números \(p,q\in\mathbf{N}\) son llamados primos consecutivos si ambos son primos, \(p<q\) y no hay ningún primo \(r\) tal que \(p<r<q\). Pruebe que el conjunto

\[
\{(p,q):p\text{ y }q\text{ son primos consecutivos}\}
\]

es \(\Sigma\)-p.r

**Ejercicio 42:** Dados \(x,y\in\omega\), diremos que \(x\) e \(y\) son coprimos cuando 1 sea el único elemento de \(\omega\) que divide a ambos. Sea \(P=\lambda xy[x\text{ e }y\text{ son coprimos}]\). Pruebe que \(P\) es \(\Sigma\)-p.r.

**Ejercicio 43:** Pruebe que los siguientes conjuntos son \(\Sigma\)-p.r..

**(a)** \(\{(x,\alpha,\beta)\in\omega\times\Sigma^\ast\times\Sigma^\ast:(\exists t\in Im(pr))\ \alpha^{Pred(Pred(x)).Pred(|\alpha|)}=\beta^t\}\)

**(b)** \(\{(x,\alpha)\in\omega\times\Sigma^\ast:(\exists\beta\in\{@,\%\}^+)\ \alpha\beta^{Pred(x)}=\beta^{Pred(x)}\alpha\}\) (aquí suponga que \(\{@,\%\}\subseteq\Sigma\))

**(c)** \(\{(x,\alpha)\in\{1,9\}\times\Sigma^+:(\exists\beta\in\Sigma^+)\ |\beta|>x\text{ y }\beta^{Pred(x)}=\alpha\}\)

(Ojo que el predicado al cual deberá aplicarle el lema de cuantificación acotada no es \(\Sigma\)-total)

**Ejercicio 44:** Sea \(\Sigma=\{@,\%\}\). Sea \(S\subseteq\omega\) un conjunto \(\Sigma\)-p.r. Pruebe que

\[
\{(x,y,\alpha)\in S\times S\times\Sigma^+:(\exists t\in S)\ |\alpha|^t=Pred(Pred(x))\}
\]

es \(\Sigma\)-p.r.. (Ojo que aquí el predicado al cual deberá aplicarle el lema de cuantificación acotada no es \(\Sigma\)-total).

Como puede notarse, en los ejercicios anteriores se aplica una sola vez el lema de cuantificación acotada. En los ejercicios que siguen veremos algunos casos en los cuales es necesario anidar cuantificaciones acotadas.

**Ejercicio 45:** Pruebe que

**(a)** \(\lambda\alpha\beta[\alpha\text{ ocurre en }\beta]\) es un predicado \(\Sigma\)-p.r..

**(b)** \(\{@^t!^l:t\in\mathbf{N}\text{ y }l\text{ es impar}\}\) es un conjunto \(\Sigma\)-p.r.. (Aplique Regla CP).

**(c)** \(\{@^t!^l:t\in\mathbf{N}\text{ y }l\text{ es impar}\}\) es un conjunto \(\Sigma\)-p.r. (aquí suponga que \(@,!\in\Sigma\)). (Aplique Regla CP).

**(d)** \(\{(2^t,\gamma^5):\gamma\in\{@,\%\}^+\text{ y }t>|\gamma|\}\) es un conjunto \(\Sigma\)-p.r. (aquí suponga que \(\{@,\%\}\subseteq\Sigma\)). (Aplique Regla CP).

**(e)** \(\{(2^{t+l},10^{t.l},\gamma):\gamma\in\{@,\%\}^+\text{ y }t>l\}\) es un conjunto \(\Sigma\)-p.r. (aquí suponga que \(\{@,\%\}\subseteq\Sigma\)). (Aplique Regla CP).

**(f)** \(\{x\in\mathbf{N}:\exists p,q\text{ tales que }x=p.q\text{ y }p,q\text{ son primos}\}\) es un conjunto \(\Sigma\)-p.r.

**Ejercicio 46:** Sea \(\Sigma=\{@,\triangle,\heartsuit,\bigcirc\}\) y sean \(L_1,L_2\subseteq\{\triangle,\heartsuit,\bigcirc\}^\ast\) conjuntos \(\Sigma\)-p.r.. Pruebe que el conjunto

\[
\{\alpha\text{@}\beta:\alpha\in L_1\text{ y }\beta\in L_2\}
\]

es \(\Sigma\)-p.r.. (Aplique Regla CP).

**Ejercicio 47:** Sea \(M=(Q,\{@,\%\},\Gamma,\delta,q_0,B,F)\) una máquina de Turing y supongamos \(Q=\{q_0,q_1\}\) es un alfabeto disjunto con \(\Gamma\). Pruebe que el conjunto \(Des\) formado por todas las descripciones instantáneas de \(M\) es \((\Gamma\cup Q)\)-p.r.. (Hint: note que \(Des=Des_0\cup Des_1\), donde \(Des_i=\{\alpha\in Des:St(\alpha)=q_i\}\), por lo cual basta con probar que cada \(Des_i\) es \((\Gamma\cup Q)\)-p.r.). Puede usar que la función \(\lambda i\alpha[[\alpha]_i]\) es \((\Gamma\cup Q)\)-p.r. (aquí la notación lambda es relativa al alfabeto \(\Gamma\cup Q\)).

## Ejercicios de examen

Cada resultado teórico que aplique en la resolución deberá enunciarlo por separado detalladamente (en la forma en la que está en las guías). Para los ejercicios listados a continuación puede usar sin demostración que las siguientes funciones son \(\Sigma\)-p.r.: \(Suc\), \(Pred\), \(d_a\) (con \(a\in\Sigma\)), \(p_j^{n,m}\) (con \(n,m,j\in\omega\) y \(1\le j\le n+m\)), \(\lambda xy[x\le y]\), \(\lambda\alpha[|\alpha|]\), \(\lambda xy[x=y]\), \(\lambda\alpha\beta[\alpha=\beta]\), \(\lambda xy[x+y]\), \(\lambda xy[x.y]\), \(\lambda xy[x\mathbin{\dot{-}}y]\), \(\lambda x\alpha[\alpha^x]\), \(\lambda xy[x^y]\), \(C_k^{n,m}\), \(C_\alpha^{n,m}\) (con \(n,m,k\in\omega\) y \(\alpha\in\Sigma^\ast\)).

**(1)** Sea \(\Sigma=\{@,\%,\$\}\) y sea \(\le\) el orden total sobre \(\Sigma\) dado por \(@<\%<\text{\$}\). Pruebe que \(s^\le\), \(\#^\le\) y \(\ast^\le\) son \(\Sigma\)-p.r.

**(2)** Defina las funciones \(Sig\) y \(Dec\).

**(a)** Pruebe que \(Sig\) y \(Des\) son \(Num\)-p.r.

**(b)** Sea \(\Gamma=\{@,\%\}\cup Num\). Pruebe que \(Dec\) es \(\Gamma\)-p.r..

**(3)** Sea \(\Sigma=\{@,!,\%\}\). Sea

\[
\begin{array}{rcl}
f:\mathbf{N}\times\{@,\%\}^\ast\times\{@,!,\%\}^+&\to&\omega\\
(x,\alpha,\beta)&\to&
\begin{cases}
Pred(|\alpha|)&\text{si }|\alpha|>2\text{ y }x\ge 1\\
|\beta|&\text{si }|\alpha|\le 2\text{ o }x=0
\end{cases}
\end{array}
\]

Pruebe que \(f\) es \(\Sigma\)-p.r..

**(4)** Sea \(\Sigma=\{@,!,\%\}\). Sea

\[
\begin{array}{rcl}
f:\{(x,\alpha,\beta)\in\omega\times\Sigma^\ast\times\Sigma^\ast:x\ge|\beta|\}&\to&\omega\\
(x,\alpha,\beta)&\to&
\begin{cases}
Pred(|\alpha|)&\text{si }|\alpha|>2\text{ y }x\ge 1\\
x&\text{si }|\alpha|\le 2\text{ o }x=0
\end{cases}
\end{array}
\]

Pruebe que \(f\) es \(\Sigma\)-p.r..

**(5)** Sea \(\Sigma=\{@,\%,!\}\). Sea

\[
\begin{array}{rcl}
f:\{1,4\}\times\mathbf{N}\times\{@,\%\}^\ast&\to&\omega\\
(x,y,\alpha)&\to&
\begin{cases}
x&\text{si }\alpha=\text{@@}\\
Pred(|\alpha|)&\text{si }\alpha\ne\text{@@}\land|\alpha|>y\\
y&\text{si }\alpha\ne\text{@@}\land|\alpha|\le y
\end{cases}
\end{array}
\]

Pruebe que \(f\) es \(\Sigma\)-p.r..

**(6)** Sea \(\Sigma=\{@,\$,\%,!\}\). Sea

\[
\begin{array}{l}
f:\{(x,y,\alpha,\beta)\in\omega^2\times\Sigma^{\ast 2}:\\
\qquad \beta\in\{@,\$\}^\ast\text{ o }x\text{ es par}\}\to\omega\\[2mm]
(x,y,\alpha,\beta)\to
\begin{cases}
x^2&\text{si }|\alpha|\le y\\
Pred(|\alpha|)&\text{si }|\alpha|>y
\end{cases}
\end{array}
\]

Pruebe que \(f\) es \(\Sigma\)-p.r..

**(7)** Sea \(\Sigma=\{@,\$,\%,!\}\). Sea

\[
\begin{array}{rcl}
f:\{(\alpha,\beta)\in\Sigma^{\ast 2}:\beta\in\{@,\$\}^\ast\text{ o }\alpha\in\{\$,!\}^+\}&\to&\Sigma^\ast\\
(\alpha,\beta)&\to&
\begin{cases}
\beta&\text{si }|\alpha|\le 5\\
\alpha^{Pred(|\alpha|)}&\text{si }|\alpha|>5
\end{cases}
\end{array}
\]

Pruebe que \(f\) es \(\Sigma\)-p.r..

**(8)** Sean \(f_1,f_2:\omega\to\omega\) funciones \(\Sigma\)-p.r.. Sea \(F:\omega\to\omega\) dada por

\[
\begin{aligned}
F(0)&=0\\
F(1)&=f_1(0)\\
F(2)&=f_2(f_1(0))\\
F(3)&=f_1(f_2(f_1(0)))\\
F(4)&=f_2(f_1(f_2(f_1(0))))\\
&\vdots
\end{aligned}
\]

Pruebe que \(F\) es \(\Sigma\)-p.r..

**(9)** Sea \(\Sigma=\{@,!,\%\}\).

**(a)** Describa el dominio de \(\lambda i\alpha[[\alpha]_i]\) (según manda la notación lambda)

**(b)** Pruebe que \(\lambda i\alpha[[\alpha]_i]\) es \(\Sigma\)-p.r..

**(10)** Sea

\[
G=\lambda zxx_1\alpha\left[\prod_{t=1}^{t=|\alpha|}z^t.Pred(x.|\alpha|)\right]
\]

**(a)** Describa el dominio de \(G\) (según manda la notación lambda)

**(b)** Pruebe que \(G\) es \(\Sigma\)-p.r.. (Ojo que la la \(f\) a la cual le debe aplicar el lema de la sumatoria no es \(\Sigma\)-total)

**(11)** Sea \(g:\omega\to\omega\) una función \(\Sigma\)-p.r.. Sea

\[
G=\lambda zx_1\alpha\left[\prod_{t=1}^{t=|\alpha|}g(Pred((t+1).x_1.|\alpha|))\right]
\]

**(a)** Describa el dominio de \(G\) (según manda la notación lambda)

**(b)** Pruebe que \(G\) es \(\Sigma\)-p.r.. (Ojo que la la \(f\) a la cual le debe aplicar el lema de la sumatoria no es \(\Sigma\)-total)

**(12)** Sea \(g:\omega\to\Sigma^\ast\) una función \(\Sigma\)-p.r.. Sea

\[
G=\lambda zx_1x_2\alpha\left[\operatorname*{C}_{t=x_2}^{t=z+5}g(t.Pred(x_1.|\alpha|))\right]
\]

**(a)** Describa el dominio de \(G\) (según manda la notación lambda)

**(b)** Pruebe que \(G\) es \(\Sigma\)-p.r.. (Ojo que la la \(f\) a la cual le debe aplicar el lema de la sumatoria no es \(\Sigma\)-total)

**(13)** Sea

\[
G=\lambda xzyx_2\left[\sum_{t=Pred(y)}^{t=x}Pred(z)^t\right]
\]

**(a)** Describa el dominio de \(G\) (según manda la notación lambda)

**(b)** Pruebe que \(G\) es \(\Sigma\)-p.r.. (Ojo que la la \(f\) a la cual le debe aplicar el lema de la sumatoria no es \(\Sigma\)-total)

**(14)** Sea

\[
G=\lambda xzyx_2\left[\sum_{t=Pred(x_2)}^{t=x_2}x.y.z.t\right]
\]

**(a)** Describa el dominio de \(G\) (según manda la notación lambda)

**(b)** Pruebe que \(G\) es \(\Sigma\)-p.r.. (Ojo que la la \(f\) a la cual le debe aplicar el lema de la sumatoria no es \(\Sigma\)-total)

**(15)** Sea \(\Sigma=\{@,!,\%\}\).

**(a)** Describa el dominio de \(\lambda x[x\text{ es primo}]\) (según manda la notación lambda)

**(b)** Pruebe que \(\lambda x[x\text{ es primo}]\) es \(\Sigma\)-p.r..

**(16)** Sea \(\Sigma=\{@,\%,!\}\). Sea \(S=\{x\in\omega:x\text{ es par}\}\). Pruebe que

\[
L=\{\alpha\in\Sigma^\ast:\text{ si }[\alpha]_i=@,\text{ entonces }[\alpha]_{i+1}=\%,\text{ para cada }i\in S\}
\]

es \(\Sigma\)-p.r.. Puede usar que la función \(\lambda i\alpha[[\alpha]_i]\) es \(\Sigma\)-p.r..

**(17)** Sea \(\Sigma=\{@,\%,!\}\). Sea \(L=\{\alpha\in\Sigma^\ast:|\alpha|\text{ es impar}\}\). Pruebe que

\[
H=\{(\alpha,\beta,\rho)\in L\times\Sigma^\ast\times L:(\exists\gamma\in L)\ \beta\rho=\alpha\text{ y }\beta^{Pred(|\gamma|)}=\alpha\}
\]

es \(\Sigma\)-p.r.. (Ojo que aquí el predicado al cual deberá aplicarle el lema de cuantificación acotada no es \(\Sigma\)-total).

**(18)** Sea \(\Sigma=\{\triangle,\bigcirc\}\). Sea \(S=\{x\in\omega:x\text{ es par}\}\). Pruebe que

\[
H=\{(x,\alpha)\in\omega\times\{\triangle\}^\ast:(\exists t\in S)\ t^2=|\alpha|.Pred(x)\}
\]

es \(\Sigma\)-p.r.. (Ojo que aquí el predicado al cual deberá aplicarle el lema de cuantificación acotada no es \(\Sigma\)-total).

**(19)** Sea \(\Sigma=\{@,\triangle,\heartsuit,\bigcirc\}\). Sea \(S=\{x\in\omega:10\le x\}\). Pruebe que

\[
H=\{(x,\alpha,\beta)\in\omega\times\{@,\triangle\}^\ast\times\Sigma^+:(\exists t\in S)\ \alpha^{Pred(Pred(x)).Pred(|\alpha|)}=\beta^t\}
\]

es \(\Sigma\)-p.r.. (Ojo que aquí el predicado al cual deberá aplicarle el lema de cuantificación acotada no es \(\Sigma\)-total).

**(20)** Sea \(\Sigma=\{@,\triangle,\heartsuit,\bigcirc\}\). Sea \(S=\{x\in\omega:100\le x\}\). Pruebe que

\[
H=\{(x,\alpha,\rho)\in S\times\Sigma^\ast\times\Sigma^+:(\exists\beta\in\{@,\triangle\}^\ast)\ \alpha\beta^{Pred(x)}=\rho\alpha\}
\]

es \(\Sigma\)-p.r.. (Ojo que aquí el predicado al cual deberá aplicarle el lema de cuantificación acotada no es \(\Sigma\)-total).

**(21)** Sea \(\Sigma=\{@,\triangle,\heartsuit,\bigcirc\}\). Sea \(S=\{x\in\omega:3\text{ divide a }x\}\). Pruebe que

\[
H=\{(x,\alpha)\in S\times\Sigma^\ast:(\exists\beta\in\{\triangle,\heartsuit,\bigcirc\}^+)\ |\beta|>x\text{ y }\beta^{Pred(x)}=\alpha\}
\]

es \(\Sigma\)-p.r.. (Ojo que aquí el predicado al cual deberá aplicarle el lema de cuantificación acotada no es \(\Sigma\)-total).

**(22)** Sea \(\Sigma=\{@,\%\}\). Sea \(L\subseteq\Sigma^\ast\) un conjunto \(\Sigma\)-p.r. Pruebe que

\[
H=\{(x,y,\alpha)\in\omega\times\omega\times L:(\exists t\in\mathbf{N})\ t^2=|\alpha|.y^{Pred(Pred(x))}\}
\]

es \(\Sigma\)-p.r.. (Ojo que aquí el predicado al cual deberá aplicarle el lema de cuantificación acotada no es \(\Sigma\)-total).

**(23)** Sea \(\Sigma=\{@,\%\}\). Sea \(S\subseteq\omega\) un conjunto \(\Sigma\)-p.r. Pruebe que

\[
H=\{(x,y,\alpha)\in S\times S\times\Sigma^+:(\exists t\in S)\ |\alpha|^t=Pred(Pred(x))\}
\]

es \(\Sigma\)-p.r.. (Ojo que aquí el predicado al cual deberá aplicarle el lema de cuantificación acotada no es \(\Sigma\)-total).

**(24)** Sea \(\Sigma=\{@,\triangle,\heartsuit,\bigcirc\}\) y sean \(L_1,L_2\subseteq\{\triangle,\heartsuit,\bigcirc\}^\ast\) conjuntos \(\Sigma\)-p.r.. Pruebe que el conjunto

\[
H=\{\alpha\text{@}\beta:\alpha\in L_1\text{ y }\beta\in L_2\}
\]

es \(\Sigma\)-p.r..

**(25)** Sea \(\Sigma=\{@,\triangle,\heartsuit,\bigcirc\}\) y sean \(L\subseteq\{\triangle,\heartsuit,\bigcirc\}^\ast\) y \(S\subseteq\omega\) conjuntos \(\Sigma\)-p.r.. Pruebe que el conjunto

\[
H=\{[\alpha]_i@\alpha:\alpha\in L\text{ y }i\in S\}
\]

es \(\Sigma\)-p.r.. Puede usar que la función \(\lambda i\alpha[[\alpha]_i]\) es \(\Sigma\)-p.r..

**(26)** Sea \(\Sigma=\{\triangle,\heartsuit,\bigcirc\}\) y sean \(L\subseteq\{\triangle,\heartsuit,\bigcirc\}^\ast\) y \(S\subseteq\omega\) conjuntos \(\Sigma\)-p.r.. Pruebe que el conjunto

\[
H=\{\alpha^x:\alpha\in L\text{ y }x\in S\}
\]

es \(\Sigma\)-p.r

**(27)** Sea \(\Sigma=\{\triangle,\heartsuit,\bigcirc\}\). Sean \(S_1,S_2\subseteq\omega\) conjuntos \(\Sigma\)-p.r.. Pruebe que el conjunto

\[
H=\{(x.y,\triangle\triangle\bigcirc):x\in S_1\text{ y }y\in S_2\}
\]

es \(\Sigma\)-p.r

**(28)** Sea \(\Sigma=\{@,!\}\). Pruebe que

\[
H=\{2^t5^l:t,l\in\mathbf{N}\text{ y }t>l\}
\]

es \(\Sigma\)-p.r..

**(29)** Sea \(\Sigma=\{@,!\}\). Pruebe que

\[
H=\{(2^t,(\text{@@!!})^l):t,l\in\mathbf{N}\text{ y }t>l\}
\]

es \(\Sigma\)-p.r..

**(30)** Sea \(\Sigma=\{@,\%,!\}\). Pruebe que

\[
H=\{(2^t,\gamma^5):\gamma\in\{@,\%\}^+\text{ y }t>|\gamma|\}
\]

es \(\Sigma\)-p.r..

**(31)** Sea \(\Sigma=\{@,\%,!\}\). Pruebe que

\[
H=\{(2^{t+l},10^{t.l},\gamma):\gamma\in\{@,\%\}^+\text{ y }t>l\}
\]

es \(\Sigma\)-p.r..

**(32)** Sea \(M=(Q,\{@,\%\},\Gamma,\delta,q_0,B,F)\) una máquina de Turing y supongamos \(Q=\{q_0,q_1\}\) es un alfabeto disjunto con \(\Gamma\). Pruebe que el conjunto \(Des\) formado por todas las descripciones instantáneas de \(M\) es \((\Gamma\cup Q)\)-p.r.. (Hint: note que \(Des=Des_0\cup Des_1\), donde \(Des_i=\{\alpha\in Des:St(\alpha)=q_i\}\), por lo cual basta con probar que cada \(Des_i\) es \((\Gamma\cup Q)\)-p.r.). Puede usar que la función \(\lambda i\alpha[[\alpha]_i]\) es \((\Gamma\cup Q)\)-p.r. (aquí la notación lambda es relativa al alfabeto \(\Gamma\cup Q\)).

**(33)** Sea \(\Gamma=\{N,\leftarrow\}\cup Num\). Para hacer más ágil la notación escribiremos \(\overline{n}\) en lugar de \(Dec(n)\). Sea

\[
L=\{N\overline{k}\leftarrow N\overline{n}:k,n\in\mathbf{N}\}
\]

Pruebe que \(L\) es \(\Gamma\)-p.r.. (Puede usar que \(Dec\) es \(\Gamma\)-p.r.).
