# Lema 23, guia 5: caso de la sumatoria

**Enunciado.** Sea \(\Sigma\) un alfabeto finito. Si
\[
f:\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\to\omega
\]
es \(\Sigma\)-p.r., con \(S_i\subseteq\omega\) y \(L_j\subseteq\Sigma^\ast\) no vacios, entonces
\[
\lambda xy\overrightarrow{x}\overrightarrow{\alpha}\left[\sum_{t=x}^{t=y} f(t,\overrightarrow{x},\overrightarrow{\alpha})\right]
\]
es \(\Sigma\)-p.r.

**Demostracion.** Definimos
\[
G=\lambda tx\overrightarrow{x}\overrightarrow{\alpha}\left[\sum_{i=x}^{i=t}f(i,\overrightarrow{x},\overrightarrow{\alpha})\right].
\]
Omitimos las listas vacias de variables o proyecciones cuando \(n=0\) o \(m=0\).
Como la funcion del enunciado satisface
\[
\lambda xy\overrightarrow{x}\overrightarrow{\alpha}\left[\sum_{t=x}^{t=y} f(t,\overrightarrow{x},\overrightarrow{\alpha})\right]
=G\circ[p_2^{n+2,m},p_1^{n+2,m},p_3^{n+2,m},\ldots,p_{n+m+2}^{n+2,m}],
\]
basta probar que \(G\) es \(\Sigma\)-p.r.

Sean \(B=\omega\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\) y
\(C=\omega^3\times S_1\times\cdots\times S_n\times L_1\times\cdots\times L_m\). Como \(f\) es \(\Sigma\)-p.r.,
\(B=D_f\) es \(\Sigma\)-p.r. por la Proposicion 20 de la Guia 5 (caracterizacion de conjuntos \(\Sigma\)-p.r. como dominios); por el Lema 17 de la Guia 5 (caracterizacion de productos \(\Sigma\)-p.r.) tambien lo son los \(S_i,L_j\), y entonces \(C\) es \(\Sigma\)-p.r. Definimos
\[
\begin{aligned}
D_1&=\{(x,\overrightarrow{x},\overrightarrow{\alpha})\in B:x>0\},&
D_2&=\{(x,\overrightarrow{x},\overrightarrow{\alpha})\in B:x=0\},\\
H_1&=\{(A,t,x,\overrightarrow{x},\overrightarrow{\alpha})\in C:x>t+1\},&
H_2&=\{(A,t,x,\overrightarrow{x},\overrightarrow{\alpha})\in C:x\le t+1\}.
\end{aligned}
\]
Estos cuatro conjuntos son \(\Sigma\)-p.r., pues se obtienen intersectando \(B\) o \(C\) con predicados numericos \(\Sigma\)-p.r.; ademas \(D_1,D_2\) particionan \(B\), y \(H_1,H_2\) particionan \(C\).

Ahora ponemos
\[
h=C_0^{n+1,m}|_{D_1}\cup
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[f(0,\overrightarrow{x},\overrightarrow{\alpha})]|_{D_2},
\]
\[
g=C_0^{n+3,m}|_{H_1}\cup
\lambda Atx\overrightarrow{x}\overrightarrow{\alpha}[A+f(t+1,\overrightarrow{x},\overrightarrow{\alpha})]|_{H_2}.
\]
Las funciones sin restringir que aparecen aqui son \(\Sigma\)-p.r. por composicion:
\[
\lambda x\overrightarrow{x}\overrightarrow{\alpha}[f(0,\overrightarrow{x},\overrightarrow{\alpha})]
=f\circ[C_0^{n+1,m},p_2^{n+1,m},\ldots,p_{n+m+1}^{n+1,m}],
\]
\[
\lambda Atx\overrightarrow{x}\overrightarrow{\alpha}[A+f(t+1,\overrightarrow{x},\overrightarrow{\alpha})]
=\lambda uv[u+v]\circ
[p_1^{n+3,m},f\circ[Suc\circ p_2^{n+3,m},p_4^{n+3,m},\ldots,p_{n+m+3}^{n+3,m}]].
\]
Por el Lema 18 de la Guia 5 (restriccion de una funcion \(\Sigma\)-p.r. a un dominio \(\Sigma\)-p.r.), sus restricciones a \(D_1,D_2,H_1,H_2\) son \(\Sigma\)-p.r.; por el Lema 21 de la Guia 5 (division por casos para funciones \(\Sigma\)-p.r., usando el caso \(O=\omega\)), \(h\) y \(g\) son \(\Sigma\)-p.r.

Por definicion de suma,
\[
G(0,x,\overrightarrow{x},\overrightarrow{\alpha})=h(x,\overrightarrow{x},\overrightarrow{\alpha}),\qquad
G(t+1,x,\overrightarrow{x},\overrightarrow{\alpha})
=g(G(t,x,\overrightarrow{x},\overrightarrow{\alpha}),t,x,\overrightarrow{x},\overrightarrow{\alpha}).
\]
Luego \(G=R(h,g)\), asi que \(G\) es \(\Sigma\)-p.r. por clausura por recursion primitiva. En consecuencia, la funcion del enunciado es \(\Sigma\)-p.r. por composicion.
