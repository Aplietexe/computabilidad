# Combos de definiciones y convenciones notacionales de la materia Lenguajes formales y computabilidad

**Combo 1.**

$(1)$ Defina cuando un conjunto $S\subseteq\omega^n\times\Sigma^{\ast m}$ es llamado $\Sigma$-recursivo (no hace falta que defina "función $\Sigma$-recursiva")

$(2)$ Defina $\langle s_1,s_2,\ldots\rangle$

$(3)$ Defina "$f$ es una función $\Sigma$-mixta"

$(4)$ Defina "familia $\Sigma$-indexada de funciones"

$(5)$ Defina $R(f,\mathcal{G})$ (haga el caso de valores numéricos)

**Combo 2.** Defina:

$(1)$ $d\overset{n}{\vdash}d'$ y $d\overset{\ast}{\vdash}d'$ (no hace falta que defina $\vdash$)

$(2)$ $L(M)$

$(3)$ "$f$ es una función de tipo $(n,m,s)$"

$(4)$ $(x)$

$(5)$ $(x)_i$

**Combo 3.**

$(1)$ Defina cuando un conjunto $S\subseteq\omega^n\times\Sigma^{\ast m}$ es llamado $\Sigma$-recursivamente enumerable (no hace falta que defina "función $\Sigma$-recursiva")

$(2)$ Defina $s^\le$

$(3)$ Defina $\ast^\le$

$(4)$ Defina $\#^\le$

**Combo 4.** Defina cuando una función $f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\omega$ es llamada $\Sigma$-efectivamente computable y defina "el procedimiento $\mathbb{P}$ computa a la función $f$"

**Combo 5.** Defina cuando un conjunto $S\subseteq\omega^n\times\Sigma^{\ast m}$ es llamado $\Sigma$-efectivamente computable y defina: "el procedimiento efectivo $\mathbb{P}$ decide la pertenencia a $S$"

**Combo 6.** Defina cuando un conjunto $S\subseteq\omega^n\times\Sigma^{\ast m}$ es llamado $\Sigma$-efectivamente enumerable y defina: "el procedimiento efectivo $\mathbb{P}$ enumera a $S$"

**Combo 7.** Defina cuando una función $f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\omega$ es llamada $\Sigma$-Turing computable y defina "la máquina de Turing $M$ computa a la función $f$"

**Combo 8.** Defina:

$(1)$ $M(P)$

$(2)$ $Lt$

$(3)$ Conjunto rectangular

$(4)$ "$S$ es un conjunto de tipo $(n,m)$"

**Combo 9.** Defina:

$(1)$ "$I$ es una instrucción de $S^\Sigma$"

$(2)$ "$\mathcal{P}$ es un programa de $S^\Sigma$"

$(3)$ $I_i^\mathcal{P}$

$(4)$ $n(\mathcal{P})$

$(5)$ $Bas$

**Combo 10.** Defina relativo al lenguaje $S^\Sigma$:

$(1)$ "estado"

$(2)$ "descripción instantánea"

$(3)$ $S_\mathcal{P}$ (dar la definición matemática)

$(4)$ "estado obtenido luego de correr $t$ pasos a $\mathcal{P}$, partiendo del estado $(\overrightarrow{s},\overrightarrow{\sigma})$"

$(5)$ "$\mathcal{P}$ se detiene (luego de $t$ pasos), partiendo desde el estado $(\overrightarrow{s},\overrightarrow{\sigma})$"

**Combo 11.** Defina:

$(1)$ $\Psi_\mathcal{P}^{n,m,\#}$

$(2)$ "$f$ es $\Sigma$-computable"

$(3)$ "$\mathcal{P}$ computa a $f$"

$(4)$ $M^\le(P)$

**Combo 12.** Defina cuando un conjunto $S\subseteq\omega^n\times\Sigma^{\ast m}$ es llamado $\Sigma$-computable, cuando es llamado $\Sigma$-enumerable y defina "el programa $\mathcal{P}$ enumera a $S$"

**Combo 13.** Defina:

$(1)$ $i^{n,m}$

$(2)$ $E_\#^{n,m}$

$(3)$ $E_\ast^{n,m}$

$(4)$ $E_{\#j}^{n,m}$

$(5)$ $E_{\ast j}^{n,m}$

$(6)$ $Halt^{n,m}$

$(7)$ $T^{n,m}$

$(8)$ $AutoHalt^\Sigma$

$(9)$ Los conjuntos $A$ y $N$

**Combo 14.** Explique en forma detallada la notación lambda

**Combo 15.** Dada una función $f:D_f\subseteq\omega\times\Sigma^\ast\to\omega$, describa qué tipo de objeto es y qué propiedades debe tener (cuando exista) el macro:

$$
\left[V2\leftarrow f(V1,W1)\right]
$$

**Combo 16.** Dado un predicado $P:D_f\subseteq\omega\times\Sigma^\ast\to\omega$, describa qué tipo de objeto es y qué propiedades debe tener (cuando exista) el macro:

$$
\left[\mathrm{IF}\ P(V1,W1)\ \mathrm{GOTO}\ A1\right]
$$

**Combo 17.** Defina el concepto de función y desarrolle las tres Convenciones Notacionales asociadas a dicho concepto (Guía 1)

# Combos de teoremas de la materia Lenguajes formales y computabilidad

La siguiente lista contiene 9 combos de resultados de la teoría los cuales serán utilizados para la parte teórica del examen. Algunas observaciones:

$(1)$ Cuando el alumno desarrolle una prueba de un resultado perteneciente a un combo, podrá utilizar un resultado previo sin necesidad de demostrarlo, salvo que justo el combo exija la prueba de dicho resultado. Esto implica, por ejemplo, que se pueden usar en cualquier combo que las funciones suma, producto, etc son $\Sigma$-p.r.

$(2)$ Cuando el alumno aplique algún resultado que no figura en los resultados del combo que está desarrollando, deberá referirse a él en forma descriptivamente clara, preferentemente enunciándolo. Por ejemplo, no vale poner "por Lema 13 de la Guía 5, tenemos que\ldots."

**Combo 1.**

**Proposición (Caracterización de conjuntos $\Sigma$-p.r.).** *Un conjunto $S$ es $\Sigma$-p.r. sii $S$ es el dominio de alguna función $\Sigma$-p.r.*

(En la inducción de la prueba hacer solo el caso de la composición)

**Teorema (Neumann vence a Gödel).** *Si $h$ es $\Sigma$-recursiva, entonces $h$ es $\Sigma$-computable*

(En la inducción de la prueba hacer solo el caso $h=R(f,\mathcal{G})$, con $I_h\subseteq\omega$)

**Combo 2.**

**Lema (Lema de división por casos para funciones $\Sigma$-p.r.).** *Supongamos $f_i:D_{f_i}\subseteq\omega^n\times\Sigma^{\ast m}\to\Sigma^\ast$, $i=1,\ldots,k$, son funciones $\Sigma$-p.r. tales que $D_{f_i}\cap D_{f_j}=\emptyset$ para $i\ne j$. Entonces $f_1\cup\cdots\cup f_k$ es $\Sigma$-p.r.*

(Hacer el caso $k=2$, $n=2$ y $m=1$)

**Proposición (Caracterización básica de conjuntos $\Sigma$-enumerables).** *Sea $S\subseteq\omega^n\times\Sigma^{\ast m}$ un conjunto no vacío. Entonces son equivalentes:*

$(1)$ *$S$ es $\Sigma$-enumerable*

$(2)$ *Hay un programa $\mathcal{P}\in\mathrm{Pro}^\Sigma$ tal que:*

$(a)$ *Para cada $x\in\omega$, tenemos que $\mathcal{P}$ se detiene partiendo desde el estado $\lVert x\rVert$ y llega a un estado de la forma $((x_1,\ldots,x_n,y_1,\ldots),(\alpha_1,\ldots,\alpha_m,\beta_1,\ldots))$, donde $(x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m)\in S$.*

$(b)$ *Para cada $(x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m)\in S$ hay un $x\in\omega$ tal que $\mathcal{P}$ se detiene partiendo desde el estado $\lVert x\rVert$ y llega a un estado de la forma $((x_1,\ldots,x_n,y_1,\ldots),(\alpha_1,\ldots,\alpha_m,\beta_1,\ldots))$*

(Hacer el caso $n=2$ y $m=1$)

**Combo 3.**

**Teorema (Gödel vence a Neumann).** *Si $f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\Sigma^\ast$ es $\Sigma$-computable, entonces $f$ es $\Sigma$-recursiva.*

**Teorema (Caracterización de conjuntos $\Sigma$-efectivamente computables).** *Sea $S\subseteq\omega^n\times\Sigma^{\ast m}$. Son equivalentes*

$(a)$ *$S$ es $\Sigma$-efectivamente computable*

$(b)$ *$S$ y $(\omega^n\times\Sigma^{\ast m})-S$ son $\Sigma$-efectivamente enumerables*

(Haga solo (b) implica (a). La prueba de este resultado está al final de la Guía 3)

**Combo 4.**

**Proposición (Caracterización básica de conjuntos $\Sigma$-enumerables).** *Sea $S\subseteq\omega^n\times\Sigma^{\ast m}$ un conjunto no vacío. Entonces son equivalentes:*

$(1)$ *$S$ es $\Sigma$-enumerable*

$(2)$ *Hay un programa $\mathcal{P}\in\mathrm{Pro}^\Sigma$ tal que:*

$(a)$ *Para cada $x\in\omega$, tenemos que $\mathcal{P}$ se detiene partiendo desde el estado $\lVert x\rVert$ y llega a un estado de la forma $((x_1,\ldots,x_n,y_1,\ldots),(\alpha_1,\ldots,\alpha_m,\beta_1,\ldots))$, donde $(x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m)\in S$.*

$(b)$ *Para cada $(x_1,\ldots,x_n,\alpha_1,\ldots,\alpha_m)\in S$ hay un $x\in\omega$ tal que $\mathcal{P}$ se detiene partiendo desde el estado $\lVert x\rVert$ y llega a un estado de la forma $((x_1,\ldots,x_n,y_1,\ldots),(\alpha_1,\ldots,\alpha_m,\beta_1,\ldots))$*

(Hacer el caso $n=2$ y $m=1$)

**Lema (Lema de la sumatoria).** *Sea $\Sigma$ un alfabeto finito. Si*

$$
f:\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega
$$

*es $\Sigma$-p.r., con $S_1,\ldots,S_n\subseteq\omega$ y $L_1,\ldots,L_m\subseteq\Sigma^\ast$ no vacíos, entonces la función*

$$
\lambda xy\overrightarrow{x}\overrightarrow{\alpha}\left[\sum_{t=x}^{t=y} f(t,\overrightarrow{x},\overrightarrow{\alpha})\right]
$$

*es $\Sigma$-p.r.*

**Combo 5.**

**Lema.** *Sea $\Sigma=\{@,\%,!\}$. Sea*

$$
f:S_1\times S_2\times L_1\times L_2\to\omega
$$

*con $S_1,S_2\subseteq\omega$ y $L_1,L_2\subseteq\Sigma^\ast$ conjuntos no vacíos y sea $\mathcal{G}$ una familia $\Sigma$-indexada de funciones tal que*

$$
\mathcal{G}_a:\omega\times S_1\times S_2\times L_1\times L_2\times\Sigma^\ast\to\omega
$$

*para cada $a\in\Sigma$. Si $f$, $\mathcal{G}_{@}$, $\mathcal{G}_{\%}$ y $\mathcal{G}_{!}$ son $\Sigma$-efectivamente computables, entonces $R(f,\mathcal{G})$ lo es.*

(Es un ejercicio de la Guía 5)

**Lema (Lema de cuantificación acotada).** *Sea $\Sigma$ un alfabeto finito. Sea $P:S\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega$ un predicado $\Sigma$-p.r., con $S,S_1,\ldots,S_n\subseteq\omega$ y $L_1,\ldots,L_m\subseteq\Sigma^\ast$ no vacíos. Supongamos $\overline{S}\subseteq S$ es $\Sigma$-p.r.. Entonces*

$$
\lambda x\overrightarrow{x}\overrightarrow{\alpha}\left[(\forall t\in\overline{S})_{t\le x}\ P(t,\overrightarrow{x},\overrightarrow{\alpha})\right]
$$

*es $\Sigma$-p.r.*

**Combo 6.**

**Lema ($\Sigma$-efectivamente computable implica $\Sigma$-efectivamente enumerable).** *Si $S\subseteq\omega^n\times\Sigma^{\ast m}$ es $\Sigma$-efectivamente computable entonces $S$ es $\Sigma$-efectivamente enumerable.*

**Teorema (Caracterización de conjuntos $\Sigma$-r.e.).** *Dado $S\subseteq\omega^n\times\Sigma^{\ast m}$, son equivalentes*

$(1)$ *$S$ es $\Sigma$-recursivamente enumerable*

$(2)$ *$S=I_F$, para alguna $F:D_F\subseteq\omega^k\times\Sigma^{\ast l}\to\omega^n\times\Sigma^{\ast m}$ tal que cada $F_{(i)}$ es $\Sigma$-recursiva.*

$(3)$ *$S=D_f$, para alguna función $\Sigma$-recursiva $f$*

(Haga solo la prueba de $(2)\Rightarrow(3)$, caso $k=l=1$ y $n=m=2$)

**Combo 7.**

**Lema (Lema de minimización acotada).** *Sean $n,m\ge 0$. Sea $P:D_P\subseteq\omega\times\omega^n\times\Sigma^{\ast m}\to\omega$ un predicado $\Sigma$-p.r.. Entonces*

$(a)$ *$M(P)$ es $\Sigma$-recursiva.*

$(b)$ *Si hay una función $\Sigma$-p.r. $f:\omega^n\times\Sigma^{\ast m}\to\omega$ tal que*

$$
M(P)(\overrightarrow{x},\overrightarrow{\alpha})=\min_t P(t,\overrightarrow{x},\overrightarrow{\alpha})\le f(\overrightarrow{x},\overrightarrow{\alpha}),
\quad\text{para cada }(\overrightarrow{x},\overrightarrow{\alpha})\in D_{M(P)},
$$

*entonces $M(P)$ es $\Sigma$-p.r..*

**Lema.** *Supongamos $f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to O$ es $\Sigma$-recursiva y $S\subseteq D_f$ es $\Sigma$-r.e., entonces $f|_S$ es $\Sigma$-recursiva.*

(Haga solo el caso $S$ no vacío, $n=m=1$ y $O=\Sigma^\ast$)

**Combo 8.**

**Lema.** *Supongamos $\Sigma\supseteq\Sigma_p$. Entonces $AutoHalt^\Sigma$ no es $\Sigma$-recursivo.*

**Teorema.** *Supongamos $\Sigma\supseteq\Sigma_p$. Entonces $AutoHalt^\Sigma$ no es $\Sigma$-efectivamente computable. Es decir no hay ningún procedimiento efectivo que decida si un programa de $S^\Sigma$ termina partiendo de sí mismo.*

**Lema.** *Supongamos que $\Sigma\supseteq\Sigma_p$. Entonces*

$$
A=\{\mathcal{P}\in\mathrm{Pro}^\Sigma:AutoHalt^\Sigma(\mathcal{P})=1\}
$$

*es $\Sigma$-r.e. y no es $\Sigma$-recursivo. Más aún el conjunto*

$$
N=\{\mathcal{P}\in\mathrm{Pro}^\Sigma:AutoHalt^\Sigma(\mathcal{P})=0\}
$$

*no es $\Sigma$-r.e.*

**Teorema (Neumann vence a Gödel).** *Si $h$ es $\Sigma$-recursiva, entonces $h$ es $\Sigma$-computable.*

(En la inducción de la prueba hacer solo el caso $h=M(P)$)

**Combo 9.**

**Lema (Lema de división por casos para funciones $\Sigma$-recursivas).** *Supongamos $f_i:D_{f_i}\subseteq\omega^n\times\Sigma^{\ast m}\to O$, $i=1,\ldots,k$, son funciones $\Sigma$-recursivas tales que $D_{f_i}\cap D_{f_j}=\emptyset$ para $i\ne j$. Entonces la función $f_1\cup\cdots\cup f_k$ es $\Sigma$-recursiva.*

(Haga el caso $k=2$, $n=m=1$ y $O=\omega$)

**Teorema (Gödel vence a Neumann).** *Si $f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\omega$ es $\Sigma$-computable, entonces $f$ es $\Sigma$-recursiva.*
