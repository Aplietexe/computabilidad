# GUÍA 1 DE LENGUAJES: NOTACIÓN Y CONCEPTOS BÁSICOS

Usaremos $\mathbf{R}$ para denotar el conjunto de los números reales, $\mathbf{Z}$ para denotar el conjunto de los números enteros, $\mathbf{N}$ para denotar el conjunto de los números naturales y $\omega$ para denotar al conjunto $\mathbf{N} \cup \{0\}$.

Dado un conjunto $A$, usaremos $\mathcal{P}(A)$ para denotar el conjunto formado por todos los subconjuntos de $A$, es decir:

$$
\mathcal{P}(A) = \{S : S \subseteq A\}
$$

Si $A$ es un conjunto finito, entonces $|A|$ denotará la cantidad de elementos de $A$.

Para $x, y \in \omega$, definamos

$$
x \mathbin{\dot{-}} y =
\begin{cases}
x-y & \text{si } x \ge y,\\
0 & \text{caso contrario}
\end{cases}
$$

Dados $x, y \in \omega$ diremos que $x$ divide a $y$ cuando haya un $z \in \omega$ tal que $y = z.x$. Notar que 0 divide a 0, 3 divide a 0 y 0 no divide a 23. Escribiremos $x \mid y$ para expresar que $x$ divide a $y$. Si bien no hay una definición natural en matemática de cuánto vale $0^0$ (0 elevado a la 0), por convención para nosotros $0^0 = 1$

## Producto cartesiano

Dados conjuntos $A_1, \ldots, A_n$, con $n \ge 2$, usaremos $A_1 \times \ldots \times A_n$ para denotar el producto Cartesiano de $A_1, \ldots, A_n$, es decir el conjunto formado por todas las $n$-uplas $(a_1, \ldots, a_n)$ tales que $a_1 \in A_1, \ldots, a_n \in A_n$. Si $A_1 = \ldots = A_n = A$, con $n \ge 2$, entonces escribiremos $A^n$ en lugar de $A_1 \times \ldots \times A_n$. Para $n = 1$, definimos $A^n = A$, es decir $A^1 = A$. Usaremos $\diamond$ para denotar la única 0-upla. Definimos entonces $A^0 = \{\diamond\}$. Si $A$ es un conjunto denotaremos con $A^{\mathbf{N}}$ al conjunto formado por todas las infinituplas $(a_1, a_2, \ldots)$ tales que $a_i \in A$ para cada $i \in \mathbf{N}$. Por ejemplo

$$
(1, 2, 3, 4, \ldots) \in \omega^{\mathbf{N}}
$$

donde $(1, 2, 3, 4, \ldots)$ es una forma intuitiva de denotar la infinitupla cuyo $i$-ésimo elemento es el número natural $i$.

Si $(A_1, A_2, \ldots)$ es una infinitupla de conjuntos, entonces usaremos $\bigcup_{i=1}^{\infty} A_i$ o $\bigcup_{i \ge 1} A_i$ para denotar al conjunto

$$
\{a : a \in A_i, \text{ para algún } i \in \mathbf{N}\}
$$

## Conjuntos

Supondremos que el lector sabe las nociones básicas sobre conjuntos, aunque resaltaremos algunas de las más importantes para que el lector las repase.

La propiedad de extensionalidad nos dice que, dados conjuntos $A, B$, se tiene que $A = B$ si y solo si para cada objeto $x$ se da que

$$
x \in A \text{ si y solo si } x \in B
$$

Esta propiedad es importante metodológicamente ya que a la hora de probar que dos conjuntos $A, B$ son iguales, extensionalidad nos asegura que basta con ver que se dan las dos inclusiones $A \subseteq B$ y $B \subseteq A$.

Otro tema importante es manejar correctamente la notación cuando definimos un conjunto usando llaves y mediante propiedades que caracterizan la pertenencia al mismo. Algunos ejercicios para entrenar esta notación:

**Ejercicio 1:** Entender en forma precisa que conjunto se está denotando en cada uno de los siguientes casos

**(a)** $\{x \in \mathbf{N} : x = 1 \text{ o } x \ge 5\}$

**(b)** $\{x : x \in \mathbf{R} \text{ y } x^2 \ge 100\}$

**(c)** $\{x : x = 100\}$

**(d)** $\{x^2 + 1 : x \in \omega\}$

**(e)** $\{x + y + z : x, y, z \in \{1, 2\}\}$

**Ejercicio 2:** V o F o I, justifique.

**(a)** $\{x.y : x, y \in \omega\} = \omega$

**(b)** $|\{x.y : x, y \in \omega \text{ y } 1 \le x, y \le 5\}| = 25$

**(c)** Dados $A, B \subseteq \omega$, se tiene que $\{a \in A \text{ y } b \in B : a + b = 1000\} \subseteq A \times B$

**(d)** $\{a \in \mathbf{N}, a \ge 3\} \subseteq \omega$

**(e)** $\{x + 1 : x \in \{1, 2, 3\}\} = \{1, 2, 3, 4\}$

## Alfabetos

Un alfabeto es un conjunto finito de símbolos. Nótese que $\emptyset$ es un alfabeto. Si $\Sigma$ es un alfabeto, entonces $\Sigma^\ast$ denotará el conjunto de todas las palabras formadas con símbolos de $\Sigma$. Las palabras de longitud 1 son exactamente los elementos de $\Sigma$, en particular esto nos dice que $\Sigma \subseteq \Sigma^\ast$. La única palabra de longitud 0 es denotada con $\varepsilon$. Ya que en $\varepsilon$ no ocurren símbolos, tenemos que $\varepsilon \in \Sigma^\ast$, para cualquier alfabeto, más aún nótese que $\emptyset^\ast = \{\varepsilon\}$. Usaremos $|\alpha|$ para denotar la longitud de la palabra $\alpha$. Si $\alpha \in \Sigma^\ast$ y $\sigma \in \Sigma$, usaremos $|\alpha|_\sigma$ para denotar la cantidad de ocurrencias del símbolo $\sigma$ en $\alpha$. Nótese que funciones, $n$-uplas y palabras son objetos de distinto tipo, por lo cual $\emptyset$, $\diamond$ y $\varepsilon$ son tres objetos matemáticos diferentes.

Si $\alpha_1, \ldots, \alpha_n \in \Sigma^\ast$, con $n \ge 0$, usaremos $\alpha_1 \ldots \alpha_n$ para denotar la concatenación de las palabras $\alpha_1, \ldots, \alpha_n$ (nótese que cuando $n = 0$, resulta que $\alpha_1 \ldots \alpha_n = \varepsilon$). Si $\alpha_1 = \ldots = \alpha_n = \alpha$, entonces escribiremos $\alpha^n$ en lugar de $\alpha_1 \ldots \alpha_n$. O sea que $\alpha^0 = \varepsilon$.

Un lenguaje sobre $\Sigma$ será un subconjunto de $\Sigma^\ast$. Si $L$ es un lenguaje sobre $\Sigma$, entonces denotaremos con $L^+$ al conjunto formado por todas las concatenaciones de sucesiones finitas no nulas de elementos de $L$. Es decir:

$$
L^+ = \{\alpha_1 \ldots \alpha_n : \alpha_1, \ldots, \alpha_n \in L \text{ y } n \ge 1\}
$$

Definamos también

$$
L^\ast = L^+ \cup \{\varepsilon\}
$$

Nótese que en particular obtenemos que $\Sigma^+ = \Sigma^\ast - \{\varepsilon\}$.

Diremos que $\alpha$ es subpalabra (propia) de $\beta$ cuando ($\alpha \notin \{\varepsilon, \beta\}$ y) existan palabras $\delta, \gamma$ tales que $\beta = \delta\alpha\gamma$. Diremos que $\beta$ es un tramo inicial (propio) de $\alpha$ si hay una palabra $\gamma$ tal que $\alpha = \beta\gamma$ (y $\beta \notin \{\varepsilon, \alpha\}$). En forma similar se define tramo final (propio).

Dados $i \in \omega$ y $\alpha \in \Sigma^\ast$ definamos

$$
[\alpha]_i =
\begin{cases}
i\text{-ésimo elemento de } \alpha & \text{si } 1 \le i \le |\alpha|,\\
\varepsilon & \text{caso contrario}
\end{cases}
$$

Dada $\gamma \in \Sigma^\ast$, definamos

$$
\gamma^R =
\begin{cases}
[\gamma]_{|\gamma|}[\gamma]_{|\gamma|-1}\ldots[\gamma]_1 & \text{si } |\gamma| \ge 1,\\
\varepsilon & \text{caso contrario}
\end{cases}
$$

La palabra $\gamma^R$ es llamada la recíproca de $\gamma$. Dada $\alpha \in \Sigma^\ast$, definamos

$$
\begin{aligned}
\curvearrowright\alpha &=
\begin{cases}
[\alpha]_2 \ldots [\alpha]_{|\alpha|} & \text{si } |\alpha| \ge 2,\\
\varepsilon & \text{si } |\alpha| \le 1,
\end{cases}
&
\alpha\curvearrowleft &=
\begin{cases}
[\alpha]_1 \ldots [\alpha]_{|\alpha|-1} & \text{si } |\alpha| \ge 2,\\
\varepsilon & \text{si } |\alpha| \le 1.
\end{cases}
\end{aligned}
$$

**Ocurrencias.** Dadas palabras $\alpha, \beta \in \Sigma^\ast$, con $|\alpha|, |\beta| \ge 1$, y un natural $i \in \{1, \ldots, |\beta|\}$, se dice que $\alpha$ ocurre a partir de $i$ en $\beta$ cuando se dé que existan palabras $\delta, \gamma$ tales que $\beta = \delta\alpha\gamma$ y $|\delta| = i - 1$. Intuitivamente hablando $\alpha$ ocurre a partir de $i$ en $\beta$ cuando se dé que si comenzamos a leer desde el lugar $i$-ésimo de $\beta$ en adelante, leeremos la palabra $\alpha$ completa y luego posiblemente seguirán otros símbolos.

Nótese que una palabra $\alpha$ puede ocurrir en $\beta$, a partir de $i$, y también a partir de $j$, con $i \ne j$. En virtud de esto, hablaremos de las distintas ocurrencias de $\alpha$ en $\beta$. Por ejemplo hay dos ocurrencias de la palabra `aba` en la palabra

```text
cccccccabaccccabaccccc
```

y también hay dos ocurrencias de la palabra `aba` en la palabra

```text
cccccccababacccccccccc
```

En el primer caso diremos que dichas ocurrencias de `aba` son disjuntas ya que ocupan espacios disjuntos dentro de la palabra. En cambio en el segundo caso puede apreciarse que las dos ocurrencias se superponen en una posición. A veces diremos que una ocurrencia está contenida o sucede dentro de otra. Por ejemplo la segunda ocurrencia de `ab` en `babbbfabcccfabccc` está contenida en la primera ocurrencia de `fabc` en `babbbfabcccfabccc`.

No definiremos en forma matemática precisa el concepto de ocurrencia pero el lector no tendrá problemas en comprenderlo y manejarlo en forma correcta.

**Reemplazos de ocurrencias.** También haremos reemplazos de ocurrencias por palabras. Por ejemplo el resultado de reemplazar la primera ocurrencia de `abb` en `ccabbgfgabbgg` por `oolala` es la palabra `ccoolalagfgabbgg`. Cuando todas las ocurrencias de una palabra $\alpha$ en una palabra $\beta$ sean disjuntas entre sí, podemos hablar del resultado de reemplazar simultáneamente cada ocurrencia de $\alpha$ en $\beta$ por $\gamma$. Por ejemplo si tenemos

```text
α = yet
β = ghsyetcjjjyetbcpyeteabc
γ = %%
```

entonces `ghs%%cjjj%%bcp%%eabc` es el resultado de reemplazar simultáneamente cada ocurrencia de $\alpha$ en $\beta$ por $\gamma$. Es importante notar que los reemplazos se hacen simultáneamente y no secuencialmente (i.e. reemplazando la primera ocurrencia de $\alpha$ por $\gamma$ y luego al resultado reemplazarle la primera ocurrencia de $\alpha$ por $\gamma$ y así sucesivamente). Obviamente el reemplazo secuencial puede dar un resultado distinto al simultáneo (que es el que usaremos en general) e incluso puede suceder que en el reemplazo secuencial el proceso se pueda iterar indefinidamente. Dejamos al lector armar ejemplos de estas situaciones.

También se pueden hacer reemplazos simultáneos de distintas palabras en una palabra dada. Supongamos tenemos palabras $\alpha_1, \ldots, \alpha_n$ (con $\alpha_i \ne \alpha_j$, para $i \ne j$) las cuales tienen la propiedad de que las distintas ocurrencias de ellas en la palabra $\beta$ son siempre disjuntas de a pares, y tenemos además palabras $\gamma_1, \ldots, \gamma_n$. Entonces hablaremos del resultado de reemplazar simultáneamente:

- cada ocurrencia de $\alpha_1$ en $\beta$, por $\gamma_1$
- cada ocurrencia de $\alpha_2$ en $\beta$, por $\gamma_2$
- $\vdots$
- cada ocurrencia de $\alpha_n$ en $\beta$, por $\gamma_n$

Por ejemplo si tomamos

$$
\begin{aligned}
\alpha_1 &= \text{gh}\\
\alpha_2 &= \text{yet}\\
\alpha_3 &= \text{ana}\\
\beta &= \text{ghbbbyetbbgh\%\%ana\#\#ana!!!ana}\\
\gamma_1 &= \text{AA}\\
\gamma_2 &= \text{BBBB}\\
\gamma_3 &= \text{CCC}
\end{aligned}
$$

entonces `AAbbbBBBBbbAA%%CCC##CCC!!!CCC` es el resultado de reemplazar simultáneamente:

- cada ocurrencia de $\alpha_1$ en $\beta$, por $\gamma_1$
- cada ocurrencia de $\alpha_2$ en $\beta$, por $\gamma_2$
- cada ocurrencia de $\alpha_3$ en $\beta$, por $\gamma_3$

## Matemática orientada a objetos

Nuestro estilo o enfoque matemático pondrá énfasis en los objetos, es decir haremos matemática prestando atención a los distintos objetos matemáticos involucrados, los cuales siempre serán definidos en forma precisa en términos de objetos más primitivos. Hay ciertos objetos matemáticos los cuales no definiremos y supondremos que el lector tiene una idea clara y precisa de los mismos. Por ejemplo un tipo de objeto matemático, quizás el más famoso, son los números. No diremos qué es un número pero supondremos que el lector tiene una intuición clara acerca de este tipo de objetos y de sus propiedades básicas. Otro tipo de objeto que no definiremos y que será clave para nuestro enfoque son los conjuntos. Nuevamente, no diremos qué es un conjunto pero supondremos que el lector tiene una intuición clara acerca de estos objetos y sus propiedades básicas. Es importante que en nuestro enfoque, números y conjuntos son objetos de distinta naturaleza por lo cual nunca un número es un conjunto ni un conjunto es un número. En particular esto nos dice que el número 0 y el conjunto $\emptyset$ son objetos distintos. Otro tipo de objeto matemático muy importante para la matemática discreta son los símbolos. No discutiremos qué es un símbolo sino que aceptaremos este concepto en forma primitiva. También constituyen un tipo de objeto matemático las palabras, las cuales intuitivamente hablando son yuxtaposiciones de símbolos. Otro tipo de objeto matemático muy importante son los pares ordenados o 2-uplas, es decir los objetos de la forma $(a, b)$, donde $a$ y $b$ son objetos matemáticos cualesquiera. También son objetos matemáticos y de distinta naturaleza las 3-uplas, las 4-uplas y en general las $n$-uplas para $n$ un número natural mayor o igual a 2. Cabe destacar que en nuestro enfoque no habrá 1-uplas. Sin embargo, si bien hay una sola 0-upla, ella constituye un tipo de objeto matemático distinto a los antes mencionados. El último tipo de objeto matemático que consideraremos es aquel de las infinituplas.

Tenemos entonces dividido nuestro universo matemático en las distintas categorías o tipos de objetos:

```text
NÚMERO
CONJUNTO
PALABRA
0-UPLA
2-UPLA
3-UPLA
...
INFINITUPLA
```

(Notar que los símbolos quedan contenidos en la categoría de las palabras). Es importante entender que las anteriores categorías o tipos de objetos son disjuntas entre sí, es decir nunca un número será una palabra o una palabra será una 3-upla etc. Esto nos permite definir una función $Ti$ la cual a un objeto matemático le asigna su tipo de objeto matemático según la lista anterior. Por ejemplo:

$$
\begin{aligned}
Ti(\pi) &= \mathrm{NÚMERO}\\
Ti(\mathbf{N}) &= \mathrm{CONJUNTO}\\
Ti(\mathcal{P}(\mathbf{N})) &= \mathrm{CONJUNTO}\\
Ti((1, 2, 3)) &= \mathrm{3\text{-}UPLA}\\
Ti(\emptyset) &= \mathrm{CONJUNTO}\\
Ti(\varepsilon) &= \mathrm{PALABRA}\\
Ti(\diamond) &= \mathrm{0\text{-}UPLA}\\
Ti(\alpha) &= \mathrm{PALABRA}, \text{ si } \alpha \text{ es un símbolo}
\end{aligned}
$$

## Numerales

Llamaremos numerales a los siguientes símbolos

```text
0 1 2 3 4 5 6 7 8 9
```

Usaremos $Num$ para denotar el conjunto de numerales. Nótese que $Num \cap \omega = \emptyset$. Es decir, no debemos confundir los símbolos que usualmente denotan los primeros diez elementos de $\omega$ con los números que ellos denotan. De hecho en china o japón los primeros diez elementos de $\omega$ se denotan con otros símbolos. Similarmente las palabras pertenecientes a $Num^\ast$ denotan (notación decimal) a los números de $\omega$ pero debemos tener en cuenta que $Num^\ast \cap \omega = \emptyset$. Cuando tratamos con palabras de $Num^\ast$, debemos ser cuidadosos ya que muchas veces en nuestro discurso matemático (es decir las guías, el apunte, lo que escriben los profesores en el pizarrón, etc) representamos dos objetos diferentes de la misma forma. Por ejemplo 45 puede estar denotando al número entero cuarenta y cinco o también 45 puede estar denotando la palabra de longitud 2 cuyo primer símbolo es el numeral 4 y cuyo segundo símbolo es el numeral 5, es decir a ella misma. Por dar otro ejemplo, el símbolo 1 en nuestro discurso algunas veces se denotará a sí mismo y otras veces denotará al número uno. Resumiendo, hay muchas palabras que algunas veces en nuestro discurso se representan a sí mismas y otras veces representan a otro objeto matemático y es tarea del lector saber qué corresponde en cada caso.

Los numerales bold son los numerales en modo negrita, es decir

**0 1 2 3 4 5 6 7 8 9**

Cabe aclarar que estos numerales bold son distintos a los numerales antes introducidos. También usaremos los numerales itálicos

*0 1 2 3 4 5 6 7 8 9*

que obviamente son símbolos distintos a los numerales clásicos y a los bold.

## Escarabajo y Mariposa

Para hacer divertido nuestro desarrollo crearemos dos personajes que con su personalidad nos dejarán analizar las distintas maneras de hacer matemática. El escarabajo es netamente sintáctico y mecánico, no le gusta pensar los conceptos matemáticos imaginando los objetos involucrados en los mismos, simplemente quiere avanzar (sin mucho pensamiento) aplicando reglas sintácticas que le permitan obtener nuevas ecuaciones o expresiones matemáticas. Él vive en el mundo plano de las palabras y ahí se siente apasionado por sus hábiles movimientos mecánicos. El escarabajo es en algún sentido una maravilla de la destreza mecánico-simbólica. La mariposa es todo lo contrario, le interesa pensar en los objetos matemáticos como si fueran reales dentro de su imaginación fantástica y con su habilidad de volar contempla el universo matemático desde un punto de vista conceptual e independiente de la manipulación sintáctica. Reconoce como objetos reales de su universo matemático no solo a los objetos finitarios (palabras, números, etc) sino también a toda la gama de objetos sofisticados transfinitos que se pueden construir con la imaginación y la especulación matemática. Mantiene este universo matemático en su imaginación dándole existencia y coherencia más allá del mundo limitado de los objetos sintácticos que usa para expresarse. La mariposa es en algún sentido una maravilla de la imaginación matemática coherente.

A modo de ejemplo, al escarabajo la matemática orientada a objetos descripta en la sección anterior no le hace mucha gracia ya que es perezoso para imaginar los objetos asociados a los símbolos. Al contrario, la mariposa solo concibe la matemática orientada a objetos, los cuales piensa e imagina con un grado de realidad exacerbado.

En general la matemática se enseña con un estilo muy escarabajo y aún en las universidades esto persiste, manifestándose más en las carreras de ciencias de la computación que en las vinculadas a la matemática clásica. Es natural que esto suceda ya que los informáticos manipulan constantemente objetos sintácticos usando reglas mecánicas y a veces los objetos subyacentes (semántica) pasan a un segundo plano.

## El concepto de función

Asumiremos que el lector tiene una idea intuitiva del concepto de función. Daremos aquí una definición matemática de dicho concepto. Una función es un conjunto $f$ de pares ordenados con la siguiente propiedad

$$
\text{(F) Si } (x, y) \in f \text{ y } (x, z) \in f, \text{ entonces } y = z.
$$

Por ejemplo, si tomamos $f = \{(x, x^2) : x \in \omega\}$ se puede ver fácilmente que $f$ cumple la propiedad (F). Dada una función $f$, llamaremos dominio de $f$ al conjunto

$$
\{x : (x, y) \in f \text{ para algún } y\}
$$

y lo denotaremos con $D_f$ o $\mathrm{Dom}(f)$. Llamaremos imagen de $f$ al conjunto

$$
\{y : (x, y) \in f \text{ para algún } x\}
$$

y la denotaremos con $I_f$ o $\mathrm{Im}(f)$. Nótese que $\emptyset$ es una función y que $D_\emptyset = I_\emptyset = \emptyset$. Si $f = \{(x, x^2) : x \in \omega\}$ se tiene que $D_f = \omega$ y $I_f = \{y : y = x^2 \text{ para algún } x \in \omega\}$. Si $f = \{(x, 1) : x \in \{1, 6, 18\}\}$, entonces $D_f = \{1, 6, 18\}$ y $I_f = \{1\}$.

**Convención Notacional 1:** Como es usual, dado $x \in D_f$, usaremos $f(x)$ para denotar al único $y \in I_f$ tal que $(x, y) \in f$. Por ejemplo, si $f = \{(x, x^2) : x \in \omega\}$ se tiene que $f(x) = x^2$, para cada $x \in D_f = \omega$.

**Convención Notacional 2:** Escribiremos $f : S \subseteq A \to B$ para expresar que $f$ es una función tal que $D_f = S \subseteq A$ y $I_f \subseteq B$. También escribiremos $f : A \to B$ para expresar que $f$ es una función tal que $D_f = A$ y $I_f \subseteq B$. En tal contexto llamaremos a $B$ conjunto de llegada. Por supuesto $B$ no está determinado por $f$ ya que solo debe cumplir $I_f \subseteq B$. Es decir que cualquier conjunto $B$ que contenga a $I_f$ puede ser considerado conjunto de llegada de $f$.

**Convención Notacional 3:** Muchas veces para definir una función $f$, lo haremos dando su dominio y su regla de asignación, es decir especificaremos en forma precisa que conjunto es el dominio de $f$ y además especificaremos en forma precisa quién es $f(x)$ para cada $x$ de dicho dominio. Obviamente esto determina por completo a la función $f$ ya que siempre se da que $f = \{(x, f(x)) : x \in D_f\}$. Por ejemplo si decimos que $f$ es la función dada por:

$$
\begin{aligned}
D_f &= \omega\\
f(x) &= 23x^2
\end{aligned}
$$

nos estaremos refiriendo a la función $\{(x, 23x^2) : x \in \omega\}$. También escribiremos

$$
\begin{aligned}
f &: \omega \to \omega\\
x &\mapsto 23x^2
\end{aligned}
$$

para describir a $f$. Es decir, a veces para hacer más intuitiva aún la descripción de la función, también incluiremos un conjunto de llegada de dicha función y a la regla de asignación la escribiremos usando una flecha. Para dar otro ejemplo, si escribimos sea $f$ dada por:

$$
\begin{aligned}
f &: \mathbf{N} \to \omega\\
x &\mapsto
\begin{cases}
x+1 & \text{si } x \text{ es par}\\
x^2 & \text{si } x \text{ es impar}
\end{cases}
\end{aligned}
$$

estaremos diciendo que $f$ es la función

$$
\{(x, x + 1) : x \text{ es par y } x \in \mathbf{N}\} \cup \{(x, x^2) : x \text{ es impar y } x \in \mathbf{N}\}
$$

**Función identidad.** Dado un conjunto $A$, a la función

$$
\begin{aligned}
A &\to A\\
a &\mapsto a
\end{aligned}
$$

La denotaremos con $Id_A$ y la llamaremos la función identidad sobre $A$. Nótese que $Id_A = \{(a, a) : a \in A\}$.

**Igualdad de funciones.** Sean $f$ y $g$ dos funciones. Ya que las mismas son conjuntos, tendremos que $f$ será igual a $g$ si y solo si para cada par $(a, b)$, se tiene que $(a, b) \in f$ sii $(a, b) \in g$. Muchas veces será útil el siguiente criterio de igualdad de funciones:

**Lema 1.** Sean $f$ y $g$ funciones. Entonces $f = g$ sii $D_f = D_g$ y para cada $x \in D_f$ se tiene que $f(x) = g(x)$

.

**Ejercicio 3:** Pruebe el lema anterior (en el apunte está probado)

**Ejercicio 4:** V o F o I, justifique.

**(a)** Si

$$
\begin{aligned}
f &: \mathbf{N} \to \omega && g &: \mathbf{N} \to \mathbf{R}\\
x &\mapsto x^3 && x &\mapsto x^3
\end{aligned}
$$

entonces $f = g$

**(b)** Si

$$
\begin{aligned}
f &: \mathbf{N} \to \omega && g &: \mathbf{N} \to \omega\\
x &\mapsto x^3 && x &\mapsto x^4/x
\end{aligned}
$$

entonces $f = g$

**(c)** Si $f$ es una función y $z \in D_f$, entonces $Ti(z) = \mathrm{CONJUNTO}$

**(d)** $\mathrm{Dom}((1, 2)) = \{1\}$

**(e)** $\mathrm{Dom}(\{(1, 2)\}) + 1 = 2$

**(f)** Si $f$ es una función, entonces $D_f = \{a : (a, b) \in f\}$

**(g)** Si $f : A \to B$, entonces $D_f \subseteq A$

**(h)** Si $f : A \to B$, entonces $I_f = B$

**(i)** Si $f$ es una función y $g \subseteq f$, entonces $g$ es una función

**Función característica de un subconjunto.** Sea $X$ un conjunto cualquiera y sea $S \subseteq X$. Usaremos $\chi_S^X$ para denotar la función

$$
\begin{aligned}
\chi_S^X &: X \to \omega\\
x &\mapsto
\begin{cases}
1 & \text{si } x \in S\\
0 & \text{si } x \notin S
\end{cases}
\end{aligned}
$$

Llamaremos a $\chi_S^X$ la función característica de $S$ con respecto a $X$. Muchas veces cuando el conjunto $X$ esté fijo y sea claro el contexto, escribiremos $\chi_S$ en lugar de $\chi_S^X$.

**Restricción de una función.** Dada una función $f$ y un conjunto $S \subseteq D_f$, usaremos $f|_S$ para denotar la restricción de $f$ al conjunto $S$, i.e. $f|_S = f \cap (S \times I_f)$. Nótese que $f|_S$ es la función dada por

$$
\begin{aligned}
D_{f|_S} &= S\\
f|_S(e) &= f(e), \text{ para cada } e \in S
\end{aligned}
$$

Nótese que cualesquiera sea la función $f$ tenemos que $f|_\emptyset = \emptyset$ y $f|_{D_f} = f$.

## Principio de Inducción

Consideremos el siguiente:

- **Principio de Inducción:** Supongamos:

$$
\mathrm{Enu}_1, \mathrm{Enu}_2, \mathrm{Enu}_3, \mathrm{Enu}_4, \ldots
$$

es una sucesión de enunciados, cada uno de los cuales está escrito en forma precisa y es ya sea verdadero o falso. Supongamos además que

- $\mathrm{Enu}_1$ es verdadero
- Cada vez que uno de los enunciados es verdadero, el siguiente también lo es.

Entonces todos los enunciados deben ser verdaderos

El principio anterior es obvio ya que al ser verdadero $\mathrm{Enu}_1$ podemos inferir por la segunda propiedad que $\mathrm{Enu}_2$ lo es pero esto a su vez nos dice que $\mathrm{Enu}_3$ es verdadero, y así sucesivamente.

El Principio de Inducción da lugar a la siguiente regla la cual es extremadamente útil para realizar demostraciones en matemática.

- **Regla de Inducción:** Supongamos:

$$
\mathrm{Enu}_1, \mathrm{Enu}_2, \mathrm{Enu}_3, \mathrm{Enu}_4, \ldots
$$

es una sucesión de enunciados, cada uno de los cuales está escrito en forma precisa y es ya sea verdadero o falso. Entonces para probar que cada uno de los enunciados es verdadero, basta con

- Probar que $\mathrm{Enu}_1$ es verdadero
- Probar que para cada $n \in \mathbf{N}$, se tiene que si $\mathrm{Enu}_n$ es verdadero, entonces $\mathrm{Enu}_{n+1}$ lo es.

Por supuesto, la Regla de Inducción es (como buena regla) netamente mecánico-operativa y nos dice cómo operar para probar infinitos enunciados cumpliendo dos tareas concretas. El Principio de Inducción justifica la corrección de esta regla. En algún sentido el Principio de Inducción es más puro o primitivo ya que solo describe una situación acerca de los valores de verdad de los enunciados bajo la cual todos resultan verdaderos. La Regla de Inducción se basa en este principio para decirnos que si hacemos ciertas demostraciones, entonces podemos concluir que hemos demostrado todos los enunciados $\mathrm{Enu}_n$. Pero si esto le parece muy filosófico, tiene razón y siga leyendo que lo que viene es más concreto y útil!

Veamos un ejemplo. Para cada $n \in \mathbf{N}$ sea $\mathrm{Enu}_n$ el siguiente enunciado:

$$
\mathrm{Enu}_n : 1 + 2 + \ldots + n = \frac{n.(n+1)}{2}
$$

Nótese que

$$
\begin{aligned}
\mathrm{Enu}_1 &: 1 = \frac{1.(1+1)}{2}\\
\mathrm{Enu}_2 &: 1 + 2 = \frac{2.(2+1)}{2}\\
\mathrm{Enu}_3 &: 1 + 2 + 3 = \frac{3.(3+1)}{2}, \text{ etc.}
\end{aligned}
$$

Es fácil corroborar que alguno en particular es verdadero, simplemente hay que computar y ver si se da la igualdad. Pero por más que corroboremos un millón de enunciados, no podremos garantizar la veracidad de todos, si no hacemos algún tipo de razonamiento genérico. Justamente la Regla de Inducción nos dice que cosas tenemos que probar para garantizar que todos los enunciados sean verdaderos. Hagamos entonces las pruebas encomendadas por la regla.

**Prueba de $\mathrm{Enu}_1$:** Note que

$$
\frac{1.(1 + 1)}{2} = \frac{1.2}{2} = \frac{2}{2} = 1
$$

por lo cual $1 = \frac{1.(1+1)}{2}$.

**Prueba de que para cada $n \in \mathbf{N}$, se tiene que si $\mathrm{Enu}_n$ es verdadero, entonces $\mathrm{Enu}_{n+1}$ lo es:** Sea entonces un $n_0 \in \mathbf{N}$ fijo y supongamos que $\mathrm{Enu}_{n_0}$ es verdadero. Probaremos que $\mathrm{Enu}_{n_0+1}$ lo es. Tenemos entonces que

$$
1 + 2 + \ldots + n_0 = \frac{n_0.(n_0 + 1)}{2}
$$

por lo cual

$$
1 + 2 + \ldots + n_0 + (n_0 + 1) = \frac{n_0.(n_0 + 1)}{2} + (n_0 + 1)
$$

Pero

$$
\frac{n_0.(n_0 + 1)}{2} + (n_0 + 1)
= \frac{n_0.(n_0 + 1) + 2.(n_0 + 1)}{2}
= \frac{(n_0 + 2).(n_0 + 1)}{2}
= \frac{(n_0 + 1).(n_0 + 2)}{2}
$$

lo que nos dice que

$$
1 + 2 + \ldots + n_0 + (n_0 + 1) = \frac{(n_0 + 1).((n_0 + 1) + 1)}{2}
$$

que es justo lo que afirma $\mathrm{Enu}_{n_0+1}$. Ya que $n_0$ era arbitrario la implicación vale para cada $n \in \mathbf{N}$.

**Variaciones del Principio de Inducción.** Nada cambia si la sucesión de enunciados en lugar de comenzar desde 1, lo hace desde el 0. Es decir

- **Principio de Inducción desde 0:** Supongamos:

$$
\mathrm{Enu}_0, \mathrm{Enu}_1, \mathrm{Enu}_2, \mathrm{Enu}_3, \ldots
$$

es una sucesión de enunciados, cada uno de los cuales está escrito en forma precisa y es ya sea verdadero o falso. Supongamos además que

- $\mathrm{Enu}_0$ es verdadero
- Cada vez que uno de los enunciados es verdadero, el siguiente también lo es.

Entonces todos los enunciados deben ser verdaderos

Dejamos al lector que escriba la Regla de Inducción desde 0. Este caso será muy usado tanto para la parte de computabilidad como para la parte de lógica.

También la sucesión de enunciados puede comenzar desde 4, por ejemplo la regla quedaría:

- **Regla de Inducción desde 4:** Supongamos:

$$
\mathrm{Enu}_4, \mathrm{Enu}_5, \mathrm{Enu}_6, \mathrm{Enu}_7, \ldots
$$

es una sucesión de enunciados, cada uno de los cuales está escrito en forma precisa y es ya sea verdadero o falso. Entonces para probar que cada uno de los enunciados es verdadero, basta con

- Probar que $\mathrm{Enu}_4$ es verdadero
- Probar que para cada $n \ge 4$, se tiene que si $\mathrm{Enu}_n$ es verdadero, entonces $\mathrm{Enu}_{n+1}$ lo es.

Por ejemplo para cada $n \ge 4$ sea $\mathrm{Enu}_n$ el siguiente enunciado:

$$
\mathrm{Enu}_n : n! > 2^n
$$

O sea

$$
\begin{aligned}
\mathrm{Enu}_4 &: 4! > 2^4\\
\mathrm{Enu}_5 &: 5! > 2^5\\
\mathrm{Enu}_6 &: 6! > 2^6, \text{ etc.}
\end{aligned}
$$

Dejamos al lector la prueba de que $\mathrm{Enu}_4, \mathrm{Enu}_5, \mathrm{Enu}_6, \mathrm{Enu}_7, \ldots$ son verdaderos usando la Regla de Inducción desde 4.

Nótese que para $n < 4$ no es cierto el enunciado $n! > 2^n$ por lo cual la Regla de Inducción desde 4 nos viene justo para este caso. Obviamente en otros casos en lugar de 4 nos será útil otro elemento de $\omega$. Enunciamos entonces la regla en forma más gral:

- **Regla de Inducción desde $n_0$:** Supongamos:

$$
\mathrm{Enu}_{n_0}, \mathrm{Enu}_{n_0+1}, \mathrm{Enu}_{n_0+2}, \mathrm{Enu}_{n_0+3}, \ldots
$$

es una sucesión de enunciados, con $n_0 \in \omega$, cada uno de los cuales está escrito en forma precisa y es ya sea verdadero o falso. Entonces para probar que cada uno de los enunciados es verdadero, basta con

- Probar que $\mathrm{Enu}_{n_0}$ es verdadero
- Probar que para cada $n \ge n_0$, se tiene que si $\mathrm{Enu}_n$ es verdadero, entonces $\mathrm{Enu}_{n+1}$ lo es.

**Inducción Completa.** Consideremos la siguiente:

- **Regla de Inducción Completa desde $n_0$:** Supongamos:

$$
\mathrm{Enu}_{n_0}, \mathrm{Enu}_{n_0+1}, \mathrm{Enu}_{n_0+2}, \mathrm{Enu}_{n_0+3}, \ldots
$$

es una sucesión de enunciados, con $n_0 \in \omega$, cada uno de los cuales está escrito en forma precisa y es ya sea verdadero o falso. Entonces para probar que cada uno de los enunciados es verdadero, basta con

- Probar que $\mathrm{Enu}_{n_0}$ es verdadero
- Probar que para cada $n \ge n_0$, si $\mathrm{Enu}_j$ es verdadero para cada $j \le n$, entonces $\mathrm{Enu}_{n+1}$ lo es.

El lector no tendrá inconvenientes en comprender la validez de esta regla. Hay casos en los cuales la Regla de Inducción desde $n_0$ no nos es útil ya que de saber que es cierto $\mathrm{Enu}_n$ no se nos ocurre cómo probar $\mathrm{Enu}_{n+1}$, pero si asumimos que $\mathrm{Enu}_j$ es verdadero para cada $j \le n$ entonces si se nos ocurre cómo probar $\mathrm{Enu}_{n+1}$. En estos casos es natural aplicar la Regla de Inducción Completa desde $n_0$. Veamos un ejemplo.

Para cada $n \ge 2$ sea $\mathrm{Enu}_n$ el siguiente enunciado:

$$
\mathrm{Enu}_n : \text{Existen números primos } p_1, \ldots, p_k, \text{ con } k \ge 1 \text{ tales que } n = p_1.p_2.\ldots.p_k
$$

O sea

$$
\begin{aligned}
\mathrm{Enu}_2 &: \text{Existen números primos } p_1, \ldots, p_k, \text{ con } k \ge 1 \text{ tales que } 2 = p_1.p_2.\ldots.p_k\\
\mathrm{Enu}_3 &: \text{Existen números primos } p_1, \ldots, p_k, \text{ con } k \ge 1 \text{ tales que } 3 = p_1.p_2.\ldots.p_k\\
\mathrm{Enu}_4 &: \text{Existen números primos } p_1, \ldots, p_k, \text{ con } k \ge 1 \text{ tales que } 4 = p_1.p_2.\ldots.p_k
\end{aligned}
$$

etc. Para probar que

$$
\mathrm{Enu}_2, \mathrm{Enu}_3, \mathrm{Enu}_4, \ldots
$$

son verdaderos, hagamos las pruebas encomendadas por la Regla de Inducción Completa desde 2.

**Prueba de $\mathrm{Enu}_2$:** Podemos tomar $k = 1$ y $p_1 = 2$

**Prueba de que para cada $n \ge 2$, si $\mathrm{Enu}_j$ es verdadero para cada $j \le n$, entonces $\mathrm{Enu}_{n+1}$ lo es:** Sea entonces $n \ge 2$ fijo y supongamos que $\mathrm{Enu}_j$ es verdadero para cada $j \le n$. Probaremos que $\mathrm{Enu}_{n+1}$ lo es. Si $n + 1$ es primo, entonces podemos tomar $k = 1$ y $p_1 = n + 1$ para concluir que $\mathrm{Enu}_{n+1}$ es cierto. Supongamos entonces que $n + 1$ no es primo. Entonces hay $a, b$ tales que $n + 1 = a.b$ y $a, b \ge 2$. Nótese que entonces $a, b \le n$. Por hipótesis tenemos que entonces $\mathrm{Enu}_a$ y $\mathrm{Enu}_b$ son ciertos por lo cual existen primos $p_1, \ldots, p_k$, con $k \ge 1$ tales que $a = p_1.\ldots.p_k$ y existen primos $q_1, \ldots, q_m$, con $m \ge 1$ tales que $b = q_1.\ldots.q_m$. Tenemos entonces que

$$
n + 1 = p_1.\ldots.p_k.q_1.\ldots.q_m
$$

de lo cual claramente obtenemos que $\mathrm{Enu}_{n+1}$ es verdadero.

Dejamos al lector que experimente un rato la dificultad de intentar usar la Regla de Inducción desde 2 para este caso.

**El principio de inducción usado en la ficción de una prueba.** Casi siempre que en matemática probamos algún enunciado, nuestro argumento involucra cierta ficción. Es decir en general, los enunciados matemáticos tienen hipótesis las cuales suponen que ciertos objetos cumplen ciertas propiedades y tienen su conclusión o tesis que es justamente lo que el enunciado asegura debe suceder si se dan las hipótesis. Esto hace que en la prueba se comience suponiendo que se dan las hipótesis y luego se empiece a desarrollar una ficción dentro de la cual vía cierto desarrollo se llegará a la conclusión (que también es parte de esa ficción). Por ejemplo consideremos el siguiente famoso enunciado:

$$
\mathrm{Enu}_1 : \text{Supongamos } p \text{ es un polinomio a coeficientes complejos de grado mayor que } 0. \text{ Entonces } p \text{ tiene al menos una raíz compleja, es decir hay un número complejo } c \text{ tal que } p(c) = 0.
$$

En la prueba del mismo asumiremos que $p$ es un polinomio a coeficientes complejos de grado mayor que 0. Este será el actor inicial de nuestra demostración (película) la cual nos terminará convenciendo de que hay un número complejo $c$ tal que $p(c) = 0$. Para dar otro ejemplo, consideremos el enunciado:

$$
\mathrm{Enu}_2 : \text{Sean } f, g \text{ funciones. Supongamos } f \circ g \ne \emptyset. \text{ Entonces } I_g \cap D_f \ne \emptyset.
$$

En la prueba asumiremos que $f, g$ son funciones y que $f \circ g \ne \emptyset$. Ellas serán los actores iniciales de nuestra (ficción) demostración, la cual nos terminará convenciendo que $I_g \cap D_f \ne \emptyset$.

Pero debemos notar que a lo largo de una demostración pueden surgir nuevos actores en escena. Es muy común que en el medio de una demostración probemos que existe al menos un objeto con cierta propiedad y que inmediatamente digamos sea $e$ uno de tales objetos, fijado para el resto de nuestra demostración. Claramente $e$ es un nuevo actor en la ficción de nuestra prueba (película). Para dar otro ejemplo, dentro de una demostración puede suceder que probemos que cierto objeto $r$ es un número racional. Obviamente $r$ ya era un actor dentro de la ficción de la prueba, pero ahora podemos incorporar dos nuevos actores $a, b \in \mathbf{Z}$tales que $r = a/b$. Y nuestro argumento (película) sigue ahora con dos nuevos actores. Por ejemplo en la prueba de $\mathrm{Enu}_2$, la cual puede verse en el apunte, aparte de los actores $f$ y $g$ surge el nuevo actor $e$ tal que $e \in D_g$ y $g(e) \in D_f$, el cual sirve para concluir que $I_g \cap D_f \ne \emptyset$.

Resumiendo, en la ficción de una prueba, aparte de los objetos reales de la matemática pueden estar involucrados objetos que son solo parte de la ficción correspondiente al argumento de la prueba. Cabe destacar que parte de la madurez de un matemático profesional consiste en tratar e imaginar a dichos objetos como si fueran reales y concretos. Muchas veces en el transcurso de una prueba, se usará alguna versión de la Regla de Inducción aplicada a una sucesión de enunciados que involucran objetos que sólo existen en la ficción de la prueba misma y no fuera de ella.

Esto no trae inconvenientes dado que aún dentro de la ficción de una prueba los conceptos de verdad y de demostración tienen las propiedades que hacen válidos al Principio de Inducción y a la Regla de Inducción, en todas sus versiones.

## Funciones $\Sigma$-mixtas

Sea $\Sigma$ un alfabeto finito. Dados $n, m \in \omega$, usaremos $\omega^n \times \Sigma^{\ast m}$ para abreviar la expresión

$$
\overbrace{\omega \times \cdots \times \omega}^{n\text{ veces}}
\times
\overbrace{\Sigma^\ast \times \cdots \times \Sigma^\ast}^{m\text{ veces}}
$$

Por ejemplo, $\omega^3 \times \Sigma^{\ast 4}$ será una forma abreviada de escribir $\omega \times \omega \times \omega \times \Sigma^\ast \times \Sigma^\ast \times \Sigma^\ast \times \Sigma^\ast$. Debe quedar claro que estamos haciendo cierto abuso notacional ya que en principio si no hacemos esta convención notacional, $\omega^3 \times \Sigma^{\ast 4}$ denota un conjunto de pares y $\omega \times \omega \times \omega \times \Sigma^\ast \times \Sigma^\ast \times \Sigma^\ast \times \Sigma^\ast$ es un conjunto de 7-uplas.

Nótese que:

- Cuando $n = m = 0$, tenemos que $\omega^n \times \Sigma^{\ast m}$ denota el conjunto $\{\diamond\}$
- Si $m = 0$, entonces $\omega^n \times \Sigma^{\ast m}$ denota el conjunto $\omega^n$
- Si $n = 0$, entonces $\omega^n \times \Sigma^{\ast m}$ denota el conjunto $\Sigma^{\ast m}$
- Cuando $\Sigma = \emptyset$, tenemos que $\Sigma^\ast = \{\varepsilon\}$. O sea que por ejemplo

$$
\omega^n \times \Sigma^{\ast 5} = \{(x_1, \ldots, x_n, \varepsilon, \varepsilon, \varepsilon, \varepsilon, \varepsilon) : x_1, \ldots, x_n \in \omega\}
$$

Es decir que tenemos que tener cuidado cuando leemos esta notación y no caer en la confusión de interpretarla mal.

Con esta convención notacional, un elemento genérico de $\omega^n \times \Sigma^{\ast m}$ es una $(n+m)$-upla de la forma $(x_1, \ldots, x_n, \alpha_1, \ldots, \alpha_m)$. Para abreviar, escribiremos $(\overrightarrow{x}, \overrightarrow{\alpha})$ en lugar de $(x_1, \ldots, x_n, \alpha_1, \ldots, \alpha_m)$.

**Definición de función $\Sigma$-mixta.** Sea $\Sigma$ un alfabeto finito. Dada una función $f$, diremos que $f$ es $\Sigma$-mixta si cumple las siguientes propiedades

(M1) Existen $n, m \ge 0$, tales que $D_f \subseteq \omega^n \times \Sigma^{\ast m}$

(M2) Ya sea $I_f \subseteq \omega$ o $I_f \subseteq \Sigma^\ast$

Algunos ejemplos:

(E1) Sea $\Sigma = \{$`□`, `%`, `▲`$\}$. La función

$$
\begin{aligned}
f : \{(1,\text{□\%\%}), (100,\text{\%▲▲})\} &\to \omega\\
(x,\alpha) &\mapsto x + |\alpha|
\end{aligned}
$$

es $\Sigma$-mixta ya que se cumple (M1) con $n = m = 1$ y también cumple (M2). Nótese que $f$ no es $\{$`□`, `%`$\}$-mixta ya que no cumple (M1) respecto del alfabeto $\{$`□`, `%`$\}$. Sin embargo note que $f$ es $\{$`□`, `%`, `▲`, `@`$\}$-mixta

(E2) La función

$$
\begin{aligned}
\omega^4 &\to \omega\\
(x, y, z, w) &\mapsto x + y
\end{aligned}
$$

es $\Sigma$-mixta cualesquiera sea el alfabeto $\Sigma$

(E3) Sea $\Sigma = \{$`□`, `@`$\}$. La función

$$
\begin{aligned}
\{\text{□□□}, \text{@@}\} &\to \omega\\
\alpha &\mapsto |\alpha|
\end{aligned}
$$

es $\Sigma$-mixta ya que se cumple (M1) (con $n = 0$ y $m = 1$) y (M2)

(E4) Supongamos $\Sigma = \emptyset$. Tenemos entonces que $\Sigma^\ast = \{\varepsilon\}$. Por ejemplo

$$
\begin{aligned}
D &\to \omega\\
(x, \varepsilon, \varepsilon, \varepsilon) &\mapsto x^2
\end{aligned}
$$

donde $D = \{(x, \varepsilon, \varepsilon, \varepsilon) : x \text{ es impar}\}$, es $\Sigma$-mixta (con $n = 1$ y $m = 3$ en (M1)). También nótese que

$$
\begin{aligned}
\{(\varepsilon, \varepsilon)\} &\to \{\varepsilon\}\\
(\varepsilon, \varepsilon) &\mapsto \varepsilon
\end{aligned}
$$

es $\Sigma$-mixta (con $n = 0$ y $m = 2$ en (M1)).

Dejamos al lector la fácil prueba del siguiente resultado básico.

**Lema 2.** Supongamos $\Sigma \subseteq \Gamma$ son alfabetos finitos. Entonces si $f$ es una función $\Sigma$-mixta, $f$ es $\Gamma$-mixta

Una función $\Sigma$-mixta $f$ es $\Sigma$-total cuando haya $n, m \in \omega$ tales que $D_f = \omega^n \times \Sigma^{\ast m}$. El lema anterior nos dice que si $\Sigma \subseteq \Gamma$, entonces toda función $\Sigma$-mixta es $\Gamma$-mixta. Sin embargo una función puede ser $\Sigma$-total y no ser $\Gamma$-total, cuando $\Sigma \subseteq \Gamma$. Por ejemplo tomemos $\Sigma = \{$`□`, `%`, `▲`$\}$ y $\Gamma = \{$`□`, `%`, `▲`, `!`$\}$, y consideremos la función

$$
\begin{aligned}
f : \omega \times \Sigma^\ast &\to \omega\\
(x, \alpha) &\mapsto x + |\alpha|
\end{aligned}
$$

Es claro que $f$ es $\Sigma$-mixta y $\Sigma$-total. También es $\Gamma$-mixta ya que $D_f \subseteq \omega \times \Gamma^\ast$ y $I_f \subseteq \omega$, por lo cual cumple (M1) y (M2). Sin embargo $f$ no es $\Gamma$-total ya que $D_f$ no es igual a $\omega^n \times \Gamma^{\ast m}$, cualesquiera sean $n$ y $m$.

Como hemos visto recién, una función $f$ puede ser $\Sigma$-mixta y $\Gamma$-mixta para dos alfabetos distintos $\Sigma$ y $\Gamma$ e incluso es fácil construir un ejemplo en el cual $\Sigma$ y $\Gamma$ sean incomparables como conjuntos, es decir que ninguno incluya al otro. Dejamos al lector convencerse de que si $f$ es una función que es $\Sigma$-mixta para algún alfabeto $\Sigma$, entonces hay un alfabeto $\Sigma_0$ el cual es el menor de todos los alfabetos respecto de los cuales $f$ es mixta, es decir $\Sigma_0$ cumple que $f$ es $\Sigma_0$-mixta y si $\Gamma$ es tal que $f$ es $\Gamma$-mixta, entonces $\Sigma_0 \subseteq \Gamma$.

A continuación daremos algunas funciones $\Sigma$-mixtas básicas las cuales serán frecuentemente usadas.

**Funciones $Suc$ y $Pred$.** La función sucesor es definida por

$$
\begin{aligned}
Suc : \omega &\to \omega\\
n &\mapsto n+1
\end{aligned}
$$

La función predecesor es definida por

$$
\begin{aligned}
Pred : \mathbf{N} &\to \omega\\
n &\mapsto n-1
\end{aligned}
$$

**Las funciones $d_a$.** Sea $\Sigma$ un alfabeto no vacío. Para cada $a \in \Sigma$, definamos

$$
\begin{aligned}
d_a : \Sigma^\ast &\to \Sigma^\ast\\
\alpha &\mapsto \alpha a
\end{aligned}
$$

La función $d_a$ es llamada la función derecha sub $a$, respecto del alfabeto $\Sigma$.

**Las funciones $p_i^{n,m}$.** Sea $\Sigma$ un alfabeto. Para $n, m \in \omega$ e $i$ tal que $1 \le i \le n$, definamos

$$
\begin{aligned}
p_i^{n,m} : \omega^n \times \Sigma^{\ast m} &\to \omega\\
(\overrightarrow{x}, \overrightarrow{\alpha}) &\mapsto x_i
\end{aligned}
$$

Para $n, m \in \omega$ e $i$ tal que $n + 1 \le i \le n + m$, definamos

$$
\begin{aligned}
p_i^{n,m} : \omega^n \times \Sigma^{\ast m} &\to \Sigma^\ast\\
(\overrightarrow{x}, \overrightarrow{\alpha}) &\mapsto \alpha_{i-n}
\end{aligned}
$$

Las funciones $p_i^{n,m}$ son llamadas proyecciones. La función $p_i^{n,m}$ es llamada la proyección $n,m,i$, respecto del alfabeto $\Sigma$. Nótese que esta definición requiere que $n + m \ge 1$ ya que $i$ debe cumplir $1 \le i \le n + m$. Además nótese que siempre la función $p_i^{n,m}$ aplicada a una $(n + m)$-upla da la coordenada $i$-ésima de dicha $(n + m)$-upla. Por ejemplo:

$$
\begin{aligned}
p_3^{1,3} : \omega \times \Sigma^\ast \times \Sigma^\ast \times \Sigma^\ast &\to \Sigma^\ast\\
(x, \alpha_1, \alpha_2, \alpha_3) &\mapsto \alpha_2
\end{aligned}
$$

**Las funciones $C_k^{n,m}$ y $C_\alpha^{n,m}$.** Sea $\Sigma$ un alfabeto. Para $n, m, k \in \omega$, y $\alpha \in \Sigma^\ast$, definamos

$$
\begin{aligned}
C_k^{n,m} : \omega^n \times \Sigma^{\ast m} &\to \omega
&
C_\alpha^{n,m} : \omega^n \times \Sigma^{\ast m} &\to \Sigma^\ast\\
(\overrightarrow{x}, \overrightarrow{\alpha}) &\mapsto k
&
(\overrightarrow{x}, \overrightarrow{\alpha}) &\mapsto \alpha
\end{aligned}
$$

Por ejemplo:

$$
\begin{aligned}
C_3^{1,3} : \omega \times \Sigma^\ast \times \Sigma^\ast \times \Sigma^\ast &\to \omega
&
C_\varepsilon^{1,3} : \omega \times \Sigma^\ast \times \Sigma^\ast \times \Sigma^\ast &\to \omega\\
(x, \alpha_1, \alpha_2, \alpha_3) &\mapsto 3
&
(x, \alpha_1, \alpha_2, \alpha_3) &\mapsto \varepsilon
\end{aligned}
$$

Nótese que $C_k^{0,0} : \{\diamond\} \to \{k\}$ y que $C_\alpha^{0,0} : \{\diamond\} \to \{\alpha\}$.

**Ejercicio 5:** V o F o I, justifique.

**(a)** La función $x + 1$ es $\emptyset$-mixta

**(b)** La función

$$
\begin{aligned}
\{(x,\alpha)\in \omega \times \{\#, \&, \text{@}\}^\ast : |\alpha|_{\#} = 0\} &\to \omega\\
(x,\alpha) &\mapsto |\alpha|.x
\end{aligned}
$$

es `{&, @}`-mixta

**(c)** $f$ es $\Sigma$-mixta si existen $n, m \ge 0$, tales que $D_f \subseteq \omega^n \times \Sigma^{\ast m}$ y $I_f \subseteq \omega \cup \Sigma^\ast$

**(d)** Sea

$$
\begin{aligned}
f : \omega &\to \omega\\
x &\mapsto C_2^{1,0}
\end{aligned}
$$

Entonces $f(5) = 2$

**El tipo de una función mixta.** Dada una función $\Sigma$-mixta $f$, si $n, m \in \omega$ son tales que $D_f \subseteq \omega^n \times \Sigma^{\ast m}$ y además $I_f \subseteq \omega$, entonces diremos que $f$ es una función de tipo $(n, m, \#)$. Similarmente si $n, m \in \omega$ son tales que $D_f \subseteq \omega^n \times \Sigma^{\ast m}$ y además $I_f \subseteq \Sigma^\ast$, entonces diremos que $f$ es una función de tipo $(n, m, \ast)$. Nótese que si $f \ne \emptyset$, entonces hay únicos $n, m \in \omega$ y $s \in \{\#, \ast\}$ tales que $f$ es una función de tipo $(n, m, s)$. Sin embargo $\emptyset$ es una función de tipo $(n, m, s)$ cualesquiera sean $n, m \in \omega$ y $s \in \{\#, \ast\}$. De esta forma, cuando $f \ne \emptyset$ hablaremos de "el tipo de $f$" para referirnos a esta única terna $(n, m, s)$. Nótese que $Suc$ es de tipo $(1, 0, \#)$ y $d_a$ es de tipo $(0, 1, \ast)$.

**Ejercicio 6:** Hacer

**(a)** De qué tipo es cada una de las siguientes funciones

**(i)** $C_\varepsilon^{1,2}$

**(ii)**

$$
\begin{aligned}
\{(x,\alpha)\in \omega \times \{\#, \&, \text{@}\}^\ast : |\alpha|_{\#} = 0\} &\to \omega\\
(x,\alpha) &\mapsto |\alpha|.x
\end{aligned}
$$

**(iii)** $Id_\omega$

**(iv)** $Id_{\Sigma^\ast}$

**(v)**

$$
\begin{aligned}
\Sigma^\ast &\to \omega\\
\alpha &\mapsto |\alpha|
\end{aligned}
$$

**(vi)**

$$
\begin{aligned}
\{(\varepsilon, \varepsilon)\} &\to \{\varepsilon\}\\
(\varepsilon, \varepsilon) &\mapsto \varepsilon
\end{aligned}
$$

**(vii)**

$$
\begin{aligned}
\{\diamond\} &\to \omega\\
\diamond &\mapsto 0
\end{aligned}
$$

**(b)** Qué significa la frase

- la relación "$f$ es una función de tipo $(n, m, s)$" no depende del alfabeto $\Sigma$

Intente expresar esto en forma matemática

**Predicados $\Sigma$-mixtos.** Un predicado $\Sigma$-mixto es una función $f$ la cual es $\Sigma$-mixta y además cumple que $I_f \subseteq \{0, 1\}$. Por ejemplo

$$
\begin{aligned}
\omega \times \omega &\to \omega\\
(x, y) &\mapsto
\begin{cases}
1 & \text{si } x = y\\
0 & \text{si } x \ne y
\end{cases}
\end{aligned}
$$

$$
\begin{aligned}
\{1, 2, 3, 4, 5\} \times \Sigma^\ast &\to \omega\\
(x, \alpha) &\mapsto
\begin{cases}
1 & \text{si } x = |\alpha|\\
0 & \text{si } x \ne |\alpha|
\end{cases}
\end{aligned}
$$

**Operaciones lógicas entre predicados.** Dados predicados $P : S \subseteq \omega^n \times \Sigma^{\ast m} \to \{0, 1\}$ y $Q : S \subseteq \omega^n \times \Sigma^{\ast m} \to \{0, 1\}$, con el mismo dominio, definamos nuevos predicados $(P \lor Q)$, $(P \land Q)$ y $\neg P$ de la siguiente manera

$$
\begin{aligned}
(P \lor Q) : S &\to \omega\\
(\overrightarrow{x}, \overrightarrow{\alpha}) &\mapsto
\begin{cases}
1 & \text{si } P(\overrightarrow{x}, \overrightarrow{\alpha}) = 1 \text{ o } Q(\overrightarrow{x}, \overrightarrow{\alpha}) = 1\\
0 & \text{caso contrario}
\end{cases}
\end{aligned}
$$

$$
\begin{aligned}
(P \land Q) : S &\to \omega\\
(\overrightarrow{x}, \overrightarrow{\alpha}) &\mapsto
\begin{cases}
1 & \text{si } P(\overrightarrow{x}, \overrightarrow{\alpha}) = 1 \text{ y } Q(\overrightarrow{x}, \overrightarrow{\alpha}) = 1\\
0 & \text{caso contrario}
\end{cases}
\end{aligned}
$$

$$
\begin{aligned}
\neg P : S &\to \omega\\
(\overrightarrow{x}, \overrightarrow{\alpha}) &\mapsto
\begin{cases}
1 & \text{si } P(\overrightarrow{x}, \overrightarrow{\alpha}) = 0\\
0 & \text{si } P(\overrightarrow{x}, \overrightarrow{\alpha}) = 1
\end{cases}
\end{aligned}
$$

## Composición de funciones

Dadas funciones $f$ y $g$ definamos la función $f \circ g$ de la siguiente manera:

$$
\begin{aligned}
D_{f \circ g} &= \{e \in D_g : g(e) \in D_f\}\\
f \circ g(e) &= f(g(e))
\end{aligned}
$$

Nótese que

$$
f \circ g = \{(e, f(g(e))) : e \in D_g \text{ y } g(e) \in D_f\}
$$

(ver Convención Notacional 3). Veamos un ejemplo. Si $f$ es dada por

$$
\begin{aligned}
f : \mathbf{N} &\to \{\text{@}, \text{\%}\}^\ast\\
x &\mapsto \text{@}\text{\%}^{x}\text{@}
\end{aligned}
$$

y $g$ es dada por

$$
\begin{aligned}
g : \mathbf{R} &\to \mathbf{R}\\
x &\mapsto x^2
\end{aligned}
$$

entonces tenemos que $f \circ g$ es la función

$$
\begin{aligned}
f \circ g : \{x \in \mathbf{R} : x^2 \in \mathbf{N}\} &\to \{\text{@}, \text{\%}\}^\ast\\
x &\mapsto \text{@}\text{\%}^{x^2}\text{@}
\end{aligned}
$$

Notar que $f \circ g = \{(u, v) : \text{existe } z \text{ tal que } (u, z) \in g \text{ y } (z, v) \in f\}$ (por una prueba ver el apunte).

**Ejercicio 7:** V o F o I, justifique

**(a)** Si $D_f = \omega$, entonces $f \circ \{(x, x) : x \in \omega\} = f$

**(b)** Si $D_f = \omega$, entonces $f \circ x = f$

**(c)** $Pred = Pred \circ (Pred \circ Suc)$

**(d)** $Pred \circ (Suc \circ Pred) = Pred$

**(e)** $Pred \circ (Suc \circ \{(x, x) : x \in \mathbf{N}\}) = Pred \circ Suc$

**(f)** $\emptyset \circ f = f \circ \emptyset = \emptyset$ cualquiera sea la función $f$

**(g)** Sea $\Sigma$ un alfabeto finito. Si $x_1, x_2, x_3, x_4, x_5 \in \omega$ se tiene que $(Suc \circ p_2^{5,0})(x_1, x_2, x_3, x_4, x_5) = x_3$

**(h)** Sea $\Sigma$ un alfabeto finito. Entonces $Suc \circ Pred = p_1^{1,0}$

**(i)** $Suc \circ x = Suc$

**(j)** $Suc \circ 4 = 5$

**(k)** Sea $\Sigma$ un alfabeto finito. Entonces $\emptyset = Pred \circ C_0^{0,0}$

**(l)** Si $f : D_f \subseteq \omega \to \omega$ y $g : D_g \subseteq \omega \to \omega$, entonces $D_{f \circ g} = \{x \in \omega : x \in D_g \text{ y } I_g \subseteq D_f\}$

A la hora de probar enunciados acerca de funciones hay una regla o idea básica que si la tenemos en cuenta nos facilitará la construcción de la prueba.

**Regla Pertenecer a la Imagen:** Si $f$ es una función y ud sabe que $b \in I_f$, entonces escriba a $b$ en la forma $f(a)$ donde $a$ denotará un elemento fijo de $D_f$ tal que $f(a) = b$

Muchas veces tener esta regla en mente es de suma utilidad al hacer pruebas. Por ejemplo el lector puede usarla para hacer una prueba rigurosa del $(\Leftarrow)$ del enunciado del siguiente ejercicio. Esa regla aquí es simplemente un consejo o sugerencia pero gana su existencia material en un entorno de inteligencia artificial al transformarse en parte de la estructura de un probador automático de teoremas!

**Ejercicio 8:** Pruebe que $f \circ g \ne \emptyset$ si y solo si $I_g \cap D_f \ne \emptyset$ (está probado en el apunte). Nótese que este resultado nos dice que muchas veces sucederá que $f \circ g = \emptyset$.

## Funciones de la forma $[f_1, \ldots, f_n]$

Dadas funciones $f_1, \ldots, f_n$, con $n \ge 2$, definamos la función $[f_1, \ldots, f_n]$ de la siguiente manera:

$$
\begin{aligned}
D_{[f_1,\ldots,f_n]} &= D_{f_1} \cap \ldots \cap D_{f_n}\\
[f_1, \ldots, f_n](e) &= (f_1(e), \ldots, f_n(e))
\end{aligned}
$$

Nótese que $I_{[f_1,\ldots,f_n]} \subseteq I_{f_1} \times \cdots \times I_{f_n}$. Por conveniencia notacional (que el lector entenderá más adelante) definiremos $[f_1] = f_1$. Es decir que hemos definido para cada sucesión de funciones $f_1, \ldots, f_n$, con $n \ge 1$, una nueva función la cual denotamos con $[f_1, \ldots, f_n]$.

**Ejercicio 9:** V o F o I, justifique

**(a)** Sea $\Sigma$ un alfabeto y supongamos $\# \in \Sigma$. Entonces

$$
p_4^{2,3} \circ [p_1^{1,1}, p_1^{1,1}, p_2^{1,1}, C_{\#\#}^{1,1}, p_2^{1,1}] = C_{\#\#}^{1,1}
$$

**(b)** Si $f : \omega^2 \to \omega$, entonces $f = f \circ [x, y]$

**(c)** $[p_2^{2,3}, Suc] = \emptyset$

**(d)** Supongamos $f_i : \omega \to \omega$, para $i \in \{1, \ldots, n\}$, con $n \ge 2$. Entonces $I_{[f_1,\ldots,f_n]} = I_{f_1} \times \cdots \times I_{f_n}$

## Funciones inyectivas, suryectivas y biyectivas

Una función $f$ es inyectiva cuando no se da que $f(a) = f(b)$ para algún par de elementos distintos $a, b \in D_f$. Dicho de otra manera, $f$ será inyectiva cuando se dé la implicación

$$
f(a) = f(b) \text{ implica } a = b
$$

cualesquiera sean $a, b \in D_f$. Dada una función $f : A \to B$ diremos que $f$ es suryectiva cuando $I_f = B$. Debe notarse que el concepto de suryectividad depende de un conjunto de llegada previamente fijado, es decir que no tiene sentido hablar de la suryectividad de una función $f$ si no decimos respecto de qué conjunto de llegada lo es. Muchas veces diremos que una función $f$ es sobre para expresar que es suryectiva.

Dada una función $f : A \to B$ diremos que $f$ es biyectiva cuando $f$ sea inyectiva y suryectiva. También diremos que $f$ es una biyección de $A$ en $B$ cuando $f : A \to B$ sea biyectiva. Nótese que si $f : A \to B$ es biyectiva, entonces para cada $b \in B$ hay un único $a \in A$ tal que $f(a) = b$. Entonces cuando $f : A \to B$ es biyectiva podemos definir una nueva función $f^{-1} : B \to A$, de la siguiente manera:

$$
f^{-1}(b) = \text{único } a \in A \text{ tal que } f(a) = b
$$

La función $f^{-1}$ será llamada la inversa de $f$. Nótese que $f \circ f^{-1} = Id_B$ y $f^{-1} \circ f = Id_A$. El siguiente lema muestra que esta última propiedad caracteriza la inversa.

**Ejercicio 10:** V o F o I, justifique.

**(a)** Una función $f$ es inyectiva si $f(x) = f(y)$ cada vez que $x = y$

**(b)** $F : A \to B$ es suryectiva sii para cada $a \in A$ existe un $b \in B$ tal que $b = F(a)$

**Ejercicio 11:** Hacer:

**(a)** Dar una biyección entre $\mathbf{N}$ y $\omega$. Idem entre $\omega$ y $\{x \in \omega : x \text{ es par}\}$

**(b)** Dar una función inyectiva de $\omega^2$ en $\omega$

**(c)** Dar una función sobreyectiva de $\omega$ en $\omega^5$

**Lema 3.** Supongamos $f : A \to B$ y $g : B \to A$ son tales que $f \circ g = Id_B$ y $g \circ f = Id_A$. Entonces $f$ y $g$ son biyectivas, $f^{-1} = g$ y $g^{-1} = f$.

**Ejercicio 12:** Haga una prueba del lema anterior (está probado en el apunte)

## Conjuntos $\Sigma$-mixtos

Un conjunto $S$ es llamado $\Sigma$-mixto si existen $n, m \in \omega$ tales que $S \subseteq \omega^n \times \Sigma^{\ast m}$. Por ejemplo,

$$
\begin{gathered}
\{(x,\alpha)\in \omega \times \{\text{▲}, \text{!}\}^\ast : |\alpha| = x\}\\
\{(0,\text{▲▲▲},\varepsilon), (1,\text{\%▲\%},\text{▲▲})\}
\end{gathered}
$$

son conjuntos `{▲, %, !}`-mixtos. También nótese que $\emptyset$ y $\{\diamond\}$ son conjuntos $\Sigma$-mixtos, cualesquiera sea el alfabeto $\Sigma$. Por último el conjunto

$$
\{(x, \varepsilon, \varepsilon, \varepsilon) : x \in \omega \text{ y } x \text{ es impar}\}
$$

es $\emptyset$-mixto (con $n = 1$ y $m = 3$).

**Ejercicio 13:** V o F o I, justifique.

**(a)** Un conjunto $S$ es $\Sigma$-mixto sii $S = D_f$ para alguna función $\Sigma$-mixta $f$

**(b)** $\{(1, 2, \varepsilon), (1, 2)\}$ es un conjunto $\Sigma$-mixto, cualesquiera sea el alfabeto finito $\Sigma$

**El tipo de un conjunto mixto.** Dado un conjunto $\Sigma$-mixto $S$, si $n, m \in \omega$ son tales que $S \subseteq \omega^n \times \Sigma^{\ast m}$, entonces diremos que $S$ es un conjunto de tipo $(n, m)$. Nótese que si $S \ne \emptyset$, entonces hay únicos $n, m \in \omega$ tales que $S$ es un conjunto de tipo $(n, m)$. De esta forma, cuando $S \ne \emptyset$ hablaremos de "el tipo de $S$" para referirnos a este único par $(n, m)$. También es importante notar que de la definición anterior sale inmediatamente que $\emptyset$ es un conjunto de tipo $(n, m)$ cualesquiera sean $n, m \in \omega$, por lo cual cuando hablemos de EL tipo de un conjunto deberemos estar seguros de que dicho conjunto es no vacío.

Nótese que $\omega$ es de tipo $(1, 0)$ y $\Sigma^\ast$ es de tipo $(0, 1)$.

**Ejercicio 14:** Hacer

**(a)** De qué tipo es cada uno de los siguientes conjuntos

**(i)**

$$
\{(x,\alpha)\in \omega \times \{\#, \&, \text{@}\}^\ast : |\alpha|_{\#} = 0\}
$$

**(ii)** $\{1, 2, 3\}$

**(iii)** $\{\varepsilon\}$

**(iv)** $\{\diamond\}$

**(v)** $\{(1, \varepsilon)\}$

**(vi)** $\{(\varepsilon, \varepsilon)\}$

**(b)** Para el caso $\Sigma = \emptyset$, describa para un $m \in \omega$ dado, cómo son los conjuntos no vacíos de tipo $(0, m)$.

**(c)** Qué significa la frase

- la relación "$S$ es un conjunto de tipo $(n, m)$" no depende del alfabeto $\Sigma$

Intente expresar esto en forma matemática

## Notación lambda

Usaremos la notación lambda de Church en la forma que se explica a continuación. Esta notación siempre depende de un alfabeto finito previamente fijado. En general en nuestro lenguaje matemático utilizamos diversas expresiones las cuales involucran variables que una vez fijadas en sus valores hacen que la expresión también represente un determinado valor u objeto.

En el contexto de la notación lambda solo se podrán utilizar expresiones con características muy especiales por lo cual a continuación iremos describiendo qué condiciones tienen que cumplir las expresiones para que puedan ser usadas en la notación lambda.

(1) Solo utilizaremos expresiones que involucran variables numéricas, las cuales se valuarán en números de $\omega$, y variables alfabéticas, las cuales se valuarán en palabras del alfabeto previamente fijado. Las variables numéricas serán seleccionadas de la lista

$$
\begin{gathered}
x, y, z, w, n, m, k, \ldots\\
x_1, x_2, \ldots\\
y_1, y_2, \ldots\\
\text{etc}
\end{gathered}
$$

Las variables alfabéticas serán seleccionadas de la lista

$$
\begin{gathered}
\alpha, \beta, \gamma, \eta, \ldots\\
\alpha_1, \alpha_2, \ldots\\
\beta_1, \beta_2, \ldots\\
\text{etc}
\end{gathered}
$$

(2) Por ejemplo la expresión:

$$
x + y + 1
$$

tiene dos variables numéricas $x$ e $y$ (y ninguna alfabética). Si le asignamos a $x$ el valor 2 y a $y$ el valor 45, entonces la expresión $x + y + 1$ produce o representa el valor $48 = 2 + 45 + 1$.

(3) Otro ejemplo, consideremos la expresión

$$
|\alpha\beta| + |\alpha|^x
$$

la cual tiene una variable numérica $x$ y dos variables alfabéticas $\alpha$ y $\beta$. Supongamos además que el alfabeto previamente fijado es $\{@, \%\}$. Si le asignamos a $x$ el valor 2, a $\alpha$ el valor `@@` y a $\beta$ el valor `%%%`, entonces la expresión $|\alpha\beta| + |\alpha|^x$ produce o representa el valor $|$`@@%%%`$| + |$`@@`$|^2 = 9$.

(4) Para ciertas valuaciones de sus variables la expresión puede no estar definida en el sentido que cuando reemplazamos en ella dichos valores la palabra obtenida no representa en forma precisa un objeto. Por ejemplo la expresión

$$
Pred(|\alpha|)
$$

cuando le asignamos a $\alpha$ la palabra $\varepsilon$, nos queda la expresión $Pred(|\varepsilon|)$ la cual no representa un objeto matemático en forma precisa. Otro ejemplo, consideremos la expresión

$$
x/(y - |\alpha|)^2
$$

Esta expresión no está definida o no asume valor para aquellas asignaciones de valores a sus variables en las cuales el valor asignado a $y$ sea igual a la longitud del valor asignado a $\alpha$. Un último ejemplo, la expresión

$$
x/y/z
$$

no está definida en forma precisa cuando le damos a $x, y, z$ los valores $100, 10, 5$ ya que nos queda la expresión $100/10/5$ la cual es imprecisa puesto que es ambigua ya que no sabemos en qué orden dividir.

(5) En los ejemplos anteriores las expresiones producen valores numéricos pero también trabajaremos con expresiones que producen valores alfabéticos. Por ejemplo la expresión

$$
\beta^y
$$

tiene una variable numérica, $y$, una variable alfabética, $\beta$, y una vez valuadas estas variables produce un valor alfabético, a saber el resultado de elevar el valor asignado a la variable $\beta$, al valor asignado a $y$.

(6) También consideraremos expresiones en las cuales no ocurren variables, es decir ellas representan un valor concreto. Por ejemplo la expresión

$$
5
$$

siempre produce el valor 5. O la expresión

$$
17 + 11
$$

siempre produce el valor 28. También la expresión

$$
1/0
$$

no tiene variables y además es siempre indefinida. Es decir no representa un valor u objeto.

(7) Una expresión $E$ para poder ser utilizada en la notación lambda relativa a un alfabeto $\Sigma$ deberá cumplir alguna de las dos siguientes propiedades

**(a)** los valores que asuma $E$ cuando hayan sido asignados valores de $\omega$ a sus variables numéricas y valores de $\Sigma^\ast$ a sus variables alfabéticas deberán ser siempre elementos de $\omega$

**(b)** los valores que asuma $E$ cuando hayan sido asignados valores de $\omega$ a sus variables numéricas y valores de $\Sigma^\ast$ a sus variables alfabéticas deberán ser siempre elementos de $\Sigma^\ast$

Cabe destacar que la expresión $E$ puede, para alguna asignación de valores de $\omega$ a sus variables numéricas y valores de $\Sigma^\ast$ a sus variables alfabéticas, no estar definida o representar en forma precisa algún objeto matemático.

(8) Por ejemplo la expresión

$$
x/2
$$

no cumple la propiedad dada en (7) ya que para ciertos valores de $\omega$ asignados a la variable $x$, la expresión da valores numéricos que se salen de $\omega$ por lo cual no cumple ni (a) ni (b).

(9) Otro ejemplo, si el alfabeto fijado es $\Sigma = \{@, \%\}$, entonces la expresión

$$
\text{@}^x\text{\$}^y
$$

no cumple la propiedad dada en (7) ya que por ejemplo cuando le asignamos a $x$ el valor 2 y a $y$ el valor 6, la expresión nos da la palabra `@@$$$$$$` la cual no pertenece a $\Sigma^\ast$ por lo cual no cumple ni (a) ni (b).

(10) No necesariamente las expresiones que usaremos en la notación lambda deben ser hechas como combinación de operaciones matemáticas conocidas. Muchas veces usaremos expresiones que involucran incluso lenguaje coloquial castellano. Por ejemplo la expresión

```text
el menor número primo que es mayor que x
```

Es claro que esta expresión para cada valor de $\omega$ asignado a la variable $x$ produce o representa un valor concreto de $\omega$. Otro ejemplo:

```text
el tercer símbolo de α
```

nótese que esta expresión, una vez fijado un alfabeto $\Sigma$, estará definida o producirá un valor solo cuando le asignamos a $\alpha$ una palabra de $\Sigma^\ast$ de longitud mayor o igual a 3.

(11) **Expresiones Booleanas.** A las expresiones Booleanas tales como

$$
x = y + 1 \text{ y } |\alpha| \le 22
$$

las pensaremos que asumen valores del conjunto $\{0, 1\} \subseteq \omega$. Por ejemplo la expresión anterior asume o produce el valor 1 cuando le asignamos a $x$ el valor 11, a $y$ el valor 10 y a $\alpha$ la palabra $\varepsilon$. Las expresiones Booleanas pensadas de esta forma podrán ser utilizadas en la notación lambda si es que también cumplen con las anteriores condiciones. Otro ejemplo

$$
11 = 17
$$

es una expresión Booleana que no tiene variables y siempre produce el valor 0.

(12) Seremos muy estrictos en lo que respecta a cuando "una expresión $E$ está definida (o representa o produce) en forma precisa un valor, para una valuación dada de sus variables". El criterio será similar al usado en la tómbola con los vofois en el sentido que la más mínima imprecisión ya implicará que para esa valuación la expresión no está definida. Algunos ejemplos:

**(a)** Consideremos la expresión

$$
0.Suc(z, z)
$$

Uno podría pensar que cualquiera sea el valor de $\omega$ asignado a la variable $z$, la expresión produce el valor 0, ya que cualquiera sea el valor de $Suc(z, z)$, al multiplicarlo por 0 nos dará 0. Sin embargo para nosotros la expresión $0.Suc(z, z)$ no estará definida en forma precisa cualquiera sea el valor que le asignemos a $z$ y esto es porque $Suc(z, z)$ tiene una imprecisión ya que $Suc$ no se aplica a pares ordenados.

**(b)** Consideremos la expresión

$$
0.(4/x/2)
$$

Esta expresión no estará definida en forma precisa para ningún valor de $x$ ya que la expresión $4/x/2$ es ambigua puesto que no aclara en qué orden se realizan las divisiones. Nótese que aunque al multiplicar por 0 podríamos pensar que la expresión produce siempre 0, optamos por convenir que la expresión nunca produce en forma precisa valores u objetos.

**(c)** Consideremos la expresión Booleana

$$
Pred(0) = 1 \text{ o } 5 \le x
$$

Uno podría pensar que esta expresión produce el valor 1 cuando le asignamos a $x$ un valor mayor o igual a 5 ya que independientemente de que signifique $Pred(0) = 1$ se hace verdadero que $5 \le x$ por lo cual será verdadero el "o" de ambos enunciados. Sin embargo esta expresión no está definida en forma precisa para ninguna asignación de valores a $x$ ya que $Pred(0)$ es una imprecisión que es parte de la expresión. (O sea sucede lo mismo que en los vofois).

**(d)** Consideremos la expresión Booleana

$$
(\forall t \in \emptyset)\ Pred(x).t \text{ es impar}
$$

Uno podría pensar que esta expresión produce el valor 1 independientemente de cuánto vale $x$ ya que debemos chequear que $Pred(x).t$ sea impar para 0 valores posibles de $t$. Sin embargo esta expresión no está definida en forma precisa para el caso en que hacemos valer 0 a $x$ ya que en este caso $Pred$ no está definida. Obviamente para cualquier valor de $\mathbf{N}$ que asignemos a $x$ la expresión produce en forma precisa el valor 1

**Expresiones lambdificables con respecto a $\Sigma$.** Dado un alfabeto $\Sigma$ a las expresiones que cumplan las características dadas anteriormente las llamaremos lambdificables con respecto a $\Sigma$. Nótese que este concepto es intuitivo y no un concepto matemáticamente definido en forma precisa. Más aún el concepto de expresión tampoco ha sido definido matemáticamente (aunque obviamente si sabemos que una expresión es una palabra de cierto alfabeto). Esto no nos traerá problemas para el uso notacional que las utilizaremos. Recién en las secciones de lógica veremos la matematización de ciertas expresiones (no las lambdificables) y nos servirá de ejemplo para imaginar cómo podríamos matematizar el concepto de expresión lambdificable.

Algunos ejemplos:

(E1) $x/2$ no es lambdificable con respecto a $\Sigma$ cualesquiera sea $\Sigma$

(E2) $\text{@}^x\text{\$}^y$ es lambdificable con respecto a `{@, $}` y no es lambdificable con respecto a `{@, #, %}`

(E3) $x = y + 1$ es lambdificable con respecto a $\Sigma$ cualesquiera sea $\Sigma$

(E4) la expresión

$$
\text{el menor número primo que es mayor que } x^{|\beta|}
$$

es lambdificable con respecto a $\Sigma$ cualesquiera sea $\Sigma$

(E5) la expresión

$$
5
$$

es lambdificable con respecto a $\Sigma$ cualesquiera sea $\Sigma$

(E6) la expresión

$$
Suc(x/20)
$$

es lambdificable con respecto a $\Sigma$ cualesquiera sea $\Sigma$. Nótese que esta expresión no está definida o no asume valor para aquellas asignaciones de valores a $x$ en las cuales $x/20$ no sea un elemento de $\omega$ ya que en estos casos $x/20$ no pertenece al dominio de $Suc$. Más concretamente dicha expresión está definida o produce un valor cuando le asignamos a $x$ un valor múltiplo de 20. Nótese que sin embargo, la expresión

$$
(x/20) + 1
$$

no es lambdificable con respecto a $\Sigma$ cualesquiera sea $\Sigma$ (por qué?).

**Definición de $\lambda x_1...x_n\alpha_1...\alpha_m [E]$.** Supongamos ya hemos fijado un alfabeto finito $\Sigma$ y supongamos $E$ es una expresión la cual es lambdificable con respecto a $\Sigma$. Sea $x_1, \ldots, x_n, \alpha_1, \ldots, \alpha_m$ (con $n, m \in \omega$) una lista de variables todas distintas tal que las variables numéricas que ocurren en $E$ están todas contenidas en la lista $x_1, \ldots, x_n$ y las variables alfabéticas que ocurren en $E$ están en la lista $\alpha_1, \ldots, \alpha_m$ (puede suceder que haya variables de la lista $x_1, \ldots, x_n, \alpha_1, \ldots, \alpha_m$ las cuales no ocurran en $E$). Entonces

$$
\lambda x_1...x_n\alpha_1...\alpha_m [E]
$$

denotará la función definida por:

(L1) El dominio de $\lambda x_1...x_n\alpha_1...\alpha_m [E]$ es el conjunto de las $(n + m)$-uplas $(k_1, \ldots, k_n, \beta_1, \ldots, \beta_m) \in \omega^n \times \Sigma^{\ast m}$ tales que $E$ está definida en forma precisa cuando le asignamos a cada $x_i$ el valor $k_i$ y a cada $\alpha_i$ el valor $\beta_i$.

(L2) $\lambda x_1...x_n\alpha_1...\alpha_m [E](k_1, \ldots, k_n, \beta_1, \ldots, \beta_m) =$ valor que asume, produce o representa $E$ cuando le asignamos a cada $x_i$ el valor $k_i$ y a cada $\alpha_i$ el valor $\beta_i$.

Nótese que por tener $E$ la propiedad (7) de más arriba, la función $\lambda x_1...x_n\alpha_1...\alpha_m [E]$ es $\Sigma$-mixta de tipo $(n, m, s)$ para algún $s \in \{\#, \ast\}$. También nótese que cuando $n = m = 0$ la expresión $E$ deberá no tener variables y $\lambda x_1...x_n\alpha_1...\alpha_m [E]$ pasará a ser $\lambda [E]$. Además $\lambda [E]$ será la función vacía cuando $E$ no produzca o represente un valor y en caso contrario $\lambda [E]$ tendrá dominio igual a $\{\diamond\}$. Algunos ejemplos:

**(a)** Supongamos fijamos el alfabeto `Σ = {@, ?, ¡}`. Entonces $\lambda x\alpha [\alpha^{2x}]$ es la función

$$
\begin{aligned}
\omega \times \{\text{@}, \text{?}, \text{¡}\}^\ast &\to \{\text{@}, \text{?}, \text{¡}\}^\ast\\
(x, \alpha) &\mapsto \alpha^{2x}
\end{aligned}
$$

Aquí el lector puede notar la dependencia de la notación lambda respecto del alfabeto fijado. Si en lugar de fijar `Σ = {@, ?, ¡}` hubiéramos fijado `Σ = {%}`, entonces $\lambda x\alpha [\alpha^{2x}]$ denotaría otra función, a saber

$$
\begin{aligned}
\omega \times \{\text{\%}\}^\ast &\to \{\text{\%}\}^\ast\\
(x, \alpha) &\mapsto \alpha^{2x}
\end{aligned}
$$

**(b)** Supongamos fijamos el alfabeto `Σ = {@, ?, ¡}`. Entonces $\lambda x\alpha [5]$ es la función

$$
\begin{aligned}
\omega \times \{\text{@}, \text{?}, \text{¡}\}^\ast &\to \omega\\
(x, \alpha) &\mapsto 5
\end{aligned}
$$

**(c)** Supongamos fijamos el alfabeto `Σ = {%, !}`. Entonces $\lambda\alpha\beta [\alpha\beta]$ es la función

$$
\begin{aligned}
\{\text{\%}, \text{!}\}^\ast \times \{\text{\%}, \text{!}\}^\ast &\to \{\text{\%}, \text{!}\}^\ast\\
(\alpha, \beta) &\mapsto \alpha\beta
\end{aligned}
$$

También tenemos que $\lambda\beta\alpha [\alpha\beta]$ es la función

$$
\begin{aligned}
\{\text{\%}, \text{!}\}^\ast \times \{\text{\%}, \text{!}\}^\ast &\to \{\text{\%}, \text{!}\}^\ast\\
(\beta, \alpha) &\mapsto \alpha\beta
\end{aligned}
$$

Nótese que estas funciones son distintas. Por ejemplo $\lambda\alpha\beta [\alpha\beta](\%, !) = \%!$ y $\lambda\beta\alpha [\alpha\beta](\%, !) = !\%$

**(d)** Independientemente de quién sea $\Sigma$ el alfabeto previamente fijado, tenemos que $\lambda xy[x + y]$ es la función

$$
\begin{aligned}
\omega^2 &\to \omega\\
(x, y) &\mapsto x + y
\end{aligned}
$$

También $\lambda xyzw[x + w]$ es la función

$$
\begin{aligned}
\omega^4 &\to \omega\\
(x, y, z, w) &\mapsto x + w
\end{aligned}
$$

**(e)** Supongamos fijamos el alfabeto `Σ = {@, ?, ¡}`. Entonces por la cláusula (L1) tenemos que el dominio de la función $\lambda xy\alpha\beta [Pred(|\alpha|) + Pred(y)]$ es

$$
D = \{(x, y, \alpha, \beta) \in \omega^2 \times \Sigma^{\ast 2} : |\alpha| \ge 1 \text{ y } y \ge 1\}
$$

Es decir que $\lambda xy\alpha\beta [Pred(|\alpha|) + Pred(y)]$ es la función

$$
\begin{aligned}
D &\to \omega\\
(x, y, \alpha, \beta) &\mapsto Pred(|\alpha|) + Pred(y)
\end{aligned}
$$

**(f)** Atentos a (11) de más arriba, la función $\lambda xy [x = y]$ es el predicado

$$
\begin{aligned}
\omega \times \omega &\to \omega\\
(x, y) &\mapsto
\begin{cases}
1 & \text{si } x = y\\
0 & \text{si } x \ne y
\end{cases}
\end{aligned}
$$

y $\lambda x\alpha [Pred(x) = |\alpha|]$ es el predicado

$$
\begin{aligned}
\mathbf{N} \times \Sigma^\ast &\to \omega\\
(x, \alpha) &\mapsto
\begin{cases}
1 & \text{si } Pred(x) = |\alpha|\\
0 & \text{si } Pred(x) \ne |\alpha|
\end{cases}
\end{aligned}
$$

También $\lambda\alpha\beta [\alpha = \beta]$ es el predicado

$$
\begin{aligned}
\Sigma^\ast \times \Sigma^\ast &\to \omega\\
(\alpha, \beta) &\mapsto
\begin{cases}
1 & \text{si } \alpha = \beta\\
0 & \text{si } \alpha \ne \beta
\end{cases}
\end{aligned}
$$

**(g)** Notar que para $S \subseteq \omega^n \times \Sigma^{\ast m}$ se tiene que $\chi_S^{\omega^n \times \Sigma^{\ast m}} = \lambda x_1...x_n\alpha_1...\alpha_m [(\overrightarrow{x}, \overrightarrow{\alpha}) \in S]$

**(h)** Como dijimos, la notación lambda depende del alfabeto previamente fijado, aunque para el caso en que la lista de variables que sigue a la letra $\lambda$ no tenga variables alfabéticas, la función representada no depende del alfabeto.

**(i)** La función $\lambda x [Suc(x/20)]$ es la siguiente función:

$$
\begin{aligned}
\{x \in \omega : 20 \text{ divide a } x\} &\to \omega\\
x &\mapsto x+1
\end{aligned}
$$

**(j)** La función $\lambda [5]$ es la función

$$
\begin{aligned}
\{\diamond\} &\to \omega\\
\diamond &\mapsto 5
\end{aligned}
$$

**(k)** La función $\lambda [1/0]$ es la función vacía, es decir $\lambda [1/0] = \emptyset$

**(l)** La función $\lambda [11 = 17]$ es la función

$$
\begin{aligned}
\{\diamond\} &\to \omega\\
\diamond &\mapsto 0
\end{aligned}
$$

**Algunos ejemplos sutiles.**

**(a)** La expresión

$$
Suc
$$

no es lambdificable respecto de cualquier alfabeto $\Sigma$. Esto es porque si bien cualesquiera sea el valor asignado a las variables, ella asume el valor $Suc$ (ya que no tiene variables), no cumple (6) de más arriba ya que $Suc$ no es un elemento de $\omega$ ni tampoco una palabra (es una función!)

**(b)** La expresión

$$
Suc + (|\beta| + 1)
$$

es lambdificable con respecto a $\Sigma$ cualesquiera sea $\Sigma$. Por ejemplo $\lambda x\beta[Suc+(|\beta| + 1)]$ es la función $\emptyset$, ya que la expresión $Suc + (|\beta| + 1)$ cualesquiera sean los valores de $x$ y $\beta$ no está definida.

**(c)** La expresión

$$
Suc + 1
$$

es lambdificable con respecto a $\Sigma$ cualesquiera sea $\Sigma$ ya que no está definida nunca y obtenemos entonces que $\lambda x_1...x_n\alpha_1...\alpha_m [Suc + 1]$ es la función $\emptyset$, cualesquiera sean las variables $x_1...x_n\alpha_1...\alpha_m$. En particular $\lambda[Suc+1] = \emptyset$.

**Ejercicio 15:** V o F o I, justifique

**(a)** La expresión

$$
|\alpha\#@@| + x
$$

no es lambdificable con respecto a $\{\#, \%\}$

**(b)** La expresión

$$
x + 1 = 1/3
$$

es lambdificable con respecto a $\Sigma$ cualquiera sea $\Sigma$

**(c)** La expresión

$$
\lambda x[x^2] + (|\beta| + 1)
$$

es lambdificable con respecto a $\Sigma$ cualquiera sea $\Sigma$

**Ejercicio 16:** V o F o I, justifique

**(a)** $\lambda xy[x + y] = \lambda yx[x + y]$

**(b)** Si $f : \Sigma^{\ast 2} \to \omega$, entonces $\lambda\alpha\beta[f(\alpha, \beta)] = \lambda\beta\alpha[f(\beta, \alpha)]$

**(c)** $\lambda xy\alpha\beta [Pred(|\alpha|) + Pred(y)]$ es la función

$$
\begin{aligned}
\{(x, y, \alpha, \beta) \in \omega^2 \times \Sigma^{\ast 2} : |\alpha|.y \ne 0\} &\to \omega\\
(x, y, \alpha, \beta) &\mapsto (|\alpha| + y) - 2
\end{aligned}
$$

**(d)** $D_{\lambda xy[x^2]} = \omega$

**(e)** $\lambda x[Pred(x).0] = C_0^{1,0}$

**(f)** $Suc = \lambda x[Suc]$

**(g)** $\lambda xy[x.y] \circ [\lambda xy[x.y], C_1^{2,0}] = \lambda xy[x.y]$

**(h)** Sea $\Sigma = \{\text{▽}, \text{□}\}$. Entonces

$$
\lambda\alpha\beta[\alpha = \text{□}\beta]
= \lambda\alpha\beta[\alpha = \beta] \circ
\left[
p_1^{0,2},
\lambda\alpha\beta[\alpha\beta] \circ
\left[d_{\text{□}} \circ C_\varepsilon^{0,0}, p_2^{0,2}\right]
\right]
$$

## Ordenes totales

Sea $A$ un conjunto. Recordemos que una relación binaria sobre $A$ es un subconjunto de $A^2$. Algunos ejemplos:

(E1) Sea $R = \{(1, 2), (2, 3)\}$. Entonces $R$ es una relación binaria sobre $\mathbf{N}$.

(E2) Sea $R = \{(x, y) \in \omega^2 : x \text{ divide a } y\}$. Entonces $R$ es una relación binaria sobre $\omega$.

(E3) Sea $R = \{(r, t) \in \mathbf{R}^2 : r \le t\}$. Entonces $R$ es una relación binaria sobre $\mathbf{R}$

(E4) $\emptyset$ es una relación binaria sobre $A$, cualesquiera sea el conjunto $A$.

(E5) Sea $R = \{(x, y) \in \omega^2 : x < y \text{ o } y = 0\}$. Entonces $R$ es una relación binaria sobre $\omega$

Nótese que si $R$ es una relación binaria sobre $A$ y $A \subseteq B$ entonces $R$ es una relación binaria sobre $B$. Por ejemplo las relaciones dadas en los ejemplos (E1), (E2), (E4) y (E5) también son relaciones binarias sobre $\mathbf{R}$

Como es usual, cuando $R$ sea una relación binaria sobre un conjunto $A$, algunas veces escribiremos $aRb$ en lugar de $(a, b) \in R$.

Recordemos que una relación binaria $R$ sobre un conjunto $A$ es llamada un orden parcial sobre $A$ si cumple las siguientes tres propiedades:

**Reflexividad** $xRx$, cualesquiera sea $x \in A$

**Transitividad** $xRy$ y $yRz$ implica $xRz$, cualesquiera sean $x, y, z \in A$

**Antisimetria** $xRy$ y $yRx$ implica $x = y$, cualesquiera sean $x, y \in A$

Algunos ejemplos:

(E1) $\{(r, t) \in \mathbf{R}^2 : r \le t\}$ es un orden parcial sobre $\mathbf{R}$, llamado el orden usual de $\mathbf{R}$

(E2) Sea $R = \{(1, 2), (1, 3), (1, 1), (2, 2), (3, 3)\}$. Entonces $R$ es un orden parcial sobre $\{1, 2, 3\}$

(E3) Sea $R = \{(S, T) \in \mathcal{P}(\omega)^2 : S \subseteq T\}$. Entonces $R$ es un orden parcial sobre $\mathcal{P}(\omega)$

(E4) $\{(x, y) \in \omega^2 : x \le y\}$ es un orden parcial sobre $\omega$.

(E5) Sea $R = \{(1, 1)\}$. Entonces $R$ es un orden parcial sobre $\{1\}$.

(E6) $\{(a, b) \in A^2 : a = b\}$ es un orden parcial sobre $A$, cualesquira sea el conjunto $A$

(E7) Sea $\le = \{(n, m) \in \mathbf{N}^2 : n \mid m\}$. Es fácil ver que $\le$ es un orden parcial sobre $\mathbf{N}$

Nótese que las relaciones dadas en (E1) y (E4) son distintas, además

**Ejercicio 17:** Es la relación dada en (E4) un orden parcial sobre $\mathbf{R}$?

Muchas veces denotaremos con $\le$ a una relación binaria que sea un orden parcial. Esto hace más intuitiva nuestra escritura pero siempre hay que tener en cuenta que $\le$ en estos casos está denotando cierto conjunto de pares ordenados previamente definido.

Usaremos la siguiente

**Convención notacional** Si hemos denotado con $\le$ a cierto orden parcial sobre un conjunto $A$, entonces

- Denotaremos con $<$ a la relación binaria $\{(a, b) \in A^2 : a \le b \text{ y } a \ne b\}$. Es decir que $< = \{(a, b) \in A^2 : a \le b \text{ y } a \ne b\}$. Cuando se dé $a < b$ diremos que $a$ es menor que $b$ o que $b$ es mayor que $a$ (respecto de $\le$)

Por ejemplo, si $A = \{1, 2, 3, 4\}$ y $\le = \{(1, 2), (2, 3), (1, 3), (1, 1), (2, 2), (3, 3), (4, 4)\}$, entonces $< = \{(1, 2), (2, 3), (1, 3)\}$.

Ahora sí estamos en condiciones de definir orden total. Sea $A$ un conjunto cualquiera. Por un orden total sobre $A$ entenderemos un orden parcial $\le$ sobre $A$ el cual cumple:

(C) $a \le b$ o $b \le a$, cualesquiera sean $a, b \in A$

**Ejercicio 18:** Decida cuáles órdenes parciales de la lista de ejemplos (E1)-(E7) son órdenes totales.

Supongamos $A$ es finito, no vacío, y que $\le$ es un orden total sobre $A$. La propiedad (C) nos permite probar que para cada conjunto no vacío $S \subseteq A$, hay un elemento $s \in S$ el cual cumple $s \le s'$ para cada $s' \in S$. Por supuesto, $s$ es único (por qué?) y habitualmente es llamado el menor elemento de $S$, ya que es menor que todo otro elemento de $S$.

Si $A$ es finito, no vacío, y $\le$ es un orden total sobre $A$, podemos definir recursivamente una función $f : \{1, \ldots, |A|\} \to A$ de la siguiente manera:

- $f(1) =$ menor elemento de $A$
- Si $i \in \{1, \ldots, |A|-1\}$, entonces
- $f(i+1) =$ menor elemento de $A - \{f(1), \ldots, f(i)\}$

Como es habitual, $f(i)$ es llamado el $i$-ésimo elemento de $A$.

Muchas veces para dar un orden total sobre un conjunto finito $A$, daremos simplemente sus elementos en forma creciente ya que esto determina el orden por completo. Por ejemplo si $A = \{1, 2, 3\}$, el orden total dado por $2 < 1 < 3$ es la relación $\le = \{(2, 1), (1, 3), (2, 3), (1, 1), (2, 2), (3, 3)\}$.

**Ejercicio 19:** Sea $A$ un conjunto finito de $n$ elementos, con $n > 0$. Encuentre una biyección entre $\{R : R \text{ es un orden total sobre } A\}$ y $\{(a_1, \ldots, a_n) \in A^n : a_i \ne a_j \text{ para } i \ne j\}$. ¿Por qué este resultado se puede considerar informático?
