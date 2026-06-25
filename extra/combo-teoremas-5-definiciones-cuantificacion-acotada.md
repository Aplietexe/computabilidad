# Definiciones formales para cuantificacion acotada

## Variable numerica cuantificada

Sean

\[
P:S\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega
\]

un predicado, con \(S,S_1,\ldots,S_n\subseteq\omega\) y
\(L_1,\ldots,L_m\subseteq\Sigma^\ast\). Sea \(\overline{S}\subseteq S\).

Definimos

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}
[(\forall t\in\overline{S})_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]
\]

como el predicado de dominio

\[
\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m
\]

tal que, para cada \((x,\overrightarrow{x},\overrightarrow{\alpha})\) en ese
dominio,

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}
[(\forall t\in\overline{S})_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]
(x,\overrightarrow{x},\overrightarrow{\alpha})=1
\]

si y solo si

\[
\forall t\in\overline{S}\ (t\le x\Rightarrow
P(t,\overrightarrow{x},\overrightarrow{\alpha})=1).
\]

En caso contrario, el valor es \(0\).

Analogamente,

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}
[(\exists t\in\overline{S})_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]
\]

es el predicado con el mismo dominio que vale \(1\) en
\((x,\overrightarrow{x},\overrightarrow{\alpha})\) si y solo si

\[
\exists t\in\overline{S}\ (t\le x\land
P(t,\overrightarrow{x},\overrightarrow{\alpha})=1),
\]

y vale \(0\) en caso contrario.

La condicion \(\overline{S}\subseteq S\) garantiza que todos los valores de
\(P\) mencionados estan definidos. Ademas, la cota \(t\le x\) hace que la
cuantificacion recorra un conjunto finito.

## Variable alfabetica cuantificada

Sean

\[
P:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times L\to\omega
\]

un predicado, con \(S_1,\ldots,S_n\subseteq\omega\) y
\(L_1,\ldots,L_m,L\subseteq\Sigma^\ast\). Sea \(\overline{L}\subseteq L\).

Definimos

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}
[(\forall\beta\in\overline{L})_{|\beta|\le x}
P(\overrightarrow{x},\overrightarrow{\alpha},\beta)]
\]

como el predicado de dominio

\[
\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m
\]

tal que, para cada \((x,\overrightarrow{x},\overrightarrow{\alpha})\) en ese
dominio,

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}
[(\forall\beta\in\overline{L})_{|\beta|\le x}
P(\overrightarrow{x},\overrightarrow{\alpha},\beta)]
(x,\overrightarrow{x},\overrightarrow{\alpha})=1
\]

si y solo si

\[
\forall\beta\in\overline{L}\ (|\beta|\le x\Rightarrow
P(\overrightarrow{x},\overrightarrow{\alpha},\beta)=1).
\]

En caso contrario, el valor es \(0\).

Analogamente,

\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}
[(\exists\beta\in\overline{L})_{|\beta|\le x}
P(\overrightarrow{x},\overrightarrow{\alpha},\beta)]
\]

es el predicado con el mismo dominio que vale \(1\) en
\((x,\overrightarrow{x},\overrightarrow{\alpha})\) si y solo si

\[
\exists\beta\in\overline{L}\ (|\beta|\le x\land
P(\overrightarrow{x},\overrightarrow{\alpha},\beta)=1),
\]

y vale \(0\) en caso contrario.

La condicion \(\overline{L}\subseteq L\) garantiza que todos los valores de
\(P\) mencionados estan definidos. Ademas, como \(\Sigma\) es finito, la cota
\(|\beta|\le x\) hace que la cuantificacion recorra un conjunto finito.
