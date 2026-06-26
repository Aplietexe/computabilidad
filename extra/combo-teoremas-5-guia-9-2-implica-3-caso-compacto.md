# Teorema 5, guia 9: \((2)\Rightarrow(3)\), caso \(k=l=1\), \(n=m=2\)

**Demostracion.** Supongamos \(S\subseteq\omega^2\times\Sigma^{\ast2}\) y
\[
F:D_F\subseteq\omega\times\Sigma^\ast\to\omega^2\times\Sigma^{\ast2}
\]
con \(I_F=S\) y \(F_{(1)},F_{(2)},F_{(3)},F_{(4)}\) \(\Sigma\)-recursivas. Para cada \(i\in\{1,2,3,4\}\), sea \(\mathcal P_i\) un programa que computa \(F_{(i)}\), y sea \(\le\) un orden total sobre \(\Sigma\).

Definimos, para \(i=1,2,3,4\),
\[
H_i=\lambda tx_1\alpha_1\left[\neg Halt^{1,1}(t,x_1,\alpha_1,\mathcal P_i)\right].
\]
Para \(i=1,2\), definimos
\[
E_i=\lambda xtx_1\alpha_1\left[x\ne E_{\#1}^{1,1}(t,x_1,\alpha_1,\mathcal P_i)\right],
\]
y para \(i=3,4\),
\[
E_i=\lambda tx_1\alpha_1\alpha\left[\alpha\ne E_{\ast1}^{1,1}(t,x_1,\alpha_1,\mathcal P_i)\right].
\]
Las \(H_i\) tienen dominio \(\omega^2\times\Sigma^\ast\). Por el resultado de la Guia 8 que afirma que \(Halt^{n,m}\) es \((\Sigma\cup\Sigma_p)\)-p.r., cada \(H_i\) es \((\Sigma\cup\Sigma_p)\)-p.r.; como \(H_i\) es \(\Sigma\)-mixta, por el Teorema de Independencia del Alfabeto de la Guia 8 es \(\Sigma\)-p.r. Por el resultado de la Guia 8 que afirma que \(E_{\#j}^{n,m}\) y \(E_{\ast j}^{n,m}\) son \((\Sigma\cup\Sigma_p)\)-p.r., las \(E_i\) son \((\Sigma\cup\Sigma_p)\)-p.r.; como son \(\Sigma\)-mixtas, por el mismo Teorema de Independencia del Alfabeto son \(\Sigma\)-p.r. Ademas, \(\lambda x[(x)_1]\), \(\lambda x[(x)_2]\) y \(\lambda x[\ast^\le((x)_3)]\) son \(\Sigma\)-p.r. porque las funciones de bajada \((x)_j\) y \(\ast^\le\) son \(\Sigma\)-p.r.

Por el Segundo Manantial de Macros (todo predicado o funcion \(\Sigma\)-recursiva tiene el macro correspondiente), existen los macros de test para \(H_i\) y \(E_i\), que escribiremos, respectivamente, como
\[
\left[\mathrm{IF}\ \neg Halt^{1,1}(V2,V1,W1,\mathcal P_i)\ \mathrm{GOTO}\ A1\right]\quad(i=1,2,3,4),
\]
\[
\left[\mathrm{IF}\ V2\ne E_{\#1}^{1,1}(V3,V1,W1,\mathcal P_i)\ \mathrm{GOTO}\ A1\right]\quad(i=1,2),
\]
\[
\left[\mathrm{IF}\ W2\ne E_{\ast1}^{1,1}(V2,V1,W1,\mathcal P_i)\ \mathrm{GOTO}\ A1\right]\quad(i=3,4).
\]
Tambien existen los macros de asignacion
\[
\left[V2\leftarrow(V1)_1\right],\qquad
\left[V2\leftarrow(V1)_2\right],\qquad
\left[W1\leftarrow\ast^\le((V1)_3)\right].
\]

Sea \(\mathcal P\) el siguiente programa de \(S^\Sigma\):
\[
\begin{array}{rl}
L1 & \mathrm{N}20\leftarrow \mathrm{N}20+1\\
& \left[\mathrm{N}10\leftarrow(\mathrm{N}20)_1\right]\\
& \left[\mathrm{N}3\leftarrow(\mathrm{N}20)_2\right]\\
& \left[\mathrm{P}3\leftarrow \ast^\le((\mathrm{N}20)_3)\right]\\
& \left[\mathrm{IF}\ \neg Halt^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal P_1)\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \neg Halt^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal P_2)\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \neg Halt^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal P_3)\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \neg Halt^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal P_4)\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \mathrm{N}1\ne E_{\#1}^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal P_1)\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \mathrm{N}2\ne E_{\#1}^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal P_2)\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \mathrm{P}1\ne E_{\ast1}^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal P_3)\ \mathrm{GOTO}\ L1\right]\\
& \left[\mathrm{IF}\ \mathrm{P}2\ne E_{\ast1}^{1,1}(\mathrm{N}10,\mathrm{N}3,\mathrm{P}3,\mathcal P_4)\ \mathrm{GOTO}\ L1\right].
\end{array}
\]

En cada vuelta, \(\mathrm{N}20\) toma un valor \(q\in\mathbf N\) y al variar \(q\) se consideran todos los \((t,u,\beta)\in\omega^2\times\Sigma^\ast\). La vuelta correspondiente a \((t,u,\beta)\) no vuelve a \(L1\) sii
\[
Halt^{1,1}(t,u,\beta,\mathcal P_i)=1\quad(i=1,2,3,4),
\]
\[
x_1=E_{\#1}^{1,1}(t,u,\beta,\mathcal P_1),\quad
x_2=E_{\#1}^{1,1}(t,u,\beta,\mathcal P_2),
\]
\[
\alpha_1=E_{\ast1}^{1,1}(t,u,\beta,\mathcal P_3),\quad
\alpha_2=E_{\ast1}^{1,1}(t,u,\beta,\mathcal P_4).
\]
Como \(\mathcal P_i\) computa \(F_{(i)}\), el programa \(\mathcal P\) se detiene sobre \((x_1,x_2,\alpha_1,\alpha_2)\) sii existe \((u,\beta)\in D_F\) tal que
\[
F(u,\beta)=(x_1,x_2,\alpha_1,\alpha_2),
\]
es decir, sii \((x_1,x_2,\alpha_1,\alpha_2)\in I_F=S\). En tal caso la salida numerica es \(\mathrm{N}1=x_1\). Por lo tanto \(\mathcal P\) computa \(p_1^{2,2}|_S\); entonces \(p_1^{2,2}|_S\) es \(\Sigma\)-computable y, por el teorema Godel vence a Neumann de la Guia 8 (toda funcion \(\Sigma\)-computable es \(\Sigma\)-recursiva), es \(\Sigma\)-recursiva. Como \(D_{p_1^{2,2}|_S}=S\), queda probado \((3)\). \(\blacksquare\)
