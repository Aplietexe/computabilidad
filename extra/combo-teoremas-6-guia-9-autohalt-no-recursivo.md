# Lema 6, guia 9: \(AutoHalt^\Sigma\) no es \(\Sigma\)-recursivo

**Enunciado.** Si \(\Sigma\supseteq\Sigma_p\), entonces \(AutoHalt^\Sigma\) no es \(\Sigma\)-recursivo.

**Demostracion.** Recordemos que, para todo \(\mathcal P\in Pro^\Sigma\),
\[
(*)\quad AutoHalt^\Sigma(\mathcal P)=1\Longleftrightarrow \mathcal P\text{ se detiene partiendo del estado }\lVert\mathcal P\rVert.
\]
Supongamos que \(AutoHalt^\Sigma\) es \(\Sigma\)-recursivo. Por el Segundo Manantial existe el macro
\[
\left[\mathrm{IF}\ AutoHalt^\Sigma(W1)\ \mathrm{GOTO}\ A1\right].
\]
Sea \(\mathcal P_0\) el programa de \(S^\Sigma\)
\[
L1\ \left[\mathrm{IF}\ AutoHalt^\Sigma(\mathrm{P}1)\ \mathrm{GOTO}\ L1\right].
\]
Al partir de \(\lVert\mathcal P_0\rVert\), \(\mathrm{P}1\) contiene \(\mathcal P_0\), de modo que \(\mathcal P_0\) termina sii \(AutoHalt^\Sigma(\mathcal P_0)=0\): si vale \(1\), vuelve a \(L1\); si vale \(0\), no salta y termina. Esto contradice \((*)\) aplicado a \(\mathcal P=\mathcal P_0\). Por lo tanto \(AutoHalt^\Sigma\) no es \(\Sigma\)-recursivo. \(\blacksquare\)
