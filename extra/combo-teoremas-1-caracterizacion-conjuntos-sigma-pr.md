# Proposicion 20, guia 5

**Enunciado.** Sea \(S\subseteq\omega^n\times\Sigma^{\ast m}\). Entonces \(S\) es \(\Sigma\)-p.r. sii \(S=D_F\) para alguna funcion \(\Sigma\)-p.r. \(F\).

**Demostracion.**

\((\Rightarrow)\) Si \(S\) es \(\Sigma\)-p.r., entonces \(\chi_S^{\omega^n\times\Sigma^{\ast m}}\) es \(\Sigma\)-p.r. Luego
\[
F=Pred\circ\chi_S^{\omega^n\times\Sigma^{\ast m}}
\]
es \(\Sigma\)-p.r. y, como \(D_{Pred}=\mathbf N=\omega-\{0\}\),
\[
e\in D_F \Longleftrightarrow \chi_S^{\omega^n\times\Sigma^{\ast m}}(e)=1 \Longleftrightarrow e\in S.
\]
Por lo tanto \(D_F=S\).

\((\Leftarrow)\) Basta probar que toda funcion \(\Sigma\)-p.r. tiene dominio \(\Sigma\)-p.r. Lo hacemos por induccion en \(k\) para \(F\in PR_k^\Sigma\). Para \(k=0\), los dominios de las funciones iniciales
\[
Suc,\ Pred,\ C_0^{0,0},\ C_\varepsilon^{0,0},\ d_a,\ p_j^{n,m}
\]
son \(\omega\), \(\mathbf N\), \(\{\diamond\}\), \(\Sigma^\ast\) o \(\omega^n\times\Sigma^{\ast m}\), todos \(\Sigma\)-p.r.

Supongamos probado para \(PR_k^\Sigma\):
\[
F=g\circ[g_1,\ldots,g_r],\qquad g,g_1,\ldots,g_r\in PR_k^\Sigma.
\]
Si \(F=\emptyset\), entonces \(D_F=\emptyset\) es \(\Sigma\)-p.r. Si no, por el Lema 1 de la Guia 5 (lema de composicion de funciones \(\Sigma\)-mixtas), \(r=a+b\) y existen \(p,q\in\omega\) tales que
\[
g:D_g\subseteq\omega^a\times\Sigma^{\ast b}\to O,\qquad
g_i:D_{g_i}\subseteq\omega^p\times\Sigma^{\ast q}\to
\begin{cases}
\omega,&i\le a,\\
\Sigma^\ast,&i>a.
\end{cases}
\]
Por hipotesis inductiva, \(D_g,D_{g_1},\ldots,D_{g_{a+b}}\) son \(\Sigma\)-p.r.; luego tambien
\[
T=\bigcap_{i=1}^{a+b}D_{g_i}
\]
lo es. Por el Lema 19 de la Guia 5 (extension total de funciones \(\Sigma\)-p.r.), existen extensiones totales \(\Sigma\)-p.r. \(\overline g_i:\omega^p\times\Sigma^{\ast q}\to\omega\) para \(i\le a\) y \(\overline g_i:\omega^p\times\Sigma^{\ast q}\to\Sigma^\ast\) para \(i>a\), con \(\overline g_i|_{D_{g_i}}=g_i\). Entonces, para todo \(e\in\omega^p\times\Sigma^{\ast q}\),
\[
e\in D_F \Longleftrightarrow e\in T\ \land\ (\overline g_1(e),\ldots,\overline g_{a+b}(e))\in D_g.
\]
Equivalente:
\[
\chi_{D_F}^{\omega^p\times\Sigma^{\ast q}}=\chi_T^{\omega^p\times\Sigma^{\ast q}}\land\left(\chi_{D_g}^{\omega^a\times\Sigma^{\ast b}}\circ[\overline g_1,\ldots,\overline g_{a+b}]\right).
\]
El lado derecho es \(\Sigma\)-p.r. por clausura por composicion y conectivos booleanos; por lo tanto \(D_F\) es \(\Sigma\)-p.r. Los otros constructores del paso inductivo se verifican desde la forma de sus dominios. En consecuencia, si \(S=D_F\) para alguna \(F\) \(\Sigma\)-p.r., entonces \(S\) es \(\Sigma\)-p.r.
