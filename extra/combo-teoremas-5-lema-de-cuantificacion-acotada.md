# Lema 24, guia 5: caso \(\forall\) numerico

**Enunciado.** Sea \(\Sigma\) un alfabeto finito y sea
\[
P:S\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega
\]
un predicado \(\Sigma\)-p.r., con \(S,S_1,\ldots,S_n\subseteq\omega\) y \(L_1,\ldots,L_m\subseteq\Sigma^\ast\) todos no vacios. Si \(\overline S\subseteq S\) es \(\Sigma\)-p.r., entonces
\[
Q=\lambda x\overrightarrow{x}\overrightarrow{\alpha}[(\forall t\in\overline S)_{t\le x}P(t,\overrightarrow{x},\overrightarrow{\alpha})]
\]
es \(\Sigma\)-p.r.

**Demostracion.** Sea
\[
A=S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m
\]
(omitiendo las listas vacias, como siempre). Definimos
\[
\widetilde P=P|_{\overline S\times A}\cup C_1^{1+n,m}|_{(\omega-\overline S)\times A}.
\]
Entonces \(D_{\widetilde P}=\omega\times A\) y
\[
\widetilde P(t,\overrightarrow{x},\overrightarrow{\alpha})=\begin{cases}P(t,\overrightarrow{x},\overrightarrow{\alpha})&\text{si }t\in\overline S,\\1&\text{si }t\notin\overline S.\end{cases}
\]
Como \(P\) es \(\Sigma\)-p.r., \(D_P=S\times A\) es \(\Sigma\)-p.r.; por el Lema 17, los factores de \(A\) son \(\Sigma\)-p.r. Luego \(\overline S\times A\) y \((\omega-\overline S)\times A\) son \(\Sigma\)-p.r. (usando tambien clausura por complemento para \(\omega-\overline S\); si \(\overline S=\emptyset\), el primer conjunto es vacio). Por el Lema 18, las dos restricciones que definen \(\widetilde P\) son \(\Sigma\)-p.r.; como sus dominios son disjuntos, el Lema 21 implica que \(\widetilde P\) es \(\Sigma\)-p.r.

Por el caso de la productoria del Lema 23,
\[
H=\lambda xy\overrightarrow{x}\overrightarrow{\alpha}\left[\prod_{t=x}^{t=y}\widetilde P(t,\overrightarrow{x},\overrightarrow{\alpha})\right]
\]
es \(\Sigma\)-p.r. Para \((x,\overrightarrow{x},\overrightarrow{\alpha})\in\omega\times A\), como \(\widetilde P\) solo toma valores \(0,1\),
\[
H(0,x,\overrightarrow{x},\overrightarrow{\alpha})=1\Longleftrightarrow\forall t\le x\ \widetilde P(t,\overrightarrow{x},\overrightarrow{\alpha})=1\Longleftrightarrow\forall t\in\overline S\ (t\le x\Rightarrow P(t,\overrightarrow{x},\overrightarrow{\alpha})=1).
\]
Por la definicion de cuantificacion acotada,
\[
Q=H\circ[C_0^{1+n,m},p_1^{1+n,m},\ldots,p_{1+n+m}^{1+n,m}],
\]
y por clausura por composicion concluimos que \(Q\) es \(\Sigma\)-p.r.
