# Teorema 9, guia 8: caso \(O=\Sigma^\ast\)

**Enunciado.** Si \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\Sigma^\ast\) es \(\Sigma\)-computable, entonces \(f\) es \(\Sigma\)-recursiva.

**Demostracion.** Sea \(\mathcal P_0\in Pro^\Sigma\) un programa que computa a \(f\) y sea \(\Gamma=\Sigma\cup\Sigma_p\). Respecto de \(\Gamma\), definimos
\[
G=
E_{\ast1}^{n,m}\circ
\left[
T^{n,m}\circ[p_1^{n,m},\ldots,p_{n+m}^{n,m},C_{\mathcal P_0}^{n,m}],
p_1^{n,m},\ldots,p_{n+m}^{n,m},C_{\mathcal P_0}^{n,m}
\right].
\]
Por Proposiciones 8 y 5, y porque proyecciones y constantes son \(\Gamma\)-p.r., \(G\) es \(\Gamma\)-recursiva.

Ademas,
\[
D_G=\{(\vec x,\vec\alpha)\in\omega^n\times\Sigma^{\ast m}:\mathcal P_0\text{ se detiene desde }\lVert\vec x,\vec\alpha\rVert\}=D_f.
\]
Si \(t=T^{n,m}(\vec x,\vec\alpha,\mathcal P_0)\), entonces
\[
G(\vec x,\vec\alpha)
=E_{\ast1}^{n,m}(t,\vec x,\vec\alpha,\mathcal P_0)
=\Psi_{\mathcal P_0}^{n,m,\ast}(\vec x,\vec\alpha)
=f(\vec x,\vec\alpha).
\]
Luego \(G=f\), asi que \(f\) es \(\Gamma\)-recursiva. Como \(f\) es \(\Sigma\)-mixta y \(\Gamma\)-mixta, por Independencia del Alfabeto \(f\) es \(\Sigma\)-recursiva. \(\blacksquare\)
