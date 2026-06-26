# Lema 2, guia 3

**Enunciado.** Si \(S\subseteq\omega^n\times\Sigma^{\ast m}\) es \(\Sigma\)-efectivamente computable, entonces \(S\) es \(\Sigma\)-efectivamente enumerable.

**Demostracion.** Supongamos \(S \ne \emptyset\). Sea \((\overrightarrow{z}, \overrightarrow{\gamma}) \in S\), fijo. Sea \(\mathbb{P}\) un procedimiento efectivo que compute a \(\chi_S^{\omega^n \times \Sigma^{\ast m}}\). Ya vimos en el ejemplo anterior que \(\omega^2 \times \Sigma^{\ast 3}\) es \(\Sigma\)-efectivamente enumerable. En forma similar se puede ver que \(\omega^n \times \Sigma^{\ast m}\) lo es. Sea \(\mathbb{P}_1\) un procedimiento efectivo que enumere a \(\omega^n \times \Sigma^{\ast m}\). Entonces el siguiente procedimiento enumera a \(S\):

Dato de entrada: \(x \in \omega\)

Etapa 1: Realizar \(\mathbb{P}_1\) con \(x\) de entrada para obtener como salida un \((\overrightarrow{x}, \overrightarrow{\alpha}) \in \omega^n \times \Sigma^{\ast m}\).

Etapa 2: Realizar \(\mathbb{P}\) con \((\overrightarrow{x}, \overrightarrow{\alpha})\) de entrada para obtener el valor Booleano \(e\) de salida.

Etapa 3: Si \(e = 1\) dar como dato de salida \((\overrightarrow{x}, \overrightarrow{\alpha})\). Si \(e = 0\) dar como dato de salida \((\overrightarrow{z}, \overrightarrow{\gamma})\). \(\blacksquare\)
