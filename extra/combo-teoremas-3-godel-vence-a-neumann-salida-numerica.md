# Teorema: Godel vence a Neumann, salida numerica

**Enunciado.** Si \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to\omega\) es \(\Sigma\)-computable, entonces \(f\) es \(\Sigma\)-recursiva.

**Demostracion.** Sea \(\mathcal P_0\in Pro^\Sigma\) un programa que computa a \(f\) y sea \(\Gamma=\Sigma\cup\Sigma_p\). Respecto de \(\Gamma\), definimos
\[
G=
E_{\#1}^{n,m}\circ
\left[
T^{n,m}\circ[p_1^{n,m},\ldots,p_{n+m}^{n,m},C_{\mathcal P_0}^{n,m}],
p_1^{n,m},\ldots,p_{n+m}^{n,m},C_{\mathcal P_0}^{n,m}
\right].
\]
Por la Proposicion 8 de la Guia 8 (\(T^{n,m}\) es \((\Sigma\cup\Sigma_p)\)-recursiva), \(T^{n,m}\) es \(\Gamma\)-recursiva; por la Proposicion 5 de la Guia 8 (las funciones \(E_{\#j}^{n,m}\) y \(E_{\ast j}^{n,m}\) son \((\Sigma\cup\Sigma_p)\)-p.r.), \(E_{\#1}^{n,m}\) es \(\Gamma\)-p.r.; y proyecciones y constantes son \(\Gamma\)-p.r. Luego \(G\) es \(\Gamma\)-recursiva.

Ademas,
\[
D_G=\{(\vec x,\vec\alpha)\in\omega^n\times\Sigma^{\ast m}:\mathcal P_0\text{ se detiene desde }\lVert\vec x,\vec\alpha\rVert\}=D_f.
\]
Entonces
\[
G(\vec x,\vec\alpha)
=E_{\#1}^{n,m}(T^{n,m}(\vec x,\vec\alpha,\mathcal P_0),\vec x,\vec\alpha,\mathcal P_0)
=\Psi_{\mathcal P_0}^{n,m,\#}(\vec x,\vec\alpha)
=f(\vec x,\vec\alpha).
\]
Asi \(G=f\), luego \(f\) es \(\Gamma\)-recursiva. Como \(f\) es \(\Sigma\)-mixta y \(\Gamma\)-mixta, por el Teorema de Independencia del Alfabeto citado en la Guia 8, \(f\) es \(\Sigma\)-recursiva. \(\blacksquare\)
