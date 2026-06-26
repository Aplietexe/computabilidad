# Lema: restriccion de funciones \(\Sigma\)-recursivas a conjuntos \(\Sigma\)-r.e.

**Enunciado.** Supongamos \(f:D_f\subseteq\omega^n\times\Sigma^{\ast m}\to O\) es \(\Sigma\)-recursiva y \(S\subseteq D_f\) es \(\Sigma\)-r.e., entonces \(f|_S\) es \(\Sigma\)-recursiva.

**Demostracion (caso \(S\) no vacio, \(n=m=1\) y \(O=\Sigma^\ast\)).** Como \(S\ne\emptyset\), existe
\[
F:\omega\to\omega\times\Sigma^\ast
\]
tal que \(I_F=S\) y \(F_{(1)},F_{(2)}\) son \(\Sigma\)-recursivas. Por el Segundo Manantial hay macros
\[
\begin{array}{c}
\left[W2\leftarrow f(V1,W1)\right]\\
\left[V2\leftarrow F_{(1)}(V1)\right]\\
\left[W1\leftarrow F_{(2)}(V1)\right].
\end{array}
\]
Como \(D=\lambda xy[x\ne y]\) y \(D'=\lambda\alpha\beta[\alpha\ne\beta]\) son \(\Sigma\)-p.r., tambien hay macros
\[
\begin{array}{c}
\left[\mathrm{IF}\ V1\ne V2\ \mathrm{GOTO}\ A1\right]\\
\left[\mathrm{IF}\ W1\ne W2\ \mathrm{GOTO}\ A1\right].
\end{array}
\]
Sea \(\mathcal P\) el programa
\[
\begin{array}{rl}
L2 & \left[\mathrm{N}2\leftarrow F_{(1)}(\mathrm{N}20)\right]\\
& \left[\mathrm{P}2\leftarrow F_{(2)}(\mathrm{N}20)\right]\\
& \left[\mathrm{IF}\ \mathrm{N}1\ne \mathrm{N}2\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \mathrm{P}1\ne \mathrm{P}2\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{P}1\leftarrow f(\mathrm{N}1,\mathrm{P}1)\right]\\
& \mathrm{GOTO}\ L3\\
L1 & \mathrm{N}20\leftarrow \mathrm{N}20+1\\
& \mathrm{GOTO}\ L2\\
L3 & \mathrm{SKIP}.
\end{array}
\]
Con entrada \((x,\alpha)\), \(\mathcal P\) recorre \(q=0,1,2,\ldots\) en \(\mathrm{N}20\). En la vuelta \(q\) calcula \(F(q)\); si \(F(q)\ne(x,\alpha)\), vuelve a \(L1\). Si \(F(q)=(x,\alpha)\), ejecuta \(f(x,\alpha)\) y termina. Por lo tanto, si \((x,\alpha)\in S=I_F\), algun \(q\) coincide y, como \(S\subseteq D_f\), la salida es \(f(x,\alpha)\); si \((x,\alpha)\notin S\), ningun \(q\) coincide y el programa no termina. Asi \(\mathcal P\) computa \(f|_S\), luego \(f|_S\) es \(\Sigma\)-computable y, por Godel vence a Neumann, \(\Sigma\)-recursiva. \(\blacksquare\)
