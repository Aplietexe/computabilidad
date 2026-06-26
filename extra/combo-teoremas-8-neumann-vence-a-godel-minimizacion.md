# Teorema 1, guia 8: Neumann vence a Godel, caso \(h=M(P)\)

**Enunciado.** Si \(h\) es \(\Sigma\)-recursiva, entonces \(h\) es \(\Sigma\)-computable.

**Demostracion (caso \(h=M(P)\)).** Probamos por induccion en \(k\) que
\[
(\ast_k)\qquad h\in R_k^\Sigma\Rightarrow h\text{ es }\Sigma\text{-computable}.
\]
Supongamos \((\ast_k)\) y \(h=M(P)\), con
\[
P:\omega\times\omega^n\times\Sigma^{\ast m}\to\omega
\]
un predicado en \(R_k^\Sigma\). Por hipotesis inductiva, \(P\) es \(\Sigma\)-computable; luego existe el macro
\[
\left[\mathrm{IF}\ P(V1,\ldots,V\overline{n+1},W1,\ldots,W\overline m)\ \mathrm{GOTO}\ A1\right].
\]
Consideremos el programa
\[
\begin{array}{rl}
L2 & \left[\mathrm{IF}\ P(\mathrm{N}\overline{n+1},\mathrm{N}1,\ldots,\mathrm{N}\overline n,\mathrm{P}1,\ldots,\mathrm{P}\overline m)\ \mathrm{GOTO}\ L1\right]\\
& \mathrm{N}\overline{n+1}\leftarrow \mathrm{N}\overline{n+1}+1\\
& \mathrm{GOTO}\ L2\\
L1 & \mathrm{N}1\leftarrow \mathrm{N}\overline{n+1}.
\end{array}
\]
Con entrada \((\vec x,\vec\alpha)\), el registro \(\mathrm{N}\overline{n+1}\) recorre \(t=0,1,2,\ldots\); como \(P\) es total, cada test termina, y el programa se detiene exactamente en el menor \(t\) tal que \(P(t,\vec x,\vec\alpha)=1\), dejando ese valor en \(\mathrm{N}1\). Si no existe tal \(t\), no se detiene. Por lo tanto computa \(M(P)=h\). \(\blacksquare\)
