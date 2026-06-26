# Lema 5, guia 6: minimizacion acotada

**Enunciado.** Sea \(E=\omega^n\times\Sigma^{\ast m}\). Si
\[
P:D_P\subseteq\omega\times E\to\omega
\]
es un predicado \(\Sigma\)-p.r., entonces \(M(P)\) es \(\Sigma\)-recursiva. Si ademas existe \(f:E\to\omega\) \(\Sigma\)-p.r. tal que
\[
M(P)(e)=\min_tP(t,e)\le f(e)\qquad(e\in D_{M(P)}),
\]
entonces \(M(P)\) es \(\Sigma\)-p.r.

**Demostracion.** Definimos
\[
\overline P=P\cup C_0^{n+1,m}|_{(\omega\times E)-D_P}.
\]
Como \(P\) es \(\Sigma\)-p.r., \(D_P\) y \((\omega\times E)-D_P\) son \(\Sigma\)-p.r.; por restriccion y division por casos, \(\overline P\) es \(\Sigma\)-p.r. y \(\Sigma\)-total. Ademas, para todo \(e\in E\),
\[
\{t:P(t,e)=1\}=\{t:\overline P(t,e)=1\},
\]
luego \(M(P)=M(\overline P)\).

Para **(a)**, si \(\overline P\in PR_k^\Sigma\), entonces \(\overline P\in R_k^\Sigma\); como es total, \(M(\overline P)\in R_{k+1}^\Sigma\). Luego \(M(P)\in R^\Sigma\).

Para **(b)** basta probar que \(M(\overline P)\) es \(\Sigma\)-p.r. Sea \(D=D_{M(\overline P)}\). Por la cota \(f\),
\[
\chi_D^E(e)=[(\exists t\in\omega)_{t\le f(e)}\overline P(t,e)]
\]
y, equivalentemente,
\[
\chi_D^E=
\lambda x\overrightarrow{x}\overrightarrow{\alpha}
[(\exists t\in\omega)_{t\le x}\overline P(t,\overrightarrow{x},\overrightarrow{\alpha})]
\circ[f,p_1^{n,m},\ldots,p_{n+m}^{n,m}].
\]
El Lema de cuantificacion acotada da que \(D\) es \(\Sigma\)-p.r.

Sea
\[
P_1=\lambda t\overrightarrow{x}\overrightarrow{\alpha}
[\overline P(t,\overrightarrow{x},\overrightarrow{\alpha})\land
(\forall j\in\omega)_{j\le t}(j=t\lor\neg\overline P(j,\overrightarrow{x},\overrightarrow{\alpha}))].
\]
Por clausura booleana y cuantificacion acotada, \(P_1\) es \(\Sigma\)-p.r.; ademas
\[
P_1(t,e)=1\Longleftrightarrow e\in D\text{ y }t=M(\overline P)(e).
\]
Sea
\[
q=\lambda t\overrightarrow{x}\overrightarrow{\alpha}
[t^{P_1(t,\overrightarrow{x},\overrightarrow{\alpha})}].
\]
Como la exponenciacion es \(\Sigma\)-p.r., \(q\) es \(\Sigma\)-p.r. Por el Lema de la sumatoria/productoria,
\[
G=\lambda xy\overrightarrow{x}\overrightarrow{\alpha}
\left[\prod_{t=x}^{y}q(t,\overrightarrow{x},\overrightarrow{\alpha})\right]
\]
es \(\Sigma\)-p.r.; por composicion, tambien lo es
\[
F=G\circ[C_0^{n,m},f,p_1^{n,m},\ldots,p_{n+m}^{n,m}].
\]
Si \(e\in D\), hay un unico \(r\le f(e)\) con \(P_1(r,e)=1\), y para todo \(t\ne r\), \(P_1(t,e)=0\); usando \(u^0=1\), al evaluar la composicion anterior se obtiene \(F(e)=r=M(\overline P)(e)\). Entonces
\[
M(\overline P)=F|_D.
\]
Como \(D\) es \(\Sigma\)-p.r., por restriccion \(F|_D\) es \(\Sigma\)-p.r. Por \(M(P)=M(\overline P)\), \(M(P)\) es \(\Sigma\)-p.r. \(\blacksquare\)
