# Teorema 3, guia 3: solo \((a)\Rightarrow(b)\)

**Enunciado.** Sea \(S\subseteq\omega^n\times\Sigma^{\ast m}\). Si \(S\) es \(\Sigma\)-efectivamente computable, entonces \(S\) y \((\omega^n\times\Sigma^{\ast m})-S\) son \(\Sigma\)-efectivamente enumerables.

**Demostracion.** Como \(S\) es \(\Sigma\)-efectivamente computable, existe un procedimiento efectivo \(\mathbb P\) que, para toda entrada \(e\in\omega^n\times\Sigma^{\ast m}\), termina y devuelve
\[
\chi_S^{\omega^n\times\Sigma^{\ast m}}(e)=
\begin{cases}
1&\text{si }e\in S,\\
0&\text{si }e\notin S.
\end{cases}
\]
Por el Lema 2, \(S\) es \(\Sigma\)-efectivamente enumerable.

Ademas, \((\omega^n\times\Sigma^{\ast m})-S\) tambien es \(\Sigma\)-efectivamente computable: basta usar el procedimiento que corre \(\mathbb P\) sobre \(e\) y, si la salida es \(1\), devuelve \(0\), mientras que si la salida es \(0\), devuelve \(1\). Este procedimiento termina siempre y computa \(\chi_{(\omega^n\times\Sigma^{\ast m})-S}^{\omega^n\times\Sigma^{\ast m}}\). Aplicando nuevamente el Lema 2, \((\omega^n\times\Sigma^{\ast m})-S\) es \(\Sigma\)-efectivamente enumerable. \(\blacksquare\)
