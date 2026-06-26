# Lema: recursion alfabetica preserva computabilidad efectiva

**Enunciado.** Sea \(\Sigma=\{@,\%,!\}\). Sea
\[
f:S_1\times S_2\times L_1\times L_2\to\omega
\]
con \(S_1,S_2\subseteq\omega\) y \(L_1,L_2\subseteq\Sigma^\ast\) conjuntos no vacios, y sea \(\mathcal{G}\) una familia \(\Sigma\)-indexada de funciones tal que
\[
\mathcal{G}_a:\omega\times S_1\times S_2\times L_1\times L_2\times\Sigma^\ast\to\omega
\]
para cada \(a\in\Sigma\). Si \(f\), \(\mathcal{G}_{@}\), \(\mathcal{G}_{\%}\) y \(\mathcal{G}_{!}\) son \(\Sigma\)-efectivamente computables, entonces \(R(f,\mathcal{G})\) lo es.

**Demostracion.** Sean \(\mathbb P_f,\mathbb P_{@},\mathbb P_{\%}\) y \(\mathbb P_{!}\) procedimientos efectivos que computan respectivamente a
\[
f,\qquad \mathcal G_{@},\qquad \mathcal G_{\%},\qquad \mathcal G_{!}.
\]
Construimos un procedimiento efectivo \(\mathbb P\) que computa a \(R(f,\mathcal G)\).

Dado el dato de entrada \((x_1,x_2,\alpha_1,\alpha_2,\gamma)\in\omega^2\times\Sigma^{\ast 3}\), el procedimiento \(\mathbb P\) es el siguiente:

Etapa 1: Correr \(\mathbb P_f\) con dato de entrada \((x_1,x_2,\alpha_1,\alpha_2)\) y guardar la salida en \(Y\). Hacer \(B=\varepsilon\) e ir a Etapa 2.

Etapa 2: Si \(B=\gamma\), dar \(Y\) como salida y terminar. En caso contrario, escribir \(\gamma=Ba\delta\), con \(a\in\{@,\%,!\}\), y proceder asi: si \(a=@\), ir a Etapa 3; si \(a=\%\), ir a Etapa 4; si \(a=!\), ir a Etapa 5.

Etapa 3: Correr \(\mathbb P_{@}\) con dato de entrada \((Y,x_1,x_2,\alpha_1,\alpha_2,B)\), guardar la salida en \(Y\), hacer \(B=B@\) e ir a Etapa 2.

Etapa 4: Correr \(\mathbb P_{\%}\) con dato de entrada \((Y,x_1,x_2,\alpha_1,\alpha_2,B)\), guardar la salida en \(Y\), hacer \(B=B\%\) e ir a Etapa 2.

Etapa 5: Correr \(\mathbb P_{!}\) con dato de entrada \((Y,x_1,x_2,\alpha_1,\alpha_2,B)\), guardar la salida en \(Y\), hacer \(B=B!\) e ir a Etapa 2.

Veamos que \(\mathbb P\) computa a \(R(f,\mathcal G)\). Si \((x_1,x_2,\alpha_1,\alpha_2,\gamma)\in S_1\times S_2\times L_1\times L_2\times\Sigma^\ast\), la Etapa 1 termina y deja
\[
Y=f(x_1,x_2,\alpha_1,\alpha_2)=R(f,\mathcal G)(x_1,x_2,\alpha_1,\alpha_2,\varepsilon).
\]
Luego, cada vuelta por las Etapas 2--5 preserva el invariante
\[
Y=R(f,\mathcal G)(x_1,x_2,\alpha_1,\alpha_2,B),
\]
pues si la proxima letra es \(a\), la subrutina correspondiente devuelve
\[
\mathcal G_a(Y,x_1,x_2,\alpha_1,\alpha_2,B)
=R(f,\mathcal G)(x_1,x_2,\alpha_1,\alpha_2,Ba).
\]
Como \(\gamma\) es finita, eventualmente \(B=\gamma\), y la Etapa 2 devuelve \(R(f,\mathcal G)(x_1,x_2,\alpha_1,\alpha_2,\gamma)\).

Si \((x_1,x_2,\alpha_1,\alpha_2,\gamma)\notin S_1\times S_2\times L_1\times L_2\times\Sigma^\ast\), entonces \((x_1,x_2,\alpha_1,\alpha_2)\notin D_f\). Por lo tanto \(\mathbb P_f\) no se detiene en la Etapa 1, y \(\mathbb P\) tampoco se detiene. Concluimos que \(R(f,\mathcal G)\) es \(\Sigma\)-efectivamente computable.
