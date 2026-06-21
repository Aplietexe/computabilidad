# Combo 1

## 1. Defina cuando un conjunto $S\subseteq\omega^n\times\Sigma^{\ast m}$ es llamado $\Sigma$-recursivo

(no hace falta que defina "función Σ-recursiva")

Un conjunto $S\subseteq\omega^n\times\Sigma^{\ast m}$ es llamado $\Sigma$-recursivo si y solo si su función característica $\chi_S^{\omega^n\times\Sigma^{\ast m}}$ es $\Sigma$-recursiva.

## 2. Defina $\langle s_1,s_2,\ldots\rangle$

Usamos $\langle s_1,s_2,\ldots\rangle$ para denotar al número $\prod_{i=1}^{\infty}pr(i)^{s_i}$.

## 3. Definición de función $\Sigma$-mixta

Sea $\Sigma$ un alfabeto finito. Dada una función $f$, diremos que $f$ es $\Sigma$-mixta si

cumple las siguientes propiedades

1. Existen $n,m\ge0$, tales que $D_f\subseteq\omega^n\times\Sigma^{\ast m}$

2. Ya sea $I_f\subseteq\omega$ o $I_f\subseteq\Sigma^\ast$

## 4. Defina "familia $\Sigma$-indexada de funciones"

Dado un alfabeto $\Sigma$, una familia $\Sigma$-indexada de funciones será una función $\mathcal{G}$ tal que $D_{\mathcal{G}}=\Sigma$ y para cada $a\in D_{\mathcal{G}}$ se tiene que $\mathcal{G}(a)$ es una función.

## 5. Defina $R(f,\mathcal{G})$ (caso de valores numéricos)

Sea

$$
f:S_1\times\ldots\times S_n\times L_1\times\ldots\times L_m\to\omega
$$

con $S_1,\ldots,S_n\subseteq\omega$ y $L_1,\ldots,L_m\subseteq\Sigma^\ast$ conjuntos no vacíos y sea $\mathcal{G}$ una familia $\Sigma$-indexada de funciones tal que

$$
\mathcal{G}_a:\omega\times S_1\times\ldots\times S_n\times L_1\times\ldots\times L_m\times\Sigma^\ast\to\omega
$$

para cada $a\in\Sigma$. Definamos

$$
R(f,\mathcal{G}):S_1\times\ldots\times S_n\times L_1\times\ldots\times L_m\times\Sigma^\ast\to\omega
$$

de la siguiente manera

1. $R(f,\mathcal{G})(\overrightarrow{x},\overrightarrow{\alpha},\varepsilon)=f(\overrightarrow{x},\overrightarrow{\alpha})$

2. $R(f,\mathcal{G})(\overrightarrow{x},\overrightarrow{\alpha},\alpha a)=\mathcal{G}_a(R(f,\mathcal{G})(\overrightarrow{x},\overrightarrow{\alpha},\alpha),\overrightarrow{x},\overrightarrow{\alpha},\alpha)$

Diremos que $R(f,\mathcal{G})$ es obtenida por recursión primitiva a partir de $f$ y $\mathcal{G}.$
