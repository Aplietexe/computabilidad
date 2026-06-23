# GUÍA 8 DE LENGUAJES: BATALLAS ENTRE PARADIGMAS, TESIS DE CHURCH

En esta guía compararemos los tres paradigmas de computabilidad efectiva que hemos desarrollado anteriormente. Para esto probaremos que cada uno de dichos paradigmas "vence" al otro en el sentido que incluye por lo menos todas las funciones que incluye el otro en su modelización del concepto de función \(\Sigma\)-efectivamente computable. Por supuesto, esto dice que los tres son equivalentes.

## Neumann vence a Gödel

Usando macros podemos ahora probar que el paradigma imperativo de Neumann es por lo menos tan abarcativo como el funcional de Gödel. Más concretamente:

**Teorema 1 (Neumann vence a Gödel).** Si \(h\) es \(\Sigma\)-recursiva, entonces \(h\) es \(\Sigma\)-computable.

**Proof.** Probaremos por inducción en \(k\) que

\[
(*)\quad\text{Si }h\in R_k^\Sigma,\text{ entonces }h\text{ es }\Sigma\text{-computable.}
\]

El caso \(k=0\) es dejado al lector. Supongamos \((*)\) vale para \(k\), veremos que vale para \(k+1\). Sea \(h\in R_{k+1}^\Sigma-R_k^\Sigma\). Hay varios casos

Caso 1. Supongamos \(h=M(P)\), con \(P:\omega\times\omega^n\times\Sigma^{\ast m}\to\omega\), un predicado perteneciente a \(R_k^\Sigma\). Por hipótesis inductiva, \(P\) es \(\Sigma\)-computable y por lo tanto tenemos un macro

\[
\left[\mathrm{IF}\ P(V1,\ldots,V\overline{n+1},W1,\ldots,W\overline{m})\ \mathrm{GOTO}\ A1\right]
\]

lo cual nos permite realizar el siguiente programa

\[
\begin{array}{rl}
L2 & \left[\mathrm{IF}\ P(\mathrm{N}\overline{n+1},\mathrm{N}1,\ldots,\mathrm{N}\overline{n},\mathrm{P}1,\ldots,\mathrm{P}\overline{m})\ \mathrm{GOTO}\ L1\right]\\
& \mathrm{N}\overline{n+1}\leftarrow \mathrm{N}\overline{n+1}+1\\
& \mathrm{GOTO}\ L2\\
L1 & \mathrm{N}1\leftarrow \mathrm{N}\overline{n+1}
\end{array}
\]

Es fácil chequear que este programa computa \(h\).

Caso 2. Supongamos \(h=R(f,\mathcal{G})\), con

\[
\begin{aligned}
f&:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\Sigma^\ast\\
\mathcal{G}_a&:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times\Sigma^\ast\times\Sigma^\ast\to\Sigma^\ast,\quad a\in\Sigma
\end{aligned}
\]

elementos de \(R_k^\Sigma\). Sea \(\Sigma=\{a_1,\ldots,a_r\}\). Por hipótesis inductiva, las funciones \(f\), \(\mathcal{G}_a\), \(a\in\Sigma\), son \(\Sigma\)-computables y por lo tanto tenemos macros

\[
\left[W\overline{m+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\right]
\]

\[
\left[W\overline{m+3}\leftarrow \mathcal{G}_{a_i}(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m},W\overline{m+1},W\overline{m+2})\right],\quad i=1,\ldots,r
\]

Podemos entonces hacer el siguiente programa:

\[
\begin{array}{rl}
& \left[\mathrm{P}\overline{m+3}\leftarrow f(\mathrm{N}1,\ldots,\mathrm{N}\overline{n},\mathrm{P}1,\ldots,\mathrm{P}\overline{m})\right]\\
L\overline{r+1} & \mathrm{IF}\ \mathrm{P}\overline{m+1}\ \mathrm{BEGINS}\ a_1\ \mathrm{GOTO}\ L1\\
& \vdots\\
& \mathrm{IF}\ \mathrm{P}\overline{m+1}\ \mathrm{BEGINS}\ a_r\ \mathrm{GOTO}\ L\overline{r}\\
& \mathrm{GOTO}\ L\overline{r+2}\\
L1 & \mathrm{P}\overline{m+1}\leftarrow\curvearrowright\mathrm{P}\overline{m+1}\\
& \left[\mathrm{P}\overline{m+3}\leftarrow \mathcal{G}_{a_1}(\mathrm{N}1,\ldots,\mathrm{N}\overline{n},\mathrm{P}1,\ldots,\mathrm{P}\overline{m},\mathrm{P}\overline{m+2},\mathrm{P}\overline{m+3})\right]\\
& \mathrm{P}\overline{m+2}\leftarrow \mathrm{P}\overline{m+2}.a_1\\
& \mathrm{GOTO}\ L\overline{r+1}\\
& \vdots\\
L\overline{r} & \mathrm{P}\overline{m+1}\leftarrow\curvearrowright\mathrm{P}\overline{m+1}\\
& \left[\mathrm{P}\overline{m+3}\leftarrow \mathcal{G}_{a_r}(\mathrm{N}1,\ldots,\mathrm{N}\overline{n},\mathrm{P}1,\ldots,\mathrm{P}\overline{m},\mathrm{P}\overline{m+2},\mathrm{P}\overline{m+3})\right]\\
& \mathrm{P}\overline{m+2}\leftarrow \mathrm{P}\overline{m+2}.a_r\\
& \mathrm{GOTO}\ L\overline{r+1}\\
L\overline{r+2} & \mathrm{P}1\leftarrow \mathrm{P}\overline{m+3}
\end{array}
\]

Es fácil chequear que este programa computa \(h\).

El resto de los casos son dejados al lector. Un corolario importante de esta batalla es el:

**Proposición 2 (Segundo Manantial de Macros).** Sea \(\Sigma\) un alfabeto finito. Si

\[
\begin{aligned}
f&:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\\
g&:D_g\subseteq\omega^n\times\Sigma^{\ast m}\to\Sigma^\ast\\
P&:D_P\subseteq\omega^n\times\Sigma^{\ast m}\to\{0,1\}
\end{aligned}
\]

son \(\Sigma\)-recursivas, entonces en \(S^\Sigma\) hay macros

\[
\left[V\overline{n+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\right]
\]

\[
\left[W\overline{m+1}\leftarrow g(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\right]
\]

\[
\left[\mathrm{IF}\ P(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\ \mathrm{GOTO}\ A1\right]
\]

Recordemos que el Primer Manantial de Macros es dado en la Guía 7 al final de la sección sobre macros.

**Ejercicio 1:** Pruebe el Segundo Manantial de Macros.

**Se lleno de macros.** Cabe destacar que el Segundo Manantial de Macros nos dice que en \(S^\Sigma\) hay macros

\[
\left[V\overline{n+1}\leftarrow f(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\right]
\]

\[
\left[W\overline{m+1}\leftarrow g(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\right]
\]

\[
\left[\mathrm{IF}\ P(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\ \mathrm{GOTO}\ A1\right]
\]

para todas las funciones \(\Sigma\)-mixtas y predicados \(\Sigma\)-mixtos que hemos trabajado hasta el momento en la materia ya que todas eran \(\Sigma\)-p.r.. Esto fortalece mucho al lenguaje \(S^\Sigma\) ya que ahora tenemos macros para todas las funciones y predicados cotidianos en la matemática, además de tener macros para todas las funciones y predicados \(\Sigma\)-computables, debido al Primer Manantial de Macros. Veamos un ejemplo:

**Lema 3.** Supongamos \(S_1,S_2\subseteq\omega^n\times\Sigma^{\ast m}\) son conjuntos \(\Sigma\)-enumerables. Entonces \(S_1\cup S_2\) es \(\Sigma\)-enumerable.

**Proof.** Podemos suponer que ni \(S_1\) ni \(S_2\) son vacíos ya que de lo contrario el resultado es trivial. Además supondremos que \(n=2\) y \(m=1\).

La idea de la prueba es la misma que la que usamos para probar que la unión de conjuntos \(\Sigma\)-efectivamente enumerables es \(\Sigma\)-efectivamente enumerable. Daremos usando macros un programa que enumera a \(S_1\cup S_2\) y luego aplicaremos la Proposición de Caracterización de \(\Sigma\)-enumerabilidad de la Guía 7. Por hipótesis hay funciones \(F:\omega\to\omega\times\omega\times\Sigma^\ast\) y \(G:\omega\to\omega\times\omega\times\Sigma^\ast\) tales que \(F_{(1)}\), \(F_{(2)}\), \(F_{(3)}\), \(G_{(1)}\), \(G_{(2)}\) y \(G_{(3)}\) son \(\Sigma\)-computables, \(\operatorname{Im}(F)=S_1\) y \(\operatorname{Im}(G)=S_2\). O sea que nuestro Primer Manantial de Macros nos dice que en \(S^\Sigma\) hay macros

\[
\begin{array}{c}
\left[V2\leftarrow F_{(1)}(V1)\right]\\
\left[V2\leftarrow F_{(2)}(V1)\right]\\
\left[W1\leftarrow F_{(3)}(V1)\right]\\
\left[V2\leftarrow G_{(1)}(V1)\right]\\
\left[V2\leftarrow G_{(2)}(V1)\right]\\
\left[W1\leftarrow G_{(3)}(V1)\right]
\end{array}
\]

Ya que el predicado \(Par=\lambda x[x\text{ es par}]\) es \(\Sigma\)-p.r., el Segundo Manantial de Macros nos dice que en \(S^\Sigma\) hay un macro:

\[
\left[\mathrm{IF}\ Par(V1)\ \mathrm{GOTO}\ A1\right]
\]

el cual escribiremos de la siguiente manera más intuitiva

\[
\left[\mathrm{IF}\ V1\text{ es par }\mathrm{GOTO}\ A1\right]
\]

Ya que la función \(D=\lambda x[\lfloor x/2\rfloor]\) es \(\Sigma\)-p.r., el Segundo Manantial de Macros nos dice que hay un macro:

\[
\left[V2\leftarrow D(V1)\right]
\]

el cual escribiremos de la siguiente manera más intuitiva

\[
\left[V2\leftarrow \lfloor V1/2\rfloor\right]
\]

Sea \(\mathcal{P}\) el siguiente programa:

\[
\begin{array}{rl}
& \left[\mathrm{IF}\ \mathrm{N}1\text{ es par }\mathrm{GOTO}\ L1\right]\\
& \mathrm{N}1\leftarrow \mathrm{N}1\mathbin{\dot{-}}1\\
& \left[\mathrm{N}1111\leftarrow \lfloor \mathrm{N}1/2\rfloor\right]\\
& \left[\mathrm{N}1\leftarrow G_{(1)}(\mathrm{N}1111)\right]\\
& \left[\mathrm{N}2\leftarrow G_{(2)}(\mathrm{N}1111)\right]\\
& \left[\mathrm{P}1\leftarrow G_{(3)}(\mathrm{N}1111)\right]\\
& \mathrm{GOTO}\ L2\\
L1 & \left[\mathrm{N}1111\leftarrow \lfloor \mathrm{N}1/2\rfloor\right]\\
& \left[\mathrm{N}1\leftarrow F_{(1)}(\mathrm{N}1111)\right]\\
& \left[\mathrm{N}2\leftarrow F_{(2)}(\mathrm{N}1111)\right]\\
& \left[\mathrm{P}1\leftarrow F_{(3)}(\mathrm{N}1111)\right]\\
L2 & \mathrm{SKIP}
\end{array}
\]

Es fácil ver que \(\mathcal{P}\) cumple (a) y (b) de (2) de la Proposición de Caracterización de \(\Sigma\)-enumerabilidad de la Guía 7 por lo cual \(S_1\cup S_2\) es \(\Sigma\)-enumerable.

En forma análoga a lo hecho recién, se pueden probar, copiando la respectiva idea en el paradigma de la computabilidad efectiva, los siguientes resultados, los cuales son dejados como ejercicios.

**Ejercicio 2:** Use los macros asociados a las "bajadas" y a \(\ast^\le\) para dar un programa que enumere a \(\omega\times\omega\times\Sigma^\ast\), es decir que cumpla (a) y (b) de (2) de la Proposición de Caracterización de \(\Sigma\)-enumerabilidad de la Guía 7.

**Ejercicio 3:** Supongamos \(S_1,S_2\subseteq\omega^n\times\Sigma^{\ast m}\) son conjuntos \(\Sigma\)-enumerables. Entonces \(S_1\cap S_2\) es \(\Sigma\)-enumerable. (Hacer el caso \(n=2\), \(m=1\) e inspírese en el paradigma efectivo)

En la Guía 3 probamos que si \(S\subseteq\omega^n\times\Sigma^{\ast m}\) es \(\Sigma\)-efectivamente computable entonces \(S\) es \(\Sigma\)-efectivamente enumerable. Vía el uso de macros adecuados podemos copiar la idea de la prueba de dicho resultado para probar el siguiente

**Lema 4.** Sea \(S\subseteq\omega^n\times\Sigma^{\ast m}\). Si \(S\) es \(\Sigma\)-computable, entonces \(S\) es \(\Sigma\)-enumerable

**Ejercicio 4:** Pruebe el lema anterior (haga el caso \(n=2\), \(m=1\))

**Ejercicio 5:** Si \(S\subseteq\Sigma^\ast\) es \(\Sigma\)-enumerable, entonces

\[
T=\{\alpha\in\Sigma^\ast:\text{ existe }\beta\in S\text{ tal que }\alpha\text{ es subpalabra de }\beta\}
\]

también es \(\Sigma\)-enumerable.

**Ejercicio 6:** Sean \(S\subseteq\omega\) y \(L\subseteq\{@,\uparrow\}^\ast\) tales que \((0,\varepsilon)\in S\times L\). Entonces \(S\times L\) es \(\{@,\uparrow\}\)-enumerable si y solo si ambos \(S\) y \(L\) son \(\{@,\uparrow\}\)-enumerables

O sea que con el uso de nuestros poderosos macros asociados a funciones y predicados \(\Sigma\)-p.r. (gracias al Segundo Manantial) más los que provee el Primer Manantial podemos simular los procedimientos efectivos realizados dentro del paradigma filosófico con programas concretos del lenguaje \(S^\Sigma\). Pero esto no es del todo así, ya que los ejemplos vistos recién no hacen uso del concepto de "ejecución de una cantidad de pasos", idea que en muchos diseños de nuestros procedimientos efectivos es usada. Por ejemplo si queremos "copiar" dentro del paradigma imperativo la prueba del resultado

- Si \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) es una función \(\Sigma\)-efectivamente computable, entonces \(D_f\) es \(\Sigma\)-efectivamente enumerable

notaremos la dificultad de aún no poder hablar de cantidad de pasos en la ejecución del programa que compute a \(f\). O sea nuestro Primer Manantial nos da un macro de asignación para \(f\) pero no es claro de cómo correr una expansión de dicho macro una cierta cantidad de veces. Esto lo lograremos usando macros asociados a las funciones \(Halt^{n,m}\), \(E_\#^{n,m}\) y \(E_\ast^{n,m}\) las cuales se usan en la batalla Gödel vence a Neumann que viene a continuación. Estas funciones serán clave a la hora de simular con programas a procedimientos efectivos que en su funcionamiento involucran el funcionamiento de otros procedimientos efectivos.

O sea que luego de ambas batallas entre Gödel y Neumann, el paradigma imperativo se verá fortalecido sustancialmente. También más adelante en la Guía 9 veremos cómo los desarrollos hechos en ambas batallas entre Gödel y Neumann fortalecen al paradigma funcional.

## Gödel vence a Neumann

Primero definiremos tres funciones las cuales contienen toda la información acerca del funcionamiento del lenguaje \(S^\Sigma\). Sean \(n,m\in\omega\), fijos. Definamos

\[
\begin{aligned}
i^{n,m}&:\omega\times\omega^n\times\Sigma^{\ast m}\times Pro^\Sigma\to\omega\\
E_\#^{n,m}&:\omega\times\omega^n\times\Sigma^{\ast m}\times Pro^\Sigma\to\omega^{[\mathbf{N}]}\\
E_\ast^{n,m}&:\omega\times\omega^n\times\Sigma^{\ast m}\times Pro^\Sigma\to\Sigma^{\ast[\mathbf{N}]}
\end{aligned}
\]

de la siguiente manera

\[
\begin{aligned}
&(i^{n,m}(0,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}),E_\#^{n,m}(0,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}),E_\ast^{n,m}(0,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}))\\
&\quad=(1,(x_1,\ldots,x_n,0,\ldots),(\alpha_1,\ldots,\alpha_m,\varepsilon,\ldots))\\
&(i^{n,m}(t+1,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}),E_\#^{n,m}(t+1,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}),E_\ast^{n,m}(t+1,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}))\\
&\quad=S_\mathcal{P}(i^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}),E_\#^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}),E_\ast^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}))
\end{aligned}
\]

Nótese que

\[
(i^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}),E_\#^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}),E_\ast^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}))
\]

es la descripción instantánea que se obtiene luego de correr \(\mathcal{P}\) una cantidad \(t\) de pasos partiendo del estado

\[
((x_1,\ldots,x_n,0,\ldots),(\alpha_1,\ldots,\alpha_m,\varepsilon,\ldots))
\]

Es importante notar que si bien \(i^{n,m}\) es una función \((\Sigma\cup\Sigma_p)\)-mixta, ni \(E_\#^{n,m}\) ni \(E_\ast^{n,m}\) lo son.

Definamos para cada \(j\in\mathbf{N}\), funciones

\[
\begin{aligned}
E_{\#j}^{n,m}&:\omega\times\omega^n\times\Sigma^{\ast m}\times Pro^\Sigma\to\omega\\
E_{\ast j}^{n,m}&:\omega\times\omega^n\times\Sigma^{\ast m}\times Pro^\Sigma\to\Sigma^\ast
\end{aligned}
\]

de la siguiente manera

\[
\begin{aligned}
E_{\#j}^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P})&=j\text{-ésima coordenada de }E_\#^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P})\\
E_{\ast j}^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P})&=j\text{-ésima coordenada de }E_\ast^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P})
\end{aligned}
\]

(es claro que estas funciones son \((\Sigma\cup\Sigma_p)\)-mixtas). Nótese que

\[
\begin{aligned}
E_\#^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P})&=(E_{\#1}^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}),E_{\#2}^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}),\ldots)\\
E_\ast^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P})&=(E_{\ast1}^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}),E_{\ast2}^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P}),\ldots)
\end{aligned}
\]

Aceptaremos sin prueba la siguiente proposición (ver el apunte por una prueba).

**Proposición 5.** Sean \(n,m\ge 0\). Las funciones \(i^{n,m}\), \(E_{\#j}^{n,m}\), \(E_{\ast j}^{n,m}\), \(j=1,2,\ldots\), son \((\Sigma\cup\Sigma_p)\)-p.r.

**Las funciones \(Halt^{n,m}\) y \(T^{n,m}\).** Dados \(n,m\in\omega\), definamos:

\[
Halt^{n,m}=\lambda t\overrightarrow{x}\overrightarrow{\alpha}\mathcal{P}\left[i^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P})=n(\mathcal{P})+1\right]
\]

Nótese que \(D_{Halt^{n,m}}=\omega\times\omega^n\times\Sigma^{\ast m}\times Pro^\Sigma\) (ojo que aquí la notación lambda es respecto del alfabeto \(\Sigma\cup\Sigma_p\)). Además nótese que usamos la variable \(\mathcal{P}\) en la notación lambda por un tema de comodidad psicológica dado que \(i^{n,m}\) está definida solo cuando la última coordenada es un programa pero podríamos haber escrito \(\lambda t\overrightarrow{x}\overrightarrow{\alpha}\alpha[i^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\alpha)=n(\alpha)+1]\) y sigue siendo la misma función.

Cabe destacar que \(Halt^{n,m}\) tiene una descripción muy intuitiva, ya que dado \((t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P})\in\omega\times\omega^n\times\Sigma^{\ast m}\times Pro^\Sigma\), tenemos que \(Halt^{n,m}(t,\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P})=1\) si y solo si el programa \(\mathcal{P}\) se detiene luego de \(t\) pasos partiendo desde el estado \(\lVert x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\rVert\). En particular \(Halt^{0,0}\) tiene dominio igual a \(\omega\times Pro^\Sigma\) y tenemos que \(Halt^{0,0}(t,\mathcal{P})=1\) si y solo si el programa \(\mathcal{P}\) se detiene luego de \(t\) pasos partiendo desde el estado \(\lVert\diamond\rVert\).

Aceptaremos sin demostración el siguiente lema (ver el apunte por una prueba).

**Lema 6.**

**(a)** \(Pro^\Sigma\) es un conjunto \((\Sigma\cup\Sigma_p)\)-p.r.

**(b)** \(\lambda\mathcal{P}[n(\mathcal{P})]\) y \(\lambda i\mathcal{P}[I_i^\mathcal{P}]\) son funciones \((\Sigma\cup\Sigma_p)\)-p.r..

**Ejercicio 7:** De una función \(f:\omega\times Pro^\Sigma\to Pro^\Sigma\) la cual sea \((\Sigma\cup\Sigma_p)\)-p.r. y cumpla que

**(a)** \(D_{\Psi_{f(x,\mathcal{P})}^{0,1,\#}}=D_{\Psi_\mathcal{P}^{0,1,\#}}\), para cada \(x\in\omega\) y \(\mathcal{P}\in Pro^\Sigma\)

**(b)** \(\Psi_{f(x,\mathcal{P})}^{0,1,\#}(\alpha)=\Psi_\mathcal{P}^{0,1,\#}(\alpha)+x\), para cada \(x\in\omega\), \(\mathcal{P}\in Pro^\Sigma\) y \(\alpha\in D_{\Psi_\mathcal{P}^{0,1,\#}}\)

Pruebe que \(f\) es \((\Sigma\cup\Sigma_p)\)-p.r.

Ahora podemos probar el siguiente importante resultado.

**Lema 7.** \(Halt^{n,m}\) es \((\Sigma\cup\Sigma_p)\)-p.r.

**Proof.** Notar que

\[
Halt^{n,m}=\lambda xy[x=y]\circ\left[i^{n,m},\lambda\mathcal{P}[n(\mathcal{P})+1]\circ p_{1+n+m+1}^{1+n,m+1}\right].
\]

Ahora definamos \(T^{n,m}=M(Halt^{n,m})\). Nótese que

\[
\begin{aligned}
D_{T^{n,m}}=\{(\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P})\in{}&\omega^n\times\Sigma^{\ast m}\times Pro^\Sigma:\\
&\mathcal{P}\text{ se detiene partiendo de }\lVert x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\rVert\}
\end{aligned}
\]

y para \((\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P})\in D_{T^{n,m}}\) tenemos que \(T^{n,m}(\overrightarrow{x},\overrightarrow{\alpha},\mathcal{P})=\) cantidad de pasos necesarios para que \(\mathcal{P}\) se detenga partiendo de \(\lVert x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\rVert\). En algún sentido, la función \(T^{n,m}\) mide el "tiempo" que tarda en detenerse \(\mathcal{P}\) desde \(\lVert x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m\rVert\) y de ahí su nombre. Nótese que para el caso \(n=m=0\) tenemos que

\[
D_{T^{0,0}}=\{\mathcal{P}\in Pro^\Sigma:\mathcal{P}\text{ se detiene partiendo de }\lVert\diamond\rVert\}
\]

y para \(\mathcal{P}\in D_{T^{0,0}}\) tenemos que \(T^{0,0}(\mathcal{P})=\) cantidad de pasos necesarios para que \(\mathcal{P}\) se detenga partiendo de \(\lVert\diamond\rVert\).

**Proposición 8.** \(T^{n,m}\) es \((\Sigma\cup\Sigma_p)\)-recursiva

**Proof.** Es directo del lema de minimización ya que \(Halt^{n,m}\) es \((\Sigma\cup\Sigma_p)\)-p.r.

Ahora nos será fácil probar que el paradigma de Gödel es por lo menos tan abarcativo como el imperativo de Von Neumann. Más concretamente:

**Teorema 9 (Gödel vence a Neumann).** Si \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to O\) es \(\Sigma\)-computable, entonces \(f\) es \(\Sigma\)-recursiva.

**Proof.** Haremos el caso \(O=\Sigma^\ast\). Sea \(\mathcal{P}_0\) un programa que compute a \(f\). Primero veremos que \(f\) es \((\Sigma\cup\Sigma_p)\)-recursiva. Note que

\[
f=E_{\ast1}^{n,m}\circ\left[T^{n,m}\circ[p_1^{n,m},\ldots,p_{n+m}^{n,m},C_{\mathcal{P}_0}^{n,m}],p_1^{n,m},\ldots,p_{n+m}^{n,m},C_{\mathcal{P}_0}^{n,m}\right]
\]

donde cabe destacar que \(p_1^{n,m},\ldots,p_{n+m}^{n,m}\) son las proyecciones respecto del alfabeto \(\Sigma\cup\Sigma_p\), es decir que tienen dominio \(\omega^n\times(\Sigma\cup\Sigma_p)^{\ast m}\). Esto nos dice que \(f\) es \((\Sigma\cup\Sigma_p)\)-recursiva. O sea que el Teorema de Independencia del Alfabeto nos dice que \(f\) es \(\Sigma\)-recursiva.

Aceptaremos sin prueba la siguiente proposición.

**Proposición 10.** La función \(T^{n,m}\) no es \((\Sigma\cup\Sigma_p)\)-p.r.

**Corolario 11.** En general la minimización de un predicado \(\Sigma\)-p.r. no necesariamente es \(\Sigma\)-p.r.

**Proof.** Si consideramos el alfabeto \((\Sigma\cup\Sigma_p)\) tenemos que \(T^{n,m}=M(Halt^{n,m})\) y \(T^{n,m}\) no es \((\Sigma\cup\Sigma_p)\)-p.r.

**Uso de macros asociados a las funciones \(Halt^{n,m}\), \(E_\#^{n,m}\) y \(E_\ast^{n,m}\).** Aquí veremos, con ejemplos, cómo ciertos macros nos permitirán dentro de un programa hablar acerca del funcionamiento de otro programa. En este sentido los desarrollos de las dos batallas entre Neumann y Gödel nos permiten fortalecer notablemente al paradigma imperativo en su rol modelizador (o simulador) de los procedimientos efectivos. Esto es importante ya que el paradigma más cómodo, amplio e intuitivo es sin duda el filosófico de Leibniz.

Veamos el primer ejemplo. Probaremos que:

- Si \(f:D_f\subseteq\omega\to\omega\) es \(\Sigma\)-computable, \(0\in D_f\) y \(f(0)=2\), entonces

\[
S=\{x\in D_f:f(x)\ne 0\}
\]

es \(\Sigma\)-enumerable.

Nótese que \(0\in S\) por lo cual \(S\) es no vacío así que en virtud de la Caracterización de \(\Sigma\)-enumerabilidad dada en la Guía 7, deberemos encontrar un programa \(\mathcal{P}\in Pro^\Sigma\) que enumere a \(S\), es decir tal que \(\operatorname{Dom}\Psi_\mathcal{P}^{1,0,\#}=\omega\) y \(\operatorname{Im}(\Psi_\mathcal{P}^{1,0,\#})=S\). Dicho en palabras, el programa \(\mathcal{P}\) deberá cumplir:

- Siempre que lo corramos desde un estado de la forma \(\lVert x\rVert\), con \(x\in\omega\), debe detenerse y el contenido de la variable N1 bajo detención deberá ser un elemento de \(S\)
- Para cada \(s\in S\) deberá haber un \(x\in\omega\) tal que \(s\) es el valor de la variable N1 bajo detención cuando corremos \(\mathcal{P}\) desde \(\lVert x\rVert\)

Sea \(\mathcal{P}_0\in Pro^\Sigma\) un programa que compute a \(f\). Usaremos \(\mathcal{P}_0\) para diseñar \(\mathcal{P}\). A continuación daremos una descripción intuitiva del funcionamiento de \(\mathcal{P}\) (pseudocódigo) para luego escribirlo correctamente usando macros. El programa \(\mathcal{P}\) comenzará del estado \(\lVert x\rVert\) y hará las siguientes tareas

Etapa 1: si \(x=0\) ir a Etapa 6, en caso contrario ir a Etapa 2.

Etapa 2: calcular \((x)_1\) y \((x)_2\) e ir a Etapa 3.

Etapa 3: si \(\mathcal{P}_0\) termina desde \(\lVert(x)_1\rVert\) en \((x)_2\) pasos ir a Etapa 4, en caso contrario ir a Etapa 6

Etapa 4: si el valor que queda en N1 luego de correr \(\mathcal{P}_0\) una cantidad \((x)_2\) de pasos, partiendo de \(\lVert(x)_1\rVert\), es distinto de \(0\), entonces ir a Etapa 5. En caso contrario ir a Etapa 6.

Etapa 5: asignar a N1 el valor \((x)_1\) y terminar

Etapa 6: asignar a N1 el valor \(0\) y terminar

Nótese que la descripción anterior no es ni más ni menos que un procedimiento efectivo (efectivizable) que enumera a \(S\), y nuestra misión es simularlo dentro del lenguaje \(S^\Sigma\). Para esto usaremos varios macros. Ya que la función \(f=\lambda x[(x)_1]\) es \(\Sigma\)-p.r., el Segundo Manantial de Macros nos dice que en \(S^\Sigma\) hay un macro:

\[
\left[V2\leftarrow f(V1)\right]
\]

el cual escribiremos de la siguiente manera más intuitiva:

\[
\left[V2\leftarrow (V1)_1\right]
\]

Similarmente hay un macro:

\[
\left[V2\leftarrow (V1)_2\right]
\]

También, ya que el predicado \(P=\lambda x[x=0]\) es \(\Sigma\)-recursivo, hay un macro:

\[
\left[\mathrm{IF}\ P(V1)\ \mathrm{GOTO}\ A1\right]
\]

el cual escribiremos de la siguiente manera:

\[
\left[\mathrm{IF}\ V1=0\ \mathrm{GOTO}\ A1\right]
\]

Definamos

\[
H=\lambda tx\left[Halt^{1,0}(t,x,\mathcal{P}_0)\right]
\]

Notar que \(D_H=\omega^2\) y que \(H\) es \(\Sigma\)-mixta. Además sabemos que la función \(Halt^{1,0}\) es \((\Sigma\cup\Sigma_p)\)-p.r. por lo cual resulta fácilmente que \(H\) es \((\Sigma\cup\Sigma_p)\)-p.r.. Por la Proposición de Independencia del Alfabeto tenemos que \(H\) es \(\Sigma\)-p.r.. O sea que el Segundo Manantial de Macros nos dice que en \(S^\Sigma\) hay un macro:

\[
\left[\mathrm{IF}\ H(V1,V2)\ \mathrm{GOTO}\ A1\right]
\]

Para hacer más intuitivo el uso de este macro lo escribiremos de la siguiente manera

\[
\left[\mathrm{IF}\ Halt^{1,0}(V1,V2,\mathcal{P}_0)\ \mathrm{GOTO}\ A1\right]
\]

Sea

\[
g=\lambda tx\left[E_{\#1}^{1,0}(t,x,\mathcal{P}_0)\right]
\]

Ya que \(g\) es \(\Sigma\)-recursiva (por qué?), hay en \(S^\Sigma\) un macro:

\[
\left[V3\leftarrow g(V1,V2)\right]
\]

Para hacer más intuitivo el uso de este macro lo escribiremos de la siguiente manera

\[
\left[V3\leftarrow E_{\#1}^{1,0}(V1,V2,\mathcal{P}_0)\right]
\]

Ahora sí podemos dar nuestro programa \(\mathcal{P}\) que enumera a \(S\):

\[
\begin{array}{rl}
& \mathrm{IF}\ \mathrm{N}1\ne 0\ \mathrm{GOTO}\ L1\\
& \mathrm{GOTO}\ L2\\
L1 & \left[\mathrm{N}3\leftarrow(\mathrm{N}1)_1\right]\\
& \left[\mathrm{N}4\leftarrow(\mathrm{N}1)_2\right]\\
& \left[\mathrm{IF}\ Halt^{1,0}(\mathrm{N}4,\mathrm{N}3,\mathcal{P}_0)\ \mathrm{GOTO}\ L3\right]\\
& \mathrm{GOTO}\ L2\\
L3 & \left[\mathrm{N}5\leftarrow E_{\#1}^{1,0}(\mathrm{N}4,\mathrm{N}3,\mathcal{P}_0)\right]\\
& \left[\mathrm{IF}\ \mathrm{N}5=0\ \mathrm{GOTO}\ L2\right]\\
& \mathrm{N}1\leftarrow\mathrm{N}3\\
& \mathrm{GOTO}\ L4\\
L2 & \mathrm{N}1\leftarrow 0\\
L4 & \mathrm{SKIP}
\end{array}
\]

Para hacer la próxima tanda de ejercicios recomendamos al lector que repase la definición de cuando "un programa \(\mathcal{P}\in Pro^\Sigma\) enumera a un conjunto \(S\subseteq\omega^n\times\Sigma^{\ast m}\)" (ver después de la Caracterización de \(\Sigma\)-enumerabilidad dada en la Guía 7).

**Ejercicio 8:** Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(f:D_f\subseteq\omega\times\omega\times\Sigma^\ast\to\omega\) es \(\Sigma\)-computable y \((0,0,\varepsilon)\in D_f\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto \(D_f\).

**Ejercicio 9:** Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(f:D_f\subseteq\omega\times\omega\times\Sigma^\ast\to\omega\) es \(\Sigma\)-computable y \((0,0,\varepsilon)\in D_f\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto \(\operatorname{Im}(f)\).

**Ejercicio 10:** Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(f:L_1\to L_2\), con \(L_1,L_2\subseteq\Sigma^\ast\), es \(\Sigma\)-computable y biyectiva. De un programa de \(S^\Sigma\) (usando macros) que compute a \(f^{-1}\).

**Ejercicio 11:** Sea \(\Sigma=\{\#,\$\}\) y sea \(f:D_f\subseteq\Sigma^\ast\to\omega\) una función \(\Sigma\)-computable tal que \(f(\varepsilon)=1\). Sea \(L=\{\alpha\in D_f:f(\alpha)=1\}\). De un programa \(\mathcal{Q}\in Pro^\Sigma\) (usando macros) el cual enumere a \(L\) (explicado en video en granlogico.com).

**Ejercicio 12:** Sea \(\Sigma=\{@,\%\}\) y sea \(\mathcal{P}_0\in Pro^\Sigma\). Sea

\[
S=\{(x,\alpha):\Psi_{\mathcal{P}_0}^{1,0,\#}(x)=\Psi_{\mathcal{P}_0}^{0,1,\#}(\alpha)\}
\]

Note que \((0,\varepsilon)\in S\). De un programa \(\mathcal{Q}\in Pro^\Sigma\) (usando macros) que enumere al conjunto \(S\).

**Ejercicio 13:** Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(f:S\subseteq\omega\to\omega\) es \(\Sigma\)-computable, \(0\in S\) y \(f(0)=0\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
H=\{x\in S:x\text{ es par }x/2\in S\text{ y }f(x)=f(x/2)\}
\]

**Ejercicio 14:** Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(f:S\subseteq\omega\to\omega\) es \(\Sigma\)-computable, \(0\in S\) y \(f(0)=0\). De un programa \(\mathcal{P}_0\in Pro^\Sigma\) (usando macros) tal que

\[
\operatorname{Dom}(\Psi_{\mathcal{P}_0}^{1,0,\#})=\{x\in S:x\text{ es par }x/2\in S\text{ y }f(x)=f(x/2)\}
\]

**Ejercicio 15:** Sea \(\Sigma=\{@,\&\}\). Supongamos \(f:S\subseteq\omega\times\omega\to\omega\) es \(\Sigma\)-computable. Suponga además que \((0,0)\in S\) y \(f(0,0)=0\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
H=\{(x,y)\in S:(f(x,y),y)\in S\text{ y }f(f(x,y),y)=0\}
\]

**Ejercicio 16:** Sean \(f:D_f\subseteq\omega\times\Sigma^\ast\to\omega\) y \(g:D_g\subseteq\omega\times\Sigma^\ast\to\omega\) funciones \(\Sigma\)-computables tales que \(D_f\cap D_g=\emptyset\). Sea \(F:D_f\cup D_g\to\omega\) dada por

\[
e\mapsto
\begin{cases}
f(e)&\text{si }e\in D_f\\
g(e)&\text{si }e\in D_g
\end{cases}
\]

De un programa de \(S^\Sigma\) (usando macros) que compute a \(F\).

**Enumeración de conjuntos de programas.** Ya que los programas de \(S^\Sigma\) son palabras del alfabeto \(\Sigma\cup\Sigma_p\), nos podemos preguntar cuando un conjunto \(L\) de programas es \((\Sigma\cup\Sigma_p)\)-enumerable. Daremos un ejemplo. Sea \(\Sigma=\{@,!\}\) y sea

\[
L=\{\mathcal{P}\in Pro^\Sigma:\Psi_\mathcal{P}^{1,0,\#}(10)=10\}
\]

Veremos que \(L\) es \((\Sigma\cup\Sigma_p)\)-enumerable, dando un programa \(\mathcal{Q}\in Pro^{\Sigma\cup\Sigma_p}\) que enumere a \(L\), es decir tal que \(\operatorname{Dom}(\Psi_\mathcal{Q}^{1,0,\ast})=\omega\) y \(\operatorname{Im}(\Psi_\mathcal{Q}^{1,0,\ast})=L\). Cabe destacar que aquí hay en juego dos versiones de nuestro lenguaje imperativo, es decir enumeraremos un conjunto de programas de \(S^\Sigma\) usando un programa de \(S^{\Sigma\cup\Sigma_p}\). Sea \(\le\) un orden total sobre el conjunto \(\Sigma\cup\Sigma_p\).

A continuación daremos una descripción intuitiva del funcionamiento de \(\mathcal{Q}\) (pseudocódigo) para luego escribirlo correctamente usando macros. Nótese que \(\mathrm{SKIP}\in L\). El programa \(\mathcal{Q}\) comenzará del estado \(\lVert x\rVert\) y hará las siguientes tareas

Etapa 1: si \(x=0\) ir a Etapa 6, en caso contrario ir a Etapa 2.

Etapa 2: calcular \((x)_1\), \((x)_2\) y \(\ast^\le((x)_1)\) e ir a Etapa 3.

Etapa 3: si \(\ast^\le((x)_1)\in Pro^\Sigma\) y termina partiendo desde \(\lVert10\rVert\) en \((x)_2\) pasos ir a Etapa 4, en caso contrario ir a Etapa 6

Etapa 4: si el valor que queda en N1 luego de correr \(\ast^\le((x)_1)\) una cantidad \((x)_2\) de pasos, partiendo de \(\lVert10\rVert\) es igual a \(10\), entonces ir a Etapa 5. En caso contrario ir a Etapa 6.

Etapa 5: asignar a P1 la palabra \(\ast^\le((x)_1)\) y terminar

Etapa 6: asignar a P1 la palabra SKIP y terminar

Nótese que la descripción anterior no es ni más ni menos que un procedimiento efectivo que enumera a \(L\), y nuestra misión es simularlo dentro del lenguaje \(S^{\Sigma\cup\Sigma_p}\). Para esto usaremos varios macros. Es importante notar que los macros que usaremos corresponden al lenguaje \(S^{\Sigma\cup\Sigma_p}\) ya que los usaremos en \(\mathcal{Q}\) el cual será un programa de \(S^{\Sigma\cup\Sigma_p}\).

Ya que las funciones \(\lambda x[(x)_1]\) y \(\lambda x[(x)_2]\) son \((\Sigma\cup\Sigma_p)\)-recursivas el Segundo Manantial nos dice que hay macros en \(S^{\Sigma\cup\Sigma_p}\) asociados a estas funciones los cuales escribiremos de la siguiente manera más intuitiva:

\[
\begin{array}{c}
\left[V2\leftarrow(V1)_1\right]\\
\left[V2\leftarrow(V1)_2\right]
\end{array}
\]

Ya que el predicado \(P=\lambda x[x=10]\) es \((\Sigma\cup\Sigma_p)\)-recursivo tenemos en \(S^{\Sigma\cup\Sigma_p}\) su macro asociado el cual escribiremos de la siguiente manera:

\[
\left[\mathrm{IF}\ V1=10\ \mathrm{GOTO}\ A1\right]
\]

Por un lema anterior sabemos que \(Pro^\Sigma\) es un conjunto \((\Sigma\cup\Sigma_p)\)-p.r., por lo cual \(\chi_{Pro^\Sigma}^{(\Sigma\cup\Sigma_p)^\ast}\) es \((\Sigma\cup\Sigma_p)\)-p.r., y por lo tanto hay un macro

\[
\left[\mathrm{IF}\ \chi_{Pro^\Sigma}^{(\Sigma\cup\Sigma_p)^\ast}(W1)\ \mathrm{GOTO}\ A1\right]
\]

el cual escribiremos de la siguiente manera

\[
\left[\mathrm{IF}\ W1\in Pro^\Sigma\ \mathrm{GOTO}\ A1\right]
\]

Ya que el predicado \(Halt^{1,0}\) es \((\Sigma\cup\Sigma_p)\)-recursivo tenemos un macro asociado a él, el cual escribiremos de la siguiente forma

\[
\left[\mathrm{IF}\ Halt^{1,0}(V1,V2,W1)\ \mathrm{GOTO}\ A1\right]
\]

Ya que \(E_{\#1}^{1,0}\) es \((\Sigma\cup\Sigma_p)\)-recursivo tenemos un macro asociado a ella, el cual escribiremos de la siguiente forma

\[
\left[V3\leftarrow E_{\#1}^{1,0}(V1,V2,W1)\right]
\]

También usaremos macros

\[
\begin{array}{c}
\left[V1\leftarrow 10\right]\\
\left[W1\leftarrow \mathrm{SKIP}\right]
\end{array}
\]

(dejamos al lector hacerlos a mano o también se puede justificar su existencia vía el Segundo Manantial aplicado a las funciones \(C_{10}^{0,0}\) y \(C_{\mathrm{SKIP}}^{0,0}\)).

Ahora sí podemos hacer el programa \(\mathcal{Q}\) de \(S^{\Sigma\cup\Sigma_p}\) que enumera a \(L\):

\[
\begin{array}{rl}
& \mathrm{IF}\ \mathrm{N}1\ne0\ \mathrm{GOTO}\ L1\\
& \mathrm{GOTO}\ L2\\
L1 & \left[\mathrm{N}2\leftarrow(\mathrm{N}1)_1\right]\\
& \left[\mathrm{N}3\leftarrow(\mathrm{N}1)_2\right]\\
& \left[\mathrm{P}1\leftarrow \ast^\le(\mathrm{N}2)\right]\\
& \left[\mathrm{IF}\ \mathrm{P}1\in Pro^\Sigma\ \mathrm{GOTO}\ L3\right]\\
& \mathrm{GOTO}\ L2\\
L3 & \left[\mathrm{N}4\leftarrow 10\right]\\
& \left[\mathrm{IF}\ Halt^{1,0}(\mathrm{N}3,\mathrm{N}4,\mathrm{P}1)\ \mathrm{GOTO}\ L4\right]\\
& \mathrm{GOTO}\ L2\\
L4 & \left[\mathrm{N}5\leftarrow E_{\#1}^{1,0}(\mathrm{N}3,\mathrm{N}4,\mathrm{P}1)\right]\\
& \left[\mathrm{IF}\ \mathrm{N}5=10\ \mathrm{GOTO}\ L5\right]\\
L2 & \left[\mathrm{P}1\leftarrow \mathrm{SKIP}\right]\\
L5 & \mathrm{SKIP}
\end{array}
\]

**Ejercicio 17:** (Explicado en video en granlogico.com.) Sea \(\Sigma=\{\#,\$\}\) y sea

\[
L=\{\mathcal{P}\in Pro^\Sigma:\exists n,\alpha\text{ tales que }\Psi_\mathcal{P}^{2,1,\ast}(|\mathcal{P}|,n,\alpha)=\$\}
\]

**(a)** Dar un programa \(\mathcal{Q}\in Pro^{\Sigma\cup\Sigma_p}\) tal que \(\operatorname{Dom}(\Psi_\mathcal{Q}^{0,1,\#})=L\)

**(b)** Dar un programa \(\mathcal{Q}'\in Pro^{\Sigma\cup\Sigma_p}\) tal que \(\operatorname{Dom}(\Psi_{\mathcal{Q}'}^{1,0,\ast})=\omega\) y \(\operatorname{Im}(\Psi_{\mathcal{Q}'}^{1,0,\ast})=L\)

Para cada macro que use dar la función o predicado asociado y justificar por qué existe tal macro.

**Ejercicio 18:** Sea \(\Sigma=\{@,!\}\) y sea

\[
L=\{\mathcal{P}\in Pro^\Sigma:\exists\alpha\text{ tal que }\Psi_\mathcal{P}^{0,2,\ast}(\alpha,\alpha\alpha)=\alpha\alpha\alpha\}
\]

Dar \(\mathcal{Q}\in Pro^{\Sigma\cup\Sigma_p}\) el cual enumere a \(L\). Para cada macro que use dar la función o predicado asociado y justificar por qué existe tal macro.

**Ejercicio 19:** Sea \(\Sigma=\{@,\%\}\) y sea

\[
S=\{(x,\mathcal{P})\in\omega\times Pro^\Sigma:x\in\operatorname{Dom}(\Psi_\mathcal{P}^{1,0,\#})\}
\]

Dar \(\mathcal{Q}\in Pro^{\Sigma\cup\Sigma_p}\) el cual enumere a \(S\). Para cada macro que use dar la función o predicado asociado y justificar por qué existe tal macro.

**Ejercicio 20:** Sea \(\Sigma=\{@,\%\}\) y sea

\[
S=\{(x,\mathcal{P})\in\omega\times Pro^\Sigma:\Psi_\mathcal{P}^{1,0,\#}(x)=x^2\}
\]

Dar \(\mathcal{Q}\in Pro^{\Sigma\cup\Sigma_p}\) el cual enumere a \(S\). Para cada macro que use dar la función o predicado asociado y justificar por qué existe tal macro.

**Ejercicio 21:** Sea \(\Sigma=\{@,\%\}\) y sea

\[
S=\{\mathcal{P}_1\alpha\mathcal{P}_2:\mathcal{P}_1,\mathcal{P}_2\in Pro^\Sigma,\alpha\in\Sigma^\ast\text{ y }\Psi_{\mathcal{P}_1}^{0,1,\ast}(\alpha)=\Psi_{\mathcal{P}_2}^{0,1,\ast}(\alpha)\}
\]

Dar \(\mathcal{Q}\in Pro^{\Sigma\cup\Sigma_p}\) el cual enumere a \(S\). Para cada macro que use dar la función o predicado asociado y justificar por qué existe tal macro.

**Cuando \(\Sigma\supseteq\Sigma_p\) la cosa se pone más loca...**

Cuando \(\Sigma\supseteq\Sigma_p\) podemos correr un programa \(\mathcal{P}\in Pro^\Sigma\) partiendo de un estado que asigne a sus variables alfabéticas programas (ya que los programas son meras palabras de \(\Sigma^\ast\)). En particular podríamos correr un programa \(\mathcal{P}\) desde el estado \(\lVert\mathcal{P}\rVert\). Llamaremos \(A\) al conjunto formado por aquellos programas \(\mathcal{P}\) tales que \(\mathcal{P}\) se detiene partiendo del estado \(\lVert\mathcal{P}\rVert\). Es decir

\[
A=\{\mathcal{P}\in Pro^\Sigma:\exists t\in\omega\text{ tal que }Halt^{0,1}(t,\mathcal{P},\mathcal{P})=1\}
\]

Por ejemplo \(\mathrm{SKIP}\in A\). Dicho rápida y sugestivamente \(A\) es el conjunto formado por aquellos programas que se detienen partiendo de sí mismos. Dejamos como ejercicio la tarea de hacer un programa que enumere a \(A\). Como veremos en la Guía 9, el conjunto \(A\), si bien es \(\Sigma\)-enumerable, no es \(\Sigma\)-computable.

Ahora consideremos el conjunto

\[
L=\{\mathcal{P}\in Pro^\Sigma:\Psi_\mathcal{P}^{0,0,\ast}(\diamond)=\mathcal{P}\}
\]

En palabras, un programa \(\mathcal{P}\in Pro^\Sigma\) estará en \(L\) si y solo si \(\mathcal{P}\) termina desde \(((0,0,\ldots),(\varepsilon,\varepsilon,\ldots))\) dejando en P1 la palabra \(\mathcal{P}\). En algún sentido los elementos de \(L\) son programas que se autopropagandean ya que "de la nada ellos terminan dándose a sí mismos como salida". Dejamos al lector la tarea de reflexionar hasta entender que resulta difícil encontrar "a mano" un elemento de \(L\). En algún sentido, para lograr hacer un programa que esté en \(L\) debemos ir escribiendo instrucciones que a su vez vayan garantizando que ellas mismas vayan quedando en el contenido de la variable P1. Sin embargo el Teorema de la Recursión (de Kleene) nos garantiza que \(L\) es no vacío! Dejamos como ejercicio la tarea de hacer un programa que enumere a \(L\) (obviamente utilizando un elemento fijo de \(L\)).

Consideremos ahora el conjunto

\[
S=\{(\mathcal{P}_1,\mathcal{P}_2)\in Pro^\Sigma\times Pro^\Sigma:\Psi_{\mathcal{P}_1}^{0,0,\ast}(\diamond)=\mathcal{P}_1\mathcal{P}_2=\Psi_{\mathcal{P}_2}^{0,0,\ast}(\diamond)\}
\]

Note que nuevamente es difícil imaginar cómo uno programaría un par de programas \(\mathcal{P}_1\) y \(\mathcal{P}_2\) de manera que \((\mathcal{P}_1,\mathcal{P}_2)\) esté en \(S\). El Teorema de la Recursión Doble (de Smullyan) nos garantiza que \(S\) es no vacío! Dejamos al lector la tarea de hacer un programa que enumere a \(L\) (obviamente utilizando un elemento fijo de \(S\)).

**Ejercicio 22:** Supongamos que \(\Sigma\supseteq\Sigma_p\). De un programa de \(S^\Sigma\) que enumere a \(A\).

**Ejercicio 23:** Supongamos que \(\Sigma\supseteq\Sigma_p\). Sea

\[
L=\{\mathcal{P}\in Pro^\Sigma:\Psi_\mathcal{P}^{0,0,\ast}(\diamond)=\mathcal{P}\}
\]

De un programa de \(S^\Sigma\) que enumere a \(L\).

**Ejercicio 24:** Supongamos que \(\Sigma\supseteq\Sigma_p\). Sea

\[
L=\{\mathcal{P}\in Pro^\Sigma:\Psi_\mathcal{P}^{2,1,\ast}(1,1,\mathcal{P})=\mathcal{P}\mathcal{P}\}
\]

Encuentre un elemento concreto de \(L\) y de un programa de \(S^\Sigma\) que enumere a \(L\)

**Ejercicio 25:** Supongamos que \(\Sigma\supseteq\Sigma_p\). De un programa de \(S^\Sigma\) que enumere al conjunto

\[
L=\{\mathcal{P}\in Pro^\Sigma:\exists x\text{ tal que }\Psi_\mathcal{P}^{1,1,\ast}(x,\mathcal{P})=I_1^\mathcal{P}\}
\]

**Ejercicio 26:** Supongamos que \(\Sigma\supseteq\Sigma_p\). De un programa de \(S^\Sigma\) que enumere al conjunto

\[
S=\{(x,\mathcal{P},\alpha)\in\omega\times Pro^\Sigma\times\Sigma^\ast:\Psi_\mathcal{P}^{1,2,\#}(x,\alpha,\mathcal{P}^x)=0\}
\]

**Ejercicio 27:** Supongamos que \(\Sigma\supseteq\Sigma_p\). Sea

\[
S=\{(\mathcal{P}_1,\mathcal{P}_2)\in Pro^\Sigma\times Pro^\Sigma:\Psi_{\mathcal{P}_1}^{0,0,\ast}(\diamond)=\mathcal{P}_1\mathcal{P}_2=\Psi_{\mathcal{P}_2}^{0,0,\ast}(\diamond)\}
\]

De un programa de \(S^\Sigma\) que enumere al conjunto \(S\)

## Dos batallas más

Aceptaremos sin prueba el siguiente teorema.

**Teorema 12 (Gödel vence a Turing).** Supongamos \(f:S\subseteq\omega^n\times\Sigma^{\ast m}\to O\) es \(\Sigma\)-Turing computable. Entonces \(f\) es \(\Sigma\)-recursiva.

**Ejercicio 28:** Haga un esquema a nivel de ideas (sin demostraciones y sin demasiada precisión) de la prueba del teorema anterior (la prueba completa está en el apunte).

Aceptaremos sin prueba el siguiente teorema.

**Teorema 13 (Turing vence a Neumann).** Si \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to O\) es \(\Sigma\)-computable, entonces \(f\) es \(\Sigma\)-Turing computable.

**Ejercicio 29:** Haga un esquema a nivel de ideas (sin demostraciones y sin demasiada precisión) de la prueba del teorema anterior (la prueba completa está en el apunte y en granlogico.com hay un video con la prueba del teorema)

## La tesis de Church

En virtud de los teoremas ya expuestos tenemos el siguiente teorema que asegura que los tres paradigmas son equivalentes.

**Teorema 14.** Sea \(\Sigma\) un alfabeto finito. Dada una función \(f\), las siguientes son equivalentes:

1. \(f\) es \(\Sigma\)-Turing computable
2. \(f\) es \(\Sigma\)-recursiva
3. \(f\) es \(\Sigma\)-computable.

También los tres paradigmas son equivalentes con respecto a los dos tipos de conjuntos estudiados, es decir:

**Teorema 15.** Sea \(\Sigma\) un alfabeto finito y sea \(S\subseteq\omega^n\times\Sigma^{\ast m}\). Las siguientes son equivalentes:

1. \(S\) es \(\Sigma\)-Turing enumerable
2. \(S\) es \(\Sigma\)-recursivamente enumerable
3. \(S\) es \(\Sigma\)-enumerable

**Teorema 16.** Sea \(\Sigma\) un alfabeto finito y sea \(S\subseteq\omega^n\times\Sigma^{\ast m}\). Las siguientes son equivalentes:

1. \(S\) es \(\Sigma\)-Turing computable
2. \(S\) es \(\Sigma\)-recursivo
3. \(S\) es \(\Sigma\)-computable

**Ejercicio 30:** Pruebe los dos teoremas anteriores

Otro modelo matemático de computabilidad efectiva es el llamado lambda calculus, introducido por Church, el cual también resulta equivalente a los estudiados por nosotros. El hecho de que tan distintos paradigmas computacionales hayan resultado equivalentes hace pensar que en realidad los mismos han tenido éxito en capturar la totalidad de las funciones \(\Sigma\)-efectivamente computables. Esta aseveración es conocida como la

Tesis de Church: Toda función \(\Sigma\)-efectivamente computable es \(\Sigma\)-recursiva.

Y por supuesto puede ser sintetizada diciendo que Gödel vence a Leibniz (y por lo tanto los cuatro próceres empatan!). Si bien no se ha podido dar una prueba estrictamente matemática de la Tesis de Church, es un sentimiento común de los investigadores del área que la misma es verdadera.

## Ejercicios de examen

Para cada macro que use dar la función o predicado asociado y justificar por qué existe tal macro usando alguno de los dos Manantiales de Macros (el primer Manantial está en la Guía 7 y el segundo en esta guía). Note que si ud está haciendo un programa de \(S^\Sigma\) y quiere usar los Manantiales de Macros para producir un macro, la función a la cual le aplicará el respectivo manantial debe ser \(\Sigma\)-mixta. O sea que cuando se dirija a alguno de los manantiales de macros para obtener un macro, antes piense bien en que "\(S^\Sigma\)" está ud programando.

1. Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(f:L_1\to L_2\), con \(L_1,L_2\subseteq\Sigma^\ast\), es \(\Sigma\)-computable y biyectiva.

   **(a)** Defina (dando dominio, imagen y regla) la función \(f^{-1}\).

   **(b)** De un programa de \(S^\Sigma\) (usando macros) que compute a \(f^{-1}\).

2. Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(S_1\subseteq\omega\times\Sigma^\ast\) y \(S_2\subseteq\omega\). Supongamos además que \(f:S_1\to S_2\) es \(\Sigma\)-computable y biyectiva.

   **(a)** Defina (dando dominio, imagen y regla) la función \(f^{-1}\).

   **(b)** De un programa \(\mathcal{P}\in Pro^\Sigma\) (usando macros) tal que \(f^{-1}=[\Psi_\mathcal{P}^{1,0,\#},\Psi_\mathcal{P}^{1,0,\ast}]\).

3. Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(S\subseteq\omega\times\Sigma^\ast\) y \(L\subseteq\Sigma^\ast\). Supongamos además que \(f:S\to L\) es \(\Sigma\)-computable y biyectiva.

   **(a)** Defina (dando dominio, imagen y regla) la función \(f^{-1}\).

   **(b)** De un programa \(\mathcal{P}\in Pro^\Sigma\) (usando macros) tal que \(f^{-1}=[\Psi_\mathcal{P}^{0,1,\#},\Psi_\mathcal{P}^{0,1,\ast}]\).

4. Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(S_1\subseteq\omega\) y \(S_2\subseteq\omega\times\Sigma^\ast\). Supongamos además que \(F:S_1\to S_2\) es biyectiva.

   **(a)** Defina (dando dominio, imagen y regla) la función \(F^{-1}\).

   **(b)** Suponga que \(F_{(1)}\) y \(F_{(2)}\) son \(\Sigma\)-computables. De un programa \(\mathcal{P}\in Pro^\Sigma\) (usando macros) que compute a \(F^{-1}\).

5. Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(f:S\subseteq\omega\times\omega\times\Sigma^\ast\to\omega\) es \(\Sigma\)-computable. Suponga además que \((0,0,\varepsilon)\in S\) y \(f(0,0,\varepsilon)=0\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
H=\{(x,y,\alpha)\in S:f(x,y,\alpha)=0\}
\]

6. Sea \(\Sigma=\{@,\&\}\). Supongamos \(f:S\subseteq\omega\times\omega\to\omega\) es \(\Sigma\)-computable. Suponga además que \((0,0)\in S\) y \(f(0,0)=0\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
H=\{(x,y)\in S:f(x,y)=x\}
\]

7. Sea \(\Sigma=\{@,\&\}\). Supongamos \(f:L\subseteq\Sigma^\ast\times\Sigma^\ast\to\Sigma^\ast\) es \(\Sigma\)-computable. Suponga además que \((@,\&)\in L\) y \(f(@,\&)=@@@\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
H=\{(\alpha,\beta)\in L:f(\alpha,\beta)=\alpha\alpha\alpha\}
\]

8. Sea \(\Sigma=\{@,\&\}\). Supongamos \(f:S\subseteq\omega\times\omega\to\omega\) es \(\Sigma\)-computable. Suponga además que \((0,0)\in S\) y \(f(0,0)=0\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
H=\{(x,y)\in S:(y,x)\in S\text{ y }f(x,y)=f(y,x)\}
\]

9. Sea \(\Sigma=\{@,\&\}\). Supongamos \(f:S\subseteq\omega\times\omega\to\omega\) es \(\Sigma\)-computable. Suponga además que \((0,0)\in S\) y \(f(0,0)=0\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
H=\{(x,y)\in S:(f(x,y),y)\in S\text{ y }f(f(x,y),y)=0\}
\]

10. Sea \(\Sigma=\{@,\&\}\). Supongamos \(f:S\subseteq\omega\times\omega\to\omega\) es \(\Sigma\)-computable. Suponga además que \((0,0)\in S\) y \(f(0,0)=0\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
H=\{x\in\omega:\text{ hay un }y\text{ tal que }(x,y)\in S\text{ y }f(x,y)=0\}
\]

11. Sea \(\Sigma=\{@,\&\}\). Supongamos \(f:S\subseteq\omega\times\omega\to\omega\) es \(\Sigma\)-computable. Suponga además que \((0,0)\in S\) y \(f(0,0)=0\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
H=\{(x,x):(x,x)\in S\text{ y }f(x,x)=x\}
\]

12. Sea \(\Sigma=\{@,\&\}\). Supongamos \(f:L\subseteq\Sigma^\ast\times\Sigma^\ast\to\Sigma^\ast\) es \(\Sigma\)-computable. Suponga además que \((@,@)\in L\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
H=\{(\alpha,\beta)\in L:(\beta,\alpha)\in L\text{ y }f(\alpha,\beta)=f(\beta,\alpha)\}
\]

13. Sea \(\Sigma=\{@,\&\}\). Sea \(f:S\subseteq\Sigma^\ast\to\omega\) una función \(\Sigma\)-computable. Supongamos que \(\varepsilon\in S\) y que \(f(\varepsilon)=0\). Notar que \(\varepsilon\in L\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
L=\{\alpha\in S:@^{f(\alpha)}\in S\text{ y }f(@^{f(\alpha)})=0\}
\]

14. Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(f:S\subseteq\omega\times\omega\times\Sigma^\ast\to\omega\) es \(\Sigma\)-computable. Suponga además que \((0,0,\varepsilon)\in S\) y \(f(0,0,\varepsilon)=0\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
H=\{(x,y,\alpha)\in S:(y,x,\alpha)\in S\text{ y }f(x,y,\alpha)=f(y,x,\alpha)\}
\]

15. Sea \(\Sigma=\{@,\%\}\) y sea \(\mathcal{P}_0\in Pro^\Sigma\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
L=\{\alpha\in\Sigma^\ast:(\exists x\in\omega)\ \Psi_{\mathcal{P}_0}^{1,1,\#}(x^2,\alpha)=\Psi_{\mathcal{P}_0}^{0,2,\#}(\alpha,\alpha)\}
\]

(note que \(\varepsilon\in L\)).

16. Sea \(\Sigma=\{@,\%\}\) y sea \(\mathcal{P}_0\in Pro^\Sigma\). Sea

\[
S=\{(x,\alpha):\Psi_{\mathcal{P}_0}^{1,0,\#}(x)=\Psi_{\mathcal{P}_0}^{0,1,\#}(\alpha)\}
\]

Note que \((0,\varepsilon)\in S\). De un programa \(\mathcal{Q}\in Pro^\Sigma\) (usando macros) que enumere al conjunto \(S\).

17. Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(f_1:S_1\subseteq\omega\times\omega\times\Sigma^\ast\to\omega\) y \(f_2:S_2\subseteq\omega\times\omega\times\Sigma^\ast\to\Sigma^\ast\) son \(\Sigma\)-computables y \((0,0,\varepsilon)\in S_1\cap S_2\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto \(\operatorname{Im}([f_1,f_2])\).

18. Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(f:S\subseteq\omega\to\omega\) y \(g:L\subseteq\Sigma^\ast\to\omega\) son \(\Sigma\)-computables. Supongamos además que \(0\) pertenece al conjunto

\[
H=\{x:x\in S,\ @^x\in L\text{ y }f(x)=g(@^x)\}
\]

De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto \(H\).

19. Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(f:S\subseteq\omega\to\omega\) y \(g:L\subseteq\Sigma^\ast\to\omega\) son \(\Sigma\)-computables. Supongamos además que \(\varepsilon\) pertenece al conjunto

\[
H=\{\alpha\in L:g(\alpha)\in S\text{ y }f(g(\alpha))=0\}
\]

De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto \(H\).

20. Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(f:S\subseteq\omega\to\omega\) es \(\Sigma\)-computable, \(0\in S\) y \(f(0)=0\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
H=\{x\in S:x^2\in S\text{ y }f(x)=f(x^2)\}
\]

21. Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(f:S\subseteq\omega\to\omega\) es \(\Sigma\)-computable, \(0\in S\) y \(f(0)=0\). De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto

\[
H=\{x\in S:x\text{ es par }x/2\in S\text{ y }f(x)=f(x/2)\}
\]

22. Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(L_1,L_2\subseteq\Sigma^\ast\) son \(\Sigma\)-enumerables. Supongamos además que \(\varepsilon\) pertenece al conjunto

\[
H=\{\alpha\in L_1:\text{ hay un }\beta\in L_2\text{ tal que }|\beta|=|\alpha|\}
\]

De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto \(H\).

23. Sea \(\Sigma=\{!,\%\}\). Supongamos \(S\subseteq\omega\times\omega\times\Sigma^\ast\) y \(L\subseteq\Sigma^\ast\) son \(\Sigma\)-enumerables. Supongamos además que \((0,0,\varepsilon)\) pertenece al conjunto

\[
H=\{(x,y,\alpha)\in S:\text{ hay un }\beta\in L\text{ tal que }|\beta|=|\alpha|\}
\]

De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto \(H\).

24. Sea \(\Sigma=\{!,\%\}\). Supongamos \(S\subseteq\omega\times\omega\) y \(S'\subseteq\omega\) son \(\Sigma\)-enumerables. Supongamos además que \((0,0)\) pertenece al conjunto

\[
H=\{(x,y):(x,y)\in S\text{ y }x+y\in S'\}
\]

De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto \(H\).

25. Sea \(\Sigma=\{!,\%\}\). Supongamos \(S\subseteq\Sigma^\ast\times\Sigma^\ast\) y \(L\subseteq\Sigma^\ast\) son \(\Sigma\)-enumerables. Supongamos además que \((\varepsilon,\varepsilon)\) pertenece al conjunto

\[
H=\{(\alpha,\beta)\in S:\text{ hay un }\gamma\in L\text{ tal que }\alpha=\beta\gamma\}
\]

De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto \(H\).

26. Sean \(f:D_f\subseteq\omega\times\Sigma^\ast\to\omega\) y \(g:D_g\subseteq\omega\times\Sigma^\ast\to\omega\) funciones \(\Sigma\)-computables tales que \(D_f\cap D_g=\emptyset\). Sea \(F:D_f\cup D_g\to\omega\) dada por

\[
e\mapsto
\begin{cases}
f(e)&\text{si }e\in D_f\\
g(e)&\text{si }e\in D_g
\end{cases}
\]

De un programa de \(S^\Sigma\) (usando macros) que compute a \(F\).

27. Sea \(\Sigma=\{@,!,\%\}\). Supongamos \(L_1,L_2\subseteq\Sigma^\ast\) son \(\Sigma\)-enumerables. Supongamos además que \(\varepsilon\) pertenece al conjunto

\[
H=\{\alpha\in L_1:\text{ hay un }\beta\in L_2\text{ tal que }\beta^3=\alpha\}
\]

De un programa de \(S^\Sigma\) (usando macros) que enumere al conjunto \(H\).

28. Sea \(\Sigma=\{@,\%\}\) y sea

\[
S=\{(x,\mathcal{P},\alpha)\in\omega\times Pro^\Sigma\times\Sigma^\ast:\Psi_\mathcal{P}^{1,1,\#}(x,\alpha)=0\}
\]

Dar \(\mathcal{Q}\in Pro^{\Sigma\cup\Sigma_p}\) el cual enumere a \(S\).

29. Sea \(\Sigma=\{@,\%\}\) y sea

\[
S=\{(\mathcal{P}_1,\mathcal{P}_2)\in Pro^\Sigma\times Pro^\Sigma:\exists\alpha\text{ tal que }\Psi_{\mathcal{P}_1}^{0,1,\ast}(\alpha)=\Psi_{\mathcal{P}_2}^{0,1,\ast}(\alpha)\}
\]

Dar \(\mathcal{Q}\in Pro^{\Sigma\cup\Sigma_p}\) el cual enumere a \(S\).

30. Sea \(\Sigma=\{@,!\}\) y sea

\[
L=\{\mathcal{P}\in Pro^\Sigma:\exists\alpha\text{ tal que }\Psi_\mathcal{P}^{1,1,\ast}(11,\alpha)=\alpha!@\}
\]

   **(a)** Dar un programa \(\mathcal{Q}\in Pro^{\Sigma\cup\Sigma_p}\) tal que \(\operatorname{Dom}(\Psi_\mathcal{Q}^{0,1,\#})=L\)

   **(b)** Dar un programa \(\mathcal{Q}'\in Pro^{\Sigma\cup\Sigma_p}\) tal que \(\operatorname{Dom}(\Psi_{\mathcal{Q}'}^{1,0,\ast})=\omega\) y \(\operatorname{Im}(\Psi_{\mathcal{Q}'}^{1,0,\ast})=L\)

31. Sea \(\Sigma=\{@,!\}\) y sea

\[
L=\{\mathcal{P}\in Pro^\Sigma:\exists\alpha\text{ tal que }\Psi_\mathcal{P}^{0,2,\ast}(\alpha,\alpha\alpha)=\alpha\alpha\alpha\}
\]

Dar \(\mathcal{Q}\in Pro^{\Sigma\cup\Sigma_p}\) el cual enumere a \(L\).

32. Sea \(\Sigma=\{@,\%\}\) y sea

\[
S=\{(x,\mathcal{P})\in\omega\times Pro^\Sigma:x\in\operatorname{Dom}(\Psi_\mathcal{P}^{1,0,\#})\}
\]

Dar \(\mathcal{Q}\in Pro^{\Sigma\cup\Sigma_p}\) el cual enumere a \(S\).

33. Sea \(\Sigma=\{@,\%\}\) y sea

\[
S=\{(x,\mathcal{P})\in\omega\times Pro^\Sigma:\Psi_\mathcal{P}^{1,0,\#}(x)=x^2\}
\]

Dar \(\mathcal{Q}\in Pro^{\Sigma\cup\Sigma_p}\) el cual enumere a \(S\).

34. Sea \(\Sigma=\{@,\%\}\) y sea

\[
S=\{\mathcal{P}_1\alpha\mathcal{P}_2:\mathcal{P}_1,\mathcal{P}_2\in Pro^\Sigma,\alpha\in\Sigma^\ast\text{ y }\Psi_{\mathcal{P}_1}^{0,1,\ast}(\alpha)=\Psi_{\mathcal{P}_2}^{0,1,\ast}(\alpha)\}
\]

Dar \(\mathcal{Q}\in Pro^{\Sigma\cup\Sigma_p}\) el cual enumere a \(S\).

35. Supongamos que \(\Sigma\supseteq\Sigma_p\). Sea

\[
L=\{\mathcal{P}\in Pro^\Sigma:\Psi_\mathcal{P}^{2,1,\ast}(1,1,\mathcal{P})=\mathcal{P}\mathcal{P}\}
\]

Encuentre un elemento concreto de \(L\) y de un programa de \(S^\Sigma\) que enumere a \(L\)

36. Supongamos que \(\Sigma\supseteq\Sigma_p\). De un programa de \(S^\Sigma\) que enumere al conjunto

\[
L=\{\mathcal{P}\in Pro^\Sigma:\exists x\text{ tal que }\Psi_\mathcal{P}^{1,1,\ast}(x,\mathcal{P})=I_1^\mathcal{P}\}
\]

37. Supongamos que \(\Sigma\supseteq\Sigma_p\). De un programa de \(S^\Sigma\) que enumere al conjunto

\[
S=\{(x,\mathcal{P},\alpha)\in\omega\times Pro^\Sigma\times\Sigma^\ast:\Psi_\mathcal{P}^{1,2,\#}(x,\alpha,\mathcal{P}^x)=0\}
\]

38. Supongamos que \(\Sigma\supseteq\Sigma_p\). Sea

\[
S=\{(\mathcal{P}_1,\mathcal{P}_2)\in Pro^\Sigma\times Pro^\Sigma:\mathcal{P}_1\ne\mathcal{P}_2\text{ y }\Psi_{\mathcal{P}_1}^{0,1,\ast}(\mathcal{P}_2)=\Psi_{\mathcal{P}_2}^{0,1,\ast}(\mathcal{P}_1)\}
\]

Note que \((\mathrm{P}1\leftarrow \varepsilon\mathrm{SKIP},\mathrm{P}1\leftarrow\varepsilon)\in S\). De un programa de \(S^\Sigma\) que enumere al conjunto \(S\)
