# GUÍA 9 DE LENGUAJES: RESULTADOS BÁSICOS PRESENTADOS EN PARADIGMA RECURSIVO

En esta guía presentaremos varios resultados básicos de computabilidad, expresados en el paradigma recursivo, ya que es el más habitual y cómodo. Varios de estos resultados pueden ser establecidos y probados en forma natural dentro del paradigma de la computabilidad efectiva (ver apunte). A ellos los enunciaremos dentro del paradigma de Gödel y los probaremos rigurosamente usando la teoría desarrollada hasta ahora. Sin embargo, veremos que hay otros resultados que son dependientes del desarrollo matemático hecho y aportan nueva información al paradigma filosófico (la indecidibilidad del halting problem, por ejemplo).

Como veremos muchas de las pruebas serán de naturaleza imperativa basadas en la equivalencia del paradigma de Gödel con el imperativo de Neumann.

## Lema de división por casos para funciones \(\Sigma\)-recursivas

Usando los resultados probados en las dos anteriores batallas entre los paradigmas de Gödel y Neumann podemos probar el siguiente resultado el cual a priori no parece fácil de probar si nos quedamos solo en el contexto del paradigma Gödeliano.

**Lema 1.** Supongamos \(f_i:D_{f_i}\subseteq\omega^n\times\Sigma^{\ast m}\to O\), \(i=1,\ldots,k\), son funciones \(\Sigma\)-recursivas tales que \(D_{f_i}\cap D_{f_j}=\emptyset\) para \(i\ne j\). Entonces la función \(f_1\cup\cdots\cup f_k\) es \(\Sigma\)-recursiva.

**Proof.** Probaremos el caso \(k=2\) y \(O=\Sigma^\ast\). Además supondremos que \(n=m=1\). Sean \(\mathcal{P}_1\) y \(\mathcal{P}_2\) programas que computen las funciones \(f_1\) y \(f_2\), respectivamente. Para \(i=1,2\), definamos

\[
H_i=\lambda tx_1\alpha_1\left[Halt^{1,1}(t,x_1,\alpha_1,\mathcal{P}_i)\right]
\]

Notar que \(D_{H_i}=\omega^2\times\Sigma^\ast\) y que \(H_i\) es \(\Sigma\)-mixta. Además sabemos que la función \(Halt^{1,1}\) es \((\Sigma\cup\Sigma_p)\)-p.r. por lo cual resulta fácilmente que \(H_i\) es \((\Sigma\cup\Sigma_p)\)-p.r.. Por el Teorema de Independencia del Alfabeto tenemos que \(H_i\) es \(\Sigma\)-p.r.. y por lo tanto el Segundo Manantial de Macros nos dice que en \(S^\Sigma\) hay un macro:

\[
\left[\mathrm{IF}\ H_i(V1,V2,W1)\ \mathrm{GOTO}\ A1\right]
\]

Para hacer más intuitivo el uso de este macro lo escribiremos de la siguiente manera

\[
\left[\mathrm{IF}\ Halt^{1,1}(V1,V2,W1,\mathcal{P}_i)\ \mathrm{GOTO}\ A1\right]
\]

Ya que cada \(f_i\) es \(\Sigma\)-recursiva, el Segundo Manantial nos dice que en \(S^\Sigma\) hay macros

\[
\begin{array}{c}
\left[W2\leftarrow f_1(V1,W1)\right]\\
\left[W2\leftarrow f_2(V1,W1)\right]
\end{array}
\]

Sea \(\mathcal{P}\) el siguiente programa:

\[
\begin{array}{rl}
L1 & \mathrm{N}20\leftarrow \mathrm{N}20+1\\
& \left[\mathrm{IF}\ Halt^{1,1}(\mathrm{N}20,\mathrm{N}1,\mathrm{P}1,\mathcal{P}_1)\ \mathrm{GOTO}\ L2\right]\\
& \left[\mathrm{IF}\ Halt^{1,1}(\mathrm{N}20,\mathrm{N}1,\mathrm{P}1,\mathcal{P}_2)\ \mathrm{GOTO}\ L3\right]\\
& \mathrm{GOTO}\ L1\\
L2 & \left[\mathrm{P}1\leftarrow f_1(\mathrm{N}1,\mathrm{P}1)\right]\\
& \mathrm{GOTO}\ L4\\
L3 & \left[\mathrm{P}1\leftarrow f_2(\mathrm{N}1,\mathrm{P}1)\right]\\
L4 & \mathrm{SKIP}
\end{array}
\]

Nótese que \(\mathcal{P}\) computa la función \(f_1\cup f_2\).

**Ejercicio 1:** Si \(P:D_P\subseteq\omega\times\omega^n\times\Sigma^{\ast m}\to\omega\) es un predicado \(\Sigma\)-recursivo y \(D_P\) es \(\Sigma\)-recursivo, entonces la función \(M(P)\) es \(\Sigma\)-recursiva.

## Lema de restricción de funciones \(\Sigma\)-recursivas

Nos será útil también el siguiente resultado.

**Lema 2.** Supongamos \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to O\) es \(\Sigma\)-recursiva y \(S\subseteq D_f\) es \(\Sigma\)-r.e., entonces \(f|_S\) es \(\Sigma\)-recursiva.

**Proof.** Si \(S=\emptyset\), entonces \(f|_S=\emptyset\) y por lo tanto \(f|_S\) es \(\Sigma\)-recursiva. Supongamos \(S\ne\emptyset\). Haremos el caso \(n=m=1\) y \(O=\Sigma^\ast\). Tenemos que hay una \(F:\omega\to\omega\times\Sigma^\ast\) tal que \(I_F=S\) y \(F_{(1)}\), \(F_{(2)}\) son \(\Sigma\)-recursivas. Por el Segundo Manantial en \(S^\Sigma\) hay macros

\[
\begin{array}{c}
\left[W2\leftarrow f(V1,W1)\right]\\
\left[V2\leftarrow F_{(1)}(V1)\right]\\
\left[W1\leftarrow F_{(2)}(V1)\right]
\end{array}
\]

Ya que los predicados \(D=\lambda xy[x\ne y]\) y \(D'=\lambda\alpha\beta[\alpha\ne\beta]\) son \(\Sigma\)-p.r., en \(S^\Sigma\) hay macros

\[
\begin{array}{c}
\left[\mathrm{IF}\ D(V1,V2)\ \mathrm{GOTO}\ A1\right]\\
\left[\mathrm{IF}\ D'(W1,W2)\ \mathrm{GOTO}\ A1\right]
\end{array}
\]

Para hacer más amigable la lectura los escribiremos de la siguiente manera

\[
\begin{array}{c}
\left[\mathrm{IF}\ V1\ne V2\ \mathrm{GOTO}\ A1\right]\\
\left[\mathrm{IF}\ W1\ne W2\ \mathrm{GOTO}\ A1\right]
\end{array}
\]

Sea \(\mathcal{P}\) el siguiente programa

\[
\begin{array}{rl}
L2 & \left[\mathrm{N}2\leftarrow F_{(1)}(\mathrm{N}20)\right]\\
& \left[\mathrm{P}2\leftarrow F_{(2)}(\mathrm{N}20)\right]\\
& \left[\mathrm{IF}\ \mathrm{N}1\ne \mathrm{N}2\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \mathrm{P}1\ne \mathrm{P}2\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{P}1\leftarrow f(\mathrm{N}1,\mathrm{P}1)\right]\\
& \mathrm{GOTO}\ L3\\
L1 & \mathrm{N}20\leftarrow \mathrm{N}20+1\\
& \mathrm{GOTO}\ L2\\
L3 & \mathrm{SKIP}
\end{array}
\]

Es fácil ver que \(\mathcal{P}\) computa a \(f|_S\).

## Conjuntos \(\Sigma\)-r.e. y \(\Sigma\)-r.

Daremos primero algunas propiedades básicas de los conjuntos \(\Sigma\)-r.e. y \(\Sigma\)-r. El siguiente resultado puede probarse fácilmente dentro del paradigma Gödeliano y lo dejamos como ejercicio.

**Ejercicio 2:** Sea \(\Sigma\) un alfabeto finito. Supongamos \(S_1,S_2\subseteq\omega^n\times\Sigma^{\ast m}\) son conjuntos \(\Sigma\)-recursivos. Entonces \(S_1\cup S_2\), \(S_1\cap S_2\) y \(S_1-S_2\) son \(\Sigma\)-recursivos

**Lema 3.** Sea \(\Sigma\) un alfabeto finito. Se tiene que

1. Supongamos \(S_1,S_2\subseteq\omega^n\times\Sigma^{\ast m}\) son conjuntos \(\Sigma\)-r.e.. Entonces \(S_1\cup S_2\) es \(\Sigma\)-r.e.
2. Supongamos \(S_1,S_2\subseteq\omega^n\times\Sigma^{\ast m}\) son conjuntos \(\Sigma\)-r.e.. Entonces \(S_1\cap S_2\) es \(\Sigma\)-r.e.
3. Sea \(S\subseteq\omega^n\times\Sigma^{\ast m}\). Si \(S\) es \(\Sigma\)-recursivo, entonces \(S\) es \(\Sigma\)-recursivamente enumerable

**Proof.** Los tres resultados en su versión imperativa fueron probados o dejados como ejercicio en la Guía 8, por lo que podemos aplicar los teoremas que nos dicen que los paradigmas recursivo e imperativo son equivalentes.

Tal como veremos más adelante hay conjuntos \(\Sigma\)-recursivamente enumerables los cuales no son \(\Sigma\)-recursivos. Sin embargo tenemos el siguiente interesante resultado.

**Lema 4.** Sea \(S\subseteq\omega^n\times\Sigma^{\ast m}\). Si \(S\) y \((\omega^n\times\Sigma^{\ast m})-S\) son \(\Sigma\)-recursivamente enumerables, entonces \(S\) es \(\Sigma\)-recursivo

**Proof.** (Prueba cheta) Por definición, para probar que \(S\) es \(\Sigma\)-recursivo deberemos probar que \(\chi_S^{\omega^n\times\Sigma^{\ast m}}\) es \(\Sigma\)-recursiva. Nótese que

\[
\chi_S^{\omega^n\times\Sigma^{\ast m}}
=C_1^{n,m}|_S\cup C_0^{n,m}|_{(\omega^n\times\Sigma^{\ast m})-S}.
\]

O sea que por el Lema de División por Casos, solo nos resta probar que \(C_1^{n,m}|_S\) y \(C_0^{n,m}|_{(\omega^n\times\Sigma^{\ast m})-S}\) son \(\Sigma\)-recursivas. Pero esto se desprende directamente del Lema 2 ya que \(C_1^{n,m}\) y \(C_0^{n,m}\) son \(\Sigma\)-recursivas y por hipótesis \(S\) y \((\omega^n\times\Sigma^{\ast m})-S\) son \(\Sigma\)-recursivamente enumerables.

**Ejercicio 3:** (Prueba intuitiva) Dar una prueba imperativa del lema anterior. Hint: inspírese en su análogo dentro del paradigma de la computabilidad efectiva, dado al final de la Guía 3.

El siguiente teorema es muy importante ya que caracteriza a los conjuntos \(\Sigma\)-r.e.

**Teorema 5.** Dado \(S\subseteq\omega^n\times\Sigma^{\ast m}\), son equivalentes

1. \(S\) es \(\Sigma\)-recursivamente enumerable
2. \(S=I_F\), para alguna \(F:D_F\subseteq\omega^k\times\Sigma^{\ast l}\to\omega^n\times\Sigma^{\ast m}\) tal que cada \(F_{(i)}\) es \(\Sigma\)-recursiva.
3. \(S=D_f\), para alguna función \(\Sigma\)-recursiva \(f\)
4. \(S=\emptyset\) o \(S=I_F\), para alguna \(F:\omega\to\omega^n\times\Sigma^{\ast m}\) tal que cada \(F_{(i)}\) es \(\Sigma\)-p.r.

**Proof.** El caso \(n=m=0\) es fácil y es dejado al lector. Supongamos entonces que \(n+m\ge 1\).

\((2)\Rightarrow(3)\). Haremos el caso \(k=l=1\) y \(n=m=2\). El caso general es completamente análogo. Nótese que entonces tenemos que \(S\subseteq\omega^2\times\Sigma^{\ast2}\) y \(F:D_F\subseteq\omega\times\Sigma^\ast\to\omega^2\times\Sigma^{\ast2}\) es tal que \(\operatorname{Im}F=S\) y \(F_{(1)}\), \(F_{(2)}\), \(F_{(3)}\), \(F_{(4)}\) son \(\Sigma\)-recursivas. Para cada \(i\in\{1,2,3,4\}\), sea \(\mathcal{P}_i\) un programa el cual computa a \(F_{(i)}\). Sea \(\le\) un orden total sobre \(\Sigma\). Definamos

\[
H_i=\lambda tx_1\alpha_1\left[\neg Halt^{1,1}(t,x_1,\alpha_1,\mathcal{P}_i)\right]
\]

Notar que \(D_{H_i}=\omega^2\times\Sigma^\ast\) y que \(H_i\) es \(\Sigma\)-mixta. Además sabemos que la función \(Halt^{1,1}\) es \((\Sigma\cup\Sigma_p)\)-p.r. por lo cual resulta fácilmente que \(H_i\) es \((\Sigma\cup\Sigma_p)\)-p.r.. Por la Proposición de Independencia del Alfabeto tenemos que \(H_i\) es \(\Sigma\)-p.r., lo cual por el Segundo Manantial nos dice que hay un macro:

\[
\left[\mathrm{IF}\ H_i(V2,V1,W1)\ \mathrm{GOTO}\ A1\right]
\]

Para hacer más intuitivo el uso de este macro lo escribiremos de la siguiente manera

\[
\left[\mathrm{IF}\ \neg Halt^{1,1}(V2,V1,W1,\mathcal{P}_i)\ \mathrm{GOTO}\ A1\right]
\]

Para \(i=1,2\), definamos

\[
E_i=\lambda xtx_1\alpha_1\left[x\ne E_{\#1}^{1,1}(t,x_1,\alpha_1,\mathcal{P}_i)\right]
\]

Para \(i=3,4\), definamos

\[
E_i=\lambda tx_1\alpha_1\alpha\left[\alpha\ne E_{\ast1}^{1,1}(t,x_1,\alpha_1,\mathcal{P}_i)\right]
\]

Dejamos al lector probar que las funciones \(E_i\) son \(\Sigma\)-p.r.. O sea que para cada \(i\in\{1,2\}\) hay un macro

\[
\left[\mathrm{IF}\ E_i(V2,V3,V1,W1)\ \mathrm{GOTO}\ A1\right]
\]

y para cada \(i\in\{3,4\}\) hay un macro

\[
\left[\mathrm{IF}\ E_i(V2,V1,W1,W2)\ \mathrm{GOTO}\ A1\right]
\]

Haremos más intuitiva la forma de escribir estos macros, por ejemplo para \(i=1\), lo escribiremos de la siguiente manera

\[
\left[\mathrm{IF}\ V2\ne E_{\#1}^{1,1}(V3,V1,W1,\mathcal{P}_1)\ \mathrm{GOTO}\ A1\right]
\]

Ya que la función \(f=\lambda x[(x)_1]\) es \(\Sigma\)-p.r. hay un macro

\[
\left[V2\leftarrow f(V1)\right]
\]

el cual escribiremos de la siguiente manera:

\[
\left[V2\leftarrow (V1)_1\right]
\]

Similarmente hay macros:

\[
\begin{array}{c}
\left[W1\leftarrow \ast^\le((V1)_3)\right]\\
\left[V2\leftarrow (V1)_2\right]
\end{array}
\]

(dejamos al lector entender bien el funcionamiento de estos macros). Sea \(\mathcal{P}\) el siguiente programa de \(S^\Sigma\):

\[
\begin{array}{rl}
L1 & \mathrm{N}20\leftarrow \mathrm{N}20+1\\
& \left[\mathrm{N}10\leftarrow(\mathrm{N}20)_1\right]\\
& \left[\mathrm{N}3\leftarrow(\mathrm{N}20)_2\right]\\
& \left[\mathrm{P}3\leftarrow \ast^\le((\mathrm{N}20)_3)\right]\\
& \left[\mathrm{IF}\ \neg Halt^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal{P}_1)\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \neg Halt^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal{P}_2)\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \neg Halt^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal{P}_3)\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \neg Halt^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal{P}_4)\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \mathrm{N}1\ne E_{\#1}^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal{P}_1)\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \mathrm{N}2\ne E_{\#1}^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal{P}_2)\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \mathrm{P}1\ne E_{\ast1}^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal{P}_3)\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \mathrm{P}2\ne E_{\ast1}^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal{P}_4)\ \mathrm{GOTO}\ L1\right]
\end{array}
\]

Dejamos al lector la tarea de comprender el funcionamiento de este programa y convencerse de que computa la función \(p_1^{2,2}|_S\). Pero entonces \(p_1^{2,2}|_S\) es \(\Sigma\)-computable por lo cual es \(\Sigma\)-recursiva, lo cual prueba (3) ya que \(\operatorname{Dom}(p_1^{2,2}|_S)=S\).

\((3)\Rightarrow(4)\). Supongamos \(S\ne\emptyset\). Sea \((z_1,\ldots,z_n,\gamma_1,\ldots,\gamma_m)\in S\) fijo. Sea \(\mathcal{P}\) un programa el cual compute a \(f\) y Sea \(\le\) un orden total sobre \(\Sigma\). Sea \(P:\mathbf{N}\to\omega\) dado por \(P(x)=1\) sii

\[
Halt^{n,m}((x)_{n+m+1},(x)_1,\ldots,(x)_n,\ast^\le((x)_{n+1}),\ldots,\ast^\le((x)_{n+m}),\mathcal{P})=1
\]

Es fácil ver que \(P\) es \((\Sigma\cup\Sigma_p)\)-p.r. por lo cual es \(\Sigma\)-p.r.. Sea \(\overline{P}=P\cup C_0^{1,0}|_{\{0\}}\). Para \(i=1,\ldots,n\), definamos \(F_i:\omega\to\omega\) de la siguiente manera

\[
F_i(x)=
\begin{cases}
(x)_i&\text{si }\overline{P}(x)=1\\
z_i&\text{si }\overline{P}(x)\ne 1
\end{cases}
\]

Para \(i=n+1,\ldots,n+m\), definamos \(F_i:\omega\to\Sigma^\ast\) de la siguiente manera

\[
F_i(x)=
\begin{cases}
\ast^\le((x)_i)&\text{si }\overline{P}(x)=1\\
\gamma_{i-n}&\text{si }\overline{P}(x)\ne 1
\end{cases}
\]

Por el lema de división por casos (para funciones \(\Sigma\)-p.r.), cada \(F_i\) es \(\Sigma\)-p.r.. Es fácil ver que \(F=[F_1,\ldots,F_{n+m}]\) cumple (4).

## El halting problem y los conjuntos \(A\) y \(N\)

Cuando \(\Sigma\supseteq\Sigma_p\), podemos definir

\[
AutoHalt^\Sigma=\lambda\mathcal{P}\left[(\exists t\in\omega)\ Halt^{0,1}(t,\mathcal{P},\mathcal{P})\right].
\]

Notar que el dominio de \(AutoHalt^\Sigma\) es \(Pro^\Sigma\) y que para cada \(\mathcal{P}\in Pro^\Sigma\) tenemos que

\[
(*)\quad AutoHalt^\Sigma(\mathcal{P})=1\text{ sii }\mathcal{P}\text{ se detiene partiendo del estado }\lVert\mathcal{P}\rVert.
\]

**Lema 6.** Supongamos \(\Sigma\supseteq\Sigma_p\). Entonces \(AutoHalt^\Sigma\) no es \(\Sigma\)-recursivo.

**Proof.** Supongamos \(AutoHalt^\Sigma\) es \(\Sigma\)-recursivo. Por el Segundo Manantial tenemos que hay un macro

\[
\left[\mathrm{IF}\ AutoHalt^\Sigma(W1)\ \mathrm{GOTO}\ A1\right]
\]

Sea \(\mathcal{P}_0\) el siguiente programa de \(S^\Sigma\)

\[
L1\ \left[\mathrm{IF}\ AutoHalt^\Sigma(\mathrm{P}1)\ \mathrm{GOTO}\ L1\right]
\]

Note que

- \(\mathcal{P}_0\) termina partiendo desde \(\lVert\mathcal{P}_0\rVert\) sii \(AutoHalt^\Sigma(\mathcal{P}_0)=0\),

lo cual produce una contradicción si tomamos en \((*)\) \(\mathcal{P}=\mathcal{P}_0\).

Usando el lema anterior y la Tesis de Church podemos probar el siguiente impactante resultado.

**Teorema 7.** Supongamos \(\Sigma\supseteq\Sigma_p\). Entonces \(AutoHalt^\Sigma\) no es \(\Sigma\)-efectivamente computable. Es decir no hay ningún procedimiento efectivo que decida si un programa de \(S^\Sigma\) termina partiendo de sí mismo.

**Proof.** Si \(AutoHalt^\Sigma\) fuera \(\Sigma\)-efectivamente computable, la Tesis de Church nos diría que es \(\Sigma\)-recursivo, contradiciendo el lema anterior.

Nótese que \(AutoHalt^\Sigma\) provee de un ejemplo natural en el cual la cuantificación (no acotada) de un predicado \(\Sigma\)-p.r. con dominio rectangular no es \(\Sigma\)-efectivamente computable

Ahora estamos en condiciones de dar un ejemplo natural de un conjunto \(A\) que es \(\Sigma\)-recursivamente enumerable pero el cual no es \(\Sigma\)-recursivo.

**Lema 8.** Supongamos que \(\Sigma\supseteq\Sigma_p\). Entonces

\[
A=\{\mathcal{P}\in Pro^\Sigma:AutoHalt^\Sigma(\mathcal{P})=1\}
\]

es \(\Sigma\)-r.e. y no es \(\Sigma\)-recursivo. Más aún el conjunto

\[
N=\{\mathcal{P}\in Pro^\Sigma:AutoHalt^\Sigma(\mathcal{P})=0\}
\]

no es \(\Sigma\)-r.e.

**Proof.** Para ver que \(A\) es \(\Sigma\)-r.e. se lo puede hacer imperativamente dando un programa (usando macros) que enumere a \(A\). De esta forma probaríamos que \(A\) es \(\Sigma\)-enumerable y por lo tanto es \(\Sigma\)-r.e.. Daremos ahora una prueba no imperativa de este hecho, es decir más propia del paradigma funcional. Sea \(P=\lambda t\mathcal{P}\left[Halt^{0,1}(t,\mathcal{P},\mathcal{P})\right]\). Note que \(P\) es \(\Sigma\)-p.r. por lo que \(M(P)\) es \(\Sigma\)-r.. Además note que \(D_{M(P)}=A\), lo cual implica que \(A\) es \(\Sigma\)-r.e..

Supongamos ahora que \(N\) es \(\Sigma\)-r.e.. Entonces la función \(C_0^{0,1}|_N\) es \(\Sigma\)-recursiva ya que \(C_0^{0,1}\) lo es. Además ya que \(A\) es \(\Sigma\)-r.e. tenemos que \(C_1^{0,1}|_A\) es \(\Sigma\)-recursiva. Ya que

\[
AutoHalt^\Sigma=C_1^{0,1}|_A\cup C_0^{0,1}|_N
\]

el lema de división por casos nos dice que \(AutoHalt^\Sigma\) es \(\Sigma\)-recursivo, contradiciendo el Lema 6. Esto prueba que \(N\) no es \(\Sigma\)-r.e..

Finalmente supongamos \(A\) es \(\Sigma\)-recursivo. Entonces el conjunto

\[
N=(\Sigma^\ast-A)\cap Pro^\Sigma
\]

debería serlo, lo cual es absurdo. Hemos probado entonces que \(A\) no es \(\Sigma\)-recursivo.

Usando la Tesis de Church obtenemos el siguiente resultado.

**Proposición 9.** Supongamos que \(\Sigma\supseteq\Sigma_p\). Entonces \(A\) es \(\Sigma\)-efectivamente enumerable y no es \(\Sigma\)-efectivamente computable. El conjunto \(N\) no es \(\Sigma\)-efectivamente enumerable. Es decir, \(A\) puede ser enumerado por un procedimiento efectivo pero no hay ningún procedimiento efectivo que decida la pertenencia a \(A\) y no hay ningún procedimiento efectivo que enumere a \(N\). Más aún, si un procedimiento efectivo da como salida siempre elementos de \(N\), entonces hay una cantidad infinita de elementos de \(N\) los cuales nunca da como salida.

**Ejercicio 4:** Justifique la última aseveración en la proposición anterior

Cabe destacar aquí que el dominio de una función \(\Sigma\)-recursiva no siempre será un conjunto \(\Sigma\)-recursivo. Por ejemplo si tomamos \(\Sigma\) tal que \(\Sigma\supseteq\Sigma_p\), entonces \(C_1^{0,1}|_A\) es una función \(\Sigma\)-recursiva ya que es la restricción de la función \(\Sigma\)-recursiva \(C_1^{0,1}\) al conjunto \(\Sigma\)-r.e. \(A\), pero \(\operatorname{Dom}(C_1^{0,1}|_A)=A\) no es \(\Sigma\)-recursivo.

**Ejercicio 5:** Pruebe que no es cierta la siguiente (hermosa y tentadora) propiedad

- Si \(f:S\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) es una función \(\Sigma\)-computable, entonces hay un macro

\[
\left[\mathrm{IF}\ \chi_S^{\omega^n\times\Sigma^{\ast m}}(V1,\ldots,V\overline{n},W1,\ldots,W\overline{m})\ \mathrm{GOTO}\ A1\right]
\]

**Ejercicio 6:** V o F o I. justifique.

**(a)** Sea \(\Sigma\) un alfabeto y sean \(n,m\in\omega\). Entonces el dominio de \(T^{n,m}\) es rectangular

**(b)** Para cada \(\mathcal{P}\in Pro^\Sigma\) hay un \(\mathcal{P}'\in Pro^\Sigma\) tal que \(\operatorname{Dom}(\Psi_{\mathcal{P}'}^{1,0,\#})=\omega-\operatorname{Dom}(\Psi_\mathcal{P}^{1,0,\#})\).

**(c)** Sea \(\mathcal{P}\in Pro^\Sigma\) y supongamos que para cada \(x\in\omega\), \(\mathcal{P}\) termina partiendo de \(((x,0,0\ldots),(\varepsilon,\varepsilon,\ldots))\) en a lo sumo \(n(\mathcal{P})^2+x\) pasos. Entonces \(\Psi_\mathcal{P}^{1,0,\ast}\) es \(\Sigma\)-p.r.

**(d)** Hay \(\mathcal{P}\in Pro^\Sigma\) tal que \(0\in D_{\Psi_\mathcal{P}^{1,0,\#}}\) y

\[
\Psi_\mathcal{P}^{1,0,\#}(0)=1+\min_t(i^{1,0}(t,0,\mathcal{P})=n(\mathcal{P})+1)
\]

**Ejercicio 7:** (Opcional) Pruebe que la recíproca del Ejercicio 1 no es cierta, es decir de un predicado \(\Sigma\)-recursivo \(P:D_P\subseteq\omega\times\omega^n\times\Sigma^{\ast m}\to\omega\) el cual cumpla que \(M(P)\) es \(\Sigma\)-recursiva y que \(D_P\) no es \(\Sigma\)-recursivo (Hint: tome \(P=C_1^{1,1}|_{\omega\times A}\))

Con los resultados anteriores estamos en condiciones de dar un ejemplo de un predicado \(\Sigma\)-recursivo, cuya minimización no es \(\Sigma\)-efectivamente computable (y por lo tanto no es \(\Sigma\)-recursiva). Aceptaremos el resultado sin demostración.

**Proposición 10.** Supongamos que \(\Sigma\supseteq\Sigma_p\). Sea

\[
P=C_1^{0,1}|_A\circ\lambda t\alpha\left[\alpha^{1\mathbin{\dot{-}}t}\mathrm{SKIP}^t\right]\big|_{\omega\times Pro^\Sigma}.
\]

El predicado \(P\) es \(\Sigma\)-recursivo pero la función \(M(P)\) no es \(\Sigma\)-efectivamente computable (y por lo tanto no es \(\Sigma\)-recursiva).

**Ejercicio 8:** (Opcional) Daremos aquí una guía para probar la proposición anterior.

**(a)** Pruebe que \(P\) es \(\Sigma\)-recursivo

**(b)** Pruebe que \(D_{M(P)}=Pro^\Sigma\)

**(c)** Para cada \(\mathcal{P}\in Pro^\Sigma\) se tiene que

\[
M(P)(\mathcal{P})=0\text{ sii }\mathcal{P}\in A
\]

**(d)** Pruebe que \(AutoHalt^\Sigma=\lambda x[x=0]\circ M(P)\) por lo cual \(M(P)\) no es \(\Sigma\)-recursiva

**(e)** \(M(P)\) no es \(\Sigma\)-efectivamente computable
