# Lema 8, guia 9: \(A\) es \(\Sigma\)-r.e. no \(\Sigma\)-recursivo y \(N\) no es \(\Sigma\)-r.e.

**Enunciado.** Si \(\Sigma\supseteq\Sigma_p\), entonces
\[
A=\{\mathcal P\in Pro^\Sigma:AutoHalt^\Sigma(\mathcal P)=1\}
\]
es \(\Sigma\)-r.e. y no es \(\Sigma\)-recursivo. Mas aun,
\[
N=\{\mathcal P\in Pro^\Sigma:AutoHalt^\Sigma(\mathcal P)=0\}
\]
no es \(\Sigma\)-r.e.

**Demostracion.** Sea
\[
P=\lambda t\mathcal P[Halt^{0,1}(t,\mathcal P,\mathcal P)].
\]
Como \(P\) es \(\Sigma\)-p.r., \(M(P)\) es \(\Sigma\)-recursiva, y
\[
D_{M(P)}=\{\mathcal P\in Pro^\Sigma:\exists t\ Halt^{0,1}(t,\mathcal P,\mathcal P)=1\}=A.
\]
Por lo tanto \(A\) es \(\Sigma\)-r.e.

Si \(N\) fuera \(\Sigma\)-r.e., por el Lema 2 las restricciones \(C_0^{0,1}|_N\) y \(C_1^{0,1}|_A\) serian \(\Sigma\)-recursivas. Como
\[
AutoHalt^\Sigma=C_1^{0,1}|_A\cup C_0^{0,1}|_N
\]
y \(A\cap N=\emptyset\), el lema de division por casos haria a \(AutoHalt^\Sigma\) \(\Sigma\)-recursivo, contradiciendo el Lema 6. Luego \(N\) no es \(\Sigma\)-r.e.

Finalmente, si \(A\) fuera \(\Sigma\)-recursivo, entonces
\[
N=(\Sigma^\ast-A)\cap Pro^\Sigma
\]
tambien seria \(\Sigma\)-recursivo, luego \(\Sigma\)-r.e., contradiccion. Asi \(A\) no es \(\Sigma\)-recursivo. \(\blacksquare\)
