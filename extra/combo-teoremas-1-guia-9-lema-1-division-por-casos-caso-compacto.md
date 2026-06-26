# Lema 1, guia 9: division por casos para funciones \(\Sigma\)-recursivas

**Enunciado (caso).** Supongamos \(f_i:D_{f_i}\subseteq\omega\times\Sigma^\ast\to\omega\), \(i=1,2\), son \(\Sigma\)-recursivas y \(D_{f_1}\cap D_{f_2}=\emptyset\). Entonces \(f_1\cup f_2\) es \(\Sigma\)-recursiva.

**Demostracion.** Por Neumann vence a Godel, sean \(\mathcal P_i\) programas que computan \(f_i\). Para \(i=1,2\), definimos
\[
H_i=\lambda tx\alpha\left[Halt^{1,1}(t,x,\alpha,\mathcal P_i)\right].
\]
Como \(Halt^{1,1}\) es \((\Sigma\cup\Sigma_p)\)-p.r., cada \(H_i\) es \((\Sigma\cup\Sigma_p)\)-p.r.; como \(H_i\) es \(\Sigma\)-mixta, por Independencia del Alfabeto es \(\Sigma\)-p.r. Por el Segundo Manantial hay macros
\[
\left[\mathrm{IF}\ Halt^{1,1}(V1,V2,W1,\mathcal P_i)\ \mathrm{GOTO}\ A1\right]\quad(i=1,2),
\]
y, como \(f_i\) es \(\Sigma\)-recursiva, tambien hay macros
\[
\left[V2\leftarrow f_i(V1,W1)\right]\quad(i=1,2).
\]
Sea \(\mathcal P\) el programa
\[
\begin{array}{rl}
L1 & \mathrm{N}20\leftarrow \mathrm{N}20+1\\
& \left[\mathrm{IF}\ Halt^{1,1}(\mathrm{N}20,\mathrm{N}1,\mathrm{P}1,\mathcal P_1)\ \mathrm{GOTO}\ L2\right]\\
& \left[\mathrm{IF}\ Halt^{1,1}(\mathrm{N}20,\mathrm{N}1,\mathrm{P}1,\mathcal P_2)\ \mathrm{GOTO}\ L3\right]\\
& \mathrm{GOTO}\ L1\\
L2 & \left[\mathrm{N}1\leftarrow f_1(\mathrm{N}1,\mathrm{P}1)\right]\\
& \mathrm{GOTO}\ L4\\
L3 & \left[\mathrm{N}1\leftarrow f_2(\mathrm{N}1,\mathrm{P}1)\right]\\
L4 & \mathrm{SKIP}.
\end{array}
\]
Con entrada \((x,\alpha)\), \(\mathcal P\) prueba sucesivamente si \(\mathcal P_1\) o \(\mathcal P_2\) se detiene en \(t=1,2,\ldots\) pasos sobre \((x,\alpha)\). Si \((x,\alpha)\in D_{f_j}\), entonces \(\mathcal P_j\) se detiene para algun \(t\) y, por la disjuncion de dominios, el otro programa no se detiene sobre esa entrada; por lo tanto \(\mathcal P\) entra en \(Lj\), deja en \(\mathrm{N}1\) el valor \(f_j(x,\alpha)\) y termina. Si \((x,\alpha)\notin D_{f_1}\cup D_{f_2}\), ningun test se activa y \(\mathcal P\) no termina. Asi \(\mathcal P\) computa \(f_1\cup f_2\); luego \(f_1\cup f_2\) es \(\Sigma\)-computable y, por Godel vence a Neumann, \(\Sigma\)-recursiva. \(\blacksquare\)
