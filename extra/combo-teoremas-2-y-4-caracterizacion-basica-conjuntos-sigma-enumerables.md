# Proposicion 6, guia 7: caso \(n=2,\ m=1\)

**Enunciado.** Sea \(S\subseteq\omega^2\times\Sigma^\ast\) no vacio. Son equivalentes:

**(1)** \(S\) es \(\Sigma\)-enumerable.

**(2)** Existe \(\mathcal P\in Pro^\Sigma\) tal que:

**(a)** para todo \(t\in\omega\), \(\mathcal P\) se detiene desde \(\lVert t\rVert\) y termina en un estado
\[
((x_1,x_2,y_1,\ldots),(\alpha,\beta_1,\ldots))
\]
con \((x_1,x_2,\alpha)\in S\);

**(b)** para todo \((x_1,x_2,\alpha)\in S\), existe \(t\in\omega\) tal que \(\mathcal P\), desde \(\lVert t\rVert\), termina en un estado
\[
((x_1,x_2,y_1,\ldots),(\alpha,\beta_1,\ldots)).
\]

**Demostracion.**

\((1)\Rightarrow(2)\). Sea \(F:\omega\to\omega^2\times\Sigma^\ast\) tal que \(I_F=S\) y
\[
F(t)=(F_{(1)}(t),F_{(2)}(t),F_{(3)}(t)),
\]
donde \(F_{(1)},F_{(2)}:\omega\to\omega\) y \(F_{(3)}:\omega\to\Sigma^\ast\) son \(\Sigma\)-computables. Por el Primer Manantial de Macros existen las asignaciones correspondientes. Tomemos
\[
\mathcal P\equiv
\begin{array}{l}
[\mathrm{P}1\leftarrow F_{(3)}(\mathrm{N}1)]\\
[\mathrm{N}2\leftarrow F_{(2)}(\mathrm{N}1)]\\
[\mathrm{N}1\leftarrow F_{(1)}(\mathrm{N}1)]
\end{array}
\]
con variables auxiliares fuera de \(\mathrm{N}1,\mathrm{N}2,\mathrm{P}1\) y labels auxiliares disjuntos entre expansiones.

Desde \(\lVert t\rVert\), la primera macro deja \(\mathrm{P}1=F_{(3)}(t)\) y preserva \(\mathrm{N}1=t\); la segunda deja \(\mathrm{N}2=F_{(2)}(t)\) y preserva \(\mathrm{N}1,\mathrm{P}1\); la tercera deja \(\mathrm{N}1=F_{(1)}(t)\) y preserva \(\mathrm{N}2,\mathrm{P}1\). Todas terminan porque las componentes de \(F\) son totales. Por lo tanto el estado final tiene primeras coordenadas \(F(t)\in S\), lo que prueba (a). Si \((x_1,x_2,\alpha)\in S=I_F\), existe \(t\) con \(F(t)=(x_1,x_2,\alpha)\); el mismo calculo prueba (b).

\((2)\Rightarrow(1)\). Supongamos que \(\mathcal P\) cumple (a) y (b), y definamos
\[
\mathcal P_1=\mathcal P\ \mathrm{N}1\leftarrow\mathrm{N}1,\qquad
\mathcal P_2=\mathcal P\ \mathrm{N}1\leftarrow\mathrm{N}2,\qquad
\mathcal P_3=\mathcal P\ \mathrm{P}1\leftarrow\mathrm{P}1.
\]
Sean
\[
F_1=\Psi_{\mathcal P_1}^{1,0,\#},\qquad
F_2=\Psi_{\mathcal P_2}^{1,0,\#},\qquad
F_3=\Psi_{\mathcal P_3}^{1,0,\ast}.
\]
Por (a), \(\mathcal P\) se detiene para toda entrada \(t\), luego \(D_{F_i}=\omega\) para \(i=1,2,3\). Ademas cada \(F_i\) es \(\Sigma\)-computable, por estar computada por un programa de \(S^\Sigma\).

Definimos \(F:\omega\to\omega^2\times\Sigma^\ast\) por
\[
F(t)=(F_1(t),F_2(t),F_3(t)).
\]
Si \(\mathcal P\), desde \(\lVert t\rVert\), termina con primeras coordenadas \((x_1,x_2,\alpha)\), entonces \(F(t)=(x_1,x_2,\alpha)\). Por (a), \(F(t)\in S\), asi que \(I_F\subseteq S\). Por (b), cada \((x_1,x_2,\alpha)\in S\) aparece como esas primeras coordenadas para algun \(t\), y entonces es \(F(t)\); por lo tanto \(S\subseteq I_F\). Concluimos \(I_F=S\), y como las tres componentes de \(F\) son \(\Sigma\)-computables, \(S\) es \(\Sigma\)-enumerable. \(\blacksquare\)
