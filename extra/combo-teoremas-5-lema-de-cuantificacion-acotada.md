# Lema: cuantificacion acotada universal numerica para predicados \(\Sigma\)-p.r.

**Enunciado.** Sea \(\Sigma\) un alfabeto finito. Sea
\[
P:S\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega
\]
un predicado \(\Sigma\)-p.r., con \(S,S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) no vacios. Supongamos \(\overline S\subseteq S\) es \(\Sigma\)-p.r. Entonces
\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\forall t\in\overline S)_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]
\]
es \(\Sigma\)-p.r.

**Demostracion.** Sea
\[
A=S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m
\]
Definimos
\[
\widetilde P=P|_{\overline S\times A}\cup C_1^{1+n,m}|_{(\omega-\overline S)\times A}.
\]
Entonces \(D_{\widetilde P}=\omega\times A\) y
\[
\widetilde P(t,\overrightarrow{x},\overrightarrow{\alpha})=\begin{cases}P(t,\overrightarrow{x},\overrightarrow{\alpha})&\text{si }t\in\overline S,\\1&\text{si }t\notin\overline S.\end{cases}
\]
Como \(P\) es \(\Sigma\)-p.r., \(D_P=S\times A\) es \(\Sigma\)-p.r. por la Proposicion 20 de la Guia 5 (caracterizacion de conjuntos \(\Sigma\)-p.r. como dominios); por el Lema 17 de la Guia 5 (caracterizacion de productos \(\Sigma\)-p.r.), los factores de \(A\) son \(\Sigma\)-p.r. Luego \(\overline S\times A\) y \((\omega-\overline S)\times A\) son \(\Sigma\)-p.r. (usando el Lema 16 de la Guia 5 para el complemento \(\omega-\overline S\); si \(\overline S=\emptyset\), el primer conjunto es vacio). Por el Lema 18 de la Guia 5 (restriccion de una funcion \(\Sigma\)-p.r. a un dominio \(\Sigma\)-p.r.), las dos restricciones que definen \(\widetilde P\) son \(\Sigma\)-p.r.; como sus dominios son disjuntos, el Lema 21 de la Guia 5 (division por casos para funciones \(\Sigma\)-p.r., usando el caso \(O=\omega\)) implica que \(\widetilde P\) es \(\Sigma\)-p.r.

Por el inciso (a) del Lema 23 de la Guia 5 (sumatoria y productoria de funciones \(\Sigma\)-p.r.; la guia acepta sin prueba el caso de la productoria),
\[
H=\lambda xy\overrightarrow{x}\overrightarrow{\alpha}\left[\prod_{t=x}^{t=y}\widetilde P(t,\overrightarrow{x},\overrightarrow{\alpha})\right]
\]
es \(\Sigma\)-p.r. Para \((x,\overrightarrow{x},\overrightarrow{\alpha})\in\omega\times A\), como \(\widetilde P\) solo toma valores \(0,1\),
\[
H(0,x,\overrightarrow{x},\overrightarrow{\alpha})=1\Longleftrightarrow\forall t\le x\ \widetilde P(t,\overrightarrow{x},\overrightarrow{\alpha})=1\Longleftrightarrow\forall t\in\overline S\ (t\le x\Rightarrow P(t,\overrightarrow{x},\overrightarrow{\alpha})=1).
\]
Por la definicion de cuantificacion acotada, la funcion del enunciado satisface
\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\forall t\in\overline S)_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]
=H\circ[C_0^{1+n,m},p_1^{1+n,m},\ldots,p_{1+n+m}^{1+n,m}],
\]
y por clausura por composicion concluimos que es \(\Sigma\)-p.r.
