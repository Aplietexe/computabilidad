# Teorema 3, guia 3: solo \((b)\Rightarrow(a)\)

**Enunciado.** Sea \(S \subseteq \omega^n \times \Sigma^{\ast m}\). Son equivalentes

**(a)** \(S\) es \(\Sigma\)-efectivamente computable

**(b)** \(S\) y \((\omega^n \times \Sigma^{\ast m}) - S\) son \(\Sigma\)-efectivamente enumerables

**Demostracion de \((b)\Rightarrow(a)\).** Sea \(E=\omega^n\times\Sigma^{\ast m}\). Si \(S=\emptyset\) o \(S=E\), \(\chi_S^E\) es respectivamente constante \(0\) o constante \(1\), luego es \(\Sigma\)-efectivamente computable.

Supongamos entonces \(S\ne\emptyset\) y \(E-S\ne\emptyset\). Por el Lema 1, existen procedimientos efectivos \(\mathbb P_1\) y \(\mathbb P_2\) que enumeran respectivamente a \(S\) y \(E-S\). Definimos el siguiente procedimiento:

Dato de entrada: \((\overrightarrow{x},\overrightarrow{\alpha})\in E\).

Etapa 1

Darle a la variable \(T\) el valor \(0\).

Etapa 2

Realizar \(\mathbb P_1\) con el valor de \(T\) como entrada para obtener de salida \((\overrightarrow{y},\overrightarrow{\beta})\).

Etapa 3

Realizar \(\mathbb P_2\) con el valor de \(T\) como entrada para obtener de salida \((\overrightarrow{z},\overrightarrow{\gamma})\).

Etapa 4

Si \((\overrightarrow{y},\overrightarrow{\beta})=(\overrightarrow{x},\overrightarrow{\alpha})\), detenerse y dar como dato de salida \(1\). Si \((\overrightarrow{z},\overrightarrow{\gamma})=(\overrightarrow{x},\overrightarrow{\alpha})\), detenerse y dar como dato de salida \(0\). Si no sucede ninguna de las dos posibilidades, aumentar en \(1\) el valor de \(T\) y dirigirse a la Etapa 2.

Este procedimiento es efectivo. Ademas termina: como \((\overrightarrow{x},\overrightarrow{\alpha})\in S\cup(E-S)\), alguno de los dos enumeradores lo produce para cierto \(T_0\), y en la Etapa 4 correspondiente se detiene. La salida es correcta porque \(\mathbb P_1\) solo enumera elementos de \(S\) y \(\mathbb P_2\) solo enumera elementos de \(E-S\). Luego computa \(\chi_S^E\), y \(S\) es \(\Sigma\)-efectivamente computable. \(\blacksquare\)
