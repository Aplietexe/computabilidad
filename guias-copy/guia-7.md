# GUÍA 7 DE LENGUAJES: EL PARADIGMA IMPERATIVO DE NEUMANN

En esta sección daremos una modelización matemática del concepto de función \(\Sigma\)-efectivamente computable utilizando un lenguaje de programación teórico el cual depende del alfabeto \(\Sigma\). Lo llamaremos \(S^\Sigma\) a dicho lenguaje. Dado que fue el matemático Von Neumann quien contribuyó al desarrollo de la primera computadora de propósito general (es decir a la cual se le pueden hacer correr programas tal como a las computadoras actuales), nos referiremos a este paradigma de computabilidad efectiva como el paradigma de Von Neumann. También lo llamaremos algunas veces el paradigma imperativo.

## Sintaxis de \(S^\Sigma\)

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

Nótese que para \(n\in\mathbf{N}\), la palabra \(Dec(n)\) es la notación usual decimal de \(n\). Para hacer más ágil la notación escribiremos \(\overline{n}\) en lugar de \(Dec(n)\).

La sintaxis de \(S^\Sigma\) será dada utilizando solo símbolos del alfabeto \(\Sigma\cup\Sigma_p\), donde

\[
\Sigma_p=Num\cup\{\leftarrow,+,\mathbin{\dot{-}},.,\ne,\curvearrowright,\varepsilon,\mathrm{N},\mathrm{K},\mathrm{P},\mathrm{L},\mathrm{I},\mathrm{F},\mathrm{G},\mathrm{O},\mathrm{T},\mathrm{B},\mathrm{E},\mathrm{S}\}.
\]

Cabe aclarar que la palabra de longitud \(0\) no es un elemento de \(\Sigma_p\) sino que la letra griega \(\varepsilon\) que usualmente denota esta palabra, lo es. También nótese que en \(\Sigma_p\) hay símbolos que a veces representan operaciones como por ejemplo \(+\), \(\curvearrowright\) y \(\mathbin{\dot{-}}\), pero debería quedar claro que en \(\Sigma_p\) están los símbolos \(+\), \(\curvearrowright\) y \(\mathbin{\dot{-}}\) y no las operaciones que ellos usualmente denotan.

Las palabras de la forma \(\mathrm{N}\overline{k}\), con \(k\in\mathbf{N}\), son llamadas variables numéricas de \(S^\Sigma\). Las palabras de la forma \(\mathrm{P}\overline{k}\), con \(k\in\mathbf{N}\), son llamadas variables alfabéticas de \(S^\Sigma\). Las palabras de la forma \(\mathrm{L}\overline{k}\), con \(k\in\mathbf{N}\), son llamadas labels de \(S^\Sigma\). Una instrucción básica de \(S^\Sigma\) es una palabra de \((\Sigma\cup\Sigma_p)^\ast\) la cual es de alguna de las siguientes formas

\[
\begin{array}{l}
\mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{k}+1\\
\mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{k}\mathbin{\dot{-}}1\\
\mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{n}\\
\mathrm{N}\overline{k}\leftarrow 0\\
\mathrm{P}\overline{k}\leftarrow \mathrm{P}\overline{k}.a\\
\mathrm{P}\overline{k}\leftarrow \curvearrowright \mathrm{P}\overline{k}\\
\mathrm{P}\overline{k}\leftarrow \mathrm{P}\overline{n}\\
\mathrm{P}\overline{k}\leftarrow \varepsilon\\
\mathrm{IF}\ \mathrm{N}\overline{k}\ne 0\ \mathrm{GOTO}\ \mathrm{L}\overline{n}\\
\mathrm{IF}\ \mathrm{P}\overline{k}\ \mathrm{BEGINS}\ a\ \mathrm{GOTO}\ \mathrm{L}\overline{n}\\
\mathrm{GOTO}\ \mathrm{L}\overline{n}\\
\mathrm{SKIP}
\end{array}
\]

donde \(a\in\Sigma\) y \(k,n\in\mathbf{N}\). Como puede observarse para que las instrucciones básicas sean más legibles usamos espacios entre ciertos símbolos. Por ejemplo, hemos escrito \(\mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{k}+1\) pero en realidad nos referimos a la palabra

\[
\mathrm{N}\overline{k}\leftarrow\mathrm{N}\overline{k}+1
\]

cuya longitud es \(2|\overline{k}|+5\). Otro ejemplo, hemos escrito \(\mathrm{IF}\ \mathrm{P}\overline{k}\ \mathrm{BEGINS}\ a\ \mathrm{GOTO}\ \mathrm{L}\overline{n}\) pero en realidad nos referíamos a la palabra \(\mathrm{IFP}\overline{k}\mathrm{BEGINS}a\mathrm{GOTOL}\overline{n}\) cuya longitud es \(|\overline{k}|+|\overline{n}|+15\).

Una instrucción de \(S^\Sigma\) es ya sea una instrucción básica de \(S^\Sigma\) o una palabra de la forma \(\alpha I\), donde \(\alpha\in\{\mathrm{L}\overline{n}:n\in\mathbf{N}\}\) y \(I\) es una instrucción básica de \(S^\Sigma\). Usaremos \(Ins^\Sigma\) para denotar el conjunto de todas las instrucciones de \(S^\Sigma\). Cuando la instrucción \(I\) es de la forma \(\mathrm{L}\overline{n}J\) con \(J\) una instrucción básica, diremos que \(\mathrm{L}\overline{n}\) es el label de \(I\).

**Ejercicio 1:** V o F o I, justificar

**(a)** Para cada \(n\in\mathbf{N}\), se tiene que \(\overline{n}\in\omega\)

**(b)** Si \(k\in\mathbf{N}\), entonces \(\mathrm{P}\overline{k}\leftarrow\) es una instrucción de \(S^\Sigma\)

**(c)** Sea \(\Sigma\) un alfabeto. Entonces \(Ins^\Sigma\) es un conjunto \(\Sigma\)-mixto

**(d)** \(Ti(Ins^\Sigma)=PALABRA\)

**(e)** Si \(I\in Ins^\Sigma\), entonces \(Ti(I)=PALABRA\)

**(f)** Si \(I\) es una instrucción de \(S^\Sigma\) y \(n\in\mathbf{N}\) es tal que \(\mathrm{L}\overline{n}\) es tramo inicial de \(I\), entonces \(\mathrm{L}\overline{n}\) es el label de \(I\).

Damos a continuación, a modo de ejemplo, la interpretación intuitiva asociada a ciertas instrucciones básicas de \(S^\Sigma\):

\[
\begin{array}{ll}
\mathrm{INSTRUCCIÓN}:& \mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{k}\mathbin{\dot{-}}1\\
\mathrm{INTERPRETACIÓN}:& \text{Si el contenido de }\mathrm{N}\overline{k}\text{ es }0\text{ dejarlo sin modificar;}\\
& \text{en caso contrario disminuya en }1\text{ el contenido de }\mathrm{N}\overline{k}\\[3pt]
\mathrm{INSTRUCCIÓN}:& \mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{n}\\
\mathrm{INTERPRETACIÓN}:& \text{Copiar en }\mathrm{N}\overline{k}\text{ el contenido de }\mathrm{N}\overline{n}\\
& \text{sin modificar el contenido de }\mathrm{N}\overline{n}\\[3pt]
\mathrm{INSTRUCCIÓN}:& \mathrm{P}\overline{k}\leftarrow\curvearrowright \mathrm{P}\overline{k}\\
\mathrm{INTERPRETACIÓN}:& \text{Si el contenido de }\mathrm{P}\overline{k}\text{ es }\varepsilon\text{ dejarlo sin modificar;}\\
& \text{en caso contrario remueva el }1\mathrm{er}\text{ símbolo del}\\
& \text{contenido de }\mathrm{P}\overline{k}\\[3pt]
\mathrm{INSTRUCCIÓN}:& \mathrm{P}\overline{k}\leftarrow \mathrm{P}\overline{k}.a\\
\mathrm{INTERPRETACIÓN}:& \text{Modificar el contenido de }\mathrm{P}\overline{k}\text{ agregandole}\\
& \text{el símbolo }a\text{ a la derecha}\\[3pt]
\mathrm{INSTRUCCIÓN}:& \mathrm{IF}\ \mathrm{P}\overline{k}\ \mathrm{BEGINS}\ a\ \mathrm{GOTO}\ \mathrm{L}\overline{m}\\
\mathrm{INTERPRETACIÓN}:& \text{Si el contenido de }\mathrm{P}\overline{k}\text{ comienza con }a,\text{ ejecute}\\
& \text{la primera instrucción con label }\mathrm{L}\overline{m};\text{ en caso}\\
& \text{contrario ejecute la siguiente instrucción.}
\end{array}
\]

Un programa de \(S^\Sigma\) es una palabra de la forma

\[
I_1 I_2\cdots I_n
\]

donde \(n\ge 1\), \(I_1,\ldots,I_n\in Ins^\Sigma\) y además se cumple la siguiente propiedad, llamada la ley de los GOTO,

**(G)** Para cada \(i\in\{1,\ldots,n\}\), si \(\mathrm{GOTOL}\overline{m}\) es un tramo final de \(I_i\), entonces existe \(j\in\{1,\ldots,n\}\) tal que \(I_j\) tiene label \(\mathrm{L}\overline{m}\).

Usaremos \(Pro^\Sigma\) para denotar el conjunto de todos los programas de \(S^\Sigma\). Como es usual cuando escribamos un programa lo haremos línea por línea, con la finalidad de que sea más legible. Por ejemplo, escribiremos

\[
\begin{array}{ll}
\mathrm{L}2 & \mathrm{N}12\leftarrow \mathrm{N}12\mathbin{\dot{-}}1\\
& \mathrm{P}1\leftarrow \curvearrowright \mathrm{P}1\\
& \mathrm{IF}\ \mathrm{N}12\ne 0\ \mathrm{GOTO}\ \mathrm{L}2
\end{array}
\]

en lugar de

\[
\mathrm{L}2\mathrm{N}12\leftarrow\mathrm{N}12\mathbin{\dot{-}}1\mathrm{P}1\leftarrow\curvearrowright \mathrm{P}1\mathrm{IFN}12\ne0\mathrm{GOTOL}2
\]

Un importante resultado es el siguiente lema que garantiza que los programas pueden ser parseados en forma única como concatenación de instrucciones. Lo aceptaremos sin demostración, en el apunte está probado.

**Lema 1.** Sea \(\Sigma\) un alfabeto finito. Se tiene que:

**(a)** Si \(I_1\cdots I_n=J_1\cdots J_m\), con \(I_1,\ldots,I_n,J_1,\ldots,J_m\in Ins^\Sigma\), entonces \(n=m\) y \(I_j=J_j\) para cada \(j\ge 1\).

**(b)** Si \(\mathcal{P}\in Pro^\Sigma\), entonces existe una única sucesión de instrucciones \(I_1,\ldots,I_n\) tal que \(\mathcal{P}=I_1\cdots I_n\).

**(b)** del lema anterior nos dice que dado un programa \(\mathcal{P}\), tenemos unívocamente determinados \(n(\mathcal{P})\in\mathbf{N}\) y \(I_1^\mathcal{P},\ldots,I_{n(\mathcal{P})}^\mathcal{P}\in Ins^\Sigma\) tales que \(\mathcal{P}=I_1^\mathcal{P}\cdots I_{n(\mathcal{P})}^\mathcal{P}\). Definamos también

\[
I_i^\mathcal{P}=\varepsilon
\]

cuando \(i=0\) o \(i>n(\mathcal{P})\). Nótese que las expresiones \(n(\alpha)\) y \(I_i^\alpha\) están definidas solo cuando \(\alpha\) es un programa (y \(i\) es un elemento de \(\omega\)), es decir, cierta palabra del alfabeto \(\Sigma\cup\Sigma_p\). O sea que cuando usemos notación lambda que involucre dichas expresiones, el alfabeto respecto del cual usaremos dicha notación será \(\Sigma\cup\Sigma_p\). Esto nos dice entonces que \(\lambda\alpha[n(\alpha)]\) tiene dominio igual a \(Pro^\Sigma\subseteq(\Sigma\cup\Sigma_p)^\ast\) y \(\lambda i\alpha[I_i^\alpha]\) tiene dominio igual a \(\omega\times Pro^\Sigma\). Para hacer más sugestiva la notación a veces escribiremos \(\lambda\mathcal{P}[n(\mathcal{P})]\) y \(\lambda i\mathcal{P}[I_i^\mathcal{P}]\) en lugar de \(\lambda\alpha[n(\alpha)]\) y \(\lambda i\alpha[I_i^\alpha]\).

**Ejercicio 2:** V o F o I, justificar

**(a)** \(Ins^\Sigma\subseteq Pro^\Sigma\)

**(b)** \(Ins^\Sigma\cap Pro^\Sigma=\emptyset\)

**(c)** \(\lambda i\mathcal{P}[I_i^\mathcal{P}]\) tiene dominio igual a \(\{(i,\mathcal{P})\in\mathbf{N}\times Pro^\Sigma:i\le n(\mathcal{P})\}\)

**(d)** Sea \(\Sigma\) un alfabeto. Si \(\mathcal{P}\in Pro^\Sigma\), entonces \(\mathcal{P}\in\underbrace{Ins^\Sigma\times\cdots\times Ins^\Sigma}_{n(\mathcal{P})\ \text{veces}}\)

**Ejercicio 3:** Si \(\mathcal{P}_1,\mathcal{P}_2\in Pro^\Sigma\) y \(\mathcal{P}_1\mathcal{P}_1=\mathcal{P}_2\mathcal{P}_2\), entonces \(\mathcal{P}_1=\mathcal{P}_2\).

## Semántica de \(S^\Sigma\)

Para definir la semántica nos será útil la función \(Bas:Ins^\Sigma\to(\Sigma\cup\Sigma_p)^\ast\), dada por

\[
Bas(I)=
\begin{cases}
J & \text{si }I\text{ es de la forma }\mathrm{L}\overline{k}J\text{ con }J\in Ins^\Sigma,\\
I & \text{caso contrario.}
\end{cases}
\]

Recordemos que para una palabra \(\alpha\) definíamos

\[
\curvearrowright\alpha=
\begin{cases}
[\alpha]_2\cdots[\alpha]_{|\alpha|} & \text{si }|\alpha|\ge 2,\\
\varepsilon & \text{si }|\alpha|\le 1.
\end{cases}
\]

Definamos

\[
\omega^{[\mathbf{N}]}=\{(s_1,s_2,\ldots)\in\omega^\mathbf{N}:\text{ hay }n\in\mathbf{N}\text{ tal que }s_i=0,\text{ para }i\ge n\}
\]

\[
\Sigma^{\ast[\mathbf{N}]}=\{(\sigma_1,\sigma_2,\ldots)\in\Sigma^{\ast\mathbf{N}}:\text{ hay }n\in\mathbf{N}\text{ tal que }\sigma_i=\varepsilon,\text{ para }i\ge n\}.
\]

Asumiremos siempre que en una computación vía un programa de \(S^\Sigma\), todas excepto una cantidad finita de las variables numéricas tienen el valor \(0\) y todas excepto una cantidad finita de las variables alfabéticas tienen el valor \(\varepsilon\). Esto no quita generalidad a nuestra modelización del funcionamiento de los programas ya que todo programa envuelve una cantidad finita de variables.

Un estado es un par

\[
(\overrightarrow{s},\overrightarrow{\sigma})=((s_1,s_2,\ldots),(\sigma_1,\sigma_2,\ldots))\in\omega^{[\mathbf{N}]}\times\Sigma^{\ast[\mathbf{N}]}.
\]

Si \(i\ge 1\), entonces diremos que \(s_i\) es el contenido o valor de la variable \(\mathrm{N}\overline{i}\) en el estado \((\overrightarrow{s},\overrightarrow{\sigma})\) y \(\sigma_i\) es el contenido o valor de la variable \(\mathrm{P}\overline{i}\) en el estado \((\overrightarrow{s},\overrightarrow{\sigma})\). Es decir, intuitivamente hablando, un estado es un par de infinituplas que contiene la información de que valores tienen alojados las distintas variables.

Imaginemos que corremos un programa \(\mathcal{P}\) partiendo de un estado inicial \((\overrightarrow{s},\overrightarrow{\sigma})\). Por supuesto la primera instrucción a realizar será \(I_1^\mathcal{P}\) pero, dado que \(I_1^\mathcal{P}\) puede ser de tipo GOTO, la segunda instrucción que realizaremos puede no ser \(I_2^\mathcal{P}\). Es decir en cada paso iremos decidiendo en función de la instrucción ejecutada cuál es la siguiente instrucción a realizar. O sea que mientras corremos \(\mathcal{P}\), en cada paso la información importante a tener en cuenta es, por una parte, cuáles son los valores que tienen cada una de las variables y, por otra parte, cuál es la instrucción que nos tocará realizar a continuación. Esto da lugar al concepto de descripción instantánea, a saber, un objeto matemático que describe en un instante dado de la computación cuáles son los valores de las variables y cuál es la instrucción que se debe realizar en el instante siguiente. Más formalmente una descripción instantánea es una terna \((i,\overrightarrow{s},\overrightarrow{\sigma})\) tal que \((\overrightarrow{s},\overrightarrow{\sigma})\) es un estado e \(i\in\omega\). Es decir que \(\omega\times\omega^{[\mathbf{N}]}\times\Sigma^{\ast[\mathbf{N}]}\) es el conjunto formado por todas las descripciones instantáneas. Intuitivamente hablando, cuando \(i\in\{1,\ldots,n(\mathcal{P})\}\), la descripción instantánea \((i,\overrightarrow{s},\overrightarrow{\sigma})\) nos dice que las variables están en el estado \((\overrightarrow{s},\overrightarrow{\sigma})\) y que la instrucción que debemos realizar es \(I_i^\mathcal{P}\). Dado que será conveniente para simplificar el tratamiento formal, nos abstraeremos un poco y cuando \(i=0\) o \(i>n(\mathcal{P})\) pensaremos también que la descripción instantánea \((i,\overrightarrow{s},\overrightarrow{\sigma})\) nos dice que las variables están en el estado \((\overrightarrow{s},\overrightarrow{\sigma})\) y que debemos realizar \(I_i^\mathcal{P}=\varepsilon\) (aunque por supuesto no podremos realizarla ya que no es una instrucción).

Dado un programa \(\mathcal{P}\) definiremos a continuación una función

\[
S_\mathcal{P}:\omega\times\omega^{[\mathbf{N}]}\times\Sigma^{\ast[\mathbf{N}]}\to\omega\times\omega^{[\mathbf{N}]}\times\Sigma^{\ast[\mathbf{N}]}
\]

la cual le asignará a una descripción instantánea \((i,\overrightarrow{s},\overrightarrow{\sigma})\) la descripción instantánea sucesora de \((i,\overrightarrow{s},\overrightarrow{\sigma})\) con respecto a \(\mathcal{P}\). Cuando \(i\in\{1,\ldots,n(\mathcal{P})\}\), intuitivamente hablando, \(S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})\) será la descripción instantánea que resulta luego de realizar \(I_i^\mathcal{P}\) estando en el estado \((\overrightarrow{s},\overrightarrow{\sigma})\). Cuando \(i=0\) o \(i>n(\mathcal{P})\) definiremos \(S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i,\overrightarrow{s},\overrightarrow{\sigma})\), lo cual es bastante intuitivo ya que si estamos en estado \((\overrightarrow{s},\overrightarrow{\sigma})\) y debemos realizar \(I_i^\mathcal{P}=\varepsilon\), dado que \(\varepsilon\) no es una instrucción y por lo tanto no la podremos realizar, seguiremos en el mismo estado y teniendo que realizar \(I_i^\mathcal{P}\).

Para darle una semántica más unificada al concepto de descripción instantánea sucesora debemos crear un nuevo verbo. El verbo "realizarp". Dada una actividad \(A\), diremos que un individuo \(P\) realizap la actividad \(A\), si \(P\) realiza \(A\), en caso de que pueda hacerlo. O sea realizarp una actividad es realizarla si se puede.

Para dar otro ejemplo de este tipo de verbos, consideremos el verbo "comprarp", es decir "comprar si se puede". Un hijo le pide a su padre que le compre un determinado juguete y el padre le dice "sí, hijo mío, te lo voy a comprarp". Luego el padre es despedido de su empleo y su situación económica hace que no le sea posible comprar dicho juguete. Sin embargo el padre no mintió ya que si bien no compró dicho juguete, él sí lo comprop.

Con este verbo podemos describir intuitivamente \(S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})\):

\[
\begin{aligned}
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})={}&
\text{descripción instantánea que resulta}\\
&\text{luego de realizarp }I_i^\mathcal{P},\text{ estando en estado }(\overrightarrow{s},\overrightarrow{\sigma})
\end{aligned}
\]

Ahora sí, daremos la definición matemática de \(S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})\), según se den distintos casos posibles.

Caso \(i\notin\{1,\ldots,n(\mathcal{P})\}\). Entonces \(S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i,\overrightarrow{s},\overrightarrow{\sigma})\).

Caso \(Bas(I_i^\mathcal{P})=\mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{k}\mathbin{\dot{-}}1\). Entonces

\[
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,(s_1,\ldots,s_{k-1},s_k\mathbin{\dot{-}}1,s_{k+1},\ldots),\overrightarrow{\sigma})
\]

Caso \(Bas(I_i^\mathcal{P})=\mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{k}+1\). Entonces

\[
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,(s_1,\ldots,s_{k-1},s_k+1,s_{k+1},\ldots),\overrightarrow{\sigma})
\]

Caso \(Bas(I_i^\mathcal{P})=\mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{n}\). Entonces

\[
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,(s_1,\ldots,s_{k-1},s_n,s_{k+1},\ldots),\overrightarrow{\sigma})
\]

Caso \(Bas(I_i^\mathcal{P})=\mathrm{N}\overline{k}\leftarrow 0\). Entonces

\[
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,(s_1,\ldots,s_{k-1},0,s_{k+1},\ldots),\overrightarrow{\sigma})
\]

Caso \(Bas(I_i^\mathcal{P})=\mathrm{IF}\ \mathrm{N}\overline{k}\ne0\ \mathrm{GOTO}\ \mathrm{L}\overline{m}\). Entonces tenemos dos subcasos.

Subcaso a. El valor de \(\mathrm{N}\overline{k}\) en \((\overrightarrow{s},\overrightarrow{\sigma})\) es \(0\). Entonces

\[
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,\overrightarrow{s},\overrightarrow{\sigma})
\]

Subcaso b. El valor de \(\mathrm{N}\overline{k}\) en \((\overrightarrow{s},\overrightarrow{\sigma})\) es no nulo. Entonces

\[
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(\min\{l:I_l^\mathcal{P}\text{ tiene label }\mathrm{L}\overline{m}\},\overrightarrow{s},\overrightarrow{\sigma})
\]

Caso \(Bas(I_i^\mathcal{P})=\mathrm{P}\overline{k}\leftarrow \curvearrowright\mathrm{P}\overline{k}\). Entonces

\[
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,\overrightarrow{s},(\sigma_1,\ldots,\sigma_{k-1},\curvearrowright\sigma_k,\sigma_{k+1},\ldots))
\]

Caso \(Bas(I_i^\mathcal{P})=\mathrm{P}\overline{k}\leftarrow \mathrm{P}\overline{k}.a\). Entonces

\[
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,\overrightarrow{s},(\sigma_1,\ldots,\sigma_{k-1},\sigma_k a,\sigma_{k+1},\ldots))
\]

Caso \(Bas(I_i^\mathcal{P})=\mathrm{P}\overline{k}\leftarrow \mathrm{P}\overline{n}\). Entonces

\[
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,\overrightarrow{s},(\sigma_1,\ldots,\sigma_{k-1},\sigma_n,\sigma_{k+1},\ldots))
\]

Caso \(Bas(I_i^\mathcal{P})=\mathrm{P}\overline{k}\leftarrow \varepsilon\). Entonces

\[
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,\overrightarrow{s},(\sigma_1,\ldots,\sigma_{k-1},\varepsilon,\sigma_{k+1},\ldots))
\]

Caso \(Bas(I_i^\mathcal{P})=\mathrm{IF}\ \mathrm{P}\overline{k}\ \mathrm{BEGINS}\ a\ \mathrm{GOTO}\ \mathrm{L}\overline{m}\). Entonces tenemos dos subcasos.

Subcaso a. El valor de \(\mathrm{P}\overline{k}\) en \((\overrightarrow{s},\overrightarrow{\sigma})\) comienza con \(a\). Entonces

\[
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(\min\{l:I_l^\mathcal{P}\text{ tiene label }\mathrm{L}\overline{m}\},\overrightarrow{s},\overrightarrow{\sigma})
\]

Subcaso b. El valor de \(\mathrm{P}\overline{k}\) en \((\overrightarrow{s},\overrightarrow{\sigma})\) no comienza con \(a\). Entonces

\[
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,\overrightarrow{s},\overrightarrow{\sigma})
\]

Caso \(Bas(I_i^\mathcal{P})=\mathrm{GOTO}\ \mathrm{L}\overline{m}\). Entonces

\[
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(\min\{l:I_l^\mathcal{P}\text{ tiene label }\mathrm{L}\overline{m}\},\overrightarrow{s},\overrightarrow{\sigma})
\]

Caso \(Bas(I_i^\mathcal{P})=\mathrm{SKIP}\). Entonces

\[
S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i+1,\overrightarrow{s},\overrightarrow{\sigma})
\]

**La computación partiendo de un estado.** Dado un programa \(\mathcal{P}\) y un estado \((\overrightarrow{s},\overrightarrow{\sigma})\) a la infinitupla

\[
((1,\overrightarrow{s},\overrightarrow{\sigma}),S_\mathcal{P}(1,\overrightarrow{s},\overrightarrow{\sigma}),S_\mathcal{P}(S_\mathcal{P}(1,\overrightarrow{s},\overrightarrow{\sigma})),S_\mathcal{P}(S_\mathcal{P}(S_\mathcal{P}(1,\overrightarrow{s},\overrightarrow{\sigma}))),\ldots)
\]

la llamaremos la computación de \(\mathcal{P}\) partiendo del estado \((\overrightarrow{s},\overrightarrow{\sigma})\). Diremos que

\[
\underbrace{S_\mathcal{P}(\cdots S_\mathcal{P}(S_\mathcal{P}(1,\overrightarrow{s},\overrightarrow{\sigma}))\cdots)}_{t\ \text{veces}}
\]

es la descripción instantánea obtenida luego de \(t\) pasos, partiendo del estado \((\overrightarrow{s},\overrightarrow{\sigma})\). Si

\[
\underbrace{S_\mathcal{P}(\cdots S_\mathcal{P}(S_\mathcal{P}(1,\overrightarrow{s},\overrightarrow{\sigma}))\cdots)}_{t\ \text{veces}}=(j,\overrightarrow{u},\overrightarrow{\eta})
\]

diremos que \((\overrightarrow{u},\overrightarrow{\eta})\) es el estado obtenido luego de \(t\) pasos, partiendo del estado \((\overrightarrow{s},\overrightarrow{\sigma})\).

Es claro que en la infinitupla de más arriba está toda la información de la "corrida" del programa \(\mathcal{P}\) cuando partimos del estado \((\overrightarrow{s},\overrightarrow{\sigma})\). Veamos un ejemplo. Sea \(\Sigma=\{\blacktriangle,\#\}\) y sea \(\mathcal{P}\) el siguiente programa

\[
\begin{array}{ll}
\mathrm{L}3 & \mathrm{N}4\leftarrow \mathrm{N}4+1\\
& \mathrm{P}1\leftarrow \curvearrowright \mathrm{P}1\\
& \mathrm{IF}\ \mathrm{P}1\ \mathrm{BEGINS}\ \blacktriangle\ \mathrm{GOTO}\ \mathrm{L}3\\
& \mathrm{P}3\leftarrow \mathrm{P}3.\#
\end{array}
\]

Supongamos que tomamos \((\overrightarrow{s},\overrightarrow{\sigma})\) igual al estado

\[
((2,1,0,5,3,0,0,0,\ldots),(\#\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))
\]

Tendremos entonces que la computación de \(\mathcal{P}\) partiendo del estado \((\overrightarrow{s},\overrightarrow{\sigma})\) es la infinitupla formada por la siguiente sucesión (de arriba hacia abajo) de descripciones instantáneas:

\[
\begin{array}{c}
(1,(2,1,0,5,3,0,0,0,\ldots),(\#\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_1^\mathcal{P}=\mathrm{N}4\leftarrow \mathrm{N}4+1\text{ obtenemos}\\
(2,(2,1,0,6,3,0,0,0,\ldots),(\#\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_2^\mathcal{P}=\mathrm{P}1\leftarrow\curvearrowright \mathrm{P}1\text{ obtenemos}\\
(3,(2,1,0,6,3,0,0,0,\ldots),(\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_3^\mathcal{P}=\mathrm{IF}\ \mathrm{P}1\ \mathrm{BEGINS}\ \blacktriangle\ \mathrm{GOTO}\ \mathrm{L}3\text{ obtenemos}\\
(1,(2,1,0,6,3,0,0,0,\ldots),(\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_1^\mathcal{P}=\mathrm{N}4\leftarrow \mathrm{N}4+1\text{ obtenemos}\\
(2,(2,1,0,7,3,0,0,0,\ldots),(\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_2^\mathcal{P}=\mathrm{P}1\leftarrow\curvearrowright \mathrm{P}1\text{ obtenemos}\\
(3,(2,1,0,7,3,0,0,0,\ldots),(\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_3^\mathcal{P}=\mathrm{IF}\ \mathrm{P}1\ \mathrm{BEGINS}\ \blacktriangle\ \mathrm{GOTO}\ \mathrm{L}3\text{ obtenemos}\\
(4,(2,1,0,7,3,0,0,0,\ldots),(\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_4^\mathcal{P}=\mathrm{P}3\leftarrow \mathrm{P}3.\#\text{ obtenemos}\\
(5,(2,1,0,7,3,0,0,0,\ldots),(\#\#,\varepsilon,\blacktriangle\blacktriangle\#,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{intentando realizar }I_5^\mathcal{P}=\varepsilon\text{ obtenemos}\\
(5,(2,1,0,7,3,0,0,0,\ldots),(\#\#,\varepsilon,\blacktriangle\blacktriangle\#,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{intentando realizar }I_5^\mathcal{P}=\varepsilon\text{ obtenemos}\\
(5,(2,1,0,7,3,0,0,0,\ldots),(\#\#,\varepsilon,\blacktriangle\blacktriangle\#,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{intentando realizar }I_5^\mathcal{P}=\varepsilon\text{ obtenemos}\\
(5,(2,1,0,7,3,0,0,0,\ldots),(\#\#,\varepsilon,\blacktriangle\blacktriangle\#,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\vdots
\end{array}
\]

Nótese que en este caso es natural decir que el programa \(\mathcal{P}\) se detiene, partiendo del estado inicial dado ya que llega a un punto en el que queda intentando realizar \(I_{n(\mathcal{P})+1}^\mathcal{P}\) lo cual no es una instrucción. Veamos un ejemplo de no detención. Sea \(\mathcal{Q}\) el siguiente programa

\[
\begin{array}{ll}
\mathrm{L}3 & \mathrm{N}4\leftarrow \mathrm{N}4+1\\
& \mathrm{IF}\ \mathrm{P}1\ \mathrm{BEGINS}\ \blacktriangle\ \mathrm{GOTO}\ \mathrm{L}3
\end{array}
\]

Supongamos que tomamos \((\overrightarrow{s},\overrightarrow{\sigma})\) igual al estado

\[
((2,1,0,5,3,0,0,0,\ldots),(\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))
\]

Tendremos entonces que la computación de \(\mathcal{Q}\) partiendo del estado \((\overrightarrow{s},\overrightarrow{\sigma})\) es la siguiente infinitupla (de arriba hacia abajo) de descripciones instantáneas:

\[
\begin{array}{c}
(1,(2,1,0,5,3,0,0,0,\ldots),(\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_1^\mathcal{P}=\mathrm{N}4\leftarrow \mathrm{N}4+1\text{ obtenemos}\\
(2,(2,1,0,6,3,0,0,0,\ldots),(\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_2^\mathcal{P}=\mathrm{IF}\ \mathrm{P}1\ \mathrm{BEGINS}\ \blacktriangle\ \mathrm{GOTO}\ \mathrm{L}3\text{ obtenemos}\\
(1,(2,1,0,6,3,0,0,0,\ldots),(\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_1^\mathcal{P}=\mathrm{N}4\leftarrow \mathrm{N}4+1\text{ obtenemos}\\
(2,(2,1,0,7,3,0,0,0,\ldots),(\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_2^\mathcal{P}=\mathrm{IF}\ \mathrm{P}1\ \mathrm{BEGINS}\ \blacktriangle\ \mathrm{GOTO}\ \mathrm{L}3\text{ obtenemos}\\
(1,(2,1,0,7,3,0,0,0,\ldots),(\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_1^\mathcal{P}=\mathrm{N}4\leftarrow \mathrm{N}4+1\text{ obtenemos}\\
(2,(2,1,0,8,3,0,0,0,\ldots),(\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_2^\mathcal{P}=\mathrm{IF}\ \mathrm{P}1\ \mathrm{BEGINS}\ \blacktriangle\ \mathrm{GOTO}\ \mathrm{L}3\text{ obtenemos}\\
(1,(2,1,0,8,3,0,0,0,\ldots),(\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_1^\mathcal{P}=\mathrm{N}4\leftarrow \mathrm{N}4+1\text{ obtenemos}\\
(2,(2,1,0,9,3,0,0,0,\ldots),(\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\text{realizando }I_2^\mathcal{P}=\mathrm{IF}\ \mathrm{P}1\ \mathrm{BEGINS}\ \blacktriangle\ \mathrm{GOTO}\ \mathrm{L}3\text{ obtenemos}\\
(1,(2,1,0,9,3,0,0,0,\ldots),(\blacktriangle\#\#,\varepsilon,\blacktriangle\blacktriangle,\#\blacktriangle,\#,\varepsilon,\varepsilon,\varepsilon,\ldots))\\
\vdots
\end{array}
\]

Nótese que en este caso, es claro que el programa \(\mathcal{Q}\) no se detiene partiendo del estado inicial dado ya que sigue indefinidamente realizando instrucciones.

**Ejercicio 4:** V o F o I, justificar

**(a)** Si \(S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i,\overrightarrow{s},\overrightarrow{\sigma})\), entonces \(i\notin\{1,\ldots,n(\mathcal{P})\}\)

**(b)** Sea \(\mathcal{P}\in Pro^\Sigma\) y sea \(d\) una descripción instantánea cuya primera coordenada es \(i\). Si \(I_i^\mathcal{P}=\mathrm{N}2\leftarrow \mathrm{N}2+1\), entonces

\[
S_\mathcal{P}(d)=(i+1,(\mathrm{N}1,Suc(\mathrm{N}2),\mathrm{N}3,\mathrm{N}4,\ldots),(\mathrm{P}1,\mathrm{P}2,\mathrm{P}3,\mathrm{P}4,\ldots))
\]

**(c)** Sea \(\mathcal{P}\in Pro^\Sigma\) y sea \(d\) una descripción instantánea cuya primera coordenada es \(i\). Si \(I_i^\mathcal{P}=\mathrm{N}2\leftarrow 0\), entonces

\[
S_\mathcal{P}(d)=(i+1,(\mathrm{N}1,0,\mathrm{N}3,\mathrm{N}4,\ldots),(\mathrm{P}1,\mathrm{P}2,\mathrm{P}3,\mathrm{P}4,\ldots))
\]

**(d)** Sea \(\mathcal{P}\in Pro^{\Sigma_p}\) y sea \((i,\overrightarrow{s},\overrightarrow{\sigma})\) una descripción instantánea. Supongamos \(\sigma_3=\mathrm{GOTO}\). Si \(I_i^\mathcal{P}=\mathrm{L}6\ \mathrm{IF}\ \mathrm{P}3\ \mathrm{BEGINS}\ \mathrm{G}\ \mathrm{GOTO}\ \mathrm{L}6\), entonces \(S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(i,\overrightarrow{s},\overrightarrow{\sigma})\).

**(e)** Sea \(\mathcal{P}\in Pro^\Sigma\), sea \(a\in\Sigma\) y sea \((i,\overrightarrow{s},\overrightarrow{\sigma})\) una descripción instantánea. Si \(Bas(I_i^\mathcal{P})=\mathrm{IF}\ \mathrm{P}3\ \mathrm{BEGINS}\ a\ \mathrm{GOTO}\ \mathrm{L}6\) y \([\mathrm{P}3]_1=a\), entonces \(S_\mathcal{P}(i,\overrightarrow{s},\overrightarrow{\sigma})=(j,\overrightarrow{s},\overrightarrow{\sigma})\), donde \(j\) es el menor número \(l\) tal que \(I_l^\mathcal{P}\) tiene label \(\mathrm{L}6\).

**Definición matemática de detención.** Ahora definiremos matemáticamente el concepto de detención. Cuando la primera coordenada de

\[
\underbrace{S_\mathcal{P}(\cdots S_\mathcal{P}(S_\mathcal{P}(1,\overrightarrow{s},\overrightarrow{\sigma}))\cdots)}_{t\ \text{veces}}
\]

sea igual a \(n(\mathcal{P})+1\), diremos que \(\mathcal{P}\) se detiene (luego de \(t\) pasos), partiendo desde el estado \((\overrightarrow{s},\overrightarrow{\sigma})\). Si ninguna de las primeras coordenadas en la computación

\[
((1,\overrightarrow{s},\overrightarrow{\sigma}),S_\mathcal{P}(1,\overrightarrow{s},\overrightarrow{\sigma}),S_\mathcal{P}(S_\mathcal{P}(1,\overrightarrow{s},\overrightarrow{\sigma})),S_\mathcal{P}(S_\mathcal{P}(S_\mathcal{P}(1,\overrightarrow{s},\overrightarrow{\sigma}))),\ldots)
\]

es igual a \(n(\mathcal{P})+1\), diremos que \(\mathcal{P}\) no se detiene partiendo del estado \((\overrightarrow{s},\overrightarrow{\sigma})\). Como puede observarse los programas de \(S^\Sigma\) tienen una sola manera de detenerse, i.e. siempre que se detienen lo hacen habiendo realizado la última de sus instrucciones e intentando realizar la instrucción siguiente a su última instrucción.

Nótese que en los conceptos antes definidos por "1 paso" entendemos "aplicar una vez la función \(S_\mathcal{P}\)" y esto no siempre involucra "realizar una instrucción" ya que podría pasar que aplicáramos \(S_\mathcal{P}\) a una descripción instantánea cuya primera coordenada es \(n(\mathcal{P})+1\). Podemos redondear esta idea diciendo que "1 paso" equivale a "realizarp una instrucción", donde tal como se lo explicó antes "realizarp" significa "realizar si se puede".

## Funciones \(\Sigma\)-computables

Ahora que hemos definido matemáticamente la semántica de \(S^\Sigma\) estamos en condiciones de definir el concepto de función \(\Sigma\)-computable, el cual será una modelización matemática del concepto de función \(\Sigma\)-efectivamente computable. Intuitivamente hablando una función será \(\Sigma\)-computable cuando haya un programa que la compute. Para precisar este concepto nos será útil la siguiente notación. Dados \(x_1,\ldots,x_n\in\omega\) y \(\alpha_1,\ldots,\alpha_m\in\Sigma^\ast\), con \(n,m\in\omega\), usaremos

\[
\lVert x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\rVert
\]

para denotar el estado

\[
((x_1,\ldots,x_n,0,\ldots),(\alpha_1,\ldots,\alpha_m,\varepsilon,\ldots)).
\]

Esta notación requiere aclarar un poco cómo debe interpretarse en los casos límite, es decir cuando alguno de los números \(n,m\) es igual a \(0\). Nótese que por ejemplo

\[
\lVert x\rVert=((x,0,\ldots),(\varepsilon,\ldots))
\]

(es el caso \(n=1\) y \(m=0\)). También

\[
\lVert\alpha\rVert=((0,\ldots),(\alpha,\varepsilon,\ldots))
\]

(es el caso \(n=0\) y \(m=1\)). En el caso \(n=m=0\) pensaremos que \(x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\) se transforma en \(\diamond\) por lo que se obtiene

\[
\lVert\diamond\rVert=((0,\ldots),(\varepsilon,\ldots)).
\]

Además es claro que

\[
\lVert x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\rVert
=
\left\lVert x_1,\ldots,x_n,\underbrace{0,\ldots,0}_{i},\alpha_1,\ldots,\alpha_m,\underbrace{\varepsilon,\ldots,\varepsilon}_{j}\right\rVert
\]

cualesquiera sean \(i,j\in\omega\).

Dado \(\mathcal{P}\in Pro^\Sigma\), definamos para cada par \(n,m\ge 0\), la función \(\Psi_\mathcal{P}^{n,m,\#}\) de la siguiente manera:

\[
\begin{aligned}
D_{\Psi_\mathcal{P}^{n,m,\#}}=\{(\overrightarrow{x},\overrightarrow{\alpha})\in\omega^n\times\Sigma^{\ast m}:{}&
\mathcal{P}\text{ termina, partiendo del estado}\\
&\lVert x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\rVert\}
\end{aligned}
\]

\[
\begin{aligned}
\Psi_\mathcal{P}^{n,m,\#}(\overrightarrow{x},\overrightarrow{\alpha})={}&
\text{valor de }\mathrm{N}1\text{ en el estado obtenido cuando }\mathcal{P}\text{ termina,}\\
&\text{partiendo de }\lVert x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\rVert.
\end{aligned}
\]

Análogamente definamos la función \(\Psi_\mathcal{P}^{n,m,\ast}\) de la siguiente manera:

\[
\begin{aligned}
D_{\Psi_\mathcal{P}^{n,m,\ast}}=\{(\overrightarrow{x},\overrightarrow{\alpha})\in\omega^n\times\Sigma^{\ast m}:{}&
\mathcal{P}\text{ termina, partiendo del estado}\\
&\lVert x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\rVert\}
\end{aligned}
\]

\[
\begin{aligned}
\Psi_\mathcal{P}^{n,m,\ast}(\overrightarrow{x},\overrightarrow{\alpha})={}&
\text{valor de }\mathrm{P}1\text{ en el estado obtenido cuando }\mathcal{P}\text{ termina,}\\
&\text{partiendo de }\lVert x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\rVert.
\end{aligned}
\]

Ahora sí, daremos la definición precisa de función \(\Sigma\)-computable. Una función \(\Sigma\)-mixta \(f:S\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) será llamada \(\Sigma\)-computable si hay un programa \(\mathcal{P}\) de \(S^\Sigma\) tal que \(f=\Psi_\mathcal{P}^{n,m,\#}\). En tal caso diremos que la función \(f\) es computada por \(\mathcal{P}\). Análogamente una función \(\Sigma\)-mixta \(f:S\subseteq\omega^n\times\Sigma^{\ast m}\to\Sigma^\ast\) será llamada \(\Sigma\)-computable si hay un programa \(\mathcal{P}\) de \(S^\Sigma\) tal que \(f=\Psi_\mathcal{P}^{n,m,\ast}\). En tal caso diremos que la función \(f\) es computada por \(\mathcal{P}\).

Algunos ejemplos:

**(E1)** El programa

\[
\begin{array}{ll}
\mathrm{L}2 & \mathrm{IF}\ \mathrm{N}1\ne0\ \mathrm{GOTO}\ \mathrm{L}1\\
& \mathrm{GOTO}\ \mathrm{L}2\\
\mathrm{L}1 & \mathrm{N}1\leftarrow \mathrm{N}1\mathbin{\dot{-}}1
\end{array}
\]

computa la función \(Pred\). Note que este programa también computa las funciones \(Pred\circ p_1^{n,m}\), para \(n\ge 1\) y \(m\ge 0\).

**(E2)** Sea \(\Sigma=\{\clubsuit,\triangle\}\). El programa

\[
\begin{array}{ll}
\mathrm{L}3 & \mathrm{IF}\ \mathrm{P}2\ \mathrm{BEGINS}\ \clubsuit\ \mathrm{GOTO}\ \mathrm{L}1\\
& \mathrm{IF}\ \mathrm{P}2\ \mathrm{BEGINS}\ \triangle\ \mathrm{GOTO}\ \mathrm{L}2\\
& \mathrm{GOTO}\ \mathrm{L}4\\
\mathrm{L}1 & \mathrm{P}2\leftarrow\curvearrowright \mathrm{P}2\\
& \mathrm{P}1\leftarrow \mathrm{P}1.\clubsuit\\
& \mathrm{GOTO}\ \mathrm{L}3\\
\mathrm{L}2 & \mathrm{P}2\leftarrow\curvearrowright \mathrm{P}2\\
& \mathrm{P}1\leftarrow \mathrm{P}1.\triangle\\
& \mathrm{GOTO}\ \mathrm{L}3\\
\mathrm{L}4 & \mathrm{SKIP}
\end{array}
\]

computa la función \(\lambda\alpha\beta[\alpha\beta]\).

**(E3)** Nótese que \(D_{\Psi_\mathcal{P}^{0,0,\#}}=\{\diamond\}\) en caso que \(\mathcal{P}\) termina partiendo del estado \(((0,0,\ldots),(\varepsilon,\varepsilon,\ldots))\) y en tal caso

\[
\begin{aligned}
\Psi_\mathcal{P}^{0,0,\#}(\diamond)={}&
\text{valor de }\mathrm{N}1\text{ en el estado obtenido cuando }\mathcal{P}\text{ termina,}\\
&\text{partiendo de }((0,0,\ldots),(\varepsilon,\varepsilon,\ldots)).
\end{aligned}
\]

En caso de que \(\mathcal{P}\) no termina partiendo del estado \(((0,0,\ldots),(\varepsilon,\varepsilon,\ldots))\) tenemos que \(D_{\Psi_\mathcal{P}^{0,0,\#}}=\emptyset\).

Por supuesto para que el concepto de función \(\Sigma\)-computable tenga chance de ser una modelización adecuada del concepto de función \(\Sigma\)-efectivamente computable, tiene que ser cierto el siguiente resultado.

**Proposición 2 (Leibniz vence a Neumann).** Si \(f\) es \(\Sigma\)-computable, entonces \(f\) es \(\Sigma\)-efectivamente computable.

**Ejercicio 5:** Pruebe la proposición anterior.

Sin embargo nuestro modelo imperativo de función \(\Sigma\)-efectivamente computable todavía podría no ser correcto ya que podría pasar que haya una función \(\Sigma\)-mixta que sea computada por un procedimiento efectivo pero que no exista un programa de \(S^\Sigma\) que la compute. En otras palabras el modelo imperativo o Neumanniano podría ser incompleto. Por supuesto este no es el caso y los desarrollos que veremos más adelante nos convencerán de que el paradigma imperativo es completo, es decir Neumann también vence a Leibniz.

**Ejercicio 6:** Sea \(\Sigma=\{\#,\text{@}\}\). Para cada una de las siguientes funciones haga un programa que la compute

**(a)** \(f:\{0,1,2\}\to\omega\), dada por \(f(0)=f(1)=0\) y \(f(2)=5\)

**(b)** \(\lambda xy[x+y]\)

**(c)** \(C_0^{1,1}\big|_{\{0,1\}\times\Sigma^\ast}\)

**(d)** \(p_4^{2,3}\)

**(e)** \(\lambda i\alpha[[\alpha]_i]\)

**(f)** \(\lambda\alpha[\sqrt{\alpha}]\)

**(g)** \(f:\omega^2\times\{1,2,3\}\to\omega\), \(f(x_1,x_2,x_3)=x_{x_3}\)

**Ejercicio 7:** Sea \(\Sigma=\{\text{@},\&\}\). De un programa que compute la función \(s^{\le}\), donde \(\le\) está dado por \(\text{@}<\&\).

**Ejercicio 8:** V o F o I, justificar

**(a)** Dado \(\mathcal{P}\in Pro^\Sigma\) y \(n,m\ge 0\), se tiene que \(\Psi_\mathcal{P}^{n,m,\#}:\omega^{[\mathbf{N}]}\times\Sigma^{\ast[\mathbf{N}]}\to\omega\)

**(b)** \(\Psi_{\mathrm{L}1\mathrm{IFN}1\ne0\mathrm{GOTOL}1}^{1,0,\#}=\{(0,0)\}\)

**(c)** Sea \(\Sigma\) un alfabeto y sean \(n,m\in\omega\). Sea \(\mathcal{P}\in Pro^\Sigma\). Entonces el dominio de \(\Psi_\mathcal{P}^{n,m,\#}\) es el conjunto formado por todos los estados a partir de los cuales \(\mathcal{P}\) termina

**(d)** Sea \(\Sigma\) un alfabeto y sean \(n,m\in\omega\). Entonces cualesquiera sean \(x_1,\ldots,x_n\in\omega\) y \(\alpha_1,\ldots,\alpha_m\in\Sigma^\ast\) se tiene que

\[
\Psi_{\mathrm{SKIP}}^{n,m,\#}((x_1,\ldots,x_n,0,0,\ldots),(\alpha_1,\ldots,\alpha_m,\varepsilon,\varepsilon,\ldots))=x_1
\]

**(e)** El programa

\[
\mathrm{N}1\leftarrow \mathrm{N}1\mathbin{\dot{-}}1
\]

computa la función \(\lambda x_2x_1[x_2\mathbin{\dot{-}}1]\)

**(f)** \(Suc\) se detiene para todo \(x\in\omega\)

**(g)** Si \(\mathcal{P}\) computa una función \(f:D_f\subseteq\omega^2\to\omega\), entonces \(\mathcal{P}\) computa la función \(f\circ[p_1^{1,0},C_0^{1,0}]\).

**Ejercicio 9:** Sea \(\Sigma=\Sigma_p\cup\{a,b,c,d,e,f,g,\ldots,x,y,z\}\). De una función \(f:Pro^\Sigma\to Pro^\Sigma\) la cual sea \(\Sigma\)-p.r. y tal que \(\Psi_{f(\mathcal{P})}^{1,1,\#}=\Psi_\mathcal{P}^{1,1,\#}\circ[\lambda x\alpha[x+2],C_{bb}^{1,1}]\), cualesquiera sea \(\mathcal{P}\in Pro^\Sigma\).

## Macros

Supongamos que estamos escribiendo un programa \(\mathcal{P}\) de \(S^\Sigma\) con el objeto de que realice cierta tarea. Supongamos además que nos vendría muy bien para nuestros propósitos poder usar una instrucción

\[
\mathrm{N}5\leftarrow \mathrm{N}16+\mathrm{N}3
\]

la cual por supuesto al correr el programa, debería producir el efecto de dejar en la variable \(\mathrm{N}5\) la suma de los contenidos de las variables \(\mathrm{N}16\) y \(\mathrm{N}3\), sin modificar el contenido de las variables distintas a \(\mathrm{N}5\). Lamentablemente no tenemos en \(S^\Sigma\) este tipo de instrucción pero podríamos reemplazarla por el siguiente programa

\[
\begin{array}{ll}
& \mathrm{N}1111\leftarrow \mathrm{N}16\\
& \mathrm{N}2222\leftarrow \mathrm{N}3\\
& \mathrm{N}5\leftarrow \mathrm{N}1111\\
\mathrm{L}1000 & \mathrm{IF}\ \mathrm{N}2222\ne0\ \mathrm{GOTO}\ \mathrm{L}2000\\
& \mathrm{GOTO}\ \mathrm{L}3000\\
\mathrm{L}2000 & \mathrm{N}2222\leftarrow \mathrm{N}2222\mathbin{\dot{-}}1\\
& \mathrm{N}5\leftarrow \mathrm{N}5+1\\
& \mathrm{GOTO}\ \mathrm{L}1000\\
\mathrm{L}3000 & \mathrm{SKIP}
\end{array}
\]

donde las variables \(\mathrm{N}1111\), \(\mathrm{N}2222\) y los labels \(\mathrm{L}1000\), \(\mathrm{L}2000\), \(\mathrm{L}3000\) solo serán usados aquí, es decir no aparecerán en el resto de nuestro programa \(\mathcal{P}\). Nótese que este programa cuando es corrido termina dejando en la variable \(\mathrm{N}5\) la suma de los contenidos de las variables \(\mathrm{N}16\) y \(\mathrm{N}3\) y modifica el contenido de las variables \(\mathrm{N}1111\) y \(\mathrm{N}2222\), lo cual no traerá problemas ya que \(\mathrm{N}1111\) y \(\mathrm{N}2222\) no se usan en el resto de \(\mathcal{P}\). La variables \(\mathrm{N}1111\) y \(\mathrm{N}2222\) son auxiliares y se usan justamente para preservar el valor de las variables \(\mathrm{N}16\) y \(\mathrm{N}3\) ya que ellas son variables protagonistas de nuestro programa \(\mathcal{P}\) y en esta instancia no queremos alterar su contenido sino solo realizar la asignación \(\mathrm{N}5\leftarrow \mathrm{N}16+\mathrm{N}3\). Dejamos al lector explicar por qué es necesario para que la simulación sea correcta que los labels \(\mathrm{L}1000\), \(\mathrm{L}2000\) y \(\mathrm{L}3000\) no sean usados en el resto de \(\mathcal{P}\).

Es decir el programa anterior simula la instrucción \(\mathrm{N}5\leftarrow \mathrm{N}16+\mathrm{N}3\) que no podiamos usar por no ser una instrucción de \(S^\Sigma\), con un costo bastante bajo, es decir el costo de convenir en no usar en el resto de \(\mathcal{P}\) las variables \(\mathrm{N}1111\) y \(\mathrm{N}2222\) ni los labels \(\mathrm{L}1000\), \(\mathrm{L}2000\) y \(\mathrm{L}3000\).

Ahora supongamos que seguimos escribiendo el programa \(\mathcal{P}\) y nos hace falta simular la instrucción \(\mathrm{N}20\leftarrow \mathrm{N}1+\mathrm{N}14\). Entonces es claro que podríamos modificar el programa que simulaba \(\mathrm{N}5\leftarrow \mathrm{N}16+\mathrm{N}3\) haciendole reemplazos adecuados a sus variables y labels. Por ejemplo podríamos escribir

\[
\begin{array}{ll}
& \mathrm{N}9999\leftarrow \mathrm{N}1\\
& \mathrm{N}8888\leftarrow \mathrm{N}14\\
& \mathrm{N}20\leftarrow \mathrm{N}9999\\
\mathrm{L}1001 & \mathrm{IF}\ \mathrm{N}8888\ne0\ \mathrm{GOTO}\ \mathrm{L}2002\\
& \mathrm{GOTO}\ \mathrm{L}3003\\
\mathrm{L}2002 & \mathrm{N}8888\leftarrow \mathrm{N}8888\mathbin{\dot{-}}1\\
& \mathrm{N}20\leftarrow \mathrm{N}20+1\\
& \mathrm{GOTO}\ \mathrm{L}1001\\
\mathrm{L}3003 & \mathrm{SKIP}
\end{array}
\]

donde \(\mathrm{N}9999\), \(\mathrm{N}8888\), \(\mathrm{L}1001\), \(\mathrm{L}2002\) y \(\mathrm{L}3003\) solo serán usados aquí, es decir no aparecerán en el resto de nuestro programa \(\mathcal{P}\).

Consideremos el siguiente "molde" que llamaremos \(M\)

\[
\begin{array}{ll}
& V4\leftarrow V2\\
& V5\leftarrow V3\\
& V1\leftarrow V4\\
A1 & \mathrm{IF}\ V5\ne0\ \mathrm{GOTO}\ A2\\
& \mathrm{GOTO}\ A3\\
A2 & V5\leftarrow V5\mathbin{\dot{-}}1\\
& V1\leftarrow V1+1\\
& \mathrm{GOTO}\ A1\\
A3 & \mathrm{SKIP}
\end{array}
\]

Como puede notarse, cuando reemplazamos en \(M\)

- cada ocurrencia de \(V1\) por \(\mathrm{N}5\)
- cada ocurrencia de \(V2\) por \(\mathrm{N}16\)
- cada ocurrencia de \(V3\) por \(\mathrm{N}3\)
- cada ocurrencia de \(V4\) por \(\mathrm{N}1111\)
- cada ocurrencia de \(V5\) por \(\mathrm{N}2222\)
- cada ocurrencia de \(A1\) por \(\mathrm{L}1000\)
- cada ocurrencia de \(A2\) por \(\mathrm{L}2000\)
- cada ocurrencia de \(A3\) por \(\mathrm{L}3000\)

obtenemos el programa que simulaba la instrucción \(\mathrm{N}5\leftarrow \mathrm{N}16+\mathrm{N}3\) dentro de \(\mathcal{P}\). Similarmente, cuando reemplazamos en \(M\)

- cada ocurrencia de \(V1\) por \(\mathrm{N}20\)
- cada ocurrencia de \(V2\) por \(\mathrm{N}1\)
- cada ocurrencia de \(V3\) por \(\mathrm{N}14\)
- cada ocurrencia de \(V4\) por \(\mathrm{N}9999\)
- cada ocurrencia de \(V5\) por \(\mathrm{N}8888\)
- cada ocurrencia de \(A1\) por \(\mathrm{L}1001\)
- cada ocurrencia de \(A2\) por \(\mathrm{L}2002\)
- cada ocurrencia de \(A3\) por \(\mathrm{L}3003\)

obtenemos el programa que simulaba la instrucción \(\mathrm{N}20\leftarrow \mathrm{N}1+\mathrm{N}14\) dentro de \(\mathcal{P}\). La practicidad de tener el molde \(M\) cae de maduro. Ahora en caso de necesitar una instrucción del tipo \(\mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{n}+\mathrm{N}\overline{m}\) solo tenemos que reemplazar en \(M\)

- cada ocurrencia de \(V1\) por \(\mathrm{N}\overline{k}\)
- cada ocurrencia de \(V2\) por \(\mathrm{N}\overline{n}\)
- cada ocurrencia de \(V3\) por \(\mathrm{N}\overline{m}\)

y reemplazar las "variables" \(V4\) y \(V5\) y los "labels" \(A1\), \(A2\) y \(A3\), por dos variables concretas y tres labels concretos que no se usen en el programa que estamos realizando. El programa así obtenido simulará a la instrucción \(\mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{n}+\mathrm{N}\overline{m}\).

En la jerga computacional el molde \(M\) suele llamarse macro y los programas obtenidos luego de realizar los reemplazos son llamados expansiones de \(M\). Nótese que \(Ti(M)=PALABRA\) ya que, como en el caso de los programas, escribimos a \(M\) línea por línea para facilitar su manejo pero en realidad es una sola palabra, a saber:

\[
\begin{aligned}
&V1{\leftarrow}V2V4{\leftarrow}V3A1\mathrm{IF}V4{\ne}0\mathrm{GOTO}A2\mathrm{GOTO}A3A2V4{\leftarrow}V4\mathbin{\dot{-}}1V1{\leftarrow}V1{+}1\\
&\mathrm{GOTO}A1A3\mathrm{SKIP}
\end{aligned}
\]

Es decir, como objeto matemático, \(M\) es simplemente una palabra. A las palabras de la forma \(V\overline{n}\), con \(n\in\mathbf{N}\), las llamaremos variables numéricas de macro. A las palabras de la forma \(W\overline{n}\), con \(n\in\mathbf{N}\), las llamaremos variables alfabéticas de macro y a las palabras de la forma \(A\overline{n}\), con \(n\in\mathbf{N}\), las llamaremos labels de macro. Nuestro macro \(M\) no tiene variables alfabéticas de macro pero otros macros por supuesto pueden tener este tipo de variables.

Las variables \(V1\), \(V2\) y \(V3\) son llamadas variables oficiales de \(M\) ya que son las variables que serán reemplazadas por variables que son protagonistas dentro del programa \(\mathcal{P}\) que usará la expansión de \(M\). Las palabras \(V4\) y \(V5\) son llamadas variables auxiliares de \(M\) ya que serán reemplazadas por variables que se usarán solo dentro de la expansión y no intervienen en la "trama" del programa \(\mathcal{P}\). También \(A1\), \(A2\) y \(A3\) son llamados labels auxiliares de \(M\) ya que son usados solo para su funcionamiento interno y no tienen vinculación con los labels del programa \(\mathcal{P}\).

En el siguiente ejemplo veremos un macro que tiene un label que no es auxiliar sino oficial. Supongamos que estamos escribiendo un programa \(\mathcal{P}'\) y nos hace falta simular instrucciones de la forma

\[
\mathrm{IF}\ |\mathrm{P}\overline{n}|\le \mathrm{N}\overline{m}\ \mathrm{GOTO}\ \mathrm{L}\overline{k}
\]

(por supuesto estas instrucciones no pertenecen al lenguaje \(S^\Sigma\) pero debería quedar claro cómo funcionan). Construiremos un macro que nos permita simular dicho tipo de instrucciones. Aquí la construcción del macro dependerá de quién es \(\Sigma\), es decir el macro nos servirá para simular instrucciones de \(S^\Sigma\) haciendo programas de \(S^\Sigma\) y si lo usamos haciendo un programa de \(S^\Gamma\), donde \(\Gamma\) es otro alfabeto que contenga a \(\Sigma\), el macro no funcionará bien. Haremos entonces el macro para el caso de \(\Sigma=\{\text{@},!\}\). Sea \(M'\) el siguiente macro:

\[
\begin{array}{ll}
& W2\leftarrow W1\\
& V2\leftarrow V1\\
A4 & \mathrm{IF}\ W2\ \mathrm{BEGINS}\ \text{@}\ \mathrm{GOTO}\ A2\\
& \mathrm{IF}\ W2\ \mathrm{BEGINS}\ !\ \mathrm{GOTO}\ A2\\
& \mathrm{GOTO}\ A1\\
A2 & \mathrm{IF}\ V2\ne0\ \mathrm{GOTO}\ A3\\
& \mathrm{GOTO}\ A5\\
A3 & W2\leftarrow\curvearrowright W2\\
& V2\leftarrow V2\mathbin{\dot{-}}1\\
& \mathrm{GOTO}\ A4\\
A5 & \mathrm{SKIP}
\end{array}
\]

el cual tiene

- variables oficiales \(W1\) y \(V1\) (correspondientes a \(\mathrm{P}\overline{n}\) y \(\mathrm{N}\overline{m}\))
- variables auxiliares \(W2\) y \(V2\)
- labels auxiliares \(A2\), \(A3\), \(A4\) y \(A5\)
- un label oficial \(A1\) (correspondiente a \(\mathrm{L}\overline{k}\))

Una descripción intuitiva del macro \(M'\) sería

\[
\mathrm{IF}\ |W1|\le V1\ \mathrm{GOTO}\ A1
\]

Nótese que en las primeras dos líneas el macro \(M'\) guarda los valores de las variables oficiales \(W1\) y \(V1\) en las variables auxiliares \(W2\) y \(V2\), y sigue trabajando con las auxiliares. Esto es para preservar el valor de las variables oficiales. Dado que \(\Sigma=\{\text{@},!\}\), las dos siguientes líneas sirven para decidir si el contenido de \(W2\) es \(\varepsilon\) o no ya que si una palabra de \(\Sigma^\ast\) no comienza con @ ni con !, deberá ser \(\varepsilon\) (aquí es donde notamos que nuestro macro \(M'\) funcionará bien solo para hacer programas de \(S^{\{\text{@},!\}}\)). Dejamos al lector entender el resto del funcionamiento de \(M'\).

Para dar un ejemplo de cómo usaríamos a \(M'\), supongamos que para seguir escribiendo nuestro programa \(\mathcal{P}'\) nos hace falta simular la instrucción

\[
\mathrm{IF}\ |\mathrm{P}5|\le \mathrm{N}14\ \mathrm{GOTO}\ \mathrm{L}1
\]

y supongamos que las variables \(\mathrm{P}1000\) y \(\mathrm{N}1000\) y los labels \(\mathrm{L}6666\), \(\mathrm{L}7777\), \(\mathrm{L}8888\) y \(\mathrm{L}9999\) no se usaron hasta el momento en \(\mathcal{P}'\). Entonces podemos reemplazar en \(M'\)

- cada ocurrencia de \(W1\) por \(\mathrm{P}5\)
- cada ocurrencia de \(V1\) por \(\mathrm{N}14\)
- cada ocurrencia de \(W2\) por \(\mathrm{P}1000\)
- cada ocurrencia de \(V2\) por \(\mathrm{N}1000\)
- cada ocurrencia de \(A1\) por \(\mathrm{L}1\)
- cada ocurrencia de \(A2\) por \(\mathrm{L}6666\)
- cada ocurrencia de \(A3\) por \(\mathrm{L}7777\)
- cada ocurrencia de \(A4\) por \(\mathrm{L}8888\)
- cada ocurrencia de \(A5\) por \(\mathrm{L}9999\)

y la expansión de \(M'\) así obtenida simulará la instrucción \(\mathrm{IF}\ |\mathrm{P}5|\le \mathrm{N}14\ \mathrm{GOTO}\ \mathrm{L}1\). Cabe destacar que para asegurarnos que la simulación funcione, también deberemos no usar en el resto de \(\mathcal{P}'\) las variables \(\mathrm{P}1000\) y \(\mathrm{N}1000\) y los labels \(\mathrm{L}6666\), \(\mathrm{L}7777\), \(\mathrm{L}8888\) y \(\mathrm{L}9999\).

Es decir \(M'\) funciona como un molde con el cual haciendo reemplazos adecuados podemos simular en \(S^\Sigma\) cualquier instrucción del tipo \(\mathrm{IF}\ |\mathrm{P}\overline{n}|\le \mathrm{N}\overline{m}\ \mathrm{GOTO}\ \mathrm{L}\overline{k}\), con \(n,m,k\in\mathbf{N}\).

Debería quedar claro el carácter oficial del label \(A1\) en \(M'\) ya que el label por el que se lo reemplaza para hacer la expansión es uno de los labels protagonistas del programa que se está escribiendo.

Cabe destacar que las expansiones de \(M'\) no son programas ya que si bien son concatenaciones de instrucciones, no cumplen la ley de los GOTO (llamada (G) en la definición de programa) respecto del label que reemplazó a \(A1\).

Como se vio en este último ejemplo es importante tener en cuenta que cuando construimos un macro lo hacemos relativo a un alfabeto \(\Sigma\) previamente fijado, es decir estamos pensando que dicho macro será usado para hacer programas de \(S^\Sigma\) y podría pasar que si lo usáramos para hacer un programa de \(S^\Gamma\), donde \(\Gamma\) es otro alfabeto, el macro no cumpla las propiedades esperadas. Para visualizar esto mejor, nótese que la palabra

\[
\begin{array}{ll}
& \mathrm{IF}\ W1\ \mathrm{BEGINS}\ \text{@}\ \mathrm{GOTO}\ A2\\
& \mathrm{IF}\ W1\ \mathrm{BEGINS}\ \%\ \mathrm{GOTO}\ A2\\
& \mathrm{IF}\ W1\ \mathrm{BEGINS}\ !\ \mathrm{GOTO}\ A2\\
& \mathrm{IF}\ W1\ \mathrm{BEGINS}\ \square\ \mathrm{GOTO}\ A2\\
& \mathrm{GOTO}\ A1\\
A2 & \mathrm{SKIP}
\end{array}
\]

es un macro de \(S^{\{\text{@},\%,!,\square\}}\) que simula instrucciones de la forma

\[
\mathrm{IF}\ \mathrm{P}\overline{n}=\varepsilon\ \mathrm{GOTO}\ \mathrm{L}\overline{m}
\]

(el cual obviamente podríamos denotar con \(\mathrm{IF}\ W1=\varepsilon\ \mathrm{GOTO}\ A1\)), pero es claro que esta palabra no nos servirá para simular este tipo de instrucciones en el lenguaje \(S^{\{\text{@},\%,!,\square,\triangle\}}\).

**Nota:** Siempre supondremos que la primera instrucción de los macros no es labelada. Esto es porque muchas veces cuando expandamos un macro nos interesará labelar la primera instrucción de dicha expansión. Por supuesto, esto es fácil de conseguir ya que si \(M\) es un macro, entonces \(\mathrm{SKIP}M\) es también un macro que posee las mismas propiedades.

Como hemos visto recién hay dos tipos de macros:

- los de asignación que cuando son expandidos nos dan un programa que simula la asignación a una variable dada del resultado de aplicar una función a los contenidos de ciertas otras variables; y
- los de tipo IF que cuando son expandidos nos dan un programa salvo por la ley (G), el cual direcciona al label que fue a reemplazar a \(A1\) cuando se cumple cierta propiedad (predicado) relativa a los contenidos de las variables que fueron a reemplazar a las variables oficiales.

**Ejemplo concreto de uso de macros.** Ya vimos recién que la palabra

\[
\begin{array}{ll}
& V4\leftarrow V2\\
& V5\leftarrow V3\\
& V1\leftarrow V4\\
A1 & \mathrm{IF}\ V5\ne0\ \mathrm{GOTO}\ A2\\
& \mathrm{GOTO}\ A3\\
A2 & V5\leftarrow V5\mathbin{\dot{-}}1\\
& V1\leftarrow V1+1\\
& \mathrm{GOTO}\ A1\\
A3 & \mathrm{SKIP}
\end{array}
\]

es un macro que sirve para simular instrucciones de la forma \(\mathrm{N}\overline{k}\leftarrow \mathrm{N}\overline{n}+\mathrm{N}\overline{m}\). Notemos que este macro es de asignación ya que cuando es expandido nos da un programa que simula la asignación a una variable dada del resultado de aplicar una función a los contenidos de ciertas otras variables. En este caso la función es \(SUMA=\lambda xy[x+y]\) por lo cual usaremos \([V1\leftarrow SUMA(V2,V3)]\) para denotar a dicho macro. Usaremos este macro para dar un programa \(\mathcal{P}\) que compute a la función \(\lambda xy[x.y]\). Nótese que podemos tomar \(\mathcal{P}\) igual al siguiente programa

\[
\begin{array}{ll}
\mathrm{L}1 & \mathrm{IF}\ \mathrm{N}2\ne0\ \mathrm{GOTO}\ \mathrm{L}2\\
& \mathrm{GOTO}\ \mathrm{L}3\\
\mathrm{L}2 & [\mathrm{N}3\leftarrow SUMA(\mathrm{N}3,\mathrm{N}1)]\\
& \mathrm{N}2\leftarrow \mathrm{N}2\mathbin{\dot{-}}1\\
& \mathrm{GOTO}\ \mathrm{L}1\\
\mathrm{L}3 & \mathrm{N}1\leftarrow \mathrm{N}3
\end{array}
\]

donde \([\mathrm{N}3\leftarrow SUMA(\mathrm{N}3,\mathrm{N}1)]\) es una expansión del macro \([V1\leftarrow SUMA(V2,V3)]\) hecha haciendo el reemplazo de las variables oficiales \(V1\), \(V2\) y \(V3\) por \(\mathrm{N}3\), \(\mathrm{N}3\) y \(\mathrm{N}1\), respectivamente, y haciendo reemplazos adecuados de sus variables y labels auxiliares. Hay muchas formas de hacer los reemplazos de variables y labels auxiliares pero en general no lo especificaremos explícitamente cuando expandamos un macro ya que es fácil imaginar cómo hacerlo en función del programa que estemos realizando. Por ejemplo en el caso de \(\mathcal{P}\) podríamos hacer los siguientes reemplazos:

- cada ocurrencia de \(V4\) por \(\mathrm{N}1111\)
- cada ocurrencia de \(V5\) por \(\mathrm{N}2222\)
- cada ocurrencia de \(A1\) por \(\mathrm{L}1000\)
- cada ocurrencia de \(A2\) por \(\mathrm{L}2000\)
- cada ocurrencia de \(A3\) por \(\mathrm{L}3000\)

y claramente esto no afectará la "lógica" o "idea" de nuestro programa \(\mathcal{P}\). De esta forma la expansión \([\mathrm{N}3\leftarrow SUMA(\mathrm{N}3,\mathrm{N}1)]\) es el siguiente programa:

\[
\begin{array}{ll}
& \mathrm{N}1111\leftarrow \mathrm{N}3\\
& \mathrm{N}2222\leftarrow \mathrm{N}1\\
& \mathrm{N}3\leftarrow \mathrm{N}1111\\
\mathrm{L}1000 & \mathrm{IF}\ \mathrm{N}2222\ne0\ \mathrm{GOTO}\ \mathrm{L}2000\\
& \mathrm{GOTO}\ \mathrm{L}3000\\
\mathrm{L}2000 & \mathrm{N}2222\leftarrow \mathrm{N}2222\mathbin{\dot{-}}1\\
& \mathrm{N}3\leftarrow \mathrm{N}3+1\\
& \mathrm{GOTO}\ \mathrm{L}1000\\
\mathrm{L}3000 & \mathrm{SKIP}
\end{array}
\]

el cual por supuesto está escrito con espacios y en forma vertical pero es una mera palabra. Tenemos entonces que \(\mathcal{P}\) es el programa:

\[
\begin{array}{ll}
\mathrm{L}1 & \mathrm{IF}\ \mathrm{N}2\ne0\ \mathrm{GOTO}\ \mathrm{L}2\\
& \mathrm{GOTO}\ \mathrm{L}3\\
\mathrm{L}2 & \mathrm{N}1111\leftarrow \mathrm{N}1\\
& \mathrm{N}2222\leftarrow \mathrm{N}3\\
& \mathrm{N}3\leftarrow \mathrm{N}1111\\
\mathrm{L}1000 & \mathrm{IF}\ \mathrm{N}2222\ne0\ \mathrm{GOTO}\ \mathrm{L}2000\\
& \mathrm{GOTO}\ \mathrm{L}3000\\
\mathrm{L}2000 & \mathrm{N}2222\leftarrow \mathrm{N}2222\mathbin{\dot{-}}1\\
& \mathrm{N}3\leftarrow \mathrm{N}3+1\\
& \mathrm{GOTO}\ \mathrm{L}1000\\
\mathrm{L}3000 & \mathrm{SKIP}\\
& \mathrm{N}2\leftarrow \mathrm{N}2\mathbin{\dot{-}}1\\
& \mathrm{GOTO}\ \mathrm{L}1\\
\mathrm{L}3 & \mathrm{N}1\leftarrow \mathrm{N}3
\end{array}
\]

el cual por supuesto está escrito con espacios y en forma vertical pero es una mera palabra.

**Macros asociados a funciones \(\Sigma\)-computables.** Dada una función \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\), usaremos

\[
[V\overline{n+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]
\]

para denotar un macro de \(S^\Sigma\) \(M\) el cual cumpla las siguientes propiedades (no siempre existirá dicho macro, es decir solo para ciertas funciones \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) habrá un tal macro).

**(1)** Las variables oficiales de \(M\) son \(V1,\ldots,V\overline{n},V\overline{n+1},W1,\ldots,W\overline{m}\).

**(2)** \(M\) no tiene labels oficiales.

**(3)** Si reemplazamos:

- las variables oficiales de \(M\) (i.e. \(V1,\ldots,V\overline{n},V\overline{n+1},W1,\ldots,W\overline{m}\)) por variables concretas

\[
\mathrm{N}\overline{k_1},\ldots,\mathrm{N}\overline{k_n},\mathrm{N}\overline{k_{n+1}},\mathrm{P}\overline{j_1},\ldots,\mathrm{P}\overline{j_m}
\]

(elegidas libremente, es decir los números \(k_1,\ldots,k_{n+1},j_1,\ldots,j_m\) son cualesquiera)

- las variables auxiliares de \(M\) por variables concretas (distintas de a dos) y NO pertenecientes a la lista \(\mathrm{N}\overline{k_1},\ldots,\mathrm{N}\overline{k_n},\mathrm{N}\overline{k_{n+1}},\mathrm{P}\overline{j_1},\ldots,\mathrm{P}\overline{j_m}\)
- los labels auxiliares de \(M\) por labels concretos (distintos de a dos)

entonces la palabra así obtenida es un programa \(\mathcal{E}\) de \(S^\Sigma\) que denotaremos en general con

\[
[\mathrm{N}\overline{k_{n+1}}\leftarrow f(\mathrm{N}\overline{k_1},\ldots,\mathrm{N}\overline{k_n},\mathrm{P}\overline{j_1},\ldots,\mathrm{P}\overline{j_m})]
\]

el cual debe tener la siguiente propiedad:

**(E)** Si hacemos correr \(\mathcal{E}\) partiendo de un estado \(e\) que le asigne a las variables \(\mathrm{N}\overline{k_1},\ldots,\mathrm{N}\overline{k_n},\mathrm{P}\overline{j_1},\ldots,\mathrm{P}\overline{j_m}\) valores \(x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\), entonces independientemente de los valores que les asigne \(e\) al resto de las variables (incluidas las que fueron a reemplazar a las variables auxiliares de \(M\)) se dará que

**(i)** si \((x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m)\notin D_f\), entonces \(\mathcal{E}\) no se detiene

**(ii)** si \((x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m)\in D_f\), entonces \(\mathcal{E}\) se detiene (i.e. intenta realizar la siguiente a su última instrucción) y llega a un estado \(e'\) el cual cumple:

- \(e'\) le asigna a \(\mathrm{N}\overline{k_{n+1}}\) el valor \(f(x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m)\)
- \(e'\) solo puede diferir de \(e\) en los valores que le asigna a \(\mathrm{N}\overline{k_{n+1}}\) o a las variables que fueron a reemplazar a las variables auxiliares de \(M\). Nótese que esto nos dice que los valores de las variables \(\mathrm{N}\overline{k_1},\ldots,\mathrm{N}\overline{k_n},\mathrm{P}\overline{j_1},\ldots,\mathrm{P}\overline{j_m}\) al correr \(\mathcal{E}\) desde el estado \(e\) no se modificarán, salvo cuando \(k_i\) es igual a \(k_{n+1}\), situación en la cual el valor final de \(\mathrm{N}\overline{k_i}\) será \(f(x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m)\)

El programa

\[
\mathcal{E}=[\mathrm{N}\overline{k_{n+1}}\leftarrow f(\mathrm{N}\overline{k_1},\ldots,\mathrm{N}\overline{k_n},\mathrm{P}\overline{j_1},\ldots,\mathrm{P}\overline{j_m})]
\]

es comúnmente llamado la expansión del macro \(M=[V\overline{n+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]\) con respecto a la elección de variables y labels realizada.

También, dada una función \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\Sigma^\ast\), con

\[
[W\overline{m+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]
\]

denotaremos un macro de \(S^\Sigma\) el cual cumpla condiciones análogas a las descriptas recién. Dejamos al lector escribirlas en detalle para este caso.

Es importante notar que nuestra notación

\[
[V\overline{n+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]
\]

tiene cierta ambigüedad ya que no hace mención al alfabeto \(\Sigma\) el cual está previamente fijado. Podría pasar que la función \(f\) sea \(\Gamma\)-mixta para otro alfabeto \(\Gamma\) y que el macro

\[
[V\overline{n+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]
\]

sea distinto según lo consideremos para \(S^\Sigma\) o para \(S^\Gamma\). Es decir, como ya lo remarcamos anteriormente, cuando hablamos de la existencia de un macro, es siempre relativo a un \(S^\Sigma\). Lo mismo pasa con la notación

\[
[W\overline{m+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]
\]

Dejamos al lector que piense este fenómeno para el caso de la función \(f:\{\text{@},\%\}^\ast\times\{\text{@},\%\}^\ast\to\{\text{@},\%\}^\ast\), dada por \(f(\alpha,\beta)=\alpha\beta\). Si tomamos \(\Sigma=\{\text{@},\%\}\) y \(\Gamma=\{\text{@},\%,!\}\), entonces \(f\) resulta una función \(\Sigma\)-mixta y también \(\Gamma\)-mixta y debería quedar claro que no es lo mismo hacer el macro

\[
[W3\leftarrow f(W1,W2)]
\]

para \(S^\Sigma\) que hacerlo para \(S^\Gamma\).

Otra ambigüedad de esta notación de macros de asignación es que en el nombre de los macros

\[
[V\overline{n+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]
\]

\[
[W\overline{m+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]
\]

no se especifica quiénes son las variables y labels auxiliares de dichos macros. Ambas ambigüedades no nos traerán problemas si manejamos las cosas con cierta madurez.

Aceptaremos sin demostración el siguiente resultado fundamental.

**Proposición 3.**

**(a)** Sea \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) una función \(\Sigma\)-computable. Entonces en \(S^\Sigma\) hay un macro

\[
[V\overline{n+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]
\]

**(b)** Sea \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\Sigma^\ast\) una función \(\Sigma\)-computable. Entonces en \(S^\Sigma\) hay un macro

\[
[W\overline{m+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]
\]

**Ejercicio 10:** Sea \(SUMA=\lambda xy[x+y]\). Explique por qué la palabra

\[
\begin{array}{ll}
& V1\leftarrow V2\\
& V4\leftarrow V3\\
A1 & \mathrm{IF}\ V4\ne0\ \mathrm{GOTO}\ A2\\
& \mathrm{GOTO}\ A3\\
A2 & V4\leftarrow V4\mathbin{\dot{-}}1\\
& V1\leftarrow V1+1\\
& \mathrm{GOTO}\ A1\\
A3 & \mathrm{SKIP}
\end{array}
\]

no puede ser tomada como el macro \([V3\leftarrow SUMA(V1,V2)]\).

**Ejercicio 11:** Sea \(\Sigma=\{\#,\$\}\) y sea \(f:D_f\subseteq\Sigma^\ast\to\omega\) una función \(\Sigma\)-computable. Sea \(L=\{\alpha\in D_f:f(\alpha)=1\}\). De (usando el macro \([V1\leftarrow f(W1)]\)) un programa \(\mathcal{P}\in Pro^\Sigma\) tal que \(\operatorname{Dom}(\Psi_\mathcal{P}^{0,1,\#})=L\).

**Ejercicio 12:** Sea \(\Sigma=\{\#,\$\}\) y sea \(f:\omega\to\Sigma^\ast\) una función \(\Sigma\)-computable. De (usando el macro \([W1\leftarrow f(V1)]\)) un programa \(\mathcal{P}\in Pro^\Sigma\) tal que \(\operatorname{Dom}(\Psi_\mathcal{P}^{0,1,\#})=\operatorname{Im}f\).

**Ejercicio 13:** Pruebe la recíproca de la proposición anterior, es decir pruebe que si \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) es tal que en \(S^\Sigma\) hay un macro

\[
[V\overline{n+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]
\]

entonces \(f\) es \(\Sigma\)-computable.

**Macros asociados a predicados \(\Sigma\)-computables.** Dado un predicado \(P:D_P\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\), usaremos

\[
[\mathrm{IF}\ P(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\ \mathrm{GOTO}\ A1]
\]

para denotar un macro \(M\) de \(S^\Sigma\) el cual cumpla las siguientes propiedades (no siempre existirá dicho macro, es decir solo para ciertos predicados \(P:D_P\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) habrá un tal macro).

**(1)** Las variables oficiales de \(M\) son \(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m}\).

**(2)** \(A1\) es el único label oficial de \(M\).

**(3)** Si reemplazamos:

- las variables oficiales de \(M\) (i.e. \(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m}\)) por variables concretas

\[
\mathrm{N}\overline{k_1},\ldots,\mathrm{N}\overline{k_n},\mathrm{P}\overline{j_1},\ldots,\mathrm{P}\overline{j_m}
\]

(elegidas libremente, es decir los números \(k_1,\ldots,k_n,j_1,\ldots,j_m\) son cualesquiera)

- el label oficial \(A1\) por un label concreto \(\mathrm{L}\overline{k}\) (elegido libremente, es decir \(k\) es cualquier elemento de \(\mathbf{N}\))
- las variables auxiliares de \(M\) por variables concretas (distintas de a dos) y NO pertenecientes a la lista \(\mathrm{N}\overline{k_1},\ldots,\mathrm{N}\overline{k_n},\mathrm{P}\overline{j_1},\ldots,\mathrm{P}\overline{j_m}\)
- los labels auxiliares de \(M\) por labels concretos (distintos de a dos) y ninguno igual a \(\mathrm{L}\overline{k}\)

entonces la palabra así obtenida es un programa \(\mathcal{E}\) de \(S^\Sigma\) (salvo por la ley de los GOTO respecto de \(\mathrm{L}\overline{k}\)) que denotaremos en general con

\[
[\mathrm{IF}\ P(\mathrm{N}\overline{k_1},\ldots,\mathrm{N}\overline{k_n},\mathrm{P}\overline{j_1},\ldots,\mathrm{P}\overline{j_m})\ \mathrm{GOTO}\ \mathrm{L}\overline{k}]
\]

el cual debe tener la siguiente propiedad:

**(E)** Si hacemos correr \(\mathcal{E}\) partiendo de un estado \(e\) que le asigne a las variables \(\mathrm{N}\overline{k_1},\ldots,\mathrm{N}\overline{k_n},\mathrm{P}\overline{j_1},\ldots,\mathrm{P}\overline{j_m}\) valores \(x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\), entonces independientemente de los valores que les asigne \(e\) al resto de las variables (incluidas las que fueron a reemplazar a las variables auxiliares de \(M\)) se dará que

**(i)** si \((\overrightarrow{x},\overrightarrow{\alpha})\notin D_P\), entonces \(\mathcal{E}\) no se detiene

**(ii)** si \((\overrightarrow{x},\overrightarrow{\alpha})\in D_P\) y \(P(\overrightarrow{x},\overrightarrow{\alpha})=1\), entonces luego de una cantidad finita de pasos, \(\mathcal{E}\) direcciona al label \(\mathrm{L}\overline{k}\) quedando en un estado \(e'\) el cual solo puede diferir de \(e\) en los valores que le asigna a las variables que fueron a reemplazar a las variables auxiliares de \(M\). Al resto de las variables, incluidas \(\mathrm{N}\overline{k_1},\ldots,\mathrm{N}\overline{k_n},\mathrm{P}\overline{j_1},\ldots,\mathrm{P}\overline{j_m}\) no las modifica

**(iii)** si \((\overrightarrow{x},\overrightarrow{\alpha})\in D_P\) y \(P(\overrightarrow{x},\overrightarrow{\alpha})=0\), entonces luego de una cantidad finita de pasos, \(\mathcal{E}\) se detiene (i.e. intenta realizar la siguiente a su última instrucción) quedando en un estado \(e'\) el cual solo puede diferir de \(e\) en los valores que le asigna a las variables que fueron a reemplazar a las variables auxiliares de \(M\). Al resto de las variables, incluidas \(\mathrm{N}\overline{k_1},\ldots,\mathrm{N}\overline{k_n},\mathrm{P}\overline{j_1},\ldots,\mathrm{P}\overline{j_m}\) no las modifica.

La palabra

\[
\mathcal{E}=[\mathrm{IF}\ P(\mathrm{N}\overline{k_1},\ldots,\mathrm{N}\overline{k_n},\mathrm{P}\overline{j_1},\ldots,\mathrm{P}\overline{j_m})\ \mathrm{GOTO}\ \mathrm{L}\overline{k}]
\]

es llamada la expansión del macro con respecto a la elección de variables y labels realizada. Al igual que en el caso de los macros de asignación, la notación

\[
[\mathrm{IF}\ P(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\ \mathrm{GOTO}\ A1]
\]

tiene cierta ambigüedad ya que no explicita el alfabeto ni los labels y variables auxiliares de tipo macro.

**Proposición 4.** Sea \(P:D_P\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) un predicado \(\Sigma\)-computable. Entonces en \(S^\Sigma\) hay un macro

\[
[\mathrm{IF}\ P(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\ \mathrm{GOTO}\ A1].
\]

**Proof.** Por (a) de la proposición anterior tenemos un macro \([V\overline{n+1}\leftarrow P(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]\). Nótese que la palabra

\[
[V\overline{n+1}\leftarrow P(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]\ \mathrm{IF}V\overline{n+1}\ne0\mathrm{GOTO}A1
\]

es el macro buscado. \(\blacksquare\)

**Ejercicio 14:** Pruebe la recíproca de la proposición anterior, es decir pruebe que si \(P:D_P\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) es tal que en \(S^\Sigma\) hay un macro

\[
[\mathrm{IF}\ P(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\ \mathrm{GOTO}\ A1]
\]

entonces \(P\) es \(\Sigma\)-computable.

**Ejercicio 15:** Sea \(\Sigma\) un alfabeto finito. Pruebe usando macros (de tipo IF) que si \(P:S\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) y \(Q:S\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) son predicados \(\Sigma\)-computables, entonces \((P\lor Q)\), \((P\land Q)\) y \(\neg P\) lo son también.

**Primer Manantial de Macros.** Dejamos en forma de una sola proposición los tres casos de existencia de macros.

**Proposición 5 (Primer Manantial de Macros).** Sea \(\Sigma\) un alfabeto finito. Si

\[
\begin{aligned}
f&:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\\
g&:D_g\subseteq\omega^n\times\Sigma^{\ast m}\to\Sigma^\ast\\
P&:D_P\subseteq\omega^n\times\Sigma^{\ast m}\to\{0,1\}
\end{aligned}
\]

son \(\Sigma\)-computables, entonces en \(S^\Sigma\) hay macros

\[
[V\overline{n+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]
\]

\[
[W\overline{m+1}\leftarrow g(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})]
\]

\[
[\mathrm{IF}\ P(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\ \mathrm{GOTO}\ A1].
\]

Básicamente habrá dos manantiales de macros de donde obtendremos todos los macros que potenciarán nuestro lenguaje \(S^\Sigma\). El Segundo Manantial de Macros es consecuencia del primero y de la batalla Neumann vence a Gödel que veremos en la Guía 8.

## Conjuntos \(\Sigma\)-enumerables

Ya que la noción de función \(\Sigma\)-computable es el modelo matemático Neumanniano o imperativo del concepto de función \(\Sigma\)-efectivamente computable, nos podríamos preguntar entonces cuál es el modelo matemático Neumanniano del concepto de conjunto \(\Sigma\)-efectivamente enumerable. Si prestamos atención a la definición de conjunto \(\Sigma\)-efectivamente enumerable, notaremos que depende de la existencia de ciertas funciones \(\Sigma\)-efectivamente computables por lo cual la siguiente definición cae de maduro:

Un conjunto \(S\subseteq\omega^n\times\Sigma^{\ast m}\) será llamado \(\Sigma\)-enumerable cuando sea vacío o haya una función \(F:\omega\to\omega^n\times\Sigma^{\ast m}\) tal que \(I_F=S\) y \(F_{(i)}\) sea \(\Sigma\)-computable, para cada \(i\in\{1,\ldots,n+m\}\).

Debería entonces quedar claro que si el concepto de función \(\Sigma\)-computable modeliza correctamente al concepto de función \(\Sigma\)-efectivamente computable, entonces el concepto de conjunto \(\Sigma\)-enumerable recién definido modeliza correctamente al concepto de conjunto \(\Sigma\)-efectivamente enumerable.

Nótese que según la definición que acabamos de escribir, un conjunto no vacío \(S\subseteq\omega^n\times\Sigma^{\ast m}\) es \(\Sigma\)-enumerable si y solo si hay programas \(\mathcal{P}_1,\ldots,\mathcal{P}_{n+m}\) tales que

\[
\operatorname{Dom}(\Psi_{\mathcal{P}_1}^{1,0,\#})=\cdots=\operatorname{Dom}(\Psi_{\mathcal{P}_n}^{1,0,\#})=\omega
\]

\[
\operatorname{Dom}(\Psi_{\mathcal{P}_{n+1}}^{1,0,\ast})=\cdots=\operatorname{Dom}(\Psi_{\mathcal{P}_{n+m}}^{1,0,\ast})=\omega
\]

\[
S=\operatorname{Im}([\Psi_{\mathcal{P}_1}^{1,0,\#},\ldots,\Psi_{\mathcal{P}_n}^{1,0,\#},\Psi_{\mathcal{P}_{n+1}}^{1,0,\ast},\ldots,\Psi_{\mathcal{P}_{n+m}}^{1,0,\ast}]).
\]

Como puede notarse los programas \(\mathcal{P}_1,\ldots,\mathcal{P}_{n+m}\) puestos secuencialmente a funcionar desde el estado \(\lVert x\rVert\) producen en forma natural un procedimiento efectivo (con dato de entrada \(x\in\omega\)) que enumera a \(S\). Por supuesto podemos decir que en tal caso los programas \(\mathcal{P}_1,\ldots,\mathcal{P}_{n+m}\) enumeran a \(S\). La siguiente proposición muestra que también las cosas se pueden hacer con un solo programa.

**Proposición 6 (Caracterización de \(\Sigma\)-enumerabilidad).** Sea \(S\subseteq\omega^n\times\Sigma^{\ast m}\) un conjunto no vacío. Entonces son equivalentes:

**(1)** \(S\) es \(\Sigma\)-enumerable.

**(2)** Hay un programa \(\mathcal{P}\in Pro^\Sigma\) tal que:

**(a)** Para cada \(x\in\omega\), tenemos que \(\mathcal{P}\) se detiene partiendo desde el estado \(\lVert x\rVert\) y llega a un estado de la forma \(((x_1,\ldots,x_n,y_1,\ldots),(\alpha_1,\ldots,\alpha_m,\beta_1,\ldots))\), donde \((x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m)\in S\).

**(b)** Para cada \((x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m)\in S\) hay un \(x\in\omega\) tal que \(\mathcal{P}\) se detiene partiendo desde el estado \(\lVert x\rVert\) y llega a un estado de la forma \(((x_1,\ldots,x_n,y_1,\ldots),(\alpha_1,\ldots,\alpha_m,\beta_1,\ldots))\).

**Proof.** \((1)\Rightarrow(2)\). Ya que \(S\) es no vacío, por definición tenemos que hay una \(F:\omega\to\omega^n\times\Sigma^{\ast m}\) tal que \(I_F=S\) y \(F_{(i)}\) es \(\Sigma\)-computable, para cada \(i\in\{1,\ldots,n+m\}\). Por el Primer Manantial de Macros tenemos que existen macros:

\[
\begin{array}{c}
[V2\leftarrow F_{(1)}(V1)]\\
\vdots\\
[V2\leftarrow F_{(n)}(V1)]\\
[W1\leftarrow F_{(n+1)}(V1)]\\
\vdots\\
[W1\leftarrow F_{(n+m)}(V1)]
\end{array}
\]

Sea \(\mathcal{P}\) el siguiente programa:

\[
\begin{array}{c}
[\mathrm{P}\overline{m}\leftarrow F_{(n+m)}(\mathrm{N}1)]\\
\vdots\\
[\mathrm{P}1\leftarrow F_{(n+1)}(\mathrm{N}1)]\\
[\mathrm{N}\overline{n}\leftarrow F_{(n)}(\mathrm{N}1)]\\
\vdots\\
[\mathrm{N}1\leftarrow F_{(1)}(\mathrm{N}1)]
\end{array}
\]

donde se supone que las expansiones de los macros usados son hechas usando variables auxiliares no pertenecientes a la lista \(\mathrm{N}1,\ldots,\mathrm{N}\overline{n},\mathrm{P}1,\ldots,\mathrm{P}\overline{m}\) (por supuesto, dada la fortaleza de nuestros macros se puede usar una misma variable auxiliar para dos distintas expansiones), y también se supone que los labels auxiliares usados en dichas expansiones son todos distintos, es decir no usamos el mismo label auxiliar en dos expansiones distintas (por qué?).

Dejamos al lector corroborar que el programa \(\mathcal{P}\) cumple las propiedades (a) y (b).

\((2)\Rightarrow(1)\). Supongamos \(\mathcal{P}\in Pro^\Sigma\) cumple (a) y (b) de (2). Sean

\[
\begin{array}{c}
\mathcal{P}_1=\mathcal{P}\ \mathrm{N}1\leftarrow \mathrm{N}1\\
\mathcal{P}_2=\mathcal{P}\ \mathrm{N}1\leftarrow \mathrm{N}2\\
\vdots\\
\mathcal{P}_n=\mathcal{P}\ \mathrm{N}1\leftarrow \mathrm{N}\overline{n}\\
\mathcal{P}_{n+1}=\mathcal{P}\ \mathrm{P}1\leftarrow \mathrm{P}1\\
\mathcal{P}_{n+2}=\mathcal{P}\ \mathrm{P}1\leftarrow \mathrm{P}2\\
\vdots\\
\mathcal{P}_{n+m}=\mathcal{P}\ \mathrm{P}1\leftarrow \mathrm{P}\overline{m}
\end{array}
\]

Definamos

\[
\begin{array}{c}
F_1=\Psi_{\mathcal{P}_1}^{1,0,\#}\\
F_2=\Psi_{\mathcal{P}_2}^{1,0,\#}\\
\vdots\\
F_n=\Psi_{\mathcal{P}_n}^{1,0,\#}\\
F_{n+1}=\Psi_{\mathcal{P}_{n+1}}^{1,0,\ast}\\
F_{n+2}=\Psi_{\mathcal{P}_{n+2}}^{1,0,\ast}\\
\vdots\\
F_{n+m}=\Psi_{\mathcal{P}_{n+m}}^{1,0,\ast}
\end{array}
\]

Nótese que cada \(F_i\) es \(\Sigma\)-computable y tiene dominio igual a \(\omega\). Sea \(F=[F_1,\ldots,F_{n+m}]\). Tenemos por definición que \(D_F=\omega\) y ya que \(F_{(i)}=F_i\), para cada \(i=1,\ldots,n+m\) tenemos que cada \(F_{(i)}\) es \(\Sigma\)-computable. Dejamos al lector verificar que \(I_F=S\). \(\blacksquare\)

Cuando un programa \(\mathcal{P}\) cumpla las propiedades dadas en (2) de la proposición anterior respecto de un conjunto \(S\), diremos que \(\mathcal{P}\) enumera a \(S\). Nótese que:

- Si \(S\subseteq\omega\) es no vacío, entonces \(\mathcal{P}\) enumera a \(S\) sii \(\operatorname{Dom}(\Psi_\mathcal{P}^{1,0,\#})=\omega\) y \(\operatorname{Im}(\Psi_\mathcal{P}^{1,0,\#})=S\)
- Si \(S\subseteq\Sigma^\ast\) es no vacío, entonces \(\mathcal{P}\) enumera a \(S\) sii \(\operatorname{Dom}(\Psi_\mathcal{P}^{1,0,\ast})=\omega\) y \(\operatorname{Im}(\Psi_\mathcal{P}^{1,0,\ast})=S\)

Cabe destacar que \((2)\Rightarrow(1)\) de la proposición anterior es muy útil a la hora de probar que un conjunto dado es \(\Sigma\)-enumerable ya que nos permite trabajar dentro de un solo programa.

**Ejercicio 16:** Sea \(\Sigma=\{\%,!\}\). Pruebe sin usar macros ni la proposición anterior que \(S=\{(2,\%\%),(3,!!!),(0,\varepsilon)\}\) es \(\Sigma\)-enumerable.

**Ejercicio 17:** Sea \(\Sigma=\{\%,!\}\). Pruebe sin usar macros ni la proposición anterior que \(S=\{(i,5,\%^{i}):i\in\omega\}\) es \(\Sigma\)-enumerable.

**Ejercicio 18:** Sea \(\Sigma=\{\%,!\}\). Sea \(L\subseteq\Sigma^\ast\) un conjunto no vacío y \(\Sigma\)-enumerable. De (usando macros) un programa \(\mathcal{P}\in Pro^\Sigma\) tal que \(\Psi_\mathcal{P}^{1,0,\ast}\) enumera al conjunto

\[
\{\alpha\%!:\alpha\in L\}
\]

es decir \(\operatorname{Dom}\Psi_\mathcal{P}^{1,0,\ast}=\omega\) y \(\operatorname{Im}(\Psi_\mathcal{P}^{1,0,\ast})=\{\alpha\%!:\alpha\in L\}\).

**Ejercicio 19:** Sea \(\Sigma=\{\%,!\}\). Sea

\[
S=\{(x,x+1,x+2,\%\%!!):x\in\omega\}.
\]

De sin usar macros un programa \(\mathcal{P}\in Pro^\Sigma\) el cual enumere a \(S\) (i.e. que cumpla (2) de la proposición anterior).

## Conjuntos \(\Sigma\)-computables

La versión imperativa o Neumanniana del concepto de conjunto \(\Sigma\)-efectivamente computable es fácil de dar: un conjunto \(S\subseteq\omega^n\times\Sigma^{\ast m}\) será llamado \(\Sigma\)-computable cuando la función \(\chi_S^{\omega^n\times\Sigma^{\ast m}}\) sea \(\Sigma\)-computable. O sea que \(S\subseteq\omega^n\times\Sigma^{\ast m}\) es \(\Sigma\)-computable sii hay un programa \(\mathcal{P}\in Pro^\Sigma\) el cual computa a \(\chi_S^{\omega^n\times\Sigma^{\ast m}}\), es decir:

- Si \((\overrightarrow{x},\overrightarrow{\alpha})\in S\), entonces \(\mathcal{P}\) se detiene partiendo desde \(\lVert x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\rVert\) y la variable \(\mathrm{N}1\) queda con contenido igual a \(1\)
- Si \((\overrightarrow{x},\overrightarrow{\alpha})\in(\omega^n\times\Sigma^{\ast m})-S\), entonces \(\mathcal{P}\) se detiene partiendo desde \(\lVert x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\rVert\) y la variable \(\mathrm{N}1\) queda con contenido igual a \(0\)

Si \(\mathcal{P}\) es un programa el cual computa a \(\chi_S^{\omega^n\times\Sigma^{\ast m}}\), diremos que \(\mathcal{P}\) decide la pertenencia a \(S\), con respecto al conjunto \(\omega^n\times\Sigma^{\ast m}\).

**Ejercicio 20:** Sea \(\Sigma=\{\%,!\}\). Pruebe sin usar macros que \(S=\{(2,\%\%),(3,!)\}\) es \(\Sigma\)-computable.

**Ejercicio 21:** Sea \(\Sigma=\{\%,!\}\). Pruebe sin usar macros que \(S=\{(i,\%^{i}):i\in\omega\}\) es \(\Sigma\)-computable.

**Ejercicio 22:** Sea \(\Sigma\) un alfabeto finito. Pruebe usando macros que

**(a)** Si \(P:S\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) y \(Q:S\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) son predicados \(\Sigma\)-computables, entonces \((P\lor Q)\), \((P\land Q)\) y \(\neg P\) lo son también.

**(b)** Si \(S_1,S_2\subseteq\omega^n\times\Sigma^{\ast m}\) son conjuntos \(\Sigma\)-computables, entonces \(S_1\cup S_2\), \(S_1\cap S_2\) y \(S_1-S_2\) son \(\Sigma\)-computables.

**Macros asociados a conjuntos \(\Sigma\)-computables.** El Primer Manantial de Macros nos dice que si \(S\subseteq\omega^n\times\Sigma^{\ast m}\) es un conjunto \(\Sigma\)-computable, entonces, ya que \(\chi_S^{\omega^n\times\Sigma^{\ast m}}\) es \(\Sigma\)-computable, en \(S^\Sigma\) hay un macro

\[
[\mathrm{IF}\ \chi_S^{\omega^n\times\Sigma^{\ast m}}(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\ \mathrm{GOTO}\ A1]
\]

Escribiremos el nombre de este macro de la siguiente manera más intuitiva:

\[
[\mathrm{IF}\ (V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\in S\ \mathrm{GOTO}\ A1]
\]

Nótese que las expansiones de este macro, dado que \(\chi_S^{\omega^n\times\Sigma^{\ast m}}\) es \(\Sigma\)-total, ya sea terminan por la última instrucción de la expansión o direccionan a la primera instrucción que tenga label igual al label que reemplazó a \(A1\) en la expansión. Es importante notar que para asegurar la existencia de este macro utilizamos que \(S\) es \(\Sigma\)-computable lo cual no siempre sucederá para un conjunto \(S\). Por ejemplo, puede pasar que \(S\) sea el dominio de una función \(\Sigma\)-computable pero que \(S\) no sea \(\Sigma\)-computable (esto se verá más adelante) y en tal caso no existirá en \(S^\Sigma\) un macro

\[
[\mathrm{IF}\ (V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\in S\ \mathrm{GOTO}\ A1]
\]

ya que si tal macro existiera sería fácil hacer un programa que compute a \(\chi_S^{\omega^n\times\Sigma^{\ast m}}\) lo cual nos diría que \(S\) es \(\Sigma\)-computable (ver el ejercicio posterior a la Proposición 4). Es muy común el error de suponer que existe un macro

\[
[\mathrm{IF}\ (V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\in S\ \mathrm{GOTO}\ A1]
\]

cuando \(S\) es el dominio de una función \(\Sigma\)-computable.
