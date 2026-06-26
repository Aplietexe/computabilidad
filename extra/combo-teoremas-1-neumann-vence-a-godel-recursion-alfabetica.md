# Teorema: Neumann vence a Godel, caso de recursion alfabetica

**Enunciado.** Si \(h\) es \(\Sigma\)-recursiva, entonces \(h\) es \(\Sigma\)-computable.

**Demostracion.** Probamos por induccion en \(k\) que
\[
(\ast_k)\qquad h\in R_k^\Sigma\Rightarrow h\text{ es }\Sigma\text{-computable}.
\]

Para \(k=0\), las funciones iniciales son computables por programas elementales: \(Suc\) por \(\mathrm{N}1\leftarrow\mathrm{N}1+1\); \(Pred\) por el programa que diverge en \(0\) y decrementa si \(\mathrm{N}1\ne0\); \(C_0^{0,0}\), \(C_\varepsilon^{0,0}\), \(d_a\) y las proyecciones, por asignaciones directas a \(\mathrm{N}1\) o \(\mathrm{P}1\).

Supongamos \((\ast_k)\) y
\[
h=R(f,\mathcal G),\qquad I_h\subseteq\omega,
\]
con
\[
f:S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega
\]
y, para cada \(a\in\Sigma\),
\[
\mathcal G_a:\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times\Sigma^\ast\to\omega
\]
pertenecientes a \(R_k^\Sigma\). Si \(\Sigma=\{a_1,\ldots,a_r\}\), por hipotesis inductiva \(f,\mathcal G_{a_1},\ldots,\mathcal G_{a_r}\) son \(\Sigma\)-computables; por la Proposicion 5 de la Guia 7 (Primer Manantial de Macros), existen sus macros de asignacion.

Consideremos el programa:
\[
\begin{array}{rl}
&[\mathrm{N}\overline{n+1}\leftarrow f(\mathrm{N}1,\ldots,\mathrm{N}\overline n,\mathrm{P}1,\ldots,\mathrm{P}\overline m)]\\
L\overline{r+1}&\mathrm{IF}\ \mathrm{P}\overline{m+1}\ \mathrm{BEGINS}\ a_1\ \mathrm{GOTO}\ L1\\
&\vdots\\
&\mathrm{IF}\ \mathrm{P}\overline{m+1}\ \mathrm{BEGINS}\ a_r\ \mathrm{GOTO}\ L\overline r\\
&\mathrm{GOTO}\ L\overline{r+2}\\
L1&\mathrm{P}\overline{m+1}\leftarrow\curvearrowright\mathrm{P}\overline{m+1}\\
&[\mathrm{N}\overline{n+1}\leftarrow \mathcal G_{a_1}(\mathrm{N}\overline{n+1},\mathrm{N}1,\ldots,\mathrm{N}\overline n,\mathrm{P}1,\ldots,\mathrm{P}\overline m,\mathrm{P}\overline{m+2})]\\
&\mathrm{P}\overline{m+2}\leftarrow\mathrm{P}\overline{m+2}.a_1\\
&\mathrm{GOTO}\ L\overline{r+1}\\
&\vdots\\
L\overline r&\mathrm{P}\overline{m+1}\leftarrow\curvearrowright\mathrm{P}\overline{m+1}\\
&[\mathrm{N}\overline{n+1}\leftarrow \mathcal G_{a_r}(\mathrm{N}\overline{n+1},\mathrm{N}1,\ldots,\mathrm{N}\overline n,\mathrm{P}1,\ldots,\mathrm{P}\overline m,\mathrm{P}\overline{m+2})]\\
&\mathrm{P}\overline{m+2}\leftarrow\mathrm{P}\overline{m+2}.a_r\\
&\mathrm{GOTO}\ L\overline{r+1}\\
L\overline{r+2}&\mathrm{N}1\leftarrow\mathrm{N}\overline{n+1}
\end{array}
\]

Sea la entrada \((\vec x,\vec\alpha,\gamma)\in S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\times\Sigma^\ast\). Despues de la primera linea, y luego de cada vuelta del bucle, vale el invariante:
\[
\gamma=\delta\rho,\qquad \mathrm{P}\overline{m+2}=\delta,\qquad \mathrm{P}\overline{m+1}=\rho,\qquad \mathrm{N}\overline{n+1}=h(\vec x,\vec\alpha,\delta),
\]
manteniendose fijos \(\mathrm{N}1,\ldots,\mathrm{N}\overline n\) y \(\mathrm{P}1,\ldots,\mathrm{P}\overline m\). Inicialmente \(\mathrm{P}\overline{m+2}=\delta=\varepsilon\), \(\rho=\gamma\), y el acumulador vale \(f(\vec x,\vec\alpha)=h(\vec x,\vec\alpha,\varepsilon)\). Si \(\rho=a_i\rho'\), el bloque \(Li\) reemplaza \(\rho\) por \(\rho'\), cambia el acumulador a
\[
\mathcal G_{a_i}(h(\vec x,\vec\alpha,\delta),\vec x,\vec\alpha,\delta)=h(\vec x,\vec\alpha,\delta a_i),
\]
y luego reemplaza \(\delta\) por \(\delta a_i\). Por lo tanto el invariante se preserva. Tras \(|\gamma|\) vueltas se tiene \(\rho=\varepsilon\), el programa sale del bucle y deja en \(\mathrm{N}1\) el valor \(h(\vec x,\vec\alpha,\gamma)\).

Si la entrada no pertenece al dominio de \(h\), la primera macro que queda fuera de su dominio no se detiene; si pertenece, todas las macros usadas estan definidas y el bucle termina. Luego el programa computa \(h\).
