# Teorema: \(AutoHalt^\Sigma\) no es \(\Sigma\)-efectivamente computable

**Enunciado.** Supongamos \(\Sigma\supseteq\Sigma_p\). Entonces \(AutoHalt^\Sigma\) no es \(\Sigma\)-efectivamente computable. Es decir no hay ningun procedimiento efectivo que decida si un programa de \(S^\Sigma\) termina partiendo de si mismo.

**Demostracion.** Si \(AutoHalt^\Sigma\) fuera \(\Sigma\)-efectivamente computable, por la Tesis de Church seria \(\Sigma\)-recursivo, contradiciendo el lema de la Guia 9 que afirma que \(AutoHalt^\Sigma\) no es \(\Sigma\)-recursivo. Por lo tanto, \(AutoHalt^\Sigma\) no es \(\Sigma\)-efectivamente computable. \(\blacksquare\)
