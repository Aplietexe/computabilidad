# Combo 2

## Defina $d\overset{n}{\vdash}d'$ (no hace falta definir $\vdash$)

Para $d,d^{\prime}\in Des$ y $n\ge0$, escribiremos $d\overset{n}{\vdash}d^{\prime}$ si existen $d_1,\ldots,d_{n+1}\in Des$ tales que

$$
\begin{aligned}
d & =d_1\\
d^{\prime} & =d_{n+1}\\
d_i & \vdash d_{i+1}\text{, para }i=1,\ldots,n.
\end{aligned}
$$

## Defina $L(M)$

Diremos que una palabra $\alpha\in\Sigma^\ast$ es aceptada por $M$ por alcance de estado final cuando

$$
\left\lfloor q_0B\alpha\right\rfloor \overset{\ast}{\vdash}d\text{, con }d\text{ tal que }St(d)\in F.
$$

El lenguaje aceptado por $M$ por alcance de estado final se define de la siguiente manera

$$
L(M)=\{\alpha\in\Sigma^\ast:\alpha\text{ es aceptada por }M\text{ por alcance de estado final}\}\text{.}
$$

## Defina $H(M)$

Diremos que una palabra $\alpha\in\Sigma^\ast$ es aceptada por $M$ por detención cuando $M$ se detiene partiendo de $\left\lfloor q_0B\alpha\right\rfloor$. El lenguaje aceptado por $M$ por detención se define de la siguiente manera

$$
H(M)=\{\alpha\in\Sigma^\ast:\alpha\text{ es aceptada por }M\text{ por detención}\}
$$

## Defina "$f$ es una función de tipo $(n,m,s)$"

Dada una función $\Sigma$-mixta $f$, si $n,m\in\omega$ son tales que $D_f\subseteq\omega^n\times\Sigma^{\ast m}$ y además $I_f\subseteq\omega$, entonces diremos que $f$ es una función de tipo $(n,m,\#)$. Similarmente si $n,m\in\omega$ son tales que $D_f\subseteq\omega^n\times\Sigma^{\ast m}$ y además $I_f\subseteq\Sigma^\ast$, entonces diremos que $f$ es una función de tipo $(n,m,\ast)$.

## Defina $(x)$

Dado $x\in\mathbf{N}$, usaremos $(x)$ para denotar a la única infinitupla $(s_1,s_2,\ldots)\in\omega^{[\mathbf{N}]}$ tal que

$$
x=\left\langle s_1,s_2,\ldots\right\rangle =\prod_{i=1}^{\infty}pr(i)^{s_i}
$$

## Defina $(x)_{i}$

Para $i\in\mathbf{N}$, usaremos $(x)_{i}$ para denotar a $s_i$ de dicha infinitupla (la del anterior punto). Se le suele llamar la "bajada $i$-ésima de $x$" al número $(x)_{i}$. La idea de este nombre es que para obtener $(x)_{i}$ debemos bajar el exponente de $pr(i)$ en la factorización de $x$
