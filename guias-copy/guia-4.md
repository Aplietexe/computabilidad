# GUÍA 4 DE LENGUAJES: EL PARADIGMA DE TURING

## Tres paradigmas matemáticos de la computabilidad efectiva

Ya que el concepto de procedimiento efectivo es un concepto intuitivo, impreciso y a priori no expresado en el formalismo matemático, los conceptos de

- Función \(\Sigma\)-efectivamente computable
- Conjunto \(\Sigma\)-efectivamente computable
- Conjunto \(\Sigma\)-efectivamente enumerable

también son imprecisos y están fuera del formalismo matemático, debido a que los tres se definen en términos de la existencia de procedimientos efectivos. Por supuesto, los tres conceptos son fundamentales en el estudio teórico de la computabilidad por lo que es muy importante poder dar un modelo o formalización matemática de estos conceptos. Pero nótese que los dos últimos se definen en función del primero por lo que una formalización matemática precisa del concepto de función \(\Sigma\)-efectivamente computable, resuelve el problema de modelizar en forma matemática a estos tres conceptos.

En esta materia daremos las tres formalizaciones matemáticas más clásicas del concepto de función \(\Sigma\)-efectivamente computable. La primera y la más apegada a la idea intuitiva de procedimiento efectivo es la dada por Alan Turing vía la matematización del concepto de máquina. Llamaremos a esta modelización el paradigma de Turing y lo desarrollaremos en esta guía. La segunda, es la dada por Gödel en su estudio de sistemas formales de la lógica de primer orden. Llamaremos a esta modelización el paradigma de Gödel o el paradigma funcional o el paradigma recursivo. Por último veremos una formalización vía un lenguaje de programación imperativo. En honor a la influencia que tuvo Von Neumann en el diseño de la primera computadora de carácter universal (i.e. programable de propósito general), llamaremos a este paradigma el paradigma de Neumann o el paradigma imperativo. Dada la naturaleza filosófica e imprecisa del concepto de procedimiento efectivo y de sus conceptos derivados (i.e. función \(\Sigma\)-efectivamente computable, etc ) a este conjunto de conceptos fundamentales para las ciencias de la computación lo llamaremos el paradigma filosófico. En honor al filósofo y matemático Gottfried Leibniz llamaremos también al paradigma filosófico, el paradigma de Leibniz. Cabe destacar que Leibniz creó la primera máquina de calcular, llamada la Stepped Reckoner.

Con esta manera de hablar nótese que los paradigmas matemáticos de Turing, Gödel y Neumann intentan modelizar al paradigma de Leibniz. Para darle un toque de humor expresaremos esto diciendo que Turing, Gödel y Neumann intentan vencer a Leibniz.

## Descripción informal de las máquinas de Turing

Comenzaremos estudiando el concepto de máquina de Turing, el cual fue introducido por Alan Turing para formalizar o modelizar matemáticamente la idea de procedimiento efectivo. Una vez definidas las máquinas podremos dar una modelización matemática precisa del concepto de función \(\Sigma\)-efectivamente computable. Llamaremos a estas funciones \(\Sigma\)-Turing computables y serán aquellas que (en algún sentido que será bien precisado matemáticamente) pueden ser computadas por una máquina de Turing. Por supuesto, la fidedignidad de este concepto, es decir cuán buena es la modelización matemática dada por Turing, puede no ser clara al comienzo pero a medida que vayamos avanzando en nuestro estudio y conozcamos además los otros paradigmas y su relación, quedará claro que el modelo de Turing es acertado.

Vivimos en un mundo plagado de máquinas (ascensores, celulares, relojes, taladros, etc). Una característica común a todas las máquinas es que tienen distintos estados posibles. Un estado es el conjunto de características que determinan un momento concreto posible de la máquina cuando está funcionando. Por ejemplo un estado posible de un ascensor sería:

- está en el tercer piso, con la primer puerta abierta y la otra cerrada, está apretado el botón de ir al sexto piso, etc

donde ponemos etc porque dependiendo del tipo de ascensor (si es con memoria, a que pisos puede ir, etc) habrá más datos que especificar para determinar un estado concreto.

Otra característica común de las máquinas es que interactúan de distintas formas con el usuario o más generalmente su entorno. Dependiendo de qué acción se ejecute sobre la máquina y en qué estado esté, la máquina realizará alguna tarea y además cambiará de estado. En general las máquinas son determinísticas en el sentido que siempre que estén en determinado estado y se les aplique determinada acción, realizarán la misma tarea y pasarán al mismo estado.

Las máquinas de Turing son un modelo abstracto de máquina con una cantidad finita de estados la cual trabaja sobre una cinta de papel dividida en cuadros e interactúa o recibe acciones externas por medio de una cabeza lectora la cual lee de a un cuadro de la cinta a la vez y además puede borrar el contenido del cuadro leído y escribir en el un símbolo. También la cabeza lectora puede moverse un cuadro hacia la izquierda o hacia la derecha. La cinta tiene un primer cuadro hacia su izquierda pero hacia la derecha puede extenderse todo lo necesario. En un cuadro de la cinta podrá haber un símbolo o un cuadro puede simplemente estar en blanco. Es decir que habrá un alfabeto \(\Gamma\) el cual consiste de todos los símbolos que pueden figurar en la cinta. Esto será parte de los datos o características de cada máquina, es decir, \(\Gamma\) puede cambiar dependiendo de la máquina. La máquina, en función del estado en que se encuentre y de lo que vea su cabeza lectora en el cuadro escaneado, podrá modificar lo que encuentre en dicho cuadro (borrando y escribiendo algún nuevo símbolo), moverse a lo sumo un cuadro (izquierda, derecha o quedarse quieta), y cambiar de estado (posiblemente al mismo que tenía). Para simplificar supondremos que hay en \(\Gamma\) un símbolo el cual si aparece en un cuadro de la cinta, significará que dicho cuadro está sin escribir o en blanco. Esto nos permitirá describir más fácilmente el funcionamiento de la máquina. En gral llamaremos \(B\) a tal símbolo. También por lo general llamaremos \(Q\) al conjunto de estados de la máquina.

También cada máquina tendrá un estado especial el cual será llamado su estado inicial, generalmente denotado con \(q_0\), el cual será el estado en el que estará la máquina al comenzar a trabajar sobre la cinta. Hay otras características que tendrán las máquinas de Turing pero para dar un primer ejemplo ya nos basta. Describiremos una máquina de Turing \(M\) que tendrá \(\Gamma = \{@, a, b, B\}\) y tendrá dos estados, es decir \(Q = \{q_0, q_1\}\). Obviamente \(q_0\) será su estado inicial y además el "comportamiento o personalidad" de \(M\) estará dado por las siguientes cláusulas:

- Estando en estado \(q_0\) si ve ya sea \(b\) o \(B\) o \(@\), entonces se queda en estado \(q_0\) y se mueve a la derecha
- Estando en estado \(q_0\) si ve \(a\) entonces reescribe \(@\), se mueve a la izquierda y cambia al estado \(q_1\)
- Estando en estado \(q_1\) si ve \(a\) o \(b\) o \(B\) o \(@\) entonces lo deja como está, se mueve a la izquierda y queda en estado \(q_1\)

Supongamos ahora que tomamos una palabra \(\alpha \in \Gamma^\ast\) y la distribuimos en la cinta dejando el primer cuadro en blanco y luego poniendo los símbolos de \(\alpha\) en los siguientes cuadros. Supongamos además que ponemos la máquina en estado \(q_0\) y con su cabeza lectora escaneando el primer cuadro de la cinta. Esto lo podemos representar gráficamente de la siguiente manera

\[
\begin{array}{ccccccccc}
B & \alpha_1 & \cdots & \alpha_n & B & B & B & \cdots\\
\uparrow\\
q_0
\end{array}
\]

donde \(\alpha_1, \ldots, \alpha_n\) son los sucesivos símbolos de \(\alpha\). Supongamos además que \(a\) ocurre en \(\alpha\). Dejamos al lector ir aplicando las cláusulas de \(M\) para convencerse que luego de un rato de funcionar \(M\), la situación será

\[
\begin{array}{ccccccccc}
B & \beta_1 & \cdots & \beta_n & B & B & B & \cdots\\
\uparrow\\
q_1
\end{array}
\]

donde \(\beta_1 \ldots \beta_n\) es el resultado de reemplazar en \(\alpha\) la primera ocurrencia de \(a\) por \(@\).

**Ejercicio 1:** Qué sucede cuando \(a\) no ocurre en \(\alpha\)?

Una cosa que puede pasar es que para un determinado estado \(p\) y un \(\sigma \in \Gamma\), la máquina no tenga contemplada ninguna acción posible. Por ejemplo sea \(M\) la máquina de Turing dada por \(Q = \{q_0\}\), \(\Gamma = \{@, \$, B\}\) y por la siguiente cláusula:

- Estando en estado \(q_0\) si ve ya sea \(@\) o \(B\), entonces se queda en estado \(q_0\) y se mueve a la derecha

Es fácil ver que si partimos de una situación

\[
\begin{array}{ccccccccc}
B & \alpha_1 & \cdots & \alpha_n & B & B & B & \cdots\\
\uparrow\\
q_0
\end{array}
\]

donde \(\alpha_1, \ldots, \alpha_n \in \Gamma\), entonces si ningún \(\alpha_i\) es igual a \(\$\), la máquina se moverá indefinidamente hacia la derecha y en caso contrario se moverá \(i\) pasos a la derecha y se detendrá, donde \(i\) es el menor \(l\) tal que \(\alpha_l = \$\).

Otro caso posible de detención de una máquina de Turing es cuando está escaneando el primer cuadro de la cinta y su única acción posible implica moverse un cuadro a la izquierda. También en estos casos diremos que la máquina se detiene ya que la cinta no es extensible hacia la izquierda.

Otra característica de las máquinas de Turing es que poseen un alfabeto de entrada el cual está contenido en el alfabeto \(\Gamma\) y en el cual están los símbolos que se usarán para formar la configuración inicial de la cinta (excepto \(B\)). En general lo denotaremos con \(\Sigma\) al alfabeto de entrada y los símbolos de \(\Gamma - \Sigma\) son considerados auxiliares. También habrá un conjunto \(F\) contenido en el conjunto \(Q\) de los estados de la máquina, cuyos elementos serán llamados estados finales.

**El lenguaje \(L(M)\).** Diremos que una palabra \(\alpha = \alpha_1 \ldots \alpha_n \in \Sigma^\ast\) es aceptada por \(M\) por alcance de estado final si partiendo de

\[
\begin{array}{ccccccccc}
B & \alpha_1 & \cdots & \alpha_n & B & B & B & \cdots\\
\uparrow\\
q_0
\end{array}
\]

en algún momento de la computación \(M\) está en un estado de \(F\). Llamaremos \(L(M)\) al conjunto formado por todas las palabras que son aceptadas por alcance de estado final

**Ejercicio 2:** Para cada uno de los siguientes conjuntos, encuentre una máquina de Turing \(M\) (con alfabeto de entrada \(\Sigma = \{a, b\}\)) tal que \(L(M)\) sea dicho conjunto.

**(a)** \(\{\alpha \in \{a, b\}^\ast : a \text{ ocurre en } \alpha\}\)

**(b)** \(\{ab\}\)

**(c)** \(\{a^n b^n : n \ge 2\}\) (explicada en video en granlogico.com)

**(d)** \(\{\alpha \in \{a, b\}^\ast : |\alpha|_a \text{ es par y } |\alpha|_b \text{ es impar}\}\)

## Definición matemática de máquina de Turing

Una máquina de Turing es una 7-upla \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, F)\) donde

- \(Q\) es un conjunto finito cuyos elementos son llamados estados
- \(\Gamma\) es un alfabeto que contiene a \(\Sigma\)
- \(\Sigma\) es un alfabeto llamado el alfabeto de entrada
- \(B \in \Gamma - \Sigma\) es un símbolo de \(\Gamma\) llamado el blank symbol
- \(\delta : D_\delta \subseteq Q \times \Gamma \to Q \times \Gamma \times \{L, R, K\}\)
- \(q_0\) es un estado llamado el estado inicial de \(M\)
- \(F \subseteq Q\) es un conjunto de estados llamados finales

Nótese que la función \(\delta\) da la "personalidad" de la máquina. Describiremos esto informalmente y después cuando definamos la relación \(\vdash\) más abajo esta idea quedará precisada en forma matemática.

- \(\delta(p, \sigma) = (q, \gamma, L)\) significará que: si \(M\) está en estado \(p\) y su cabezal está escaneando una casilla distinta de la primera, en la cual está dibujado el símbolo \(\sigma\), entonces la máquina hará lo siguiente:

**(a)** borrará \(\sigma\) y escribirá \(\gamma\) en su lugar, luego

**(b)** se moverá un cuadro a la izquierda y luego

**(c)** pasará al estado \(q\)

- \(\delta(p, \sigma) = (q, \gamma, K)\) significará que: si \(M\) está en estado \(p\) y su cabezal está escaneando una casilla en la cual está dibujado el símbolo \(\sigma\), entonces la máquina hará lo siguiente:

**(a)** borrará \(\sigma\) y escribirá \(\gamma\) en su lugar, luego

**(b)** pasará al estado \(q\)

(es decir que el cabezal se queda quieto)

- \(\delta(p, \sigma) = (q, \gamma, R)\) significará que: si \(M\) está en estado \(p\) y su cabezal está escaneando una casilla en la cual está dibujado el símbolo \(\sigma\), entonces la máquina hará lo siguiente:

**(a)** borrará \(\sigma\) y escribirá \(\gamma\) en su lugar, luego

**(b)** se moverá un cuadro a la derecha y luego

**(c)** pasará al estado \(q\)

Los casos arriba descriptos son los únicos en los cuales la máquina \(M\) trabajará. O sea que si \((p, \sigma) \in (Q \times \Gamma) - D_\delta\) entonces \(M\) estando en estado \(p\) y con el cabezal leyendo el símbolo \(\sigma\) no puede hacer nada es decir solo permanecer quieta en el lugar de la cinta que esté. También si \(\delta(p, \sigma) = (q, \gamma, L)\), entonces cuando \(M\) esté en estado \(p\), con su cabezal escaneando la primera casilla y en la cual esté dibujado el símbolo \(\sigma\), \(M\) no podrá hacer nada, lo cual es razonable ya que la cinta no es extensible hacia la izquierda.

**Asunción Inocua:** Si bien en nuestra definición de máquina de Turing no hay ninguna restricción acerca de la naturaleza de los elementos de \(Q\), para continuar nuestro análisis asumiremos en lo que sigue de esta guía que \(Q\) es un alfabeto disjunto con \(\Gamma\). Esto nos permitirá dar definiciones matemáticas precisas que formalizarán el funcionamiento de las máquinas de Turing en el contexto de las funciones mixtas. Debería quedar claro que el hecho que solo trabajemos con máquinas en las cuales \(Q\) es un alfabeto disjunto con \(\Gamma\), no afectará la profundidad y generalidad de nuestros resultados y definiciones.

**Ejercicio 3:** V o F o I, justifique.

**(a)** Si \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, F)\) es una máquina de Turing, entonces \(\delta\) es una función \((Q \cup \Gamma \cup \{L, K, R\})\)-mixta

**(b)** Si \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, F)\) es una máquina de Turing, entonces \(D_\delta\) es un conjunto \((Q \cup \Gamma)\)-mixto

**Descripciones instantáneas.** Una descripción instantánea será una palabra de la forma \(\alpha q \beta\), donde \(\alpha, \beta \in \Gamma^\ast\), \([\beta]_{|\beta|} \ne B\) y \(q \in Q\). Nótese que la condición \([\beta]_{|\beta|} \ne B\) nos dice que \(\beta = \varepsilon\) o el último símbolo de \(\beta\) es distinto de \(B\). La descripción instantánea \(\alpha_1 \ldots \alpha_n q \beta_1 \ldots \beta_m\), con \(\alpha_1, \ldots, \alpha_n, \beta_1, \ldots, \beta_m \in \Gamma\), \(n, m \ge 0\) representará la siguiente situación

\[
\begin{array}{cccccccccccc}
\alpha_1 & \alpha_2 & \cdots & \alpha_n & \beta_1 & \beta_2 & \cdots & \beta_m & B & B & B & \cdots\\
&&&& \uparrow\\
&&&& q
\end{array}
\]

Nótese que aquí \(n\) y \(m\) pueden ser \(0\). Por ejemplo si \(n = 0\) tenemos que \(\alpha_1 \ldots \alpha_n q \beta_1 \ldots \beta_m = q \beta_1 \ldots \beta_m\) y representa la siguiente situación

\[
\begin{array}{ccccccccc}
\beta_1 & \beta_2 & \cdots & \beta_m & B & B & B & \cdots\\
\uparrow\\
q
\end{array}
\]

Si \(m = 0\) tenemos que \(\alpha_1 \ldots \alpha_n q \beta_1 \ldots \beta_m = \alpha_1 \ldots \alpha_n q\) y representa la siguiente situación

\[
\begin{array}{cccccccc}
\alpha_1 & \alpha_2 & \cdots & \alpha_n & B & B & \cdots & \cdots\\
&&&& \uparrow\\
&&&& q
\end{array}
\]

Si ambos \(n\) y \(m\) son \(0\) entonces tenemos que \(\alpha_1 \ldots \alpha_n q \beta_1 \ldots \beta_m = q\) y representa la siguiente situación

\[
\begin{array}{cccc}
B & B & B & \cdots\\
\uparrow\\
q
\end{array}
\]

La condición de que en una descripción instantánea \(\alpha q \beta\) deba suceder que \([\beta]_{|\beta|} \ne B\) es para que haya una correspondencia biunívoca entre descripciones instantáneas y situaciones de funcionamiento de la máquina. Dejamos al lector meditar sobre esto hasta convencerse de su veracidad.

Usaremos \(Des\) para denotar el conjunto de las descripciones instantáneas. Definamos la función \(St : Des \to Q\), de la siguiente manera

\[
St(d) = \text{único símbolo de } Q \text{ que ocurre en } d
\]

**Ejercicio 4:** V o F o I, justifique.

**(a)** Si \(d\) es una descripción instantánea, entonces \(Ti(d) = 3\text{-UPLA}\)

**(b)** Si \(d\) es una descripción instantánea, entonces \(St(d) = d \cap Q\)

**La relación \(\vdash\).** Dado \(\alpha \in (Q \cup \Gamma)^\ast\), definamos \(\lfloor \alpha \rfloor\) de la siguiente manera

\[
\begin{aligned}
\lfloor \varepsilon \rfloor &= \varepsilon\\
\lfloor \alpha\sigma \rfloor &= \alpha\sigma, \text{ si } \sigma \ne B\\
\lfloor \alpha B \rfloor &= \lfloor \alpha \rfloor
\end{aligned}
\]

Es decir \(\lfloor \alpha \rfloor\) es el resultado de remover de \(\alpha\) el tramo final más grande de la forma \(B^n\). Dada cualquier palabra \(\alpha\) definimos

\[
\curvearrowright\alpha =
\begin{cases}
[\alpha]_2 \ldots [\alpha]_{|\alpha|} & \text{si } |\alpha| \ge 2\\
\varepsilon & \text{si } |\alpha| \le 1
\end{cases}
\qquad
\alpha\curvearrowleft =
\begin{cases}
[\alpha]_1 \ldots [\alpha]_{|\alpha|-1} & \text{si } |\alpha| \ge 2\\
\varepsilon & \text{si } |\alpha| \le 1
\end{cases}
\]

**Observación:** Nótese que si \(\alpha p \beta\) es una descripción instantánea, entonces en la situación real que ella describe la cabeza lectora de la máquina está leyendo el símbolo \([\beta B]_1\) (o sea el 1er símbolo de \(\beta\) si \(\beta \ne \varepsilon\) y \(B\) en caso contrario). Esta forma cheta de describir qué símbolo lee la cabeza lectora nos será útil para definir a continuación la relación \(\vdash\).

Dadas \(d_1, d_2 \in Des\), escribiremos \(d_1 \vdash d_2\) cuando existan \(\sigma \in \Gamma\), \(\alpha, \beta \in \Gamma^\ast\) y \(p, q \in Q\) tales que se cumple alguno de los siguientes casos

Caso 1.

\[
\begin{aligned}
d_1 &= \alpha p \beta\\
\delta(p, [\beta B]_1) &= (q, \sigma, R)\\
d_2 &= \alpha\sigma q\curvearrowright\beta
\end{aligned}
\]

Caso 2.

\[
\begin{aligned}
d_1 &= \alpha p \beta\\
\delta(p, [\beta B]_1) &= (q, \sigma, L) \text{ y } \alpha \ne \varepsilon\\
d_2 &= \left\lfloor \alpha\curvearrowleft q[\alpha]_{|\alpha|}\sigma\curvearrowright\beta \right\rfloor
\end{aligned}
\]

Caso 3.

\[
\begin{aligned}
d_1 &= \alpha p \beta\\
\delta(p, [\beta B]_1) &= (q, \sigma, K)\\
d_2 &= \left\lfloor \alpha q\sigma\curvearrowright\beta \right\rfloor
\end{aligned}
\]

Escribiremos \(d \not\vdash d'\) para expresar que no se da \(d \vdash d'\). Para \(d, d' \in Des\) y \(n \ge 0\), escribiremos \(d\overset{n}{\vdash}d'\) si existen \(d_1, \ldots, d_{n+1} \in Des\) tales que

\[
\begin{aligned}
d &= d_1\\
d' &= d_{n+1}\\
d_i &\vdash d_{i+1}, \text{ para } i = 1, \ldots, n.
\end{aligned}
\]

Nótese que \(d\overset{0}{\vdash}d'\) sii \(d = d'\). Finalmente definamos

\[
d\overset{\ast}{\vdash}d' \text{ sii } (\exists n \in \omega)\ d\overset{n}{\vdash}d'.
\]

**Ejercicio 5:** V o F o I, justifique.

**(a)** \(d \vdash d\), para cada \(d \in Des\)

**(b)** Si \(\alpha p \beta \not\vdash d\) para toda descripción instantánea \(d\) entonces \((p, [\beta B]_1) \notin D_\delta\)

**(c)** Si \(\delta(p, a) = (p, a, L)\) entonces \(pa \not\vdash d\) para toda descripción instantánea \(d\)

**(d)** Dadas \(d, d' \in Des\), se tiene que si \(d \vdash d'\), entonces \(|d| \le |d'| + 1\)

**Ejercicio 6:** Sea \(\Sigma = \{@, \%\}\).

**(a)** Dar el gráfico de una máquina de Turing \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, F)\) tal que para cada \(\alpha \in \Sigma^\ast\) haya un \(q \in Q\) tal que

\[
\left\lfloor q_0BB\alpha \right\rfloor \overset{\ast}{\vdash} \left\lfloor qB\alpha \right\rfloor
\]

**(b)** Dar el gráfico de una máquina de Turing \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, F)\) tal que para cada \(\alpha \in \Sigma^\ast\) haya un \(q \in Q\) tal que

\[
\left\lfloor q_0B\alpha \right\rfloor \overset{\ast}{\vdash} \left\lfloor qBB\alpha \right\rfloor
\]

**Detención (definición matemática ahora).** Dada \(d \in Des\), diremos que \(M\) se detiene partiendo de \(d\) si existe \(d' \in Des\) tal que

- \(d\overset{\ast}{\vdash}d'\)
- \(d' \not\vdash d''\), para cada \(d'' \in Des\)

**Ejercicio 7:** Estudie los dos posibles casos de detención:

**(a)** estando el cabezal sobre el primer cuadro de la cinta

**(b)** estando el cabezal en un cuadro que no es el primero

**Ejercicio 8:** V o F o I, justifique.

**(a)** Sea \(d \in Des\). Entonces existe una infinitupla \((d_1, d_2, \ldots)\) tal que \(d \vdash d_1 \vdash d_2 \vdash d_3 \vdash d_4 \vdash \cdots\) si y solo si \(M\) no se detiene partiendo de \(d\)

**(b)** Supongamos que para cada \((p, \sigma) \in Q \times \Gamma\) la tercera coordenada de \(\delta(p, \sigma)\) es igual a \(L\). Entonces \(M\) se detiene partiendo de cada \(d \in Des\)

**El lenguaje \(L(M)\) (definición matemática ahora).** Diremos que una palabra \(\alpha \in \Sigma^\ast\) es aceptada por \(M\) por alcance de estado final cuando

\[
\left\lfloor q_0B\alpha \right\rfloor \overset{\ast}{\vdash} d, \text{ con } d \text{ tal que } St(d) \in F.
\]

El lenguaje aceptado por \(M\) por alcance de estado final se define de la siguiente manera

\[
L(M) = \{\alpha \in \Sigma^\ast : \alpha \text{ es aceptada por } M \text{ por alcance de estado final}\}.
\]

**Ejercicio 9:** Para cada uno de los siguientes conjuntos, encuentre una máquina de Turing \(M\) tal que \(L(M)\) sea dicho conjunto

**(a)** \(\{\alpha \in \{@, \%\}^\ast : |\alpha|_@ = 2|\alpha|_\%\}\)

**(b)** \(\{\alpha \in \{@, \%\}^\ast : \alpha = \alpha^R\}\) (palabras capicuas)

**Ejercicio 10:** Sea \(\Sigma = \{@, \%\}\). Dar el gráfico de una máquina de Turing \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, F)\) tal que para cada \(\alpha, \beta \in \Sigma^\ast\), con \(|\alpha| = |\beta|\), haya un \(q \in Q\) tal que

\[
\left\lfloor q_0B\alpha\beta \right\rfloor \overset{\ast}{\vdash} \left\lfloor B\alpha q\beta \right\rfloor
\quad\text{y}\quad
\left\lfloor B\alpha q\beta \right\rfloor \not\vdash d, \text{ para cada } d \in Des
\]

**Ejercicio 11:** Sea \(\Sigma = \{@, \%\}\). Dar el gráfico de una máquina de Turing \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, F)\) tal que

\[
L(M) = \{\beta\beta : \beta \in \{@, \%\}^+\}
\]

**Ejercicio 12:** Sea \(\Sigma = \{@, \%\}\).

**(a)** Dar el gráfico de una máquina de Turing \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, F)\) tal que

\[
L(M) = \{@^x (@\%)^y : x \ne y \text{ y } x, y \in \mathbf{N}\}
\]

**(b)** Para cada una de los siguientes palabras \(\alpha\) dar la sucesión de descripciones instantáneas que parte de \(\left\lfloor q_0B\alpha \right\rfloor\).

**(i)** \(\alpha = @@\%\)

**(ii)** \(\alpha = \%\%\%\)

**(iii)** \(\alpha = \varepsilon\)

**(iv)** \(\alpha = @@\%@\%\)

(Note que dicha sucesión puede ser finita o infinita)

**Ejercicio 13:** V o F o I, justifique.

**(a)** Si \(q_2\) es un estado final de la máquina \(M\), \(\delta(q_0, B) = (q_1, B, R)\) y \(\delta(q_1, a) = (q_2, b, R)\) entonces \(a \in L(M)\).

**(b)** Si \(q_2\) es un estado final de la máquina \(M\), \(\delta(q_0, B) = (q_1, B, R)\) y \(\delta(q_1, a) = (q_2, b, R)\) entonces \(b \in L(M)\).

**(c)** \(\alpha \notin L(M)\) si y solo si existe una infinitupla \((d_1, d_2, \ldots)\) tal que

**(i)** \(St(d_i) \notin F\), para cada \(i = 1, 2, \ldots\)

**(ii)** \(\left\lfloor q_0B\alpha \right\rfloor \vdash d_1 \vdash d_2 \vdash d_3 \vdash d_4 \vdash \cdots\)

## Funciones \(\Sigma\)-Turing computables

Para poder computar funciones mixtas con una máquina de Turing necesitaremos un símbolo para representar números sobre la cinta. Llamaremos a este símbolo unit y lo denotaremos con \(\mid\). Más formalmente una máquina de Turing con unit es una 8-upla \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, \mid, F)\) tal que \((Q, \Sigma, \Gamma, \delta, q_0, B, F)\) es una máquina de Turing y \(\mid\) es un símbolo distinguido perteneciente a \(\Gamma - (\{B\} \cup \Sigma)\).

Diremos que una función \(f : D_f \subseteq \omega^n \times \Sigma^{\ast m} \to \Sigma^\ast\) es \(\Sigma\)-Turing computable si existe una máquina de Turing con unit, \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, \mid, F)\) tal que:

**(1)** Si \((\overrightarrow{x}, \overrightarrow{\alpha}) \in D_f\), entonces hay un \(p \in Q\) tal que

\[
\left\lfloor q_0B\mid^{x_1}B \ldots B\mid^{x_n}B\alpha_1B \ldots B\alpha_m \right\rfloor
\overset{\ast}{\vdash}
\left\lfloor pBf(\overrightarrow{x}, \overrightarrow{\alpha}) \right\rfloor
\]

y \(\left\lfloor pBf(\overrightarrow{x}, \overrightarrow{\alpha}) \right\rfloor \not\vdash d\), para cada \(d \in Des\)

**(2)** Si \((\overrightarrow{x}, \overrightarrow{\alpha}) \in \omega^n \times \Sigma^{\ast m} - D_f\), entonces \(M\) no se detiene partiendo de

\[
\left\lfloor q_0B\mid^{x_1}B \ldots B\mid^{x_n}B\alpha_1B \ldots B\alpha_m \right\rfloor.
\]

En forma similar, una función \(f : D_f \subseteq \omega^n \times \Sigma^{\ast m} \to \omega\), es llamada \(\Sigma\)-Turing computable si existe una máquina de Turing con unit, \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, \mid, F)\), tal que:

**(1)** Si \((\overrightarrow{x}, \overrightarrow{\alpha}) \in D_f\), entonces hay un \(p \in Q\) tal que

\[
\left\lfloor q_0B\mid^{x_1}B \ldots B\mid^{x_n}B\alpha_1B \ldots B\alpha_m \right\rfloor
\overset{\ast}{\vdash}
\left\lfloor pB\mid^{f(\overrightarrow{x},\overrightarrow{\alpha})} \right\rfloor
\]

y \(\left\lfloor pB\mid^{f(\overrightarrow{x},\overrightarrow{\alpha})} \right\rfloor \not\vdash d\), para cada \(d \in Des\)

**(2)** Si \((\overrightarrow{x}, \overrightarrow{\alpha}) \in \omega^n \times \Sigma^{\ast m} - D_f\), entonces \(M\) no se detiene partiendo de

\[
\left\lfloor q_0B\mid^{x_1}B \ldots B\mid^{x_n}B\alpha_1B \ldots B\alpha_m \right\rfloor
\]

Cabe destacar que la condición

\[
\left\lfloor pBf(\overrightarrow{x}, \overrightarrow{\alpha}) \right\rfloor \not\vdash d, \text{ para cada } d \in Des
\]

es equivalente a que \((p, B)\) no esté en el dominio de \(\delta\) o que si lo esté y que la tercer coordenada de \(\delta(p, B)\) sea \(L\).

Cuando una máquina de Turing con unit \(M\) cumpla los ítems (1) y (2) de la definición anterior, diremos que \(M\) computa a la función \(f\) o que \(f\) es computada por \(M\). Por supuesto esta definición no tendría sentido como modelo matemático del concepto de función \(\Sigma\)-efectivamente computable si no sucediera que toda función \(\Sigma\)-Turing computable fuera \(\Sigma\)-efectivamente computable. Este hecho es intuitivamente claro y lo presentamos a continuación en forma de proposición. En algún sentido esto nos dice que el paradigma filosófico es más amplio (o igual) al paradigma de Turing. Para darle un toque de humor expresaremos esto diciendo que Leibniz vence a Turing.

**Proposición 1 (Leibniz vence a Turing).** Si \(f : D_f \subseteq \omega^n \times \Sigma^{\ast m} \to O\), con \(O \in \{\omega, \Sigma^\ast\}\), es computada por una máquina de Turing con unit \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, \mid, F)\), entonces \(f\) es \(\Sigma\)-efectivamente computable.

Proof. Haremos el caso \(O = \Sigma^\ast\). Sea \(\mathbb{P}\) el siguiente procedimiento efectivo.

- Conjunto de datos de entrada de \(\mathbb{P}\) igual a \(\omega^n \times \Sigma^{\ast m}\)
- Conjunto de datos de salida de \(\mathbb{P}\) contenido en \(O\)
- Funcionamiento: Hacer funcionar paso a paso la máquina \(M\) partiendo de la descripción instantánea \(\left\lfloor q_0B\mid^{x_1}B \ldots B\mid^{x_n}B\alpha_1B \ldots B\alpha_m \right\rfloor\). Si en alguna instancia \(M\) termina, dar como salida el resultado de remover de la descripción instantánea final los dos primeros símbolos.

Nótese que este procedimiento termina solo en aquellos elementos \((\overrightarrow{x}, \overrightarrow{\sigma}) \in \omega^n \times \Sigma^{\ast m}\) tales que la máquina \(M\) termina partiendo desde

\[
\left\lfloor q_0B\mid^{x_1}B \ldots B\mid^{x_n}B\alpha_1B \ldots B\alpha_m \right\rfloor
\]

por lo cual termina solo en los elementos de \(D_f\) ya que \(M\) computa a \(f\). Además es claro que en caso de terminación el procedimiento da como salida \(f(\overrightarrow{x}, \overrightarrow{\sigma})\). \(\blacksquare\)

Sin embargo el modelo Turingiano podría a priori no ser del todo correcto ya que podría pasar que haya una función que sea computada por un procedimiento efectivo pero que no exista una máquina de Turing que la compute. En otras palabras el modelo podría ser incompleto. La completitud de este modelo puede no ser clara al comienzo pero a medida que vayamos avanzando en nuestro estudio y conozcamos además los otros paradigmas y su relación, quedará claro que el modelo de Turing es acertado, es decir que también pasa que Turing vence a Leibniz.

**Ejercicio 14:** Sea \(\Sigma = \{a, b\}\). Para cada una de las siguientes funciones \(\Sigma\)-mixtas dar una máquina de Turing \((Q, \Gamma, \Sigma, \delta, q_0, B, \mid, \emptyset)\) que la compute

**(a)**

\[
\begin{aligned}
Suc &: \omega \to \omega\\
n &\to n + 1
\end{aligned}
\]

**(b)**

\[
\begin{aligned}
Pred &: \mathbf{N} \to \omega\\
n &\to n - 1
\end{aligned}
\]

**(c)**

\[
\begin{aligned}
p_2^{1,1} &: \omega \times \Sigma^\ast \to \Sigma^\ast\\
(x, \alpha) &\to \alpha
\end{aligned}
\]

(explicada en video en granlogico.com)

**(d)**

\[
\begin{aligned}
C_2^{1,1} &: \omega \times \Sigma^\ast \to \omega\\
(x, \alpha) &\to 2
\end{aligned}
\]

**(e)** \(\lambda xy[x + y]\)

**(f)** \(\lambda xy[x.y]\)

**(g)**

\[
\begin{aligned}
Q &: \omega \times \mathbf{N} \to \omega\\
(x, y) &\to \text{cociente de la división de } x \text{ por } y
\end{aligned}
\]

**(h)**

\[
\begin{aligned}
R &: \omega \times \mathbf{N} \to \omega\\
(x, y) &\to \text{resto de la división de } x \text{ por } y
\end{aligned}
\]

**Ejercicio 15:** Sea \(\Sigma = \{@, \%\}\). Sea

\[
\begin{aligned}
f : \{(x, \alpha) \in \omega \times \Sigma^\ast : |\alpha| \text{ es impar}\} &\to \omega\\
(x, \alpha) &\to x + |\alpha|
\end{aligned}
\]

**(a)** De el diagrama de una máquina de Turing \(M\) la cual compute a \(f\).

**(b)** Para cada una de los siguientes pares \((x, \alpha)\) dar la sucesión de descripciones instantáneas que parte de \(\left\lfloor q_0B\mid^xB\alpha \right\rfloor\).

**(i)** \((x, \alpha) = (0, \varepsilon)\)

**(ii)** \((x, \alpha) = (100, @)\)

**(iii)** \((x, \alpha) = (3, @@\%)\)

**(iv)** \((x, \alpha) = (100, @\%)\)

(Note que dicha sucesión para ciertos casos debe ser infinita)

**Ejercicio 16:** Sea \(\Sigma = \{@, \%\}\). Sea

\[
\begin{aligned}
R : \{\beta\beta : \beta \in \{@, \%\}^+\} &\to \Sigma^\ast\\
\alpha &\to \text{único } \beta \text{ tal que } \alpha = \beta\beta
\end{aligned}
\]

**(a)** De el diagrama de una máquina de Turing \(M\) la cual compute a \(R\).

**(b)** Para cada una de las siguientes palabras \(\alpha\) dar la sucesión de descripciones instantáneas que parte de \(\left\lfloor q_0B\alpha \right\rfloor\).

**(i)** \(\alpha = \varepsilon\)

**(ii)** \(\alpha = @@\)

**(iii)** \(\alpha = @@\%\%\)

**(iv)** \(\alpha = @\%@\%\%\)

**(v)** \(\alpha = @@\%@\)

(Note que dicha sucesión para ciertos casos debe ser infinita)

**Ejercicio 17:** Sea \(\Sigma = \{@, \%\}\) y sea

\[
\begin{aligned}
f : \{(\alpha, \beta) \in \Sigma^\ast \times \Sigma^\ast : \alpha = \beta\} &\to \Sigma^\ast\\
(\alpha, \beta) &\to \alpha
\end{aligned}
\]

**(a)** De el diagrama de una máquina de Turing \(M\) la cual compute a \(f\).

**(b)** Para cada una de los siguientes pares \((\alpha, \beta)\) dar la sucesión de descripciones instantáneas que parte de \(\left\lfloor q_0B\alpha B\beta \right\rfloor\).

**(i)** \((\alpha, \beta) = (\%@, \%)\)

**(ii)** \((\alpha, \beta) = (@\%, @\%)\)

**(iii)** \((\alpha, \beta) = (\varepsilon, @@)\)

(Note que dicha sucesión para ciertos casos debe ser infinita)

**Ejercicio 18:** V o F o I, justifique.

**(a)** Sea \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, \mid, F)\) una máquina de Turing con unit y supongamos que \(M\) computa a \(f\). Entonces \(D_f = \{d \in Des : M \text{ se detiene partiendo desde } d\}\)

**(b)** Si \(f\) y \(g\) son dos funciones y \(M\) es es una máquina de Turing que computa a \(f\) y a \(g\) entonces \(f = g\).

**(c)** Sea \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, \mid, F)\) una máquina de Turing con unit y supongamos que \(M\) computa a \(f\) y que \(f\) es \(\Sigma\)-total. Entonces \(M\) se detiene partiendo desde \(d\), cualesquiera sea \(d \in Des\)

**Ejercicio 19:** Como se vio anteriormente el modelo de Turing del concepto de función \(\Sigma\)-efectivamente computable es el concepto matemático de función \(\Sigma\)-Turing computable.

**(a)** Cuál sería el modelo de Turing del concepto de conjunto \(\Sigma\)-efectivamente computable? Más concretamente ud debe continuar esta definición: " Un conjunto \(S \subseteq \omega^n \times \Sigma^{\ast m}\) es \(\Sigma\)-Turing computable cuando ....

**(b)** Cuál sería el modelo de Turing del concepto de conjunto \(\Sigma\)-efectivamente enumerable? Más concretamente ud debe continuar esta definición: " Un conjunto \(S \subseteq \omega^n \times \Sigma^{\ast m}\) es \(\Sigma\)-Turing enumerable cuando ....

## Ejercicios de examen

**(1)** Sea \(\Sigma = \{@, \%\}\).

**(a)** Dar el gráfico de una máquina de Turing \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, F)\) tal que

\[
L(M) = \{\alpha \in \Sigma^\ast : \alpha = \alpha^R\}\quad \text{(palabras capicuas)}
\]

**(b)** Para cada una de los siguientes palabras \(\alpha\) dar la sucesión de descripciones instantáneas que parte de \(\left\lfloor q_0B\alpha \right\rfloor\).

**(i)** \(\alpha = @@\%\)

**(ii)** \(\alpha = \%@\%\)

**(iii)** \(\alpha = \varepsilon\)

**(iv)** \(\alpha = \%\%\)

(Note que dicha sucesión puede ser finita o infinita)

**(2)** Sea \(\Sigma = \{@, \%\}\).

**(a)** Dar el gráfico de una máquina de Turing \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, F)\) tal que

\[
L(M) = \{@^x\%^y : x < y \text{ y } x, y \in \omega\}
\]

**(b)** Para cada una de los siguientes palabras \(\alpha\) dar la sucesión de descripciones instantáneas que parte de \(\left\lfloor q_0B\alpha \right\rfloor\).

**(i)** \(\alpha = @@\%\)

**(ii)** \(\alpha = \%@\%\)

**(iii)** \(\alpha = @\%\%\)

**(iv)** \(\alpha = \%\)

(Note que dicha sucesión puede ser finita o infinita)

**(3)** Sea \(\Sigma = \{@, \%\}\). Hacer

**(a)** Dar el gráfico de una máquina de Turing \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, F)\) tal que

\[
L(M) = \{@^{2x}\%^x : x \in \mathbf{N}\}
\]

**(b)** Para cada una de los siguientes palabras \(\alpha\) dar la sucesión de descripciones instantáneas que parte de \(\left\lfloor q_0B\alpha \right\rfloor\).

**(i)** \(\alpha = @\%\)

**(ii)** \(\alpha = \%\%\%\)

**(iii)** \(\alpha = \varepsilon\)

**(iv)** \(\alpha = @@@@\%\%\)

(Note que dicha sucesión puede ser finita o infinita)

**(4)** Sea \(\Sigma = \{@, \%\}\). Hacer

**(a)** Dar el gráfico de una máquina de Turing \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, F)\) tal que

\[
L(M) = \{@^x\%^{2x} : x \in \mathbf{N}\}
\]

**(b)** Para cada una de los siguientes palabras \(\alpha\) dar la sucesión de descripciones instantáneas que parte de \(\left\lfloor q_0B\alpha \right\rfloor\).

**(i)** \(\alpha = @\%\)

**(ii)** \(\alpha = \%\%\%\)

**(iii)** \(\alpha = \varepsilon\)

**(iv)** \(\alpha = @@\%\%\%\%\)

(Note que dicha sucesión puede ser finita o infinita)

**(5)** Sea \(\Sigma = \{@, \%\}\). Hacer

**(a)** Dar el gráfico de una máquina de Turing \(M = (Q, \Sigma, \Gamma, \delta, q_0, B, F)\) tal que

\[
L(M) = \{@^x(@\%)^y : x \ne y \text{ y } x, y \in \mathbf{N}\}
\]

**(b)** Para cada una de los siguientes palabras \(\alpha\) dar la sucesión de descripciones instantáneas que parte de \(\left\lfloor q_0B\alpha \right\rfloor\).

**(i)** \(\alpha = @@\%\)

**(ii)** \(\alpha = \%\%\%\)

**(iii)** \(\alpha = \varepsilon\)

**(iv)** \(\alpha = @@\%@\%\)

(Note que dicha sucesión puede ser finita o infinita)

**(6)** Sea \(\Sigma = \{@, \%\}\) y sea

\[
\begin{aligned}
f : \{(\alpha, \beta) \in \Sigma^\ast \times \Sigma^\ast : \alpha \ne \beta\} &\to \Sigma^\ast\\
(\alpha, \beta) &\to \alpha
\end{aligned}
\]

**(a)** De el diagrama de una máquina de Turing \(M\) la cual compute a \(f\).

**(b)** Para cada una de los siguientes pares \((\alpha, \beta)\) dar la sucesión de descripciones instantáneas que parte de \(\left\lfloor q_0B\alpha B\beta \right\rfloor\).

**(i)** \((\alpha, \beta) = (\%@, \%)\)

**(ii)** \((\alpha, \beta) = (@\%, @\%)\)

**(iii)** \((\alpha, \beta) = (\varepsilon, @@)\)

(Note que dicha sucesión para ciertos casos debe ser infinita)

**(7)** Sea \(\Sigma = \{@, \%\}\) y sea

\[
\begin{aligned}
f : \{(x, \alpha) \in \omega \times \Sigma^\ast : |\alpha| \ne x\} &\to \Sigma^\ast\\
(x, \alpha) &\to \alpha
\end{aligned}
\]

**(a)** De el diagrama de una máquina de Turing \(M\) la cual compute a \(f\).

**(b)** Para cada una de los siguientes pares \((x, \alpha)\) dar la sucesión de descripciones instantáneas que parte de \(\left\lfloor q_0B\mid^xB\alpha \right\rfloor\).

**(i)** \((x, \alpha) = (2, \%)\)

**(ii)** \((x, \alpha) = (2, @\%)\)

**(iii)** \((x, \alpha) = (0, \varepsilon)\)

(Note que dicha sucesión para ciertos casos debe ser infinita)

**(8)** Sea \(\Sigma = \{@, \%\}\) y sea

\[
\begin{aligned}
f : \{(\alpha, \beta) \in \Sigma^+ \times \Sigma^\ast : |\alpha| < |\beta|\} &\to \Sigma^\ast\\
(\alpha, \beta) &\to [\beta]_{|\alpha|}
\end{aligned}
\]

**(a)** De el diagrama de una máquina de Turing \(M\) la cual compute a \(f\).

**(b)** Para cada una de los siguientes pares \((\alpha, \beta)\) dar la sucesión de descripciones instantáneas que parte de \(\left\lfloor q_0B\alpha B\beta \right\rfloor\).

**(i)** \((\alpha, \beta) = (\%, \%)\)

**(ii)** \((\alpha, \beta) = (@, \%@\%)\)

**(iii)** \((\alpha, \beta) = (\varepsilon, @@)\)

(Note que dicha sucesión para ciertos casos debe ser infinita)

**(9)** Sea \(\Sigma = \{@, \%\}\) y sea \(\le\) el orden total sobre \(\Sigma\) dado por \(@ < \%\). De el diagrama de una máquina de Turing \(M\) la cual compute a \(\#^\le\).

**(10)** Sea \(\Sigma = \{@, \%\}\) y sea \(\le\) el orden total sobre \(\Sigma\) dado por \(@ < \%\). De el diagrama de una máquina de Turing \(M\) la cual compute a \(\ast^\le\).

**(11)** Sea \(\Sigma = \{@, \%\}\).

**(a)** De el diagrama de una máquina de Turing \(M\) la cual compute a \(\lambda\alpha\beta[\alpha = \beta]\).

**(b)** Para cada una de los siguientes pares \((\alpha, \beta)\) dar la sucesión de descripciones instantáneas que parte de \(\left\lfloor q_0B\alpha B\beta \right\rfloor\).

**(i)** \((\alpha, \beta) = (\%, \%)\)

**(ii)** \((\alpha, \beta) = (@\%, @)\)

**(iii)** \((\alpha, \beta) = (\varepsilon, @@)\)

**(12)** Sea \(\Sigma = \{@, \%\}\). De el diagrama de una máquina de Turing \(M\) la cual compute a \(\lambda\alpha\beta[\beta\alpha]\).

**(13)** Sea \(\Sigma = \{@, \%\}\) y sea \(\le\) el orden total sobre \(\Sigma\) dado por \(@ < \%\). Sea \(<\) el orden "menor" asociado al orden total de \(\Sigma^\ast\) inducido por \(\le\). De el diagrama de una máquina de Turing \(M\) la cual compute a \(\lambda\alpha\beta[\alpha < \beta]\). (Hint: use la caracterización lexicográfica de \(<\) dada en la Guía 2).
