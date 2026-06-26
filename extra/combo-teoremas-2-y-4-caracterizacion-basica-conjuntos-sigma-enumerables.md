# Proposicion 6, guia 7: caso \(n=2,\ m=1\)

**Enunciado.** Sea \(S\subseteq\omega^2\times\Sigma^\ast\) no vacio. Son equivalentes:

**(1)** \(S\) es \(\Sigma\)-enumerable.

**(2)** Hay un programa \(\mathcal P\in\mathrm{Pro}^\Sigma\) tal que:

**(a)** Para cada \(x\in\omega\), tenemos que \(\mathcal P\) se detiene partiendo desde el estado \(\lVert x\rVert\) y llega a un estado de la forma
\[
((x_1,x_2,y_1,\ldots),(\alpha_1,\beta_1,\ldots))
\]
donde \((x_1,x_2,\alpha_1)\in S\);

**(b)** Para cada \((x_1,x_2,\alpha_1)\in S\) hay un \(x\in\omega\) tal que \(\mathcal P\) se detiene partiendo desde el estado \(\lVert x\rVert\) y llega a un estado de la forma
\[
((x_1,x_2,y_1,\ldots),(\alpha_1,\beta_1,\ldots)).
\]

**Demostracion.**

\((1)\Rightarrow(2)\). Sea \(F:\omega\to\omega^2\times\Sigma^\ast\) tal que \(I_F=S\) y
\[
F(x)=(F_{(1)}(x),F_{(2)}(x),F_{(3)}(x)),
\]
donde \(F_{(1)},F_{(2)}:\omega\to\omega\) y \(F_{(3)}:\omega\to\Sigma^\ast\) son \(\Sigma\)-computables. Por la Proposicion 5 de la Guia 7 (Primer Manantial de Macros) existen las asignaciones correspondientes. Tomemos
\[
\mathcal P\equiv
\begin{array}{l}
[\mathrm{P}1\leftarrow F_{(3)}(\mathrm{N}1)]\\
[\mathrm{N}2\leftarrow F_{(2)}(\mathrm{N}1)]\\
[\mathrm{N}1\leftarrow F_{(1)}(\mathrm{N}1)]
\end{array}
\]
con variables auxiliares fuera de \(\mathrm{N}1,\mathrm{N}2,\mathrm{P}1\) y labels auxiliares disjuntos entre expansiones.

Desde \(\lVert x\rVert\), la primera macro deja \(\mathrm{P}1=F_{(3)}(x)\) y preserva \(\mathrm{N}1=x\); la segunda deja \(\mathrm{N}2=F_{(2)}(x)\) y preserva \(\mathrm{N}1,\mathrm{P}1\); la tercera deja \(\mathrm{N}1=F_{(1)}(x)\) y preserva \(\mathrm{N}2,\mathrm{P}1\). Todas terminan porque las componentes de \(F\) son totales. Por lo tanto el estado final tiene primeras coordenadas \(F(x)\in S\), lo que prueba (a). Si \((x_1,x_2,\alpha_1)\in S=I_F\), existe \(x\in\omega\) con \(F(x)=(x_1,x_2,\alpha_1)\); el mismo calculo prueba (b).

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
Por (a), \(\mathcal P\) se detiene para toda entrada \(x\), luego \(D_{F_i}=\omega\) para \(i=1,2,3\). Ademas cada \(F_i\) es \(\Sigma\)-computable, por estar computada por un programa de \(S^\Sigma\).

Definimos \(F:\omega\to\omega^2\times\Sigma^\ast\) por
\[
F(x)=(F_1(x),F_2(x),F_3(x)).
\]
Si \(\mathcal P\), desde \(\lVert x\rVert\), termina con primeras coordenadas \((x_1,x_2,\alpha_1)\), entonces \(F(x)=(x_1,x_2,\alpha_1)\). Por (a), \(F(x)\in S\), asi que \(I_F\subseteq S\). Por (b), cada \((x_1,x_2,\alpha_1)\in S\) aparece como esas primeras coordenadas para algun \(x\in\omega\), y entonces es \(F(x)\); por lo tanto \(S\subseteq I_F\). Concluimos \(I_F=S\), y como las tres componentes de \(F\) son \(\Sigma\)-computables, \(S\) es \(\Sigma\)-enumerable. \(\blacksquare\)
